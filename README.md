
# Graylog - using Docker Compose

Graylog is a leading centralized log management solution for capturing, storing, and enabling real-time analysis of terabytes of machine data.
Docker Compose that I used to fulfill my need to monitor my Home Lab logs.



## Reference

 - [Graylog Docker Image](https://hub.docker.com/r/graylog/graylog/)



## Application Setup - Graylog

The admin interface is available at http://SERVER-IP:9000/system/inputs with a default user/password of admin
*** I have set the IP addresses of the services for my convenience only.

#MONGODB
    image: mongo:3
    networks:
      graylog_network:
        ipv4_address: 172.30.0.4

#ELASTICSEARCH
    networks:
      graylog_network:
        ipv4_address: 172.30.0.2

#GRAYLOG        
      - GRAYLOG_HTTP_EXTERNAL_URI=http://0.0.0.0:9000/
      - GRAYLOG_WEB_ENDPOINT_URI=http://0.0.0.0:9000/
        
      graylog_network:
        ipv4_address: 172.30.0.3
```

How to generate your password:

root@debian-docker:/home# echo -n "Enter Password: " && head -1 < /dev/stdin | tr -d '\n' | sha256sum | cut -d " " -f1
Enter Password: youpassword
f3a4089488ba24c385f71a83508259814e0ec4b71211e46fae8bf53597d923c0

Save the generated key will be needed in the variable below:



## Environment variables

These environment variables came empty because they are optional.
Fill in the External URL variable:


-e GRAYLOG_ROOT_PASSWORD_SHA2=f3a4089488ba24c385f71a83508259814e0ec4b71211e46fae8bf53597d923c0
-e GRAYLOG_HTTP_EXTERNAL_URI="http://127.0.0.1:9000/"

## Running Locally

Clone the Project

```bash
  git clone https://github.com/omztg/graylog-docker/blob/main/docker-compose.yml
```
Start the server

```bash
  docker-compose up -d
```


## Hardware used

**Virtual Machine:**  Memory usage 4.00 GiB, 4 CPU(s), Hard Disk 80G

**Operational system:** Debian GNU/Linux 11 (bullseye) Node proxmox

**Docker version:** 20.10.16

## 🚀 About me
Infrastructure Analyst | DevOps student


## 🔗 Links
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/tiago-menegon-zimmermann-97a67b1b6/)
[![twitter](https://img.shields.io/badge/twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com/omz_tg)


## 🛠 Skills
Linux, Shell Script, Docker, Kubernetes, Ansible, Jenkins, Terraform, Python

