# NoStar - Homelab Setup
[![Pi4 - Deploy Docker Compose](https://github.com/FinnPL/NoStar/actions/workflows/pi4-deploy.yml/badge.svg)](https://github.com/FinnPL/NoStar/actions/workflows/pi4-deploy.yml)

This repository contains the configuration files for my homelab setup.
The setup is based on Docker and Traefik as a reverse proxy.

## Pi4 Setup
### CI Setup
1. Download the latest runner package
2. Configure the runner
3. Ensure Runner Auto-Restarts using Systemd

### Manual Setup

1. Clone the repository:
    ```sh
    git clone https://github.com/FinnPL/NoStar.git
    cd NoStar
    ```

2. Enter your API keys in the `.env` file:
    ```sh
    nano .env
    ```

    **Note:** The Traefik and Portainer password must be hashed using `htpasswd`. The following steps will guide you through the process.

    ```sh
    sudo apt-get install apache2-utils
    htpasswd -nb admin password
    htpasswd -nb -B admin password | cut -d ":" -f 2
    ```
    Replace `password` with your desired password. Copy the generated hash and use it in your `.env` file.
    
    **Note:** Edit traefik.yml to include your email address.

3. Start Docker in daemon mode:
    ```sh
    docker-compose up -d
    ```

4. Configure the Portainer password and obtain the Portainer API key:
    - Access Portainer at `https://port.lippok.dev`
    - Navigate to the API section to get your API key

5. Enter the Portainer API key in the `.env` file:

6. Restart the homepage container:
    ```sh
    docker-compose restart homepage
    ```
