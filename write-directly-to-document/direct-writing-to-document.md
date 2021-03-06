---
layout: page
title: Direct writing to document
parent_title: Write directly to document
permalink: /write-directly-to-document/direct-writing-to-document.html
modification_time: 2015-08-05T12:00:29+00:00
---

# Other Methods

mPDF is optimised to accept HTML code and CSS styles. Apart from WriteHTML() there are other methods that can be used to write to the PDF document, but these do not always have full functionality. These are methods available in the original FPDF and successors, and if these are all you are using you may find that you do not need to use mPDF with its extra functions that slow the program down - see FPDF and UFPDF for further details.

The methods Cell() and Text() from FPDF are still present, but should not be used directly as they will not cope with UTF-8 encoded text. Use the WriteCell() and WriteText() methods instead.

All the methods described below handle UTF-8 encoded text, and all but AutosizeText() and watermark() will reverse RTL (right-to-left) text when appropriate.

## Direct writing methods and OTL (updated: mPDF >= 6.0)

<ul>
<li>WriteText() WriteCell() Watermark() AutoSizeText() and ShadedBox() DO support complex scripts and right-to-left text (RTL).</li>
<li>Write() does NOT support complex scripts or RTL (NB this is a change - Write() used to support RTL).</li>
<li>CircularText() does NOT support complex scripts or RTL.</li>
<li>MultiCell() DOES support complex scripts and RTL, but complex-script line-breaking MAY NOT be accurate.</li>
<li> MultiCell() does not support kerning and justification. NB This includes &lt;textarea&gt; in forms which uses MultiCell() internally. </li>
<li>&lt;select&gt; form objects also do NOT support kerning.</li>
</ul>

Text containing HTML entities, as well as decimal and hex e.g. &amp; apos; &amp; #8812; or &amp; #x21a4; can be used in all of these methods, by setting:

$mpdf-&gt;text_input_as_HTML = true; (default = false)

This will convert all the above to their apropriate characters, otherwise the text will be output as it is.

For most of the methods, you are referred to the originals at <a href="http://www.fpdf.org/" target="_blank">FPDF</a> &gt;&gt; Manual for more information.

**WriteCell**(**float** w, **float** h, **string** text[, **mixed** border[, **integer** ln[, **string** align[, **integer** fill[, **mixed** link[, **float** returnx]]]]]])

Writes a single line of text directly to the PDF document at the current position.

See the details for Cell() at FPDF. An additional parameter returnx has been added; if ln is set, the current position moves not to the left margin, but to the value set as returnx.

**WriteText**(**float** w, **float** h, **string** text)

Writes a single line of text directly to the PDF document at a specified position.

See the details for Text() at FPDF.

**MultiCell**(**float** w, **float** h, **string** text[, **mixed** border[, **string** align[, **integer** fill[, **mixed** link[, **string** directionality[, **boolean** encoded]]]]]])

Writes a block of text directly to the PDF document at the current position. Lines are wrapped at the margins.

See the details for MultiCell() at FPDF. Two additional parameters have been added:

<ul>
<li>directionality

Set to 'rtl' if using RTL language (right-to-left)

Default = 'ltr'</li>
<li>encoded

When set to false (default), UTF-8 encoded text will be appropriately converted to the chosen output file format. It should only be set to true, when the input text has already been converted internally within the program.

Default = false</li>
</ul>

**SetX**(**float** x)

**SetY**(**float** y)

**SetXY**(**float** x, **float** y)

Sets the co-ordinates for the current position to write. Note only milimeters can be used as units. X and Y are measured from the top-left corner of the page.

See the details these methods at FPDF

**AutosizeText**(**string** text, **float** width, **string** font, **string** style[, **float** fontsize])

Writes a single line of text directly to the PDF document at the current position.

Font size will be automatically reduced to fit width (but is not increased).

NB Does not reverse RTL text

<ul>
<li>text

UTF-8 encoded text to write. Single line only.</li>
<li>width

Width of text in millimeters. The font size will be reduced if required to fit this size.</li>
<li>font

Font family to use</li>
<li>style

Font style used [blank for normal]|i|b|bi</li>
<li>fontsize

Maximm font size in points (pt)

Default = 72</li>
</ul>

**watermark**(**string** text[, **float** angle[, **float** fontsize[, **float** alpha]]])

Writes a single line of text centred on the page, which can be rotated and transparent i.e. a watermark.

NB Does not reverse RTL text.

<ul>
<li>text

UTF-8 encoded text</li>
<li>angle

Angle of rotation for text (anticlockwise rotation from horizontal)

Default = 45</li>
<li>fontsize

Font size in points (pt)

Default = 96</li>
<li>alpha

Transparency

Default = 0.2</li>
</ul>

**RoundedRect**(**float** x, **float** y, **float** w, **float** h, **float** radius[, **string** style])

Draws a rectangle with rounded corners directly to the PDF document at the specified position.

<ul>
<li>x

Abscissa of left edge of box - value in millimeters</li>
<li>y

Ordinate of top edge of box - value in millimeters</li>
<li>w

Width of the box - in millimeters</li>
<li>h

Width of the box - in millimeters</li>
<li>radius

Radius of the rounded corners</li>
<li>style

Box style: D or empty string - draw border (default); F - fill; DF or FD - draw and fill

Default = '' i.e. border, no fill</li>
</ul>

**shaded_box**(**string** title[, **string** font[, **float** fontstyle[, **float** fontsize[, **float** width[, **string** style[, **float** radius[, **string** backgroundcolor[, **string** color[, **float** padding]]]]]]]]])

Writes a single line of text surrounded by a box directly to the PDF document at the current position. The box can have rounded corners, and be filled with background-colour.

<ul>
<li>title

UTF-8 encoded text (single line)</li>
<li>font

Font family

Default = '' i.e. default document font</li>
<li>fontstyle

Font style as one of B (bold), I (italic), BI (bold-italic) or blank for normal

Default = 'B' i.e. bold</li>
<li>fontsize

Font size in points (pt)

Default = '' i.e. default document font size</li>
<li>width

Width of the box - any units acceptable in CSS can be used e.g. pt, px, mm, % (of page width)

Default = '70%'</li>
<li>style

Box style: D or empty string - draw border (default); F - fill; DF or FD - draw and fill

Default = 'DF' i.e. border and fill</li>
<li>radius

Radius of the rounded corners

Default = 2.5</li>
<li>backgroundcolor

Fill colour for the box - as #rrggbb

Default = '#FFFFFF'</li>
<li>color

Text colour - as #rrggbb

Default = '#000000'</li>
<li>padding

Padding between text and box border, in millimeters

Default = 2</li>
</ul>

# See Also

<ul>
<li class="manual_boxlist"><span class="manual_boxlist"><a href="{{ "/reference/mpdf-utilities/preparepretext.html" | prepend: site.baseurl }}">preparePreText()</a> - </span>Prepares text to be output ignoring the HTML markup</li>
</ul>
