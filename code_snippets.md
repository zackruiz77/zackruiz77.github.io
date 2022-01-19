---
layout: default
title: "Code snippets"
permalink: /snippets/
---
**Coming soon, some of the useful snippets I've come across**

<br>
<table>
    <caption>Table of Contents</caption>
    <td><a href="#WU_Reset">Reset Windows Update</a></td>
</table>
<br>

<a id="WU_Reset">Reset Windows Update

{% highlight powershell %}
Stop-Service -Name wuauserv #May take multiple runs, sometimes WU service doesn't want to stop
Remove-Item $env:systemroot\SoftwareDistribution -Recurse -Force
Remove-Item $env:systemroot\WindowsUpdate.log #Optional, if logs aren't needed
Start-Service -Name wuauserv
{% endhighlight %}