# Getting started

The back-end component of CloudLabs is built using Spring Boot 2.7.11, which is used to interface with the guacd service, and Google Cloud Platform API.  

GitHub repository: [cloudlabs/server](https://github.com/projectcatena/cloudlabs-server)


## Setup

The project may be deployed locally using docker/podman:
```bash
# Build the docker image (include --progress=plain --no-cache to observe stdout)
docker build  -t cloudlabs/server .

# Run the image on default port (or add --server.port=9000 for custom port)
docker run -p 8080:8080 cloudlabs/server 
```