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
One of my clients needed a custom feed of his virtuemart products. I did a quick google check and nothing came up, so I decided to write my own. Please note that I&#8217;m not a programmer and I bet it can be done faster, better and more elegant, still this works, so &#8230;

[cce LANG=&#8221;PHP&#8221;]

<!&#8211;?php  
// Please note those was developed for a Joomla 1.5 installation  
// www.sgvulcan.com

$host = &#8220;localhost&#8221;; //database location  
$user = &#8220;user&#8221;; //database username  
$pass = &#8220;pass&#8221;; //database password

$db_name = &#8220;database&#8221;; //database name

$wtxt=&#8221;;  
//database connection  
$link = mysql_connect($host, $user, $pass);

mysql\_select\_db($db_name);

$myFile = &#8220;product_export.csv&#8221;;  
$fh = fopen($myFile, &#8216;w&#8217;);

$sqlstr = mysql\_query(&#8220;SELECT * FROM jos\_vm_product&#8221;);  
if (mysql_numrows($sqlstr) != 0) {

while ($row = mysql\_fetch\_array($sqlstr)) {

// category id  
$sql\_cat\_id = mysql\_query(&#8220;SELECT * FROM jos\_vm\_product\_category\_xref WHERE product\_id = &#8221; .  
$row[&#8216;product_id&#8217;]);  
$cat\_row = mysql\_fetch\_array($sql\_cat_id);  
fwrite($fh, &#8220;&#8221;&#8221; . base64\_encode($cat\_row[&#8216;category_id&#8217;]) . &#8220;&#8221;&#8221; . &#8220;;&#8221; );

// category name  
$sql\_catname\_id = mysql\_query(&#8220;SELECT * FROM jos\_vm\_category WHERE category\_id = &#8221; .  
$cat\_row[&#8216;category\_id&#8217;]);  
$catname\_row = mysql\_fetch\_array($sql\_catname_id);  
fwrite($fh, &#8220;&#8221;&#8221; . base64\_encode($catname\_row[&#8216;category_name&#8217;]) . &#8220;&#8221;&#8221; . &#8220;;&#8221; );

// product name  
fwrite($fh, &#8220;&#8221;&#8221; . base64\_encode($row[&#8216;product\_name&#8217;]) . &#8220;&#8221;&#8221; . &#8220;;&#8221; );

// product sku  
fwrite($fh, &#8220;&#8221;&#8221; . base64\_encode($row[&#8216;product\_sku&#8217;]) . &#8220;&#8221;&#8221; . &#8220;;&#8221; );

// product short description  
fwrite($fh, &#8220;&#8221;&#8221; . base64\_encode($row[&#8216;product\_s_desc&#8217;]) . &#8220;&#8221;&#8221; . &#8220;;&#8221; );

// full size photo

fwrite($fh, &#8220;&#8221;&#8221; .  
base64\_encode(&#8220;http://www.thewebsite.com/components/com\_virtuemart/shop_image/product/&#8221; .  
$row[&#8216;product\_full\_image&#8217;]) . &#8220;&#8221;&#8221; . &#8220;;&#8221; );

// empty  
fwrite($fh, &#8220;&#8221;&#8221; . &#8220;&#8221;&#8221; . &#8220;;&#8221; );

// empty  
fwrite($fh, &#8220;&#8221;&#8221; . &#8220;&#8221;&#8221; . &#8220;;&#8221; );

// empty  
fwrite($fh, &#8220;&#8221;&#8221; . &#8220;&#8221;&#8221; . &#8220;;&#8221; );

// empty  
fwrite($fh, &#8220;&#8221;&#8221; . &#8220;&#8221;&#8221; . &#8220;;rn&#8221; );

}

}

mysql_close($link);

$domain = $\_SERVER[&#8216;HTTP\_HOST&#8217;];

$url = &#8220;http://&#8221; . $domain . &#8220;/folder/&#8221; . $myFile;

echo &#8220;File is available at &#8220;;  
echo &#8220;n[&#8221; . $url . &#8220;][1]&#8220;;

?>

[/cce]

Note that the fields are base64 encoded as per this client&#8217;s requirements, but that can be easily removed and also the virtuemart table names are hardcoded, so that must be checked too.  
You can find the code on [GitHub][2] .  
Customize it to your needs.

 [1]: ""
 [2]: https://github.com/silviuvulcan/custom_virtuemart_export