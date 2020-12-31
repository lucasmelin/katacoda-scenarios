In our data directory, we have the JSON files that come from our third-party. For this scenario, we're using data from [JSON Placeholder](https://jsonplaceholder.typicode.com/).

`ls -lrt data`{{execute}}

We can look at the contents one of the `json` files.

`cat users.json`{{execute}}

To load the data in our JSON files into our SQLite database, we'll write a simple [Python](https://www.python.org/) script.

To start working with Python, use the following command:

`python`{{execute}}
