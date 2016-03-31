---
layout: page
title: useTibetanLBR
parent_title: mPDF Variables
permalink: /reference/mpdf-variables/usetibetanlbr.html
---

<div id="bpmbook" class="bpmbook" style="direction:ltr;">
<div class="topic_user_field">
<div id="U0">
<p>(mPDF &gt;= 6.0)</p>
<h2>Description</h2>

<div class="alert alert-info" role="alert">boolean <b>useTibetanLBR</b></div>
<p>Specify whether to use mPDF algorithm to determine appropriate places for line breaks when using Tibetan text.</p>
<p>mPDF uses a simple algorithm to identify line-breaking opportunities after the characters U+0F0B (Tsheg) or U+0F0D.</p>
<p>For more information, see <a href="/what-else-can-i-do/line-breaking.html">Line breaking</a>.</p>
<h2>Values</h2>
<p class="manual_param_dt"><span class="parameter">useTibetanLBR = <span class="smallblock">FALSE</span>|<span class="smallblock">TRUE</span></span></p>
<p class="manual_param_dd"><b>Values</b>

<i><span class="smallblock">TRUE</span></i>: <span class="smallblock">DEFAULT</span> use mPDF algorithm to determine appropriate places for line breaks when using Tibetan text.

<span class="smallblock">FALSE</span>: algorithm not used. Line breaks will only be allowed according to usual line-breaking rules.</p>
<h2>Changelog</h2>
<table class="bpmTopic"> <thead>
<tr> <th>Version</th><th>Description</th> </tr>
</thead> <tbody>
<tr>
<td>6.0</td>
<td>Variable was added.</td>
</tr>
</tbody> </table>
<h2>See Also</h2>
<p><a href="/what-else-can-i-do/line-breaking.html">Line breaking</a></p>
</div>
</div>
