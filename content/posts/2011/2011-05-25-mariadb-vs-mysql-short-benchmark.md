---
title: MariaDB vs MySQL short benchmark
author: silviu
type: post
date: 2011-05-25T08:32:09+00:00
url: /2011/05/25/mariadb-vs-mysql-short-benchmark/
dsq_thread_id:
  - 326451586
categories:
  - old
tags:
  - benchmark
  - database
  - mariadb
  - mysql
  - temp_on

---
Considering switching from MySQL to MariaDB? Me too. I wanted to see if I can look towards any performance improvements (or drops). I don't have high level needs, I'm sure more comprehensive tests exist. This is simple run-all-tests.pl from sql-bench suite. The test machine was a CentOS VM with 2Gb RAM and 2 CPU cores assigned.

**Mysql:**

```bash
Benchmark DBD suite: 2.15
Date of test: 2011-05-25 2:22:27
Running tests on: Linux 2.6.18-238.el5 x86_64
Arguments:
Comments:
Limits from:
Server version: MySQL 5.0.77/
Optimization: None
Hardware:

alter-table: Total time: 7 wallclock secs ( 0.05 usr 0.02 sys + 0.00 cusr 0.00 csys = 0.07 CPU)
ATIS: Total time: 12 wallclock secs ( 3.66 usr 0.51 sys + 0.00 cusr 0.00 csys = 4.17 CPU)
big-tables: Total time: 9 wallclock secs ( 1.88 usr 0.48 sys + 0.00 cusr 0.00 csys = 2.36 CPU)
connect: Total time: 107 wallclock secs (25.93 usr 15.66 sys + 0.00 cusr 0.00 csys = 41.59 CPU)
create: Failed (output/create-mysql-Linux_2.6.18_238.el5_x86_64)
insert: Total time: 791 wallclock secs (257.43 usr 67.52 sys + 0.00 cusr 0.00 csys = 324.95 CPU)
select: Total time: 181 wallclock secs (21.49 usr 4.51 sys + 0.00 cusr 0.00 csys = 26.00 CPU)
transactions: Test skipped because the database doesn't support transactions
wisconsin: Total time: 8 wallclock secs ( 1.56 usr 0.50 sys + 0.00 cusr 0.00 csys = 2.06 CPU)

Of 9 tests, 1 tests didn't work

Totals per operation:
Operation seconds usr sys cpu tests
alter_table_add 2.00 0.01 0.00 0.01 100
alter_table_drop 3.00 0.02 0.01 0.03 91
connect 9.00 3.34 2.35 5.69 10000
connect+select_1_row 11.00 3.45 2.38 5.83 10000
connect+select_simple 11.00 4.60 2.54 7.14 10000
count 3.00 0.03 0.01 0.04 100
count_distinct 5.00 0.08 0.06 0.14 1000
count_distinct_2 8.00 0.10 0.03 0.13 1000
count_distinct_big 10.00 2.55 0.04 2.59 120
count_distinct_group 7.00 0.50 0.06 0.56 1000
count_distinct_group_on_key 6.00 0.12 0.02 0.14 1000
count_distinct_group_on_key_parts 6.00 0.41 0.06 0.47 1000
count_distinct_key_prefix 3.00 0.15 0.05 0.20 1000
count_group_on_key_parts 6.00 0.37 0.05 0.42 1000
count_on_key 48.00 4.76 0.92 5.68 50100
create_index 1.00 0.00 0.00 0.00 8
create_table 0.00 0.01 0.01 0.02 31
delete_all_many_keys 13.00 0.01 0.00 0.01 1
delete_big 0.00 0.00 0.00 0.00 1
delete_big_many_keys 13.00 0.01 0.00 0.01 128
delete_key 2.00 0.16 0.24 0.40 10000
delete_range 2.00 0.01 0.00 0.01 12
drop_index 0.00 0.00 0.00 0.00 8
drop_table 0.00 0.00 0.00 0.00 28
insert 60.00 6.77 4.48 11.25 350768
insert_duplicates 10.00 2.44 1.05 3.49 100000
insert_key 30.00 3.36 1.45 4.81 100000
insert_many_fields 2.00 0.13 0.13 0.26 2000
insert_select_1_key 1.00 0.00 0.00 0.00 1
insert_select_2_keys 1.00 0.00 0.00 0.00 1
min_max 2.00 0.01 0.00 0.01 60
min_max_on_key 23.00 9.25 3.33 12.58 85000
multiple_value_insert 1.00 0.12 0.00 0.12 100000
once_prepared_select 18.00 4.98 1.60 6.58 100000
order_by_big 8.00 6.68 0.11 6.79 10
order_by_big_key 8.00 6.96 0.17 7.13 10
order_by_big_key2 7.00 6.80 0.15 6.95 10
order_by_big_key_desc 8.00 7.07 0.16 7.23 10
order_by_big_key_diff 8.00 6.73 0.12 6.85 10
order_by_big_key_prefix 8.00 6.84 0.13 6.97 10
order_by_key2_diff 2.00 0.79 0.04 0.83 500
order_by_key_prefix 1.00 0.45 0.02 0.47 500
order_by_range 1.00 0.45 0.03 0.48 500
outer_join 10.00 0.00 0.01 0.01 10
outer_join_found 10.00 0.01 0.00 0.01 10
outer_join_not_found 7.00 0.00 0.00 0.00 500
outer_join_on_key 7.00 0.00 0.00 0.00 10
prepared_select 31.00 12.21 3.62 15.83 100000
select_1_row 10.00 2.31 0.90 3.21 100000
select_1_row_cache 11.00 2.14 1.12 3.26 100000
select_2_rows 11.00 2.49 1.01 3.50 100000
select_big 9.00 6.78 0.16 6.94 80
select_big_str 5.00 2.69 0.40 3.09 10000
select_cache 23.00 0.88 0.15 1.03 10000
select_cache2 22.00 0.88 0.11 0.99 10000
select_column+column 14.00 1.84 1.04 2.88 100000
select_diff_key 0.00 0.05 0.05 0.10 500
select_distinct 3.00 0.70 0.06 0.76 800
select_group 8.00 0.56 0.17 0.73 2911
select_join 1.00 0.19 0.01 0.20 100
select_key 59.00 23.49 5.84 29.33 200000
select_key2 68.00 26.43 8.40 34.83 200000
select_key2_return_key 56.00 22.67 6.04 28.71 200000
select_key2_return_prim 68.00 25.13 8.13 33.26 200000
select_key_prefix 72.00 28.90 8.34 37.24 200000
select_key_prefix_join 3.00 1.68 0.02 1.70 100
select_key_return_key 65.00 30.92 8.43 39.35 200000
select_many_fields 7.00 1.75 0.35 2.10 2000
select_range 27.00 3.05 0.09 3.14 410
select_range_key2 8.00 2.66 0.76 3.42 25010
select_range_prefix 8.00 2.62 0.65 3.27 25010
select_simple 13.00 1.67 2.12 3.79 100000
select_simple_cache 12.00 1.40 1.80 3.20 100000
select_simple_join 0.00 0.28 0.03 0.31 500
update_big 9.00 0.00 0.00 0.00 10
update_of_key 7.00 1.24 0.52 1.76 50000
update_of_key_big 4.00 0.02 0.02 0.04 501
update_of_primary_key_many_keys 5.00 0.01 0.00 0.01 256
update_with_key 47.00 6.28 3.86 10.14 300000
update_with_key_prefix 22.00 2.51 2.91 5.42 100000
wisc_benchmark 1.00 0.99 0.07 1.06 114
TOTALS 1111.00 307.95 88.99 396.94 3375950
```

