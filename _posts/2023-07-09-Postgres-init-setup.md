---
title: Postgres init setup
categories: ["postgres"]
---

# Install postgres

```sh
apt update
apt upgrade -y
apt install postgresql postgresql-contrib -y
```

# Set password for postgres user

switch to postgres user

```sh
su - postgres
```

enter postgres shell

```sh
psql
```

set password for postgres user

```sh
\password postgres
```

# Postgres config file

```sh
vim /etc/postgresql/14/main/postgresql.conf
vim /etc/postgresql/14/main/pg_hba.conf
```

after editing, restart postgres

```sh
systemctl restart postgresql
```

# Cancel peer authentication for postgres user

```sh
vim /etc/postgresql/14/main/pg_hba.conf
```

change

```sh
local   all             postgres                                peer
```

to

```sh
local   all             postgres                                md5
```

# Create new user

```sh
su - postgres
createuser --help
```

# Create new database

```sh
su - postgres
createdb yourdbname
```
