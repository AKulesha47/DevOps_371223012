# Runbook

## Start locally

```bash
npm install
npm run dev
```

## Check that it works


# Runbook

## Run with Compose

This project uses Docker Compose to run the application and PostgreSQL database.

### 1. Start the services

Build the application image and start the services in the background:

```bash
docker compose up -d --build
```

To also start optional tools such as Adminer:

```bash
docker compose --profile tools up -d --build
```

### 2. Check running services

List the running containers and their status:

```bash
docker compose ps
```

### 3. View logs

View logs from all services:

```bash
docker compose logs
```

Follow logs in real time:

```bash
docker compose logs -f
```

View logs for a specific service:

```bash
docker compose logs -f app
docker compose logs -f db
docker compose logs -f adminer
```

### 4. Stop the services

Stop and remove the containers and Compose network:

```bash
docker compose down
```

This does not delete the persistent PostgreSQL data stored in the named volume.

### 5. Remove services and database data

To stop and remove containers, networks, and named volumes:

```bash
docker compose down -v
```

**Warning:** The `-v` option deletes the named PostgreSQL volume (`postgres_data`). This permanently removes the database data stored in that volume.

### Difference between `down` and `down -v`

| Command | Effect |
|---|---|
| `docker compose down` | Removes containers and networks; preserves database volume |
| `docker compose down -v` | Also removes named volumes, including PostgreSQL data |

Use `docker compose down` for normal shutdowns.

Only use `docker compose down -v` when you intentionally want to reset the database.
