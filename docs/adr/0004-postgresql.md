
# 0004: Use PostgreSQL as the Application Database

## Status

Accepted

## Context

The application requires a persistent database for storing
and managing application data.

A database solution is needed that supports relational
data, reliable persistence, and integration with Docker Compose.

## Decision

PostgreSQL is selected as the application's database.

The project uses the official PostgreSQL Docker image:

postgres:17-alpine

The database runs as a Docker Compose service named `db`.

Database configuration is provided through environment variables:

- POSTGRES_USER
- POSTGRES_PASSWORD
- POSTGRES_DB

Persistent database storage is provided through the
`postgres_data` Docker named volume.

The application connects to PostgreSQL through the
Docker Compose service name `db`.

## Consequences

Positive:
- Reliable relational database management.
- Persistent storage through Docker volumes.
- Simple integration with Docker Compose.
- Database configuration can be managed through environment variables.

Negative:
- Database credentials must be configured correctly.
- Persistent volume management is required.
- Removing the database volume deletes stored data.

## Implementation

PostgreSQL is configured in compose.yaml.

The application waits for the database healthcheck
before starting.

The database healthcheck uses pg_isready.
