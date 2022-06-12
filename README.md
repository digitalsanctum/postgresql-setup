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


## config

