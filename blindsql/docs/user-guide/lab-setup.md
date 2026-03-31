# Lab Setup

The repository includes intentionally vulnerable lab targets for local testing.

## Flask + SQLite target (`lab/app.py`)

### Start server

```bash
cd lab
python app.py
```

Server default: `http://127.0.0.1:5000`

### Key endpoint

- `GET /vulnerable?id=...`

This endpoint is intentionally vulnerable and used as the timing target in local experiments.

### User management helper

```bash
python setup_users.py list
python setup_users.py default
python setup_users.py add testuser testpass test@example.com
```

## PHP + MySQL target (`lab/mysql_vulnerable.php`)

This optional target is useful for MySQL-centric payload behavior.

Supporting SQL setup script: `lab/setup_mysql.sql`

## Safety controls

- Bind to localhost only.
- Do not expose lab services on public networks.
- Treat all lab credentials and data as disposable.
- Keep this environment separate from production systems.

## Verification checklist

- App starts without traceback.
- Endpoint responds with JSON and timing field.
- A short StatSQLi run succeeds against the local URL.
- No public ingress exists to the lab host.
