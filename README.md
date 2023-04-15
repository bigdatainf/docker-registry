# docker-registry


## Server Set up
1. Launch the stack Docker Registry with an user interface   

    `
    $ docker compose up -d
    `

## User Setup Up
1. As Docker Registry is configured in our docker-compose.yml on HTTP instead of HTTPS, we have to authorize the connection to the Docker client. On a MacOS laptop, let’s open Docker Desktop and in the preferences, in the tab Docker Engine, enter the following configuration. On Linux, we would put this configuration in the /etc/docker/daemon.json file:   

    `
    { "insecure-registries":["192.168.1.159:5000"] }
    `

## Push docker images into the private registry
1. `docker login 192.168.1.159:5000`
1. `docker pull alpine`
1. `docker tag alpine 192.168.1.159:5000/alpine`
1. `docker push 192.168.1.159:5000/alpine`
1. In a Web browser on the desktop, login on the Docker Registry UI by visiting the webpage http://192.168.1.159:8086/. We have to authenticate with the credentials.

## Pull docker images from the private registry
1. `docker login 192.168.1.159:5000`
1. `docker pull 192.168.1.159:5000/alpine`
1. `docker tag 192.168.1.159:5000/alpine alpine`