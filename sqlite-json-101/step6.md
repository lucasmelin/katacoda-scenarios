Let's take a look at the top 5 rows from our posts table:

`select * from posts limit 5;`{{execute}}

There are two columns in our table - the post `id` column and the `data` column, which contains our entire JSON data.

At this point, you might be thinking to yourself "That JSON data looks pretty messy, just shoved into a single column like that. How are we ever going to be able to query it back out properly?".

Thankfully for us, many databases these days come with support for JSON data out-of-the box. In SQLite's case, it has an extension called [JSON1](https://www.sqlite.org/json1.html) which is available by default in most SQLite installations.

This extension provides specific functions available to our SQLite CLI for working with JSON data.