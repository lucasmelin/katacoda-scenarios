## Welcome!

Let's pretend for a moment that you've been given a bunch of JSON data from a third-party. You've been asked to join the data together and generate some csv exports. You also need a way for others to access the data and query it using SQL.

You think to start by looking at the JSON data and designing a relational database schema that matches the JSON data. Then, you might build a script that takes your JSON data and transforms it into a tabular format for loading into your database.

But that approach can be slow and full of pitfalls:
  * Designing a database schema that matches our data can take time.
  * If the format of the JSON data changes in the future, the database schema will need to be changed as well.
  * If the data contains nested objects, transforming the JSON data into a format that can be loaded into the database can require complex conditionals and looping logic.

But perhaps there's an easier way...

In this scenario, we're going to be using [SQLite](https://www.sqlite.org/) to work with JSON data. Let's get started!