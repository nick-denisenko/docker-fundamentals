# Docker Compose Essentials

### Basic Operations
```bash
# Start services
docker compose up

# Start in background
docker compose up -d

# Stop services
docker compose down

# View running services
docker compose ps

# View logs
docker compose logs
docker compose logs web  # specific service

# Rebuild and start
docker compose up --build
```

### Development Commands
```bash
# Execute command in service
docker compose exec web bash
docker compose exec api npm install

# Run one-time command
docker compose run api npm test

# Scale services
docker compose up --scale api=3
```

### Environment-specific Files
```bash
# Development
docker compose -f docker-compose.dev.yml up
```

## Troubleshooting Commands

```bash
# View detailed logs
docker compose logs -f --tail=100

# Check service status
docker compose ps
docker compose top

# Validate compose file
docker compose config

# Remove everything (containers, networks, volumes)
docker compose down -v --remove-orphans

# Rebuild specific service
docker compose build --no-cache web
```