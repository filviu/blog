---
title: 'Adding a form with autocalculated  fields in squarespace'
author: silviu
type: post
date: 2015-08-26T12:45:43+00:00
url: /2015/08/26/adding-a-form-with-autocalculated-fields-in-squarespace/
dsq_thread_id:
  - 4068553288
categories:
  - old
tags:
  - squarespace javascript form autocalculate
  - temp_on

---
I had to build a form on a squarespace hosted site that has to auto-calculate a couple of fields and also do field validation and offer the option to email the whole calculation to a visitor chosen address. I won&#8217;t publish the complete script here, but it shold help get you going.

First of all you will have to build this in the HTML/CSS block, you won&#8217;t be able to use the squarespace offered form builder.

First you will need a few javascript functions

[cce_html]  
function getField1() {  
var theForm = document.forms[&#8220;myform&#8221;];  
var field1Value = theForm.elements[&#8220;field1&#8221;];  
return parseInt(field1Value.value);  
}  
[/cce_html]

What this function does is return the value of a field named &#8220;field1&#8221; in your &#8220;myform&#8221; form. parseFloat might be required if you are going to use floating point values.

[cce_html]  
function calculateTotal() {  
var outputfield1Value = getField1()*5;

var elem = document.getElementById(&#8220;outputfield1Id&#8221;);  
elem.value = Math.round(outputfield1Value);

}  
[/cce_html]

This function is called each time one of your form fields is modified. What it does is change the value of the read-only form field to field1*5. This is of course just an example. You can multiply this to as many form input and output fields you need. Please note that you cannot use &#8220;disabled&#8221; fields as those cannot be POSTed.

[cce_html]  
function validateForm() {  
x = document.forms\[&#8220;myform&#8221;\]\[&#8220;field1&#8221;\].value;  
if (x == null || x == &#8220;&#8221;) {  
alert(&#8220;Please fill in the first field&#8221;);  
return false;  
}  
var x = document.forms\[&#8220;myform&#8221;\]\[&#8220;emailaddress&#8221;\].value;  
var re = /^([\w-]+(?:\.[\w-]+)\*)@((?:[\w-]+\.)\*\w[\w-]{0,66})\.([a-z]{2,6}(?:\.[a-z]{2})?)$/i;  
if (x == null || x== &#8220;&#8221; || !re.test(x)) {  
alert(&#8220;Please enter a valid email address&#8221;);  
return false;  
}  
[/cce_html]

A simple function to do field validation. This one simply checks that the fields were actually filled and that the email field is valid (check RFCs, this is not really the best version but it works for me). Please note that this validation will not stop an attacker or bot to fill bogous data in your fields (as they can POST anything without going trough this javascript)

[cce_html]

<div class="sys-block form-block sys-block-form">
  <div class="sys-block-content">
    <div class="form-wrapper">
      <div class="form-inner-wrapper">
      </div>
    </div>
  </div>
</div>

[/cce_html]

The first four div&#8217;s are there to make the form look like other Squarespace built forms. Your form will call the validation function and onchange the first field will trigger the update of the second. When working with the new &#8220;number&#8221; input field pay close attention to the step value. The default is 1 which means Chrome (Firefox ignores it I think) will not allow floating point values unless you set the step to be any (or say 0.1, if you require specific values).

I will leave the emailself.php script as an exercise to the reader. It&#8217;s really easy to screw it up though, so be sure to secure it &#8211; both the form, maybe with google a captcha and your php script that takes POSTed data and emails it as it&#8217;s really easy to miss something and open your self to becoming a SPAM sender.