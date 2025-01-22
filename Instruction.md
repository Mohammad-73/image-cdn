# set ssh key

- Generate ssh key: `ssh-keygen -t rsa -b 4096`

- copy ssh key into server: `ssh-copy-id username@server_ip`

# Install Docker

- Check and remove: `for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker  containerd runc; do sudo apt-get remove $pkg; done`

- Update packages: `sudo apt-get update`

- Install install ca-certificates curl: `sudo apt-get install ca-certificates curl`

- `sudo nano /etc/hosts > 127.0.1.1 image-cdn`

- `sudo install -m 0755 -d /etc/apt/keyrings`

## add shecan to resolve file

- `sudo nano /etc/resolv.conf`

  > nameserver 178.22.122.100
  > nameserver 185.51.200.2

- `sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc`

- `sudo chmod a+r /etc/apt/keyrings/docker.asc`

- `echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null`

- `sudo apt-get update`

`sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin`

- `docker --VERSION

- `sudo usermod -g docker ${USER}`

## install docker compose

- `sudo curl -L "https://github.com/docker/compose/releases/download/$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep -oP '"tag_name": "\K(.\*)(?=")')/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`

- `sudo chmod +x /usr/local/bin/docker-compose`

# install MinIO and Thumbor

## install MinIO

- Create a directory for MinIO and Thumbor files and configs: `sudo mkdir course-minio`

- Create docker-compose file in /opt/course-minio: `sudo nano docker-compose.yml`

- Create docker-compose file in /opt/course-minio and add minio image and other configurations: `sudo nano docker-compose.yml`

- Create a docker network: `sudo docker network create course-minIO`

- List of docker networks: `docker network ls`

- Start and run multi-container Docker applications: `docker compose up -d`

## install and configure Thumbor

- Instruction to build a Docker image for Thumbor: `sudo nano Dockerfile`

- Open docker-compose file to add Thumbor configurations for build: `sudo nano docker-compose.yml`

- Create thumbor file in /opt/course-minio and add configs: `sudo nano thumbor.conf`

- Create aws directory for config and credentials files: `sudo mkdir aws`

- Create config file in /opt/course-minio/aws: `sudo nano config`

- Create credentials file in /opt/course-minio/aws: `sudo nano credentials`

- Stop and remove containers: `docker compose down`

- Install and Run containers: `docker compose up -d`

- See container logs: `docker logs [CONTAINER_NAME]`
