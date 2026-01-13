# Deploying to Production

This guide walks you through deploying your application to a live production server with automatic HTTPS certificates, monitoring, and automated deployments.

## Overview

The application uses a containerized deployment approach with the following components:
- **Docker** containers for all services
- **Traefik** reverse proxy for automatic HTTPS
- **PostgreSQL** database with persistent storage
- **GitHub Actions** for automated deployments

Your production setup will have three web addresses:
- Main application dashboard
- API backend
- Database administration panel

## Prerequisites

Before starting, you'll need:

1. **A server** running Linux (Ubuntu 20.04+ recommended) with:
   - At least 2GB RAM
   - Docker and Docker Compose installed
   - SSH access configured

2. **A domain name** that you control with DNS access

3. **GitHub repository** with your application code

## Step 1: Prepare Your Server

### Install Required Software

Connect to your server via SSH and install Docker:

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker $USER
```

Log out and back in for the changes to take effect.

### Set Up the Traefik Network

Traefik handles incoming web traffic and automatically manages HTTPS certificates. Create the network it needs:

```bash
docker network create traefik-public
```

### Configure Traefik

Create a new directory and configuration file:

```bash
mkdir -p /opt/traefik
cd /opt/traefik
```

Create a `docker-compose.yml` file for Traefik:

```yaml
version: '3.8'

services:
  traefik:
    image: traefik:v2.10
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock:ro
      - traefik-certificates:/certificates
    command:
      - --providers.docker=true
      - --providers.docker.exposedbydefault=false
      - --entrypoints.http.address=:80
      - --entrypoints.https.address=:443
      - --certificatesresolvers.le.acme.email=your-email@example.com
      - --certificatesresolvers.le.acme.storage=/certificates/acme.json
      - --certificatesresolvers.le.acme.httpchallenge=true
      - --certificatesresolvers.le.acme.httpchallenge.entrypoint=http
      - --providers.docker.network=traefik-public

volumes:
  traefik-certificates:

networks:
  default:
    name: traefik-public
    external: true
```

Replace `your-email@example.com` with your actual email address for SSL certificate notifications.

Start Traefik:

```bash
docker-compose up -d
```

## Step 2: Configure DNS Settings

Set up DNS records for your domain to point to your server:

1. Log in to your domain registrar's DNS management panel
2. Create three A records pointing to your server's IP address:
   - `dashboard.yourdomain.com`
   - `api.yourdomain.com`
   - `adminer.yourdomain.com`

DNS changes can take up to 48 hours to propagate, but usually complete within an hour.

## Step 3: Set Up Environment Variables

Create a secure configuration file on your server that contains all necessary settings.

Create the application directory:

```bash
mkdir -p /opt/app
cd /opt/app
```

Create a `.env` file with your production settings:

```bash
# Domain Configuration
DOMAIN=yourdomain.com
STACK_NAME=myapp-prod
TAG=latest

# Frontend Configuration
FRONTEND_HOST=https://dashboard.yourdomain.com

# Environment
ENVIRONMENT=production

# Security
SECRET_KEY=generate-a-secure-random-string-here
FIRST_SUPERUSER=admin@yourdomain.com
FIRST_SUPERUSER_PASSWORD=create-a-strong-password

# Database Configuration
POSTGRES_SERVER=db
POSTGRES_PORT=5432
POSTGRES_USER=app_user
POSTGRES_PASSWORD=create-a-strong-database-password
POSTGRES_DB=app

# Docker Images
DOCKER_IMAGE_BACKEND=yourusername/app-backend
DOCKER_IMAGE_FRONTEND=yourusername/app-frontend

# CORS Origins (comma-separated)
BACKEND_CORS_ORIGINS=https://dashboard.yourdomain.com

# Email Configuration (optional but recommended)
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your-email@gmail.com
SMTP_PASSWORD=your-app-password
EMAILS_FROM_EMAIL=noreply@yourdomain.com

