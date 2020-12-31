What if we wanted to retrieve something more complicated, like a list of all the post titles, and the author of those posts?

For this, we'd need to join the data from our posts table to the data in our users table.

`select p.id, json_extract(p.data, '$.title'), json_extract(u.data, '$.name') from posts p inner join users u on u.id = json_extract(p.data, '$.userId');`{{execute}}

Using the `json_extract` function allows us retrieve any value we want from our JSON data. 

Feel free to play around with this database and some of the other [SQLite JSON functions](https://www.sqlite.org/json1.html) to get a feel for how these functions work.