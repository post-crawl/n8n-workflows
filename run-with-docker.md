# Run n8n with Docker

## Initial Setup

1. Install Docker Desktop (Mac/Windows) or Docker Engine + Docker Compose (Linux)

2. Create a volume for persistent data:
```bash
docker volume create n8n_data
```

## Running n8n

Start n8n with this command:
```bash
docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n
```

Access n8n at: http://localhost:5678

## Daily Usage

After initial setup, just run the same command to start n8n:
```bash
docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n
```

To stop: Press `Ctrl+C` in the terminal

## Using PostgreSQL (Optional)

Replace placeholders with your PostgreSQL details:
```bash
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -e DB_TYPE=postgresdb \
  -e DB_POSTGRESDB_DATABASE=<POSTGRES_DATABASE> \
  -e DB_POSTGRESDB_HOST=<POSTGRES_HOST> \
  -e DB_POSTGRESDB_PORT=<POSTGRES_PORT> \
  -e DB_POSTGRESDB_USER=<POSTGRES_USER> \
  -e DB_POSTGRESDB_SCHEMA=<POSTGRES_SCHEMA> \
  -e DB_POSTGRESDB_PASSWORD=<POSTGRES_PASSWORD> \
  -v n8n_data:/home/node/.n8n \
  docker.n8n.io/n8nio/n8n
```

## Reset Forgotten Password

To reset a forgotten n8n password, run this command after n8n is running:
```bash
docker exec -it n8n n8n user-management:reset
```

**⚠️ DANGER:** This command permanently deletes:
- ALL user accounts
- ALL saved workflows
- ALL stored credentials

After resetting, restart the Docker container:
1. Stop n8n (Ctrl+C)
2. Run the start command again
3. Create a new admin account

## Updating n8n

1. Pull the latest image:
```bash
docker pull docker.n8n.io/n8nio/n8n
```

2. Stop the running container (Ctrl+C)

3. Start n8n again with the same run command