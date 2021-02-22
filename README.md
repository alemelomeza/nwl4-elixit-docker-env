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

Edit the file `mix.exs` to install the dependency `credo`:

```
defp deps do
    [
      ...
      {:credo, "~> 1.5", only: [:dev, :test], runtime: false}
    ]
end
```

Update dependencies:
  
```sh
docker exec -it elixir mix deps.get
```

Generate configuration:

```sh
docker exec -it elixir mix credo gen.config
```

Edit file `credo.exs`:

````
{Credo.Check.Readability.ModuleDoc, false},
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

Start server:

```sh
docker exec -it elixir mix phx.server
```

Use `iex`:

```sh
docker exec -it elixir iex -S mix
```

Recompile in `iex`:

```
recompile
```

Run tests:

```sh
docker exec -it elixir mix test
```

Stop environment:

```sh
docker-compose down
```