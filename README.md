### Hexlet tests and linter status:
[![Actions Status](https://github.com/laslomakkara/devops-for-developers-project-74/actions/workflows/hexlet-check.yml/badge.svg)](https://github.com/laslomakkara/devops-for-developers-project-74/actions)

### Docker image workflow:
[![push](https://github.com/laslomakkara/devops-for-developers-project-74/actions/workflows/push.yml/badge.svg)](https://github.com/laslomakkara/devops-for-developers-project-74/actions/workflows/push.yml)

## Description

This project packages the Hexlet JS Fastify Blog application with Docker and Docker Compose.

The setup includes:

* Fastify application
* PostgreSQL database
* Caddy reverse proxy
* Docker production image
* GitHub Actions workflow for tests and Docker Hub image publishing

## Requirements

* Docker
* Docker Compose
* Make

## Environment variables

The application is configured through environment variables.

Create a local `.env` file from `.env.example`:

```bash
cp .env.example .env
```

Example values:

```env
DATABASE_HOST=db
DATABASE_NAME=postgres
DATABASE_USERNAME=postgres
DATABASE_PASSWORD=password
DATABASE_PORT=5432
```

The `.env` file is used only locally and must not be committed to the repository.

## Setup

Install application dependencies inside Docker:

```bash
make setup
```

## Development

Start the application locally:

```bash
make dev
```

The application is available through Caddy:

```text
https://localhost
```

Requests to:

```text
http://localhost
```

are redirected to HTTPS.

## Tests

Run tests inside Docker Compose:

```bash
make test
```

The CI command is:

```bash
make ci
```

Tests are executed with PostgreSQL as a Docker Compose service.

## Docker image

The production Docker image is published on Docker Hub:

```text
laslomakkara/devops-for-developers-project-74
```

Pull the image:

```bash
docker pull laslomakkara/devops-for-developers-project-74:latest
```

Run the image manually:

```bash
docker run -p 8080:8080 -e NODE_ENV=development laslomakkara/devops-for-developers-project-74 make dev
```

## Useful commands

```bash
make setup
make dev
make test
make ci
make down
```

Build the production image:

```bash
docker compose -f docker-compose.yml build app
```