# Monitoring (optional)
SENTRY_DSN=your-sentry-dsn-here
```

### Important Configuration Notes

**SECRET_KEY**: Generate a secure random string using:
```bash
openssl rand -hex 32
```

**Passwords**: Use strong, unique passwords for:
- `FIRST_SUPERUSER_PASSWORD` (your admin account)
- `POSTGRES_PASSWORD` (database access)

**Email Setup**: If using Gmail for SMTP:
1. Enable 2-factor authentication on your Google account
2. Generate an App Password in your Google Account settings
3. Use the App Password as your `SMTP_PASSWORD`

## Step 4: Deploy the Application

Copy your `docker-compose.yml` file to the server at `/opt/app/docker-compose.yml`.

Start all services:

```bash
cd /opt/app
docker-compose up -d
```

The deployment process will:
1. Start the PostgreSQL database
2. Run database migrations automatically
3. Create your first admin user
4. Start the backend API
5. Start the frontend dashboard
6. Configure automatic HTTPS certificates

### Monitor the Deployment

Watch the deployment progress:

```bash
docker-compose logs -f
```

Check that all services are running:

```bash
docker-compose ps
```

All services should show a "healthy" or "running" status.

## Step 5: Verify the Deployment

### Test HTTPS Certificates

Visit each of your domains in a web browser:
- `https://dashboard.yourdomain.com` - Your main application
- `https://api.yourdomain.com/docs` - API documentation
- `https://adminer.yourdomain.com` - Database admin panel

Each should show a valid HTTPS certificate (lock icon in the browser).

### Test the Application

1. Open `https://dashboard.yourdomain.com`
2. Log in with your admin credentials (FIRST_SUPERUSER email and password)
3. Verify you can access all features

### Verify Database Access

The database admin panel is available at `https://adminer.yourdomain.com`:
1. System: PostgreSQL
2. Server: db
3. Username: (your POSTGRES_USER)
4. Password: (your POSTGRES_PASSWORD)
5. Database: (your POSTGRES_DB)

## Step 6: Set Up Automated Backups

### Database Backups

Create a backup script at `/opt/app/backup.sh`:

```bash
#!/bin/bash
BACKUP_DIR="/opt/backups"
DATE=$(date +%Y%m%d_%H%M%S)

mkdir -p $BACKUP_DIR

docker-compose exec -T db pg_dump -U $POSTGRES_USER $POSTGRES_DB | gzip > $BACKUP_DIR/backup_$DATE.sql.gz

# Keep only last 30 days of backups
find $BACKUP_DIR -name "backup_*.sql.gz" -mtime +30 -delete
```

Make it executable:

```bash
chmod +x /opt/app/backup.sh
```

Schedule daily backups using cron:

```bash
crontab -e
```

Add this line to run backups daily at 2 AM:

```
0 2 * * * /opt/app/backup.sh
```

### Restore from Backup

If you need to restore a backup:

```bash
cd /opt/app
gunzip -c /opt/backups/backup_YYYYMMDD_HHMMSS.sql.gz | docker-compose exec -T db psql -U $POSTGRES_USER $POSTGRES_DB
```

## Step 7: Set Up Automated Deployments

Configure GitHub Actions to automatically deploy when you push code changes.

### Add Server Secrets to GitHub

In your GitHub repository:

1. Go to Settings → Secrets and variables → Actions
2. Add these secrets:

- `PRODUCTION_HOST`: Your server's IP address or hostname
- `PRODUCTION_USER`: SSH username (usually your server username)
- `PRODUCTION_SSH_KEY`: Your SSH private key for server access

### Generate SSH Key for Deployment

On your local machine:

```bash
ssh-keygen -t ed25519 -C "github-actions" -f ~/.ssh/github_deploy
```

Add the public key to your server:

```bash
ssh-copy-id -i ~/.ssh/github_deploy.pub user@your-server
```

Copy the private key content and add it as the `PRODUCTION_SSH_KEY` secret in GitHub.

### Deployment Workflow

The project includes an automated deployment workflow at `.github/workflows/deploy-production.yml`. This workflow:

1. Triggers when you push to the `main` branch
2. Builds Docker images for frontend and backend
3. Pushes images to Docker Hub
4. Connects to your server via SSH
5. Pulls the latest images
6. Restarts services with zero downtime

To deploy new changes:

```bash
git add .
git commit -m "Your changes"
git push origin main
```

The deployment happens automatically within a few minutes.

## Step 8: Configure Monitoring and Logging

### View Application Logs

Check logs for any service:

```bash
# All services
docker-compose logs -f

# Backend only
docker-compose logs -f backend

# Database only
docker-compose logs -f db
```

### Set Up Log Rotation

Prevent logs from filling your disk by configuring Docker log rotation. Create `/etc/docker/daemon.json`:

```json
{
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "10m",
    "max-file": "3"
  }
}
```

Restart Docker:

```bash
sudo systemctl restart docker
```

### Health Monitoring

The backend includes a health check endpoint. Monitor it with a simple script at `/opt/app/healthcheck.sh`:

