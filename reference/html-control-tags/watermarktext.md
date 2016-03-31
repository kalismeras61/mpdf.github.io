---
layout: page
title: watermarktext
parent_title: HTML control tags
permalink: /reference/html-control-tags/watermarktext.html
---

<div id="bpmbook" class="bpmbook" style="direction:ltr;">
<div class="topic_user_field">
<div id="U0">
<p>(mPDF &gt;= 3.0)</p>
<p>watermarktext – Set the text to use as a Watermark</p>
<h2>Description</h2>

<div class="alert alert-info" role="alert">&lt;<b>watermarktext</b>&nbsp; <span class="parameter">content</span> [ <span class="parameter">alpha</span> ] /&gt;</div>
<p>Set the text to use as a Watermark. The watermark is a semi-transparent background printed on each page, used for text such as "DRAFT". The watermark will be added to each page when the Footer is printed if the variable <a href="/reference/mpdf-variables/showwatermarktext.html">showWatermark</a> is set to 1 or <span class="smallblock">TRUE</span>.&nbsp;</p>
<h2>Parameters</h2>
<p class="manual_param_dt"><span class="parameter">content</span></p>
<p class="manual_param_dd">This parameter defines the text to use for the watermark. 

<span class="parameter">content</span> cannot contain any of the characters: &lt; &gt; &amp; ' <i>or</i> " and must use the appropriate HTML entities e.g. &lt;watermarktext content="Brian&amp;#039;s document" /&gt;&nbsp; It is recommended that you use htmlspecialchars('Content', ENT_QUOTES) for this.

If the text is blank, it will clear the watermark text, so nothing appears.

<span class="smallblock">DEFAULT</span>: <span class="smallblock">BLANK</span></p>
<p class="manual_param_dt"><span class="parameter">alpha</span></p>
<p class="manual_param_dd">This parameter defines the transparency value (alpha) to use for the watermark: either text or image. The Value should be between 0 and 1.

<span class="smallblock">DEFAULT</span>: 0.2</p>
<h2>Changelog</h2>
<table class="bpmTopic"><thead>
<tr><th>Version</th><th>Description</th></tr>
</thead> <tbody>
<tr>
<td>3.0</td>
<td>The tag was added.</td>
</tr>
</tbody></table>
<h2>Examples</h2>

{% highlight php %}
Example #1
{% endhighlight %}

{% highlight php %}
<?php

<?php

$mpdf=new mPDF();

$mpdf->showWatermarkText = true;

$mpdf->WriteHTML('<watermarktext content="DRAFT" alpha="0.4" />');

$mpdf->WriteHTML('<p>Hallo World</p>');

?>
{% endhighlight %}

<p>&nbsp;</p>
<h2>See Also</h2>
<ul>
<li class="manual_boxlist"><a href="/reference/mpdf-functions/setwatermarktext.html">SetWatermarkText()</a> - PHP equivalent to &lt;watermarktext&gt;</li>
<li class="manual_boxlist"><a href="/reference/mpdf-functions/setwatermarkimage.html">SetWatermarkImage()</a> - Set an image to use as a Watermark</li>
<li class="manual_boxlist"><a href="/reference/mpdf-variables/watermarkimagealpha.html">watermarkImageAlpha</a> - Specifies the transparency (alpha value) for the watermark image</li>
<li class="manual_boxlist"><a href="/reference/mpdf-variables/watermarktextalpha.html">watermarkTextAlpha</a> - Specifies the transparency (alpha value) for the watermark text</li>
<li class="manual_boxlist"><a href="/reference/mpdf-variables/showwatermarktext.html">showWatermarkText</a> - Specifies whether or not to show/print the watermark text

</li>
<li class="manual_boxlist"><a href="/reference/mpdf-variables/showwatermarktext.html">showWatermarkImage</a> - Specifies whether or not to show/print the watermark image</li>
<li class="manual_boxlist"><a href="/reference/mpdf-variables/watermark-font.html">watermark_font</a> - Specifies the font to use for Watermark text</li>
</ul>
<p>&nbsp;</p>
</div>
</div>
