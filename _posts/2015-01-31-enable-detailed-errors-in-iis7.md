---
layout: post
title: "Enable Detailed Errors in IIS7"
description: "Enabling Detailed Errors Mode in IIS 7"
category: "Helpful Tips" 
tags: ["IIS7", "Windows Server", "web.config"]
---
{% include JB/setup %}

I have always used the `<CustomErrors>` in the `web.config` to enable ASP.net errors on my sites.  Setting the `mode` attribute to `off` allows the full error details to be displayed on the page, which is useful when debugging issues on a .NET site.

Yesterday, I had a site that was giving me a standard 500 server error with no details.<!--more-->  I modified the `web.config` and made the `CustomErrors` mode change as described above, but the server was still not returning any error details. Here is an example of the error page I was seeing:

![Standard IIS Server Error](/assets/images/standard-server-error.png)  

Since this site is hosted in `IIS 7`, I learned that I can turn on detailed errors by editing the `<httpErrors>` node and changing the `errorMode` attribute to `Detailed`.  According to this [article](http://www.iis.net/configreference/system.webserver/httperrors), the `errorMode` value can be set to `Detailed`, `Custom`, or `DetailedLocalOnly`. With `Detailed` mode enabled, the error looks like this:

![Detailed IIS Error Page](/assets/images/detailed-server-error.png)