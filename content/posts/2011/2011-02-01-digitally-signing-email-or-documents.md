---
title: Digitally signing email or documents.
author: silviu
type: post
date: 2011-02-01T10:16:00+00:00
url: /2011/02/01/digitally-signing-email-or-documents/
dsq_thread_id:
  - 332153741
categories:
  - old
tags:
  - certificate
  - digital
  - email
  - free
  - sign
  - temp_on

---
<h2 class="western" style="font-weight: normal">
  What are email<br /> certificates used for?
</h2>

<p align="JUSTIFY">
  Email certificates provide the strongest levels of<br /> confidentiality and security for your electronic communications by<br /> allowing you to digitally sign and encrypt your mail and attachments.<br /> Encryption means that only your intended recipient will be able to<br /> read the mail while digitally signing allows them to confirm you as<br /> the sender and verify the message was not tampered with en route.
</p>

<h2 class="western" style="font-weight: normal">
  How to obtain one?
</h2>

There are many sources offering certificates for digitally
signing of email. Many of them are commercial some of them are free.
If you'd like to test this feature Comodo offers a free certificate
for personal use.

Go to
http://www.comodo.com/home/email-security/free-email-certificate.php
and click on **Free Download**

	****<span style="font-weight: normal">Fill out all the details<br /> and soon you will receive the certificate by email.</span>

<h2 class="western" style="font-weight: normal">
  How to install one?
</h2>

<p style="font-weight: normal">
  This is how it is installed in<br /> Mozilla Thunderbird running on Linux. No dobt the procedure might<br /> differ on different systems and/or email clients.
</p>

<p style="font-weight: normal">
  After install the certificate is<br /> available in Mozilla Firefox but not Thunderbird, so it needs to be<br /> exported from Firefox and imported inside Thunderbird.
</p>

<p style="font-weight: normal">
  <ol>
    <li>
      <p>
        <span style="font-weight: normal">Go to<br /> </span><b>Prefferences->Advanced->View certificates</b>
      </p>
    </li>
  
    <li>
      <p>
        <span style="font-weight: normal">Click on the certificate<br /> (it's on the </span><b>Your certificates </b><span style="font-weight: normal">tab)<br /> and click </span><b>Backup</b>
      </p>
    </li>
  
    <li>
      <p>
        <span style="font-weight: normal">Save the certificate<br /> somewhere</span><b> </b><span style="font-weight: normal">on your<br /> computer. It's a good ideea to keep a copy of your certificate for<br /> future reference and so you can password protect it so it won't be<br /> possible to be imported without knowing this password. (this will<br /> prevent unauthorized persons from posing as you using a stolen<br /> certificate backup)</span>
      </p>
    </li>
  
    <li>
      <p>
        <span style="font-weight: normal">Open Thunderbird.. Go to<br /> </span><b>Account settings=>Security </b><span style="font-weight: normal">(under<br /> the account you created the certificate for)</span>
      </p>
    </li>
  
    <li>
      <p>
        <span style="font-weight: normal">Go to </span><b>View<br /> Certificates and click import</b><span style="font-weight: normal">.<br /> Locate the certificate you exported above and import it. You will<br /> have to type the password you entered earlier.</span>
      </p>
    </li>
  </ol>

  <p style="font-weight: normal">
    <i> The above procedure will no doubt<br /> be different across operating systems and email clients but the basic<br /> steps should be the same. For example it's possible that if you use<br /> Outlook and Internet Explorer the certificate will be already<br /> installed in both without requiring extra import/export.</i>
  </p>

  <h2 class="western" style="font-weight: normal">
    Other certifcate<br /> providers:
  </h2>

  <ul>
    <li>
      <p style="font-weight: normal">
        http://www.instantssl.com/ssl-certificate-products/free-email-certificate.html
      </p>
    </li>
  
    <li>
      <p style="font-weight: normal">
        http://www.verisign.com/authentication/digital-id/index.html
      </p>
    </li>
  
    <li>
      <p style="font-weight: normal">
        http://www.pgptrustcenter.com/digital-certificate-solutions
      </p>
    </li>
  </ul>