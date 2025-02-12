# Traefik Docker Compose Setup

This repository provides a Docker Compose setup for Traefik, a modern reverse proxy and load balancer. It includes:
- Automatic HTTPS with Let's Encrypt.
- Secure access to the Traefik Dashboard with Basic Authentication.
- HTTP to HTTPS redirection.

## Prerequisites

- Docker and Docker Compose installed.
- A domain name (e.g., `example.com`) pointed to your server's IP address.

## Setup

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/traefik-docker.git
   cd traefik-docker

2. Generate Basic Authentication    
The Traefik Dashboard is protected with Basic Authentication. To generate a new username and password hash, use the following command:  
   > **Note:** When used in docker-compose.yml, all dollar signs ($) in the hash need to be doubled ($$) for escaping. [More details](https://doc.traefik.io/traefik/middlewares/http/basicauth/)
   ```bash
   htpasswd -nb admin securepassword
   
3. Update the docker-compose.yml file:
- Replace example@example.com with your email for Let's Encrypt.
- Replace traefik.example.com with your domain for the Traefik Dashboard.
- Replace the Basic Auth hash with your own (use htpasswd to generate it).

4. Create the external Docker network  
Run the following command to create the external Docker network:
   ```bash
   docker network create ingress-controller

5. Start the Traefik service:  
Start the Traefik service using Docker Compose:
   ```bash
   docker-compose up -d
