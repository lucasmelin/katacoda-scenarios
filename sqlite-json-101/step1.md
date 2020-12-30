## Loading our data

In our data directory, we have a few dummy JSON files.

`ls -lrt data`{{execute}}

For this example, we'll use Python to load the data in our JSON files into our SQLite database.

To start working with Python, use the following command:

`python`{{execute}}

We'll start by collecting all the filenames in our data directory, excluding the extension.

```
from pathlib import Path

files = list(Path("data").glob('**/*.json'))
filenames = [f.stem for f in files]

print(filenames)
```{{execute}}

Next, we'll create a database table for every one of our files:

```
import sqlite3
from contextlib import closing

with closing(sqlite3.connect('test.db')) as conn:
    with conn:
        for file in filenames:
            conn.execute(f"CREATE TABLE {file} (id varchar(3), data json)")

```{{execute}}

Now we can load the contents of each file into the corresponding database table:

```
import json

with closing(sqlite3.connect('test.db')) as conn:
    with conn:
        for file in filenames:
            with (Path("data") / file).open() as f_in:
                data = json.load(f_in)
                conn.execute(f"insert into {file} values (?, ?)", [{file}['id'], json.dumps(data)])

```{{execute}}

As you can see, it was relatively easy to load our data into the database. We didn't need to design each table individually, or choose the size or data type of each column. We also didn't need to transform the JSON data into a tabular format like a csv, or do any other manipulations to our data.

We simply created two columns, one with an `id`, and the other with a raw dump of our JSON data.

Now, let's move on to querying our data!
