---
layout: page
title: strcode2utf()
parent_title: mPDF Utilities
permalink: /reference/mpdf-utilities/strcode2utf.html
modification_time: 2015-08-05T12:02:42+00:00
---

(htmltoolkit >=1.0)

strcode2utf – Convert HTML numerical entities to UTF-8 encoded string

# Description

string **strcode2utf** ( string <span class="parameter">$text</span> [, boolean <span class="parameter">$low</span> ])

Returns a UTF-8 encoded string.

<div class="alert alert-info" role="alert">**Note:** This function is not part of the mPDF class, and is located in the htmltoolkit.php file. It is called without the class prefix e.g. $mpd-&gt;</div>

<div class="alert alert-info" role="alert">**Note:** **strcode2utf** is useful for preparing text to be used as a Watermark, or for the metadata properties of Title, Author, Creator and Keywords - which require UTF-8 encoded strings with no entities.</div>

# Parameters

<span class="parameter">$text</span>

The input string, containing HTML numerical entities e.g. &amp;#8123; or &amp;#x2022;

<span class="parameter">$low</span>

Specifies whether to convert HTML numerical entities of ASCII characters (&lt;128).

<span class="smallblock">DEFAULT</span>: <span class="smallblock">TRUE</span>

**Values**

<span class="smallblock">TRUE</span>: Convert all HTML numerical entities to UTF-8 characters

<span class="smallblock">FALSE</span>: Only convert characters above codepoint 127

<div class="alert alert-info" role="alert">**Note:** This function does not convert named character entities like &amp;amp; &amp;quot; or &amp;raquo;</div>

# Return value

Returns a UTF-8 encoded string.

# Examples

Example #1

{% highlight php %}
<?php

$mpdf = new mPDF();

$wm = strcode2utf("&amp;#1575;&amp;#1610;&amp;#1604;&amp;#1575;&amp;#1578; &amp;#1601;&amp;#1610;&amp;#1605;&amp;#1575; &amp;#1575;&amp;#1610;&amp;#1604;&amp;#1575;&amp;#1578; &amp;#1601;&amp;#1610;&amp;#1605;&amp;#1575;");

$mpdf->SetWatermarkText($wm);

$mpdf->showWatermark = true;

$mpdf->WriteHTML('
Hallo World
');

?>
{% endhighlight %}

# See Also

<ul>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-functions/setwatermarktext.html" | prepend: site.baseurl }}">SetWatermarkText()</a> - Sets the text to use for a Watermark</li>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-functions/settitle.html" | prepend: site.baseurl }}">SetTitle()</a> - Set document Title in metadata</li>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-functions/setauthor.html" | prepend: site.baseurl }}">SetAuthor()</a> - Set document Author in metadata</li>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-functions/setcreator.html" | prepend: site.baseurl }}">SetCreator()</a> - Set document Creator in metadata</li>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-functions/setsubject.html" | prepend: site.baseurl }}">SetSubject()</a> - Set document Subject in metadata</li>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-functions/setkeywords.html" | prepend: site.baseurl }}">SetKeywords()</a> - Set document Keywords in metadata</li>
</ul>
