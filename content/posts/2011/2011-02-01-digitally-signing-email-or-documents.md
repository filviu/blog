---
title: Digitally signing email or documents.
author: silviu
type: post
date: 2011-02-01T10:16:00+00:00
url: /2011/02/01/digitally-signing-email-or-documents/
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

##  What are email certificates used for?


Email certificates provide the strongest levels of confidentiality and security for your electronic communications by allowing you to digitally sign and encrypt your mail and attachments. Encryption means that only your intended recipient will be able to read the mail while digitally signing allows them to confirm you as the sender and verify the message was not tampered with en route.


## How to obtain one?

There are many sources offering certificates for digitally signing of email. Many of them are commercial some of them are free. If you'd like to test this feature Comodo offers a free certificate for personal use.

Go to http://www.comodo.com/home/email-security/free-email-certificate.php and click on **Free Download**

Fill out all the details and soon you will receive the certificate by email.

## How to install one?

This is how it is installed in Mozilla Thunderbird running on Linux. No dobt the procedure might differ on different systems and/or email clients.

After install the certificate is available in Mozilla Firefox but not Thunderbird, so it needs to be exported from Firefox and imported inside Thunderbird.

- Go to **Prefferences->Advanced->View certificates**
- Click on the certificate (it's on the **Your certificates** tab) and click **Backup**
- Save the certificate somewhere on your computer. It's a good ideea to keep a copy of your certificate for future reference and so you can password protect it so it won't be possible to be imported without knowing this password. (this will prevent unauthorized persons from posing as you using a stolen certificate backup)
- Open Thunderbird. Go to **Account settings=>Security** (under the account you created the certificate for)
- Go to **View Certificates and click import**. Locate the certificate you exported above and import it. You will have to type the password you entered earlier.
- _The above procedure will no doubt be different across operating systems and email clients but the basic steps should be the same. For example it's possible that if you use Outlook and Internet Explorer the certificate will be already installed in both without requiring extra import/export._

## Other certifcate providers:

- http://www.instantssl.com/ssl-certificate-products/free-email-certificate.html
- http://www.verisign.com/authentication/digital-id/index.html
- http://www.pgptrustcenter.com/digital-certificate-solutions
