---
title: 'MYSQL: set first letter of field to uppercase'
author: silviu
type: post
date: 2010-07-12T10:05:53+00:00
url: /2010/07/12/mysql-set-first-letter-of-field-to-uppercase/
dsq_thread_id:
  - 326479314
categories:
  - old
tags:
  - lowercase
  - mysql
  - temp_on
  - uppercase

---
<img decoding="async" loading="lazy" class="alignleft wp-image-1037 size-medium" title="Logo-mysql" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/07/Logo-mysql-300x219.jpg" alt="" width="300" height="219" />I recently had to set values of a set of values from a column from lowercase to Firstuppercase. Nothing easier, run the following code on the database:
[ccNe_sql]
UPDATE \`affected_table\` SET
\`field_in_question\` = CONCAT(UPPER(LEFT(\`field_in_question\`, 1)),
SUBSTRING(\`field_in_question\`, 2));
[/ccNe_sql]