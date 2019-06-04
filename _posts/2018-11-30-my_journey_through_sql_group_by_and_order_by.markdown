---
layout: post
title:      "My Journey Through SQL, GROUP BY, and ORDER BY"
date:       2018-11-30 03:22:57 -0500
permalink:  my_journey_through_sql_group_by_and_order_by
---


**Note to Readers:** While I will be covering SOME concepts from SQL and SQLite, I will not be covering ALL of them; I would not recommend reading further unless you have a basic understanding of SQL commands. After I give an introduction to SQL and databases and how they can be used in web applications, I will go more in depth about an issue that I struggled with: the difference between GROUP BY and ORDER BY. (I could go into syntax issues that I encountered with other commands, but I would probably need to separate that into at least three blog posts! Let's save that for another time, shall we?)

**-------------------------------**

**Part 1**

Up until this point, I have been making Ruby variables, arrays, methods, objects, etc. by using data either from the programmer, the user, or scraped websites. That all changes starting with SQL. Short for "Structured Query Language", this allows me to write data to and read data from relational databases. A relational database can be thought of as a collection of tables that can relate to each other, much like how objects in Ruby can relate to each other. There are other database types out there, but I will not get into that here. However, if anyone wishes to know more about database types, you can find some good information here: [https://dzone.com/articles/the-types-of-modern-databases](https://dzone.com/articles/the-types-of-modern-databases).

Also, I’m beginning to see how Ruby and other languages can be used to interact with databases. I could see a Ruby class method #self.new_from_database being used to split a returned string from SQLite. For instance, the Learn lesson [SQL Inserting, Updating, and Selecting](https://github.com/learn-co-students/sql-insert-select-update-code-along-v-000) has us enter the command 

`SELECT * FROM cats WHERE age < 2;`

which returns 

`3|Hannah|1|Tabby`

By sending this output to #self.new_from_database, you could EASILY make a Cat object out of that! And as the lesson mentions, SQL and databases are handy for applications that have multiple users: to let the user log in, find the user in the database whose information matches the login credentials.  There are other applications as well: everyone (especially those who manage companies and employees) who needs to keep and access a record of people, activities, items, dates, etc, will most likely use a database (and by extension, SQL or a similar language) at some point.

**-------------------------------**

**Part 2**

Now, what exactly is the difference between GROUP BY and ORDER BY, and how do I use these commands properly? For a while, I had thought that you could use both of them to sort the data; it certainly SEEMED that way at first, but then why would there be two commands that accomplish virtually the same thing?

Well, it turns out I was only half right: ORDER BY is indeed used to sort data. However, GROUP BY is another story. Now, every command/method/function that returns a set of data has to return it in some default order, but *it's not the job of every command, GROUP BY included, to actually SORT that data!* But, then, what *is* GROUP BY supposed to do?

I think the best way to explain this is with an example. Check out the table below, courtesy of [http://support.sas.com/documentation/cdl/en/sqlproc/63043/HTML/default/viewer.htm#n00fjmxaad37mgn1rszsatq472zs.htm](http://support.sas.com/documentation/cdl/en/sqlproc/63043/HTML/default/viewer.htm#n00fjmxaad37mgn1rszsatq472zs.htm).

![](http://support.sas.com/documentation/cdl/en/sqlproc/63043/HTML/default/images/proc-sql-ex3staff.png)

Let's call that table "staff". Notice that there are a few people who live in the same city. Suppose we want to know how many people live in each city. How would we do that in SQL (or SQLite)? Well, we know that we want information about the cities and the COUNT of people who live in them. Let's start with that:

```
SELECT city, COUNT(*) FROM staff;
```

Note that I am using COUNT(\*) instead of COUNT(city) or COUNT(fname), although these are perfectly acceptable as well. However, since I am simply counting the number of people living in a city (each person being a row), \* is arguably the best option in this case. (For other ways to use COUNT, visit https://community.modeanalytics.com/sql/tutorial/sql-count/).

Here's what gets returned:

```
city     | COUNT(*)

NEW YORK | 10
```

That's not what we want, is it? What happened? Well, since there's 10 people in the table, this SQL query seems to have counted them all up and displayed them next to the last city in the table, NEW YORK. How do we fix this? That's where GROUP BY comes into play. Watch what happens when we do this:

```
SELECT city, COUNT(*) FROM staff
GROUP BY city;
```

And here's what we get:

```
city         | COUNT(*)

BRIDGEPORT   | 1
NEW YORK     | 5
PATERSON	 | 1
PRINCETON    | 1
STAMFORD	 | 2
```

And there we go! That's exactly what we wanted! Why did it work? Here's what happened: GROUP BY combined *each* person/row with the same city into *one*. COUNT, in turn, counted the number of rows that had been GROUPED into one for each city. That's what GROUP BY does: *it aggregates/combines/groups rows together,* according to the column specified, and it returns rows of unique column values.

Strangely enough, it also appears to sort those column values in ASC order, at least in SQLite. Now, I know that this may not be entirely correct, but look at the facts: the cities (and everything else) in the original table is in a completely random order, yet when I GROUPED the table by city, SQLite returned them in ASC order alphabetically! As I discovered, this is also true if I reverse the order of columns (COUNT(\*), city).

Regardless, though, as I mentioned earlier, it is not the GROUP BY clause's job to sort the results; that job belongs to ORDER BY. Let's try that out. I think I would like to see the above results ORDERED by the COUNT of people in a city in descending order. And since there's more than one city containing just one person, let's sort those cities in reverse alphabetical order. Here's how:

```
SELECT city, COUNT(*) FROM staff
GROUP BY city
ORDER BY COUNT(*) DESC, city DESC;
```

That returns:

```
city          | COUNT(*)

NEW YORK	  | 5
STAMFORD	  | 2
PRINCETON 	| 1
PATERSON	  | 1
BRIDGEPORT	| 1
```

And there you go! ORDER BY sorted the data! Note that if GROUP BY was supposed to sort the data, then ORDER BY would not have been able to change the order that the cities were listed in. We can safely conclude, then, that we are supposed to use ORDER BY to sort the data, rather than GROUP BY.

Side note: I should note that SQLite is smart! When I initially tried out the ORDER BY clause, I didn't include the "city DESC" part. Despite that, however, SQLite *automatically* sorted Princeton, Paterson, and Bridgeport (the cities containing only one person) in ASC alphabetical order!

For more information on the difference between GROUP BY and SORT BY, visit https://www.essentialsql.com/what-is-the-difference-between-group-by-and-order-by/.

**-------------------------------**

**Conclusion**

So, there you have it! Just to summarize, SQL and databases are critical to the success of a web application, and they are used in many other situations as well. As for GROUP BY and ORDER BY, the main difference is that GROUP BY is used to group together rows containing the same values in a given column; when used with aggregate functions like COUNT, its importance is all the more apparent. ORDER BY, on the other hand, is used to sort the results of your query into a specified ORDER. 

Also, as I hinted at the beginning, be CAREFUL to use proper syntax; not everything works in SQL or SQLite the way you think it might. For example, you can put COUNT, SUM, and other aggregate functions in the ORDER BY clause and the HAVING clause, but *not* in the GROUP BY clause or the WHERE clause (at least in SQLite).  I would go into further detail about things like this, but that is a subject for another blog post (or two or three...). I could also go into subqueries, but I think I've gone far enough down the rabbit-hole for one day.

The absolute LAST thing I will mention is that knowing the order of statements to use in a SQL query has helped me a lot. Here is that order, courtesy of [Learn's "Grouping and Sorting Data" lesson](https://github.com/learn-co-students/sql-grouping-and-sorting-readme-v-000):

1.	SELECT 
2.	FROM
3.	JOIN
4.	ON
5.	WHERE
6.	GROUP BY
7.	HAVING
8.	ORDER BY
9.	LIMIT

I hope this helps you gain a better understanding of SQL and its applications. Congratulations on reaching the end of this blog post, and Happy Programming!

**Feedback**

I am always open to suggestions for improvement on my blog posts! If you have any feedback for me, please feel free to [raise an issue here](https://github.com/Sdcrouse/Sdcrouse.github.io). I will do my best to get back to you promptly.

