Next, we'll create our database tables, one for each file:

```
import sqlite3
from contextlib import closing

with closing(sqlite3.connect('test.db')) as conn:
    with conn:
        for filename in filenames:
            conn.execute(f"CREATE TABLE {filename} (id varchar(3), data json)")

print("Created tables")
```{{execute}}

We use the `closing` context manager to close our database connection for us automatically, since the [default SQLite context manager](https://docs.python.org/3/library/sqlite3.html#using-the-connection-as-a-context-manager) is only used for committing transactions.
