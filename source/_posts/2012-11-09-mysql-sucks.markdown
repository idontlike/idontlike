---
layout: post
title: "mysql sucks"
date: 2012-11-09 00:19
comments: true
categories: ["mysql","innodb"] 
---
## Did you know?
When you'r altering some table in mysql, maybe adding column or even just adding index *entire table is locked for writing*. That mean, if adding index takes 5 minutes, nobody will able to write to any row on the table anithing during this 5 minutes.

You know what? Do you have heavy update statement that runs every 5 minutes? Do with this something, because *whole the table is locked*. Do you want to execute delete statement that takes a lot of time? Think twice. Test the behavior on development server. I have tried `delete from some_table where not_indexed_column like '%a%b%'"`. It takes a lot of time. And i can't execute any other update query in this time.

Okey, now you will go the [manual](http://dev.mysql.com/doc/refman/5.0/en/innodb-locks-set.html)
> A locking read, an UPDATE, or a DELETE generally set record locks on every index record that is scanned in the processing of the SQL statement. It does not matter whether there are WHERE conditions in the statement that would exclude the row.

I lied (everybody lies (c) dr. House). So not allways all the table is locked, but only if every row is scanned during the process. (so don't forget indexes, it is not only speed ups the query run, but make it possible to others queries to be executed).

You know there is some work-arounds for altering table without locking as well. Just be aware. Ask your DBA before you doing things.
