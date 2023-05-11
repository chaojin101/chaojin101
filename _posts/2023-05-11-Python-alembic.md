---
title: "Python alembic usage"
categories: ["usage"]
tags: ["python"]
---

This article will introduce basic usage about alembic for migration about SQLAlchemy.

> I'm in windows 10 and python 3.11.2
> {: .prompt-info }

## Setup

I'm currently in `alembic-example` folder.

Create a virtual environment for python.

```sh
python -m venv venv
```

Activate virtual environment

```sh
.\venv\Scripts\activate
```

Install dependencies.

```sh
pip install alembic psycopg2-binary
```

Run cmd `alembic init {alembic_folder_name}`

```sh
alembic init alembic
```

It will create a folder named `alembic` and a file named `alembic.ini`.

---

In `alembic-example` folder, create an `app` folder and create a file name `database.py`.

In `database.py`, you need to configure your connection string `CONNECTION_STR`

```py
import sqlalchemy
from sqlalchemy.orm import sessionmaker, declarative_base

# Config your connction string //{username}:{password}@{host}:{port}/{database}
CONNECTION_STR = 'postgresql+psycopg2://postgres:mysecretpassword@localhost:5432/postgres'

engine = sqlalchemy.create_engine(url=CONNECTION_STR)
SessionLocal = sessionmaker(bind=engine, autocommit=False, autoflush=False)

Base = declarative_base()
```

In `app` folder, create a file named `models.py`.

In `models.py`, I simply import `database.py`'s `Base` and create a simple table.

```py
from app.database import Base

import sqlalchemy as sa

class User(Base):
    __tablename__ = 'user'

    id = sa.Column(sa.Integer, primary_key=True, nullable=False)
```

And I also create a `__init__.py` in `app` folder.

Now, the folder's structure should be similar like this:

```
alembic-example/
  alembic/
    ...
  alembic.ini
  app/
    __init__.py
    database.py
    models.py
```

## Configure alembic

In `alembic.ini`, change `sqlalchemy.url`

from

```ini
sqlalchemy.url = driver://user:pass@localhost/dbname
```

to

```ini
sqlalchemy.url = postgresql+psycopg2://postgres:mysecretpassword@localhost:5432/postgres
```

---

In `alembic/env.py`, change

from

```py
target_metadata = None
```

to

```py
from app.models import Base
target_metadata = Base.metadata
```

## Run alembic

### Create a new version

Run `alembic revision --autogenerate -m "{your simple description}"`

```sh
alembic revision --autogenerate -m "First revision"
```

This will generate a migration script in `alembic/revision/` folder and a table named `alembic_version` in database which will be used for controlling database version.

### Migrate up

Run `alembic upgrade +1` will upgrade database 1 version,

or run `alembic upgrade head` will upgrade database to newest version

```sh
alembic upgrade +1
```

Now the database create a table named `user`, a column `id` and an index for `id`

### Modify table and migrate up

Add a new column `username` for `user`

In `models.py`

```py
from app.database import Base

import sqlalchemy as sa

class User(Base):
    __tablename__ = 'user'

    id = sa.Column(sa.Integer, primary_key=True, nullable=False)
    username = sa.Column(sa.String, index=True)
```

Run

```sh
alembic revision --autogenerate -m "Add username for user"
alembic upgrade +1
```

refresh the database and see the result, it works.

### Migrate down

Migrade down 1 version

```sh
alembic downgrade -1
```

Migrade down to the base

```sh
alembic downgrade base
```

## Takeaway

I think the best pratice is:

- when you migrate up you `git commit` the related model file
- when you migrate down you `rollback to related model file`

```sh
alembic revision --autogenerate -m "First revision"
alembic upgrade +1
alembic upgrade head
alembic downgrade -1
alembic downgrade base
```

## Related

- [Intro to Database Migrations with Alembic(9min video)](https://www.youtube.com/watch?v=SdcH6IEi6nE)
- [Official doc](https://alembic.sqlalchemy.org/en/latest/tutorial.html#relative-migration-identifiers)
- [Repository for this example](https://github.com/chaojin101/alembic-example)
