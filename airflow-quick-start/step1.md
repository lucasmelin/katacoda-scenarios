Our Airflow installation needs a directory where it can store its files. By default, the directory is `airflow` under your [home directory](https://en.wikipedia.org/wiki/Home_directory), or `~/airflow` for short.

`export AIRFLOW_HOME=~/airflow`{{execute}}

Now we can install Airflow from the [Python Package Index](https://pypi.org/) using pip.

`pip install apache-airflow`{{execute}}

With the package installed on our system, we can now initialize a database.

`airflow db init`{{execute}}

This will create a new SQLite database for us, and run the migration scripts to create the necessary database tables and columns for Airflow to function.

Next, we can create a user account that will allow us to login to Airflow:

```
airflow users create \
    --username admin \
    --firstname Peter \
    --lastname Parker \
    --role Admin \
    --email spiderman@superhero.org
```{{execute}}

At this point, all that's left is to start the scheduler, which will schedule our workflows:

`airflow scheduler -D`{{execute}}

and also the webserver:

`airflow webserver --port 8080`{{execute}}

You should now be able to visit https://[[HOST_SUBDOMAIN]]-8080-[[KATACODA_HOST]].environments.katacoda.com/ to see the login page for the web UI!