---
layout: post
title: "Dealing with Plugin Install Error In NOPCommerce 3.x"
description: "Dealing with the 'Item Already Exists in the Database' error when trying to install NOPCommerce plugin"
category: "NOPCommerce" 
tags: ["NOPCommerce", "NOP Plugins"]
---
{% include JB/setup %}

I have recently begun working with an open source shopping cart called `NOPCommerce`.  I am extremely impressed with the platform so far and am excited about the potential uses of this project for our e-commerce customers.

I just completed my first simple site using `NOPCommerce` and wanted to document some basic items that I encountered during the process so that I can refer back to these items in the future.

When I published my site from Visual Studio to our server, all of our plugins were not installed on the site.  I believe this is due to the fact that the `/App_Data/InstalledPlugins.txt` file was not pushed when we published initially.
<!--more-->
I was using an existing database with the site on the live server, so some of these plugins had already created data in the database from my dev install of the site.  When I went into the `admin` site and tried to enable some of these plugins, the site gave the following error:

	There is already an item by that name in the database

Specifically, this happened for the `Payments.PurchaseOrder` plugin.  It turns out the fix for this issue was simple.  I opened the `/App_Data/InstalledPlugins.txt` file and added a new line with the following: `Payments.PurchaseOrder` and saved the file.  Then, I went to my plugins page on the site and clicked the `Reload List of Plugins` button and my plugin was successfully enabled and I was able to proceed with the configuration.

Thank you to the active forum members in the [NOPCommerce forums](http://www.nopcommerce.com/boards/){:target="_blank"} for posting the solution to this error ([link](http://www.nopcommerce.com/boards/t/28582/duplicate-object-name-in-the-database-when-installing-a-new-plugin.aspx){:target="_blank"}).