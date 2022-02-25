### Example Traefik configuration for 3rd party hosting environment with Portainer

*The following commands are for Ubuntu 20.04 LTS*

Ensure you are running the latest OS packages:
```
apt-get update
```

Install Docker dependencies:
```
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add –
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt update
```

Install Docker Community Edition (CE)
```
sudo apt-get install docker-ce
```

Create the Proxy network we'll use
```
sudo docker network create proxy
```

Generate a username and password for Traefik Portal authentication:
(traefik-data/configurations/dynamic.yml)
```
apt-get install apache2-utils
htpasswd -nb admin passwordhere
```

# Required Steps
```
1. Update the traefik-data/configurations/dynamic.yml.
2. Change the domainname in the docker labels for traefik and portainer in docker-compose.yml.

To run (foreground for debugging):
# docker-compose up

To run (background):
# docker-compose up -d
```
