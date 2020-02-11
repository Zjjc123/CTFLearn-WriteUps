# Basic Injection
Difficulty: Easy | Category: Web
## Process
Since it's called basic injection it literally just has to be SQL injection...

We see a basic wesbite with one text box

![](https://i.imgur.com/wNUP2Hk.png)

Looking at the html we see it recommends us to try the names "Hiroki, Noah, Luke"

![](https://i.imgur.com/KGAltQa.png)

Trying all three reveals Luke is a viable input.. But also reveals the datatable

We can assume the code to get the input is something like this

~~~java
name = getRequestString("name");
sql = "SELECT * FROM somedatatable WHERE Name ='" + name + '";
~~~
where the SQL statement is ran

A simple trick from [w3school](https://www.w3schools.com/sql/sql_injection.asp) is to use OR then an equality to return all data from the table

By adding something like ' OR '' = '

the SQL statement goes from 

~~~SQL
SELECT * FROM somedatatable WHERE Name = 'name inputed'
~~~

to

~~~SQL
SELECT * FROM somedatatable WHERE Name = '' OR '' = ''
~~~

which returns all data

By inputting that we get
![](https://i.imgur.com/LLowDnA.png)

It's sorta obvious from there

## Flag
~~~
th4t_is_why_you_n33d_to_sanitiz3_inputs
~~~