```bash
#!/bin/bash
HEALTH_URL="https://api.yourdomain.com/api/v1/utils/health-check/"

if curl -f -s $HEALTH_URL > /dev/null; then
    echo "$(date): Application is healthy"
else
    echo "$(date): Application health check failed!"
    # Optionally send alert
fi
```

Schedule regular health checks:

```bash
crontab -e
```

Add:

```
*/5 * * * * /opt/app/healthcheck.sh >> /var/log/healthcheck.log 2>&1
```

### Optional: Set Up Sentry for Error Tracking

For production error monitoring:

1. Create a free account at sentry.io
2. Create a new project for your application
3. Copy the DSN (Data Source Name)
4. Add it to your `.env` file as `SENTRY_DSN`
5. Restart services: `docker-compose restart backend`

Errors will now be automatically reported to Sentry with detailed stack traces.

## Step 9: Security Hardening

### Update the Firewall

Configure your server firewall to only allow necessary ports:

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable
```

### Secure SSH Access

Edit `/etc/ssh/sshd_config`:

```
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
```

Restart SSH:

```bash
sudo systemctl restart sshd
```

### Keep Software Updated

Set up automatic security updates:

```bash
sudo apt update
sudo apt install unattended-upgrades
sudo dpkg-reconfigure --priority=low unattended-upgrades
```

### Database Security

The database is not exposed to the internet - it's only accessible to other containers. The adminer interface is protected by Traefik and should be restricted to trusted users.

Consider disabling the adminer service in production or adding authentication middleware in your Traefik configuration.

## Step 10: Maintenance Tasks

### Update the Application

When you need to manually update:

```bash
cd /opt/app
docker-compose pull
docker-compose up -d
```

### View Resource Usage

Monitor server resources:

```bash
# System resources
htop

# Docker resource usage
docker stats

# Disk usage
df -h
```

### Clean Up Old Docker Images

Remove unused images to free disk space:

```bash
docker system prune -a
```

### Database Maintenance

Run database optimization periodically:

```bash
docker-compose exec db psql -U $POSTGRES_USER $POSTGRES_DB -c "VACUUM ANALYZE;"
```

## Common Issues and Solutions

### HTTPS Certificates Not Working

If certificates aren't generated:
1. Verify DNS records are pointing to your server
2. Check Traefik logs: `docker logs traefik`
3. Ensure ports 80 and 443 are accessible
4. Wait up to 10 minutes for certificate generation

### Services Won't Start

Check for errors:
```bash
docker-compose logs backend
docker-compose logs db
```

Common causes:
- Environment variables not set correctly
- Port conflicts with other services
- Insufficient server resources

### Database Connection Errors

Verify database is healthy:
```bash
docker-compose ps db
```

Check database logs:
```bash
docker-compose logs db
```

Ensure `POSTGRES_SERVER=db` in your `.env` file (not `localhost`).

### Application Running Slowly

Check resource usage:
```bash
docker stats
free -h
```

Consider upgrading your server if resources are consistently maxed out.

## Performance Optimization

### Enable Database Connection Pooling

The application uses SQLAlchemy with built-in connection pooling. No additional configuration needed.

### Scale Services

If you need more capacity, increase the number of backend instances:

```bash
docker-compose up -d --scale backend=3
```

Traefik will automatically load balance between them.

### Add a CDN

For better global performance, consider using a CDN like Cloudflare:

1. Sign up for Cloudflare
2. Add your domain
3. Update DNS to Cloudflare's nameservers
4. Enable proxy (orange cloud) for your records

## Rolling Back Deployments

If a deployment causes issues:

1. Check what version is running:
```bash
docker-compose images
```

2. Roll back to a previous version:
```bash
export TAG=previous-version-tag
docker-compose pull
docker-compose up -d
```

3. Verify the rollback:
```bash
docker-compose ps
```

## Production Checklist

Before launching to users, verify:

- [ ] All three domains (dashboard, api, adminer) show valid HTTPS
- [ ] You can log in as the admin user
- [ ] Database backups are running daily
- [ ] Error monitoring is configured (Sentry)
- [ ] Firewall is enabled and configured
- [ ] SSH is secured (no root login, no password authentication)
- [ ] Environment variables use strong passwords
- [ ] Automated deployments work via GitHub Actions
- [ ] Health checks are running every 5 minutes
- [ ] Log rotation is configured
- [ ] DNS records are correctly configured

## Getting Help

If you encounter issues:

1. Check service logs: `docker-compose logs -f`
2. Verify all environment variables are set correctly
3. Ensure your server meets minimum requirements
4. Check the GitHub repository issues for similar problems

Your application is now running in production with automatic HTTPS, backups, monitoring, and automated deployments!