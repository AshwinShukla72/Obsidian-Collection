```dockerfile
FROM node:alpine # defines the base image

LABEL maintainer ashwin7298@gmail.com # Declares the maintainer

RUN command git clone -q URL # Runs the command to clone 

WORKDIR todo # moves to new cloned directory

RUN npm install > /dev/null # runs npm instakk command

EXPOSE 8000 # specifies that the container from this built image should listen oon this port 

CMD ["npm","start"] # specifies which command needs to be run on startup  
```