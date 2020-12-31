In the comments that we loaded, there's an email field. If we wanted to find all the emails that exist in our comments table, we could use the `json_extract` function to return a list of the emails:

`select json_extract(data, '$.email') from comments;`{{execute}}

If we instead wanted to export this data to a csv file, we would have to set the mode to csv.

`.mode csv`{{execute}}

Then we could specify the file location to save our csv content.

`.once ./dataout.csv`{{execute}}

When we now re-run our original query, instead of printing the output to the console, the data is instead written to our file.

`select json_extract(data, '$.email') from comments;`{{execute}}