The `docker exec` command runs a new command in a running container.

The command started using `docker exec` only runs while the container’s primary process (`PID 1`) is running, and it is not restarted if the container is restarted.