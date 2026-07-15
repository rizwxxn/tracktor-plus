# Tracktor Plus 🏍️

A self-hosted vehicle fuel and maintenance tracker, patched to resolve data migration bugs and optimized for custom homelab deployments.

## Getting Started

You can run this project locally by building it from the source code or by pulling the pre-built image from the GitHub Container Registry. 

Here is the complete `docker-compose.yml` configuration. Choose between compiling locally or pulling the pre-built package by adjusting the comment tags:

```yaml
services:
  tracktor:
    build:
      context: .
      dockerfile: Dockerfile
    #image: ghcr.io/rizwxxn/tracktor-plus:latest
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
