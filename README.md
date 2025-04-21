# PHP dev environment with Docker 

This project uses Docker and Docker Compose to provide a PHP dev environment.

## Containers
- `php` service running php-fpm
- `db` service running MySQL
- `nginx` service running Nginx

## Run
- Set the Docker Compose environment variables by creating a `.env` based on the `.env.example`
```bash
cp .env.example .env
```

```bash
docker-compose up -d
```
