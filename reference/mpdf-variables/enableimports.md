---
layout: page
title: enableImports
parent_title: mPDF Variables
permalink: /reference/mpdf-variables/enableimports.html
modification_time: 2015-08-05T12:01:55+00:00
---

(mPDF >= 4.3)

enableImports – Enable the use of imported PDF files or templates

# Description

void **enableImports**

Enable the use of imported PDF files or templates. This causes additional files (classes) to be loaded, enabling several functions allowing you to import PDF files into the document you are writing, and using templates.

<div class="alert alert-info" role="alert">**Note:** You should only change this variable in the configuration file <span class="filename">config.php</span>  If you want to set this at runtime, use <a href="{{ "/reference/mpdf-functions/setimportuse.html" | prepend: site.baseurl }}">SetImportUse()</a></div>

<div class="alert alert-info" role="alert">**Note:** Prior to mPDF 4.3, this required calling mPDFI(). The functions have now been incorporated into the main mpdf.php file, but you must set this variable to enable them.</div>

# Values

<span class="parameter">$enableImports</span> =  <span class="smallblock">TRUE </span>| <span class="smallblock">FALSE</span>

**Values**

<span class="smallblock">TRUE </span>: enable import/template functions

<span class="smallblock">FALSE</span>: disabled

<span class="smallblock">DEFAULT</span>: <span class="smallblock">FALSE</span>

# Changelog

<table class="table"> <thead>
<tr> <th>Version</th><th>Description</th> </tr>
</thead> <tbody>
<tr>
<td>4.3</td>
<td>Variable was added.</td>
</tr>
</tbody> </table>

# See Also

<ul>
<li><a href="{{ "/reference/mpdf-functions/setimportuse.html" | prepend: site.baseurl }}">SetImportUse()</a> - Enable the use of imported PDF files or templates</li>
<li><a href="{{ "/reference/mpdf-functions/thumbnail.html" | prepend: site.baseurl }}">Thumbnail()</a> - Print thumbnails of an external PDF file</li>
<li><a href="{{ "/reference/mpdf-functions/setsourcefile.html" | prepend: site.baseurl }}">SetSourceFile()</a> - Specify the source PDF file used to import pages into the document</li>
<li><a href="{{ "/reference/mpdf-functions/importpage.html" | prepend: site.baseurl }}">ImportPage()</a> - Import a page from an external PDF file</li>
<li><a href="{{ "/reference/mpdf-functions/usetemplate.html" | prepend: site.baseurl }}">UseTemplate()</a> - Insert an imported page from an external PDF file</li>
<li><a href="{{ "/reference/mpdf-functions/setpagetemplate.html" | prepend: site.baseurl }}">SetPageTemplate()</a> - Specify a page from an external PDF file to use as a template</li>
<li><a href="{{ "/reference/mpdf-functions/setdoctemplate.html" | prepend: site.baseurl }}">SetDocTemplate()</a> - Specify an external PDF file to use as a template</li>
<li><a href="{{ "/reference/mpdf-functions/restartdoctemplate.html" | prepend: site.baseurl }}">RestartDocTemplate()</a> - Re-start the use of a Document template from the next page</li>
</ul>

