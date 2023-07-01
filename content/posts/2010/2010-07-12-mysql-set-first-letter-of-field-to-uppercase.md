---
title: 'MYSQL: set first letter of field to uppercase'
author: silviu
type: post
date: 2010-07-12T10:05:53+00:00
url: /2010/07/12/mysql-set-first-letter-of-field-to-uppercase/
categories:
  - old
tags:
  - lowercase
  - mysql
  - temp_on
  - uppercase

---
![Logo-mysql](/blog/images/2010/Logo-mysql-300x219.jpg) I recently had to set values of a set of values from a column from lowercase to Firstuppercase. Nothing easier, run the following code on the database:

```sql
UPDATE `affected_table` SET
`field_in_question` = CONCAT(UPPER(LEFT(`field_in_question`, 1)),
SUBSTRING(`field_in_question`, 2));
```