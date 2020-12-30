## Querying our data

At this point, you might be thinking to yourself "We just blindly inserted our JSON data into a single column in the database. How are we ever going to be able to query it back out properly?"

Thankfully for us, many databases these days come with support for JSON data out-of-the box. In SQLite's case, this functionality is provided by an extension called [JSON1](https://www.sqlite.org/json1.html) which is usually available by default in most SQLite installations.

This extension provides SQL functions for working with JSON data. Let's look at the `json_extract` function first.

In the comments that we loaded, there's an email field. If we wanted to find all the emails that exist in our comments table, we could use the `json_extract` function to return a list of the emails:

`select json_extract(data, '$.email') from comments;`{{execute}}