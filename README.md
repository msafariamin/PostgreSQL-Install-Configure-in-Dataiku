# PostgreSQL-Install-Configure-in-Dataiku

Installing Postgres.app on macOS:

Fisrt at all download Postgres.app from the Postgres.app website.
To install Postgres.app, just drag it to your Applications folder and double click.

Postgres.app must be placed in the /Applications folder, and you can’t rename it. The reason for this is that it includes a lot of dynamic libraries that can be used by other software. These libraries can’t be found if you change the path.

If you’d like to use the command line tools delivered with Postgres.app, execute the following command in Terminal to configure your $PATH, and then close & reopen the window:

```
sudo mkdir -p /etc/paths.d && 
echo /Applications/Postgres.app/Contents/Versions/latest/bin | sudo tee /etc/paths.d/postgresapp
```

Whatever method you use, you can check if the path is set up correctly by typing ''' which psql '''.


Create And Configure Your PostgreSQL Database in Dataiku:

You should add a user at first:
Once you've initially installed Postgres you should be able to connect almost immediately with psql -h localhost. This will put you inside your database to begin working. Of course the next step before doing anything else is to create a user account for yourself.

In the terminal type:

```
Mary$ psql -h localhost
psql (12.0)
```

```
Mary=# CREATE DATABASE dku;
CREATE DATABASE
```

```
Mary=# \c dku
You are now connected to database "dku" as user "Mary"
```

Here, i get a example for tshirt dataset of a store.

```
dku=# CREATE SCHEMA dku_tshirt;
CREATE SCHEMA
```

```
dku=# CREATE USER Mary WITH PASSWORD 'Password'
CREATE ROLE
```
New user Mary is created with password 'Password'.
Next step is to create a database (schema) and grant access to the user Mary.

```
Mary=# GRANT ALL PRIVILEGES ON SCHEMA dku_tshirt TO Mary;
GRANT
```

Now Mary has all privileges on database Mary. There are several different kinds of privilege: Select, Insert, Update, Delete, Rule, References, Trigger, Create, Temporary, Execute, and Usage.
"GRANT SELECT" allows Mary ONLY to do select query on database Mary

```
dku=# \q
```

This sample code creates the user Mary, with password Password, and grants this user all privileges (can create and delete tables) on the dku_tshirt schema in the dku database.
Similarly, user "x" has been granted all privileges on the "y" schema in the database.

Now, you have to add your database in Dataiku DSS by going to menu  > Administration > Connections > New Connection > PostgreSQL
You give here the parameters of your database and create. Now you have connected the database to Dataiku.
choose to store the new dataset into the PostgreSQL_tshirt (the name that you choose in new connection name).







