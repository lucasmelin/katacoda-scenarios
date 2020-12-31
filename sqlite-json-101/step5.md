At this point, we could continue to use python, or any other programming language to query our data.

But for this scenario, we'll look at using the SQLite CLI (command line interface).

Let's start by making sure it's installed:

`sudo apt-get install sqlite3`{{execute}}

We can then launch the CLI with the `sqlite3`{{execute}} command.

Next, we can open our database with our JSON data.

`.open test.db`{{execute}}

With a connection open to our database, we can now start querying the data.
