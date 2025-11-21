# docker-jenkins
Project docker compose jenkins

# step 1

```
# Use the same logic as your script to find the GID
if command -v getent >/dev/null 2>&1; then
  DOCKER_GID=$(getent group docker | cut -d: -f3)
else
  DOCKER_GID=$(cat /etc/group | grep docker: | awk -F\: '{print $3}')
fi
```
# setp 2
```
# Check if DOCKER_GID was found
if [ -z "$DOCKER_GID" ]; then
    echo "Error: Docker group GID not found. Cannot proceed."
    exit 1
fi

# Run the container, passing the DOCKER_GID environment variable
DOCKER_GID=$DOCKER_GID docker-compose up -d

```



