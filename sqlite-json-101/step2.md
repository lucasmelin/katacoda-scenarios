## Querying our data

At this point, you might be thinking to yourself "We just blindly inserted our JSON data into a single column in the database. How are we ever going to be able to query it back out properly?"

Thankfully for us, many databases these days come with support for JSON data out-of-the box. In SQLite's case, this functionality is provided by an extension called [JSON1](https://www.sqlite.org/json1.html) which is usually available by default in most SQLite installations.

This extension provides functions available from the SQLite CLI (command line interface) for working with JSON data.

We'll start by installing the SQLite CLI.

`sudo apt-get install sqlite3`{{execute}}

We can then launch the CLI with the `sqlite3`{{execute}} command.

Next, we can open our database with our JSON data.

`.open test.db`{{execute}}

With a connection open to our database, we can now start querying the data.

Let's look at the `json_extract` function first.

In the comments that we loaded, there's an email field. If we wanted to find all the emails that exist in our comments table, we could use the `json_extract` function to return a list of the emails:

`select json_extract(data, '$.email') from comments;`{{execute}}

If we instead wanted to export this data to a csv file, we would have to set the mode to csv.

`.mode csv`{{execute}}

Then we could specify the file location to save our csv content.

`.once ./dataout.csv`{{execute}}

When we now re-run our original query, instead of printing the output to the console, the data is instead written to our file.

`select json_extract(data, '$.email') from comments;`{{execute}}