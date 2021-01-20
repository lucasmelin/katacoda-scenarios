In the comments that we loaded, there's an email field. If we wanted to find all the emails that exist in our comments table, we could use the `json_extract` function to return a list of the emails:

`select json_extract(data, '$.email') from comments;`{{execute}}

If we instead wanted to export this data to a csv file, we would have to set the mode to csv.

`.mode csv`{{execute}}

Then we could specify the file location to save our csv content.

`.once ./dataout.csv`{{execute}}

When we now re-run our original query, instead of printing the output to the console, the data is instead written to our file.

`select json_extract(data, '$.email') from comments;`{{execute}}

If we exit the SQLite CLI `.exit`{{execute}} then we can see that our `dataout.csv` file has been generated `ls -lrt`{{execute}} and that it contains the content we expect.

`cat dataout.csv`{{execute}}

Let's jump back into the SQLite CLI to try something else.

`sqlite3`{{execute}}
`.open test.db`{{execute}}
