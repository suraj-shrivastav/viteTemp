# 🐳 Docker Usage Guide

This guide explains how to use the pre-built Docker image for this Vite application.

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/) installed on your system
- Internet connection to pull the image from Docker Hub

## Quick Start

### 1. Pull the Image

```bash
docker pull surajshrivastav/vite-app:latest
```

### 2. Run the Container

```bash
docker run -d -p 3000:5173 --name my-vite-app surajshrivastav/vite-app:latest
```

**Flags explained:**
- `-d` → Run in detached mode (background)
- `-p 3000:5173` → Map container port 5173 to host port 3000
- `--name my-vite-app` → Give the container a friendly name

### 3. Access the Application

Open your browser and navigate to:
```
http://localhost:3000
```

## Container Management

### Check if Container is Running

```bash
docker ps
```

### View Application Logs

```bash
# View all logs
docker logs my-vite-app

# Follow logs in real-time
docker logs -f my-vite-app
```

### Stop the Container

```bash
docker stop my-vite-app
```

### Start the Container Again

```bash
docker start my-vite-app
```

### Restart the Container

```bash
docker restart my-vite-app
```

### Remove the Container

```bash
# Stop and remove
docker rm -f my-vite-app
```

## Troubleshooting

### Port Already in Use

If port 3000 is already in use, change it to another port:

```bash
docker run -d -p 8080:5173 --name my-vite-app surajshrivastav/vite-app:latest
```

Then access the app at `http://localhost:8080`

### Container Not Starting

1. Check container logs:
   ```bash
   docker logs my-vite-app
   ```

2. Check if container is running:
   ```bash
   docker ps -a
   ```

3. Try running interactively to see errors:
   ```bash
   docker run -it -p 3000:5173 surajshrivastav/vite-app:latest
   ```

### Pull Latest Version

To ensure you have the latest image:

```bash
docker pull surajshrivastav/vite-app:latest
docker rm -f my-vite-app
docker run -d -p 3000:5173 --name my-vite-app surajshrivastav/vite-app:latest
```

## Using Specific Versions

You can also pull specific commit versions:

```bash
# List available tags at: https://hub.docker.com/r/surajshrivastav/vite-app/tags

# Pull specific version
docker pull surajshrivastav/vite-app:<commit-sha>

# Run specific version
docker run -d -p 3000:5173 surajshrivastav/vite-app:<commit-sha>
```

## Docker Compose (Optional)

Create a `docker-compose.yml` file:

```yaml
version: '3.8'

services:
  vite-app:
    image: surajshrivastav/vite-app:latest
    container_name: my-vite-app
    ports:
      - "3000:5173"
    restart: unless-stopped
```

Then run:

```bash
docker-compose up -d
```

## Verification Checklist

✅ **Image pulled successfully**
```bash
docker images | grep vite-app
```

✅ **Container is running**
```bash
docker ps | grep my-vite-app
```

✅ **Logs show Vite server started**
```bash
docker logs my-vite-app | grep "ready in"
```

✅ **Application accessible**
- Open http://localhost:3000 in your browser
- You should see the Vite application

---

## Need Help?

- **Docker Hub:** https://hub.docker.com/r/surajshrivastav/vite-app
- **GitHub Issues:** [Create an issue](https://github.com/surajshrivastav/vite-app/issues) (if available)
