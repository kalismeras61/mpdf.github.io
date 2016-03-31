---
layout: page
title: setAutoBottomMargin
parent_title: mPDF Variables
permalink: /reference/mpdf-variables/setautobottommargin.html
---

<div id="bpmbook" class="bpmbook" style="direction:ltr;">
<div class="topic_user_field">
<div id="U0">
<p>(mPDF &gt;= 4.0)</p>
<h2>Description</h2>

<div class="alert alert-info" role="alert">mixed <b>setAutoBottomMargin</b></div>
<p>Specify the behaviour defining the bottom-margin of the document. When <span class="parameter"></span><span class="parameter">setAutoBottomMargin</span> is set to 'stretch' then <span class="parameter">autoMarginPadding</span> defines the minimum distance in mm that will be forced between the top of the footer and the bottom of the main text.</p>
<h2>Values</h2>
<p class="manual_param_dt"><span class="parameter">setAutoBottomMargin</span></p>
<p class="manual_param_dd"><b>Values</b>

pad - the value for margin-bottom is used to set a fixed distance in mm (padding) between the top of the footer and the bottom of the main text

stretch -&nbsp; margin-bottom sets a <b>minimum</b> distance in mm between the bottom of the page and the bottom of the main text, which expands if the footer is too large to fit. 

<span class="smallblock">FALSE</span> - the defined value for margin-bottom is respected even if the footer overlaps the main body of the document.

<span class="smallblock">DEFAULT</span> <span class="smallblock">FALSE</span></p>
<h2>See Also</h2>
<ul>
<li class="manual_boxlist"><a href="/headers-footers/headers-top-margins.html">Headers &amp; Top margins </a></li>
<li class="manual_boxlist"><a href="/reference/mpdf-variables/setautotopmargin.html">setAutoTopMargin</a> -Specify mode of determining top-margin position

</li>
<li class="manual_boxlist"><a href="/reference/mpdf-variables/automarginpadding.html">autoMarginPadding</a> - Specify padding between top-margin and header in automatic mode

</li>
</ul>
<p>&nbsp;</p>
</div>
</div>
