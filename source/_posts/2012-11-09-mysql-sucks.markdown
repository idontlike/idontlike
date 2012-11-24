---
layout: post
title: "mysql sucks"
date: 2012-11-09 00:19
comments: true
categories: ["mysql","innodb"] 
---
## Did you know?
Adding index to a table in mysql locks entire table for writing.
<!-- more -->
When you'r altering some table in mysql, maybe adding column or even just adding index *entire table is locked for writing*. That mean, if adding index takes 5 minutes, nobody will able to write to any row on the table anithing during this 5 minutes.

You know what? Do you have heavy update statement that runs every 5 minutes? Do with this something, because **whole the table is locked**. Do you want to execute delete statement that takes a lot of time? Think twice. Test the behavior on development server. I have tried `delete from some_table where not_indexed_column like '%a%b%'"`. It takes a lot of time. And i can't execute any other update query in this time.

Okey, now you will go to the [manual](http://dev.mysql.com/doc/refman/5.0/en/innodb-locks-set.html)
> A locking read, an UPDATE, or a DELETE generally set record locks on every index record that is scanned in the processing of the SQL statement. It does not matter whether there are WHERE conditions in the statement that would exclude the row.

I have lied (everybody lies (c) dr. House). Not allways all tables are locked, but those that are scanned by mysql during the query process. (so don't forget to add indexes. It not only speed ups the query run, but makes it possible to others queries to be executed and not stucked waiting for a lock free).

You know there is some work arounds for altering table without locking (or with less locking time). For example you can play with temporary table making altering there and synchronizing after with original. So you can drop the original table and rename the temporary at the end.

I don't give solutions here. Just warn you. And emphasize that **i don't like** it.
