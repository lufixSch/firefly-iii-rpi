# firefly-iii-rpi
Docker Compose setup for hosting Firefly III on a raspberry pi

## Usage

Change the names of the `**.env.example` files to `**.env`. I highly reccomend to change the database secret (make sure it's changed in `.db.env` and `.env`.

You should also set the owner email as well as the encription secret in `.env`.

After this the docker compose can be started with `docker-compose up -d`

Firefly III can be accessed on port `5000`. The Firefly III Data importer is hosted on port `5050`.

In order to use the Firefly III data importer you have to create a persona access token under *Options -> Profile -> OAuth* and add it to `.fidi.env`.

### Firefly Cron jobs

Firefly III supports several features that requires you to run a cron job. As Docker by it self is not designed to run cron jobs you need to configure one on your host system. In this cron job you need to execute the coresponding command inside of the Firefly III Container

```bash
docker exec --user www-data firefly_app_1 /usr/local/bin/php /var/www/html/artisan firefly-iii:cron
```
