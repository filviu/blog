---
title: After importing products from CSV in Virtuemart a discount is showed
author: silviu
type: post
date: 2010-11-29T18:21:26+00:00
url: /2010/11/29/after-importing-products-from-csv-in-virtuemart-a-discount-is-showed/
dsq_thread_id:
  - 328152914
categories:
  - old
tags:
  - discount
  - import
  - temp_on
  - virtuemart

---
After importing products into Virtuemart using CSV Import a discount is shown being available - although offering the same price as the list price. This happens because no discount id is set in the table. Running the following on the mysql table fixes that:

```sql
UPDATE `jos_vm_product` SET `product_discount_id`=0 WHERE 1
```