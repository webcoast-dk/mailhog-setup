# Catching mails with MailHog during local development

This projects contains the necessary setup for using MailHog mail catcher in a docker based
setup for local development.

This setup is works out-of-the box with the Træfik reverse proxy setup from https://github.com/webcoast-dk/traefik. 

## Prerequisites
* https://github.com/webcoast-dk/traefik: ^1.0.0
* Docker: ^18.09.7
* docker-compose: ^1.21.0

## Installation
1. Clone this repository
   ```bash
   git clone https://github.com/webcoast-dk/mailhog-setup.git mailhog-setup
   ```
2. Change into directory
   ```bash
   cd mailhog-setup
   ```
3. Create mailhog network, if it does not exist
   ```bash
   docker network inspect mailhog &> /dev/null || docker network create mailhog
   ```
4. Copy `.env.example` to `.env` and adjust the `HOST_NAME` variable if necessary.
5. Start reverse proxy
   ```bash
   docker-compose up -d
   ```

The containers are set to `restart: always`, so they should restart automatically
with your docker daemon.

## Dashboard
You can access the mailhog dashboard through the host name you chose in the `.env` file,
e.g. http://mailhog.localhost/.
