# playlists

## Server

Playlists uses [graphene-sqlalchemy] to query data across a model of playlists, users and locations.

An example query,
```
{
 users {
   username,
   firstName,
   lastName,
   playlists {
       url,
       startDate,
       endDate,
       location {
           country,
           city,
           state,
       }
   }
 }
}
```

### Setup

#### Virtual Environment

Setup up python 3 and [poetry].

Command to install poetry, system-wide.

```bash
pip install --user poetry
```

Copy .env.example to .env

```bash
cp .env.example .env
```

Create a new postgres database and use the environment variables in .env.example based on the example.

Activate poetry shell and install the dependencies

```bash
brew switch python@3 3.7.0 # You made to brew install python 3.7.0
poetry shell
poetry install
```
Source the environment variables into your shell

`source .env`

All commands to follow require an activated virtual environment with environment variables sourced in the local shell.

#### Migrations and Seeding

Run the migrations

```bash
alembic upgrade head
```

Seed the database, by running the cli app

```bash
python playlists/cli.py
```

### Serve

Serve the server side code from the main directory

```bash
python playlists/app.py serve
```

Navigate to <http://0.0.0.0:8080/index>

## Client

### Setup

Make sure npm installed

### Serve

Serve the client side code using

`npm start`

Open <http://localhost:3000> to view it in the browser.

[graphene-sqlalchemy]: https://github.com/graphql-python/graphene-sqlalchemy
[poetry]: https://poetry.eustace.io/
