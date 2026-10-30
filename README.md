# hermdash

Self-hosted [NocoDB](https://nocodb.com) (no-code database UI) backed by PostgreSQL, run with Docker Compose.

## Setup

```bash
cp .env.example .env
```

Edit `.env`: set `POSTGRES_PASSWORD` and set `NC_AUTH_JWT_SECRET` to the output of `openssl rand -hex 32`.

```bash
docker compose up -d
```

Open http://localhost:8080 and create the admin account.

## Operations

| Task | Command |
| --- | --- |
| Logs | `docker compose logs -f nocodb` |
| Update | `docker compose pull && docker compose up -d` |
| Stop | `docker compose down` |
| Back up DB | `docker compose exec db pg_dump -U nocodb nocodb > backup.sql` |

Data lives in the `db_data` and `nocodb_data` volumes. `docker compose down -v` deletes them.
