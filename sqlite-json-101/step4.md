Now, we'll load the contents of each file into the corresponding database table:

```
import json

with closing(sqlite3.connect('test.db')) as conn:
    with conn:
        for file in files:
            with file.open() as input_file:
                data = json.load(input_file)
                for record in data:
                    conn.execute(f"insert into {file.stem} values (?, ?)", [record['id'], json.dumps(record)])

print("Loaded JSON data")
```{{execute}}

As you can see, loading our data into the database wasn't too complicated. We didn't need to design each table individually, or choose the size or data type of each column. We also didn't need to transform the JSON data into a tabular format like a csv, or do any other manipulations to our data.

We simply created two columns, one with an `id`, and the other with a raw dump of our JSON data. Super simple database schema design.

Now, let's move on to querying our data!