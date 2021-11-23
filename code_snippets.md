---
layout: default
title: "Code snippets"
permalink: /snippets/
---
**Coming soon, some of the useful snippets I've come across**

<br>
<table>
    <td><a href="#WU_Reset">Reset Windows Update</a></td>
<table>
<br>

<a id="WU_Reset">Reset Windows Update

{% highlight powershell %}
Stop-Service -Name wuauserv
Remove-Item $env:systemroot\SoftwareDistribution -Recurse -Force
Remove-Item $env:systemroot\WindowsUpdate.log
Start-Service -Name wuauserv
{% endhighlight %}