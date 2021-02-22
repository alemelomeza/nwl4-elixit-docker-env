# Elixir development environment

Elixir+PostgreSQL development environment for Rocketseat' Next Leve Week 4 (NLW#4).

Requirements:

* Docker
* docker-compose

## Installation

Start environament:

```sh
docker-compose up -d
```

Install `hex` `phx_new 1.5.7`:

```sh
docker exec -it elixir mix archive.install hex phx_new 1.5.7
```

Create project:

```sh
docker exec -it elixir mix phx.new . --no-webpack --no-html
```

Configure database hostname in files `config/dev.exs` `config/test.exs`:

```
...
hostname: "postgres",
...
```

Run migrations:

```sh
docker exec -it elixir mix ecto.setup
```

## Usage

Start environment:

```sh
docker-compose up -d
```

Access `Elixir`:

```sh
docker exec -it elixir /bin/bash
```

Access `PostgreSQL`:

```sh
docker exec -it postgres psql -U postgres
```

Stop environment:

```sh
docker-compose down
```