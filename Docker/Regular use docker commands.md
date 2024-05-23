#### Useful Container commands
- login into a container => ```
```python
docker container attach CONT_ID
``` 
- Running a container in interactive mode through `-it/ti` flag `docker run -it CONTAINER sh`, **sh** command for shell session.
- Login into a running container => `docker exec -it CONTAINER_NAME/CONTAINER_ID sh`, [[exec]] allows login to a running container. #exec
- Use a container and dump the info created on exit `docker run --rm -ti --name SET_CONTAINER_NAME sh`
- Use `-d` flag to run a container in detached mode.
- `docker inspect CONTAINER_NAME` => provides all information about a container.
