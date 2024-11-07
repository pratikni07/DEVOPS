# Docker Command Reference

## Container Management
```bash
# Run Containers
docker run [OPTIONS] IMAGE [COMMAND]
  -d          # Run in background
  -p 80:80    # Port mapping
  -v          # Volume mapping
  --name      # Assign container name
  --network   # Connect to network
  -e          # Set environment variables
  --rm        # Remove container when it exits

# Container Operations
docker start CONTAINER     # Start container
docker stop CONTAINER     # Stop container
docker restart CONTAINER  # Restart container
docker pause CONTAINER    # Pause container
docker unpause CONTAINER  # Unpause container
docker kill CONTAINER    # Kill container
docker rm CONTAINER      # Remove container
docker rename OLD_NAME NEW_NAME  # Rename container

# Container Information
docker ps                 # List running containers
docker ps -a             # List all containers
docker logs CONTAINER    # View container logs
docker inspect CONTAINER # View container details
docker top CONTAINER     # View running processes
docker stats CONTAINER   # View resource usage
docker port CONTAINER    # Show port mappings
```

## Image Management
```bash
# Image Operations
docker images            # List images
docker pull IMAGE       # Pull image from registry
docker push IMAGE       # Push image to registry
docker rmi IMAGE        # Remove image
docker build -t NAME:TAG PATH  # Build image from Dockerfile
docker tag SOURCE TARGET # Create tag TARGET that refers to SOURCE
docker save IMAGE > file.tar    # Save image to tar archive
docker load < file.tar         # Load image from tar archive
docker history IMAGE    # Show image history
```

## Network Management
```bash
# Network Operations
docker network create NETWORK   # Create network
docker network rm NETWORK      # Remove network
docker network ls             # List networks
docker network inspect NETWORK # Inspect network
docker network connect NETWORK CONTAINER    # Connect container to network
docker network disconnect NETWORK CONTAINER # Disconnect container
```

## Volume Management
```bash
# Volume Operations
docker volume create VOLUME    # Create volume
docker volume rm VOLUME       # Remove volume
docker volume ls             # List volumes
docker volume inspect VOLUME  # Inspect volume
```

## System & Registry
```bash
# System Commands
docker info               # Display system-wide information
docker version           # Show Docker version
docker events            # Get real-time events
docker system df         # Show docker disk usage
docker system prune      # Remove unused data
docker login             # Log in to registry
docker logout            # Log out from registry
```

## Container Interaction
```bash
# Execute & Interact
docker exec -it CONTAINER COMMAND  # Execute command in container
docker attach CONTAINER           # Attach to container
docker cp CONTAINER:SRC_PATH DEST_PATH  # Copy files between container and local
docker commit CONTAINER [REPOSITORY[:TAG]]  # Create image from container
```

## Docker Compose
```bash
# Compose Commands
docker-compose up       # Create and start containers
docker-compose down     # Stop and remove containers
docker-compose start    # Start services
docker-compose stop     # Stop services
docker-compose restart  # Restart services
docker-compose logs     # View output from containers
docker-compose ps       # List containers
docker-compose build    # Build or rebuild services
docker-compose pull     # Pull service images
docker-compose rm       # Remove stopped containers
```

## Best Practices
- Always use `--rm` when running temporary containers
- Tag images with meaningful versions
- Use `docker-compose` for multi-container applications
- Clean up unused resources regularly with `docker system prune`
- Use `.dockerignore` to exclude unnecessary files
- Implement health checks for production containers
- Use multi-stage builds to reduce final image size
