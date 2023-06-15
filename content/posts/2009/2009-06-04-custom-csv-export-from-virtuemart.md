---
title: Custom csv export from virtuemart
author: silviu
type: post
date: 2009-06-04T09:11:43+00:00
url: /2009/06/04/custom-csv-export-from-virtuemart/
dsq_thread_id:
  - 48858303
categories:
  - old
tags:
  - csv
  - joomla
  - php
  - temp_on
  - virtuemart

---
One of my clients needed a custom feed of his virtuemart products. I did a quick google check and nothing came up, so I decided to write my own. Please note that I'm not a programmer and I bet it can be done faster, better and more elegant, still this works, so ...

```php

<!-?php
// Please note those was developed for a Joomla 1.5 installation
// www.sgvulcan.com

$host = "localhost"; //database location
$user = "user"; //database username
$pass = "pass"; //database password

$db_name = "database"; //database name

$wtxt=";
//database connection
$link = mysql_connect($host, $user, $pass);

mysql_select_db($db_name);

$myFile = "product_export.csv";
$fh = fopen($myFile, 'w');

$sqlstr = mysql_query("SELECT * FROM jos_vm_product");
if (mysql_numrows($sqlstr) != 0) {

while ($row = mysql_fetch_array($sqlstr)) {

// category id
$sql_cat_id = mysql_query("SELECT * FROM jos_vm_product_category_xref WHERE product_id = " .
$row['product_id']);
$cat_row = mysql_fetch_array($sql_cat_id);
fwrite($fh, """ . base64_encode($cat_row['category_id']) . """ . ";" );

// category name
$sql_catname_id = mysql_query("SELECT * FROM jos_vm_category WHERE category_id = " .
$cat_row['category_id']);
$catname_row = mysql_fetch_array($sql_catname_id);
fwrite($fh, """ . base64_encode($catname_row['category_name']) . """ . ";" );

// product name
fwrite($fh, """ . base64_encode($row['product_name']) . """ . ";" );

// product sku
fwrite($fh, """ . base64_encode($row['product_sku']) . """ . ";" );

// product short description
fwrite($fh, """ . base64_encode($row['product_s_desc']) . """ . ";" );

// full size photo

fwrite($fh, """ .
base64_encode("http://www.thewebsite.com/components/com_virtuemart/shop_image/product/" .
$row['product_full_image']) . """ . ";" );

// empty
fwrite($fh, """ . """ . ";" );

// empty
fwrite($fh, """ . """ . ";" );

// empty
fwrite($fh, """ . """ . ";" );

// empty
fwrite($fh, """ . """ . ";rn" );

}

}

mysql_close($link);

$domain = $_SERVER['HTTP_HOST'];

$url = "http://" . $domain . "/folder/" . $myFile;

echo "File is available at ";
echo "n[" . $url . "][1]";

?>

```

Note that the fields are base64 encoded as per this client's requirements, but that can be easily removed and also the virtuemart table names are hardcoded, so that must be checked too.
You can find the code on [GitHub][2] .
Customize it to your needs.

 [1]: ""
 [2]: https://github.com/filviu/custom_virtuemart_export