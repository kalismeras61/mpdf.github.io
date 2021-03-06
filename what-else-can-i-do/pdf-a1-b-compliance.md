---
layout: page
title: PDF/A1-b compliance
parent_title: What Else Can I Do
permalink: /what-else-can-i-do/pdf-a1-b-compliance.html
modification_time: 2015-08-05T12:00:20+00:00
---

(mPDF >= 4.3)

PDF/A1-b is a file format for the long-term archiving of electronic documents. It is based on the PDF Reference Version 1.4 from Adobe Systems Inc. and is defined by ISO 19005-1:2005

A key element to this reproducibility is the requirement for PDF/A documents to be 100% self-contained. All of the information necessary for displaying the document in the same manner every time is embedded in the file. This includes, but is not limited to, all content (text, raster images and vector graphics), fonts, and color information. A PDF/A document is not permitted to be reliant on information from external sources (e.g. font programs and hyperlinks).

Other key elements to PDF/A compatibility include:

<ul>
<li>All fonts must be embedded and also must be legally embeddable for unlimited, universal rendering. This also applies to the Adobe standard fonts such as Times, Courier or Helvetica.</li>
<li>Colorspaces specified in a device-independent manner.</li>
<li>Encryption is not allowed.</li>
<li>Use of standards-based metadata is mandated.</li>
<li>PDF Version must be specified as 1.4</li>
</ul>

The standard specifies two levels of compliance for PDF files:

<ul>
<li>PDF/A-1a - Level A compliance in Part 1</li>
<li>PDF/A-1b - Level B compliance in Part 1</li>
</ul>

PDF/A-1b has the objective of ensuring reliable reproduction of the visual appearance of the document. PDF/A-1a includes all the requirements of PDF/A-1b and additionally requires that document structure be included (also known as being "tagged"), with the objective of ensuring that document content can be searched and repurposed.

A PDF/A document can be identified as such through PDF/A-specific metadata located in the "http://www.aiim.org/pdfa/ns/id/" namespace. However, claiming to be PDF/A and being so are not necessarily the same.

**Important**: mPDF is ***not guaranteed ***to produce fully PDF/A1-b compliant files in all circumstances. It is the users responsibility to check compliance if this is essential.

# mPDF and PDF/A1-b compliance

You can make mPDF produce mPDF/A1-b compliant files by setting:

{% highlight php %}
<?php

$this->PDFA = true; // Edit in config.php or set at runtime
{% endhighlight %}

Some changes were made in mPDF 4.3 which affect all files (PDF/A or not) to improve compliance with PDF-1.4 specification:

<ul>
<li>file version changed to PDF-1.4*</li>
<li>newline removed at end of file after %%EOF</li>
<li>an /ID object is added to the PDF trailer (this is optional in PDF-1.4. spec.) when the file is not encrypted</li>
<li>a binary file marker  (consisting of a comment line with 4 characters &gt; 127 ASCII) is added just after the first line (recommended n PDF-1.4 spec.)</li>
</ul>

* *The PDF file version was changed to 1.5 in previous versions when 'active forms were introduced as an experiment'. These are no longer viable, and the rest of mPDF generated files meet 1.4 specification.*

## Colorspaces and ICC Profiles

PDF files handle colours internally in a number of different colorspaces. PDFA files must have one defined (and embedded) colour profile for one colorspace.

The 3 colour RGB colorspace is used most commonly in PDF/A documents, although you could select a 4-colour CMYK colorspace - but you cannot use both together, and SPOT colours are not permitted. RGB colorpsace is the default in mPDF for a PDF/A1-b document.

It is likely that most content in a PDF file will be RGB unless you have specifically defined otherwise e.g. a CMYK JPG image file, or colours defined as CMYK() etc.

Colorspaces can be altered - see <a href="{{ "/reference/mpdf-variables/restrictcolorspace.html" | prepend: site.baseurl }}">restrictColorSpace</a>.

An ICC Color profile must be embedded in the file.

<ul> </li>
</ul>

The ICC Color profile will likely change the appearance of colours in your document. The ICC profile that is included with mPDF is an open licence color profile from the International Color Consortium (http://www.color.org) which seems to change colours a little as possible for an sRGB profile. Other sources of free ICC profiles are:

<ul>
<li><a href="http://www.eci.org/">http://www.eci.org</a></li>
<li><a href="http://www.color.org/profiles2.xalter">http://www.color.org/profiles2.xalter </a></li>
<li><a href="http://www.adobe.com/support/downloads/iccprofiles/iccprofiles_win.html">http://www.adobe.com/support/downloads/iccprofiles/iccprofiles_win.html </a></li>
</ul>

You can change the color profile used by mPDF by adding a  <span class="filename">*.icc</span> file to the <span class="filename">[mpdf]/iccprofiles/</span> folder. Then edit <span class="filename">config.php</span> e.g.

{% highlight php %}
<?php

$this->ICCProfile = 'eciRGB_v2';
{% endhighlight %}

## Fonts

All fonts must be embedded in a PDF/A file. mPDF normally uses the core Adobe fonts (Helvetica, Times, Courier, Symbol and Zapfdingbats) in a number of situations, and these font files are not available to embed. This affects:

<ul>
<li><span class="parameter">$useCoreFontsOnly</span> is not permitted</li>
<li>lists `&lt;ul&gt;` cannot use Zapfdingbats font for bullets</li>
<li>form element `&lt;select&gt;` cannot use Zapfdingbats character as the drop-down symbol</li>
<li>ISBN/ISSN barcode cannot use Helvetica for the ISBN number (above the bar)</li>
</ul>

Also, the fonts GB, BIG5, UHC and SJIS which reference the free CJK font pack from Adobe cannot be used

## Transparency and Annotations

Because PDF/A-1b has the objective of ensuring reliable reproduction of the visual appearance of the document, no objects may be transparent or semi-transparent. This affects:

<ul>
<li>watermarks text or images</li>
<li>images with the CSS property <span class="parameter">$opacity</span> set</li>
<li>annotation markers</li>
</ul>

# Making it happen!

When `$this->PDFA` is set to true, the following changes will automatically and silently happen:

<ul>
<li>list bullets will use the characters from the current font (if available) e.g. • ⚬ ▪ </li>
<li>the default font (which in some circumstances is set to a core Adobe font) is set to an alternative embedded font</li>
<li>annotations (including hyperlinks) have their 'flag' changed to /F 28 which should force printing (this seems to make no difference but is required for PDFA compliance)</li>
<li>a /Charset entry is included for each font when using embedded subsets</li>
<li>a Metadata object is added to the file </li>
<li>an ICC sRGB Color Profile is added as /OuputIntent</li>
</ul>

Only the first change may make a discernible change to the displayed document. All other changes are to the file structure.

## Warnings

Some problems can be fixed by mPDF, but will cause a change to the appearance of your document. By default they will generate warning messages. Once you have assessed the warnings, you can direct mPDF to make these changes automatically by setting in your script:

{% highlight php %}
<?php

$mpdf->PDFAauto = true; // Overrides warnings making changes when possible to force PDFA1-b compliance
{% endhighlight %}

The following issues will cause a warning message when you try to generate a PDFA file:

<table class="table"> <thead>
<tr>
<td>Problem detected</td>
<td>Action taken by mPDF</td>
</tr>
</thead> <tbody>
<tr>
<td>List bullets cannot be substituted from current font</td>
<td>Bullets substituted by a hypen "-"</td>
</tr>
<tr>
<td>

Character substitution (<span class="parameter">$useSubstitutions</span> or <span class="parameter">$useSubstitutionsMB</span>) is enabled.

This would attempt to substitute missing characters using core Adobe fonts which are disallowed.

</td>
<td>Character substitution is disabled

</td>
</tr>
<tr>
<td>Annotation markers are present; these cannot be semi-transparent and may hide underlying text.</td>
<td>Annotation markers are placed in the right margin</td>
</tr>
<tr>
<td>

Images which have CSS property opacity set less than 1 - PDFA does not allow transparency.

NB GIF or PNG images with a simple transparency set (not alpha-channel mask) are valid.

</td>
<td>Opacity is changed to 1 (no transparency)</td>
</tr>
<tr>
<td>JPG images in CMYK colour are not permitted.</td>
<td>

Converted to RGB (only if GD library installed).

NB This may significantly change the colour and appearance of the image

</td>
</tr>
<tr>
<td>Core fonts (Times, Helvetica, Courier) are specified directly e.g. in CSS stylesheet</td>
<td>Font will be substituted with an available sans, serif, or mono font.</td>
</tr>
<tr>
<td>Barcode of ISBN, ISSN or EAN-13 type which specifies the code to appear above the barcode (normally uses Helvetica font).</td>
<td>Substitutes available sans-serif font</td>
</tr>
<tr>
<td>Form element `&lt;select&gt;` which normally uses a Zapfdingbats character for the drop-down symbol.</td>
<td>An equal sign "=" will be substituted if ▼ is not available in the default sans-serif font.</td>
</tr>
</tbody> </table>

## Fatal Errors

Some issues cannot be fixed automatically by mPDF and will generate fatal errors:

<ul>
<li><span class="parameter">$useCoreFontsOnly</span> is set as <span class="smallblock">TRUE</span> (cannot embed core fonts)</li>
<li>BIG5, SJIS, UHC or GB fonts cannot be used (cannot be embedded)</li>
<li>Watermarks - text or image - are not permitted (transparency is disallowed so will make text unreadable)</li>
<li>Using CMYK colour in functions SetTextColor() SetDrawColor() or SetFillColor()</li>
<li>PNG images with alpha channel transparency ('masks' not allowed)</li>
<li>encryption is enabled</li>
</ul>

# See Also

<ul>
<li class="manual_boxlist"><a href="{{ "/what-else-can-i-do/pdf-x-1a-compliance.html" | prepend: site.baseurl }}">PDF/X-1a compliance</a></li>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-variables/pdfa.html" | prepend: site.baseurl }}">PDFA</a> - Create PDF/A1-b compliant document</li>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-variables/pdfx.html" | prepend: site.baseurl }}">PDFX</a> - Create PDF/X-1a compliant document</li>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-variables/pdfaauto.html" | prepend: site.baseurl }}">PDFAauto</a> - Specify whether to automatically fix issues to create PDF/A1-b compliant document</li>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-variables/pdfxauto.html" | prepend: site.baseurl }}">PDFXauto</a> - Specify whether to automatically fix issues to create PDF/X-1a compliant document</li>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-variables/iccprofile.html" | prepend: site.baseurl }}">ICCProfile</a> - Specify the ICC profile for the chosen colorspace used in the document</li>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-variables/restrictcolorspace.html" | prepend: site.baseurl }}">restrictColorSpace</a> - Specify whether to automatically limit the colorspaces used</li>
</ul>

# Useful resources

On-line PDFA Validator: <a href="http://www.validatepdfa.com/online.htm">http://www.validatepdfa.com/online.htm</a>

Useful info on PDFA: <a href="http://www.pdfa.org/doku.php?id=pdfa:en:techdoc">http://www.pdfa.org/doku.php?id=pdfa:en:techdoc</a>

