---
layout: post
title: "Enable Search By SKU in NOPCommerce 3.x"
description: ""
category: "NOPCommerce"
tags: ["Helpful Hints", "NOPCommerce"]
---
{% include JB/setup %}

I just completed my first `NOPCommerce` site and have to say I am extremely impressed with all that this `open-source` project has to offer.  I am planning to blog tips and tricks that I learn while developing with `NOPCommerce` for future reference and in hopes that they may help others who are struggling with the same issue.

Many times on an e-commerce site, it is desirable for users to be able to search by the product SKU value.  Out of the box, the default `NOPCommerce` site search does not search the SKU field.  I needed a quick fix since this project did not have a large budget and I did not want to modify the site source code, so I found a way to enable the basic search to search by SKU by modifying the `dbo.ProductLoadAllPaged` stored procedure.  This approach may not be ideal, but in this case, it was a valid solution.  

In the `dbo.ProductLoadPaged` stored procedure, I removed `line 220` where is says `IF @SearchSku = 1`.  This change will cause all request to include the `SKU` in the fields that are searched.

Moving forward, I would like to potentially add an option for selecting which fields are search via the admin panel or a plugin, but for now, the stored procedure modification works for me!
