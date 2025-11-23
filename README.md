# Frontend Deployment Test

This repository is used to test automated deployment of a frontend application using GitHub Actions and Docker Compose.

## Task

Automate the deployment of the application such that:

1. Any update on the **main** branch triggers a workflow.
2. The workflow executes a **build step** (can be a simple command like `echo "building..."`).
3. After building, the workflow performs a **deployment step** to an Ubuntu 22.04 machine.
4. The frontend application uses Docker Compose with the public image of **Uptime Kuma** from Docker Hub.

## Workflow

- The workflow is defined in `.github/workflows/main.yml`.
- Steps include:
  1. Trigger on push to `main`.
  2. Build the application.
  3. Deploy using Docker Compose to a remote Ubuntu 22.04 server.

## Deployment Details

- Ensure SSH access is configured for the Ubuntu machine.
- Docker and Docker Compose must be installed on the server.
- The public image `uptime-kuma` is used in `docker-compose.yml`.

## Example Docker Compose

```yaml
version: "3"
services:
  uptime-kuma:
    image: louislam/uptime-kuma
    container_name: uptime-kuma
    ports:
      - "3001:3001"
    restart: unless-stopped
```
## Accessing the Application
- http://<SERVER_IP>:3001

