# postgresql-setup

The following are instructions for setting up a new PostgreSQL database.

## install


```shell
# Update the package lists:

sudo apt-get update
```


```
# Install the latest version of PostgreSQL.
# If you want a specific version, use 'postgresql-12' or similar instead of 'postgresql':

sudo apt install postgresql postgresql-contrib -y
```

## create role

```
sudo -u postgres psql
createuser --interactive
```

output:
```
Enter name of role to add: shane
Shall the new role be a superuser? (y/n) y
```

An assumption that the Postgres authentication system makes by default is that for any role used to log in, that role will have a database with the same name which it can access.
```
sudo -u postgres createdb shane
```


## config

Two changes are necessary in order to allow connections to databases aside from localhost.

First, update `/etc/postgresql/12/main/postgresql.conf` and replace the line:

```
listen_addresses = 'localhost'
```

with

```
listen_addresses = '*'
```



