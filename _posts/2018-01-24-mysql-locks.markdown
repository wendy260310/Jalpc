---
layout: post
title:  "3 Steps (2 minutes) to Setup Your Personal Website with Jalpc"
date:   2017-01-31
desc: "3 Steps (2 minutes) to Setup Your Personal Website with Jalpc"
keywords: "Jalpc,Jekyll,gh-pages,website,blog,easy"
categories: [HTML]
tags: [Jalpc,Jekyll]
icon: icon-html
---
  The official [InnoDB locking doc][mysql_innodb_locking_url] gives us some info about innodb locking,but after read it , I am still confused about some questions,so this I write this post.
{% highlight ruby %}
My computer is MacBook Pro (15-inch, 2017),and my mysqlversion is
Ver 14.14 Distrib 5.7.19, for osx10.12(x86_64) using  EditLine wrapper
{% endhighlight %}
  mysql example schema is
{% highlight ruby %}
create table lock_test (
	`col1` int,
	`col2` int,
	`col3` int,
	key idx_col1(`col1`),
	unique key uniq_col2(`col2`)
)Engine=InnoDB;
insert into lock_test(`col1`,`col2`,`col3`) values(2,1,5),(3,2,5),(3,3,4),
       (1,4,6);
{% endhighlight %}
#### 1. When to use `select ... for update`
Mysql calls `select ... for update` and `select ... lock in share mode` [locking read][locking_read]
{% highlight ruby %}
If you query data and then insert or update related data within the same 
transaction, the regular SELECT statement does not give enough protection.
Other transactions can update or delete the same rows you just queried
{% endhighlight %}
The example posted in the documentation is clear enough for understand the meaning,here is a question from stackoverflow I asked before,[this question][locking_read_question] shows different behavior between
[locking read][locking_read] and [consistent nonlocking read][consistent_nonlocking_read].

#### 2. InnoDB locks with or without index
Here is a example in repeatable read isolation.
{% highlight ruby %}
case 1:(with a index)
session a :
start transaction;
select * from lock_test where `col1`= 3 for update;

session b:
update lock_test set `col3`=5 where `col1`= 2;// update success,no hangs

case 2:(no index)
session a :
start transaction;
select * from lock_test where `col3`= 5 for update;
session b:
update lock_test set `col3`= 5 where `col1`= 2 ;// hangs
{% endhighlight %}

[mysql_innodb_locking_url]:https://dev.mysql.com/doc/refman/5.7/en/innodb-locking.html
[locking_read]:https://dev.mysql.com/doc/refman/5.7/en/innodb-locking-reads.html
[consistent_nonlocking_read]:https://dev.mysql.com/doc/refman/5.7/en/innodb-consistent-read.html
[locking_read_question]:https://stackoverflow.com/questions/45558837/mysql-repeatable-read-get-other-sessions-commit-when-use-select-for-update
[lock_with_without_index]:https://www.percona.com/blog/2015/04/09/innodb-locks-deadlocks-without-index-different-isolation-level/
