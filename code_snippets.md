---
layout: default
title: "Code snippets"
permalink: /snippets/
---
**Coming soon, some of the useful snippets I've come across**

<br>
<table>
    <caption>Table of Contents</caption>
    <tr><a href="#WU_Reset">Reset Windows Update</a></tr>
    <tr><a href="#Get_user_emails">Get user names and emails</a></tr>
    <tr><a href="#Get_AD_modifications">Get last modified times for AD object</a></tr>
</table>
<br>

<a id="WU_Reset">Reset Windows Update
{% highlight powershell %}
Stop-Service -Name wuauserv #May take multiple runs, sometimes WU service doesn't want to stop
Remove-Item $env:systemroot\SoftwareDistribution -Recurse -Force
Remove-Item $env:systemroot\WindowsUpdate.log #Optional, if logs aren't needed
Start-Service -Name wuauserv
{% endhighlight %}

<a id="Get_user_emails">Get user names and emails
{% highlight powershell %}
Get-ADGroupMember -recursive -identity '[target group]' `
 | Get-ADUser `
 | Select-Object name,userprincipalname `
 | Export-CSV -notypeinformation C:\temp\user_emails.csv #Enter your target group and output location
{% endhighlight %}

<a id="Get_AD_modifications">Get last modified times for AD object
{% highlight powershell %}
Get-ADReplicationAttributeMetadata -object (Get-ADUser -identity [account name]) -server [DC name] `
 | Select-Object attributename,attributevalue,LastOriginatingChangeTime `
 | Format-Table #Enter your target user and domain controller
{% endhighlight %}