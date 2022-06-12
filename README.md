# postgresql-setup

The following are instructions for setting up a new PostgreSQL database on Ubuntu. These instructions assume that the db host does not have a public route so be careful!

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

NOTE: To install a newer vesrion (>12), following instructions here: https://wiki.postgresql.org/wiki/Apt


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

Second, update `/etc/postgresql/12/main/pg_hba.conf` and add the following lines:

```
host    all             all              0.0.0.0/0                       md5
host    all             all              ::/0                            md5
```

Now, restart postgresql server:

```
sudo service postgresql restart
```

## references
* https://www.digitalocean.com/community/tutorials/how-to-install-postgresql-on-ubuntu-20-04-quickstart
* https://www.bigbinary.com/blog/configure-postgresql-to-allow-remote-connection
* https://wiki.postgresql.org/wiki/Apt




