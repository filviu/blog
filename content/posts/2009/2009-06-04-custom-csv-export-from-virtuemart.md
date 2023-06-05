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
One of my clients needed a custom feed of his virtuemart products. I did a quick google check and nothing came up, so I decided to write my own. Please note that I'm not a programmer and I bet it can be done faster, better and more elegant, still this works, so &#8230;

[cce LANG="PHP"]

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

mysql\_select\_db($db_name);

$myFile = "product_export.csv";  
$fh = fopen($myFile, 'w');

$sqlstr = mysql\_query("SELECT * FROM jos\_vm_product");  
if (mysql_numrows($sqlstr) != 0) {

while ($row = mysql\_fetch\_array($sqlstr)) {

// category id  
$sql\_cat\_id = mysql\_query("SELECT * FROM jos\_vm\_product\_category\_xref WHERE product\_id = " .  
$row['product_id']);  
$cat\_row = mysql\_fetch\_array($sql\_cat_id);  
fwrite($fh, """ . base64\_encode($cat\_row['category_id']) . """ . ";" );

// category name  
$sql\_catname\_id = mysql\_query("SELECT * FROM jos\_vm\_category WHERE category\_id = " .  
$cat\_row['category\_id']);  
$catname\_row = mysql\_fetch\_array($sql\_catname_id);  
fwrite($fh, """ . base64\_encode($catname\_row['category_name']) . """ . ";" );

// product name  
fwrite($fh, """ . base64\_encode($row['product\_name']) . """ . ";" );

// product sku  
fwrite($fh, """ . base64\_encode($row['product\_sku']) . """ . ";" );

// product short description  
fwrite($fh, """ . base64\_encode($row['product\_s_desc']) . """ . ";" );

// full size photo

fwrite($fh, """ .  
base64\_encode("http://www.thewebsite.com/components/com\_virtuemart/shop_image/product/" .  
$row['product\_full\_image']) . """ . ";" );

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

$domain = $\_SERVER['HTTP\_HOST'];

$url = "http://" . $domain . "/folder/" . $myFile;

echo "File is available at ";  
echo "n[" . $url . "][1]";

?>

[/cce]

Note that the fields are base64 encoded as per this client's requirements, but that can be easily removed and also the virtuemart table names are hardcoded, so that must be checked too.  
You can find the code on [GitHub][2] .  
Customize it to your needs.

 [1]: ""
 [2]: https://github.com/silviuvulcan/custom_virtuemart_export