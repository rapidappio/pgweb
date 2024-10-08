# pgweb

Simple web-based and cross platform PostgreSQL database explorer.

[![Release](https://img.shields.io/github/release/sosedoff/pgweb.svg?label=Release)](https://github.com/rapidappio/pgweb/releases)
[![Linux Build](https://github.com/rapidappio/pgweb/actions/workflows/checks.yml/badge.svg)](https://github.com/rapidappio/pgweb/actions?query=branch%3Amaster)
[![Go Report Card](https://goreportcard.com/badge/github.com/rapidappio/pgweb)](https://goreportcard.com/report/github.com/rapidappio/pgweb)
[![GoDoc](https://godoc.org/github.com/rapidappio/pgweb?status.svg)](https://godoc.org/github.com/rapidappio/pgweb)
[![Docker Pulls](https://img.shields.io/docker/pulls/sosedoff/pgweb.svg)](https://hub.docker.com/r/sosedoff/pgweb/)

## Overview

Pgweb is a web-based database explorer for PostgreSQL, written in Go, and works
on Mac, Linux and Windows machines. Distributed as a simple binary with zero dependencies.
Very easy to use and packs just the right amount of features.

[See application screenshots](SCREENS.md)

## Features

- Cross-platform: Mac/Linux/Windows (64bit).
- Simple installation (distributed as a single binary).
- Zero dependencies.
- Works with PostgreSQL 9.1+.
- Supports native SSH tunnels.
- Multiple database sessions.
- Execute and analyze custom SQL queries.
- Table and query data export to CSV/JSON/XML.
- Query history.
- Server bookmarks.

Visit [WIKI](https://github.com/rapidappio/pgweb/wiki) for more details.

## Demo

Visit https://pgweb-demo.fly.dev/ to see Pgweb in action.

## Installation

- [Precompiled binaries](https://github.com/rapidappio/pgweb/releases) for supported operating systems are available.
- [More installation options](https://github.com/rapidappio/pgweb/wiki/Installation)

## Usage

Start server:

```
pgweb
```

You can also provide connection flags:

```
pgweb --host localhost --user myuser --db mydb
```

Connection URL scheme is also supported:

```
pgweb --url postgres://user:password@host:port/database?sslmode=[mode]
pgweb --url "postgres:///database?host=/absolute/path/to/unix/socket/dir"
```

### Multiple database sessions

To enable multiple database sessions in pgweb, start the server with:

```
pgweb --sessions
```

Or set environment variable:

```
PGWEB_SESSIONS=1 pgweb
```

## Testing

Before running tests, make sure you have PostgreSQL server running on `localhost:5432`
interface. Also, you must have `postgres` user that could create new databases
in your local environment. Pgweb server should not be running at the same time.

Execute test suite:

```
make test
```

If you're using Docker locally, you might also run pgweb test suite against
all supported PostgreSQL version with a single command:

```
make test-all
```

## Contribute

- Fork this repository
- Create a new feature branch for a new functionality or bugfix
- Commit your changes
- Execute test suite
- Push your code and open a new pull request
- Use [issues](https://github.com/rapidappio/pgweb/issues) for any questions
- Check [wiki](https://github.com/rapidappio/pgweb/wiki) for extra documentation

## License

The MIT License (MIT). See [LICENSE](LICENSE) file for more details.

## Notes
curl -X POST http://localhost:8081/api/connect \
-H "X-Session-ID: 953be069_9381_4119_9a66_df79ee71b922" \
-H "Content-Type: application/x-www-form-urlencoded" \
-d "url=postgresql://..."


curl -X GET http://localhost:8081/api/schemas \
-H "X-Session-ID: 953be069_9381_4119_9a66_df79ee71b922"