**MariaDB:**

```bash
Benchmark DBD suite: 2.15
Date of test: 2011-05-25 3:26:59
Running tests on: Linux 2.6.18-238.el5 x86_64
Arguments:
Comments:
Limits from:
Server version: MySQL 5.2.6 MariaDB mariadb101/
Optimization: None
Hardware:

alter-table: Total time: 8 wallclock secs ( 0.04 usr 0.01 sys + 0.00 cusr 0.00 csys = 0.05 CPU)
ATIS: Total time: 12 wallclock secs ( 3.87 usr 0.42 sys + 0.00 cusr 0.00 csys = 4.29 CPU)
big-tables: Total time: 8 wallclock secs ( 2.11 usr 0.40 sys + 0.00 cusr 0.00 csys = 2.51 CPU)
connect: Total time: 101 wallclock secs (29.79 usr 15.16 sys + 0.00 cusr 0.00 csys = 44.95 CPU)
create: Failed (output/create-mysql-Linux_2.6.18_238.el5_x86_64)
insert: Total time: 736 wallclock secs (240.44 usr 50.84 sys + 0.00 cusr 0.00 csys = 291.28 CPU)
select: Total time: 216 wallclock secs (23.22 usr 4.85 sys + 0.00 cusr 0.00 csys = 28.07 CPU)
transactions: Test skipped because the database doesn't support transactions
wisconsin: Total time: 6 wallclock secs ( 1.72 usr 0.37 sys + 0.00 cusr 0.00 csys = 2.09 CPU)

Of 9 tests, 1 tests didn't work

Totals per operation:
Operation seconds usr sys cpu tests
alter_table_add 3.00 0.02 0.00 0.02 100
alter_table_drop 3.00 0.01 0.00 0.01 91
connect 10.00 4.42 1.86 6.28 10000
connect+select_1_row 12.00 3.99 2.37 6.36 10000
connect+select_simple 11.00 3.84 2.35 6.19 10000
count 4.00 0.02 0.01 0.03 100
count_distinct 6.00 0.12 0.05 0.17 1000
count_distinct_2 9.00 0.16 0.06 0.22 1000
count_distinct_big 10.00 2.65 0.03 2.68 120
count_distinct_group 6.00 0.47 0.06 0.53 1000
count_distinct_group_on_key 7.00 0.12 0.02 0.14 1000
count_distinct_group_on_key_parts 7.00 0.47 0.09 0.56 1000
count_distinct_key_prefix 4.00 0.12 0.06 0.18 1000
count_group_on_key_parts 8.00 0.41 0.05 0.46 1000
count_on_key 68.00 5.19 0.99 6.18 50100
create_index 1.00 0.00 0.00 0.00 8
create_table 0.00 0.00 0.01 0.01 31
delete_all_many_keys 13.00 0.02 0.00 0.02 1
delete_big 0.00 0.00 0.00 0.00 1
delete_big_many_keys 13.00 0.02 0.00 0.02 128
delete_key 2.00 0.43 0.30 0.73 10000
delete_range 3.00 0.00 0.00 0.00 12
drop_index 1.00 0.00 0.00 0.00 8
drop_table 0.00 0.00 0.00 0.00 28
insert 48.00 8.87 4.79 13.66 350768
insert_duplicates 16.00 3.63 1.71 5.34 100000
insert_key 33.00 3.86 1.82 5.68 100000
insert_many_fields 2.00 0.07 0.05 0.12 2000
insert_select_1_key 1.00 0.00 0.00 0.00 1
insert_select_2_keys 2.00 0.00 0.00 0.00 1
min_max 4.00 0.01 0.01 0.02 60
min_max_on_key 23.00 9.33 2.83 12.16 85000
multiple_value_insert 1.00 0.12 0.00 0.12 100000
once_prepared_select 24.00 5.06 1.89 6.95 100000
order_by_big 8.00 6.79 0.12 6.91 10
order_by_big_key 8.00 7.03 0.17 7.20 10
order_by_big_key2 7.00 6.85 0.09 6.94 10
order_by_big_key_desc 9.00 7.05 0.16 7.21 10
order_by_big_key_diff 9.00 6.78 0.10 6.88 10
order_by_big_key_prefix 8.00 6.86 0.11 6.97 10
order_by_key2_diff 2.00 0.79 0.03 0.82 500
order_by_key_prefix 1.00 0.46 0.02 0.48 500
order_by_range 1.00 0.43 0.02 0.45 500
outer_join 11.00 0.00 0.00 0.00 10
outer_join_found 9.00 0.01 0.00 0.01 10
outer_join_not_found 8.00 0.00 0.00 0.00 500
outer_join_on_key 7.00 0.00 0.00 0.00 10
prepared_select 26.00 10.27 2.47 12.74 100000
select_1_row 11.00 3.02 1.34 4.36 100000
select_1_row_cache 10.00 2.31 1.10 3.41 100000
select_2_rows 10.00 2.65 0.94 3.59 100000
select_big 8.00 6.89 0.17 7.06 80
select_big_str 4.00 1.36 0.70 2.06 10000
select_cache 26.00 1.05 0.18 1.23 10000
select_cache2 25.00 1.03 0.19 1.22 10000
select_column+column 11.00 2.61 0.87 3.48 100000
select_diff_key 0.00 0.06 0.03 0.09 500
select_distinct 3.00 0.73 0.04 0.77 800
select_group 10.00 0.72 0.16 0.88 2911
select_join 1.00 0.22 0.01 0.23 100
select_key 70.00 26.28 7.84 34.12 200000
select_key2 48.00 21.32 3.43 24.75 200000
select_key2_return_key 60.00 24.12 5.96 30.08 200000
select_key2_return_prim 51.00 21.54 4.22 25.76 200000
select_key_prefix 47.00 20.75 3.57 24.32 200000
select_key_prefix_join 3.00 1.67 0.02 1.69 100
select_key_return_key 56.00 23.19 5.72 28.91 200000
select_many_fields 6.00 2.04 0.35 2.39 2000
select_range 31.00 3.13 0.08 3.21 410
select_range_key2 6.00 2.10 0.38 2.48 25010
select_range_prefix 8.00 2.31 0.58 2.89 25010
select_simple 11.00 2.70 1.92 4.62 100000
select_simple_cache 11.00 2.89 1.71 4.60 100000
select_simple_join 0.00 0.25 0.04 0.29 500
update_big 9.00 0.00 0.00 0.00 10
update_of_key 8.00 1.42 0.69 2.11 50000
update_of_key_big 6.00 0.02 0.01 0.03 501
update_of_primary_key_many_keys 5.00 0.01 0.01 0.02 256
update_with_key 44.00 7.05 3.74 10.79 300000
update_with_key_prefix 14.00 3.85 1.03 4.88 100000
wisc_benchmark 2.00 1.02 0.08 1.10 114
TOTALS 1084.00 297.06 71.81 368.87 3375950
```

So as you can see not much incentive here. I know that for advanced use cases MariaDB offers some new features and improvements but for a normal use case as for example the web server hosting this site there's no major advantage.