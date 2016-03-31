---
layout: page
title: IndexEntrySee()
parent_title: mPDF functions
permalink: /reference/mpdf-functions/indexentrysee.html
---

<div id="bpmbook" class="bpmbook" style="direction:ltr;">
<div class="topic_user_field">
<div id="U0">
<p>(mPDF &gt;= 2.2)</p>
<p>IndexEntrySee – Insert a cross-reference entry for the document Index</p>
<h2>Description</h2>

<div class="alert alert-info" role="alert">void <b>IndexEntrySee</b> ( string <span class="parameter">$content</span> , string <span class="parameter">$see_content</span> )</div>
<p>Insert a cross-reference entry for the document Index i.e. "Dromedary - see Camel".</p>

<div class="alert alert-info" role="alert"><b>Note: </b>The Index must be generated explicity at the end of the document using <a href="/reference/mpdf-functions/tocpagebreak.html">CreateIndex()</a> at some point before <a href="/reference/mpdf-functions/output.html">Output()</a> is called.</div>
<h2>Parameters</h2>
<p class="manual_param_dt"><span class="parameter">content</span></p>
<p class="manual_param_dd">This parameter sets the text as it will appear in the Index entry. Text should be UTF-8 encoded. Text entries passed in the form "Subject:Subcategory" will appear in the Index as "Subject, Subcategory".

<span class="smallblock">REQUIRED</span></p>
<p class="manual_param_dt"><span class="parameter">see_content</span></p>
<p class="manual_param_dd">This parameter sets the text used as the cross-reference. Text should be UTF-8 encoded. Text entries passed in the form "Subject:Subcategory" will appear in the Index as "Subject, Subcategory"

<span class="smallblock">REQUIRED</span></p>
<h2>Examples</h2>

{% highlight php %}
Example #1
{% endhighlight %}

{% highlight php %}
<?php

$mpdf->IndexEntry("Dromedary", "Camel:types");

// This will produce an entry in the Index under 'Dromedary' appearing as:

Dromedary - see Camel, types
{% endhighlight %}

<h2>See Also</h2>
<ul>
<li class="manual_boxlist"><a href="/reference/mpdf-functions/indexentry.html">IndexEntry()</a> - Mark an Index entry in the document</li>
<li class="manual_boxlist">&lt;<a href="/reference/html-control-tags/tocentry.html">indexentry</a>&gt; - Mark an Index entry in the document</li>
<li class="manual_boxlist"><a href="/reference/mpdf-functions/tocpagebreak.html">CreateIndex()</a> - Generate a document Index</li>
</ul>
</div>
</div>
