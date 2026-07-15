# Installation Guide 🚀

This document covers the two distinct ways you can install and run your custom `tracktor-plus` instance.

## Prerequisites
* Docker and Docker Compose installed on your system.
* A user architecture capable of running standard Linux containers.

---

## Method A: Manual Docker Image Build
Use this method if you want to build the Docker image yourself right on your server machine from the source code. This is ideal if you are developing or testing new features locally.

### 1. The Compose Configuration
Create or update your `docker-compose.yml` file to use the local `build` block configuration:

```yaml
services:
  tracktor:
    build:
      context: .
      dockerfile: Dockerfile
    container_name: tracktor-plus
    restart: always
    ports:
      - "3000:3000"
    volumes:
      - tracktor-plus:/data
    environment:
      - PUBLIC_DEMO_MODE=false
      - FORCE_DATA_SEED=false
      - CORS_ORIGINS="http://localhost:3000"
      - TRUST_PROXY=true
      - UPLOADS_DIR=/data/uploads

volumes:
  tracktor-plus:
    name: tracktor-plus
