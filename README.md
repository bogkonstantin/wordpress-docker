## Prerequisites

You need [Docker](https://docs.docker.com/get-docker/) to be installed with docker-compose.  

Also, a WordPress backup plugin is needed. The plugin should download the database dump in SQL format and all necessary WordPress files.   

I tested it with [backwpup](https://backwpup.com/) plugin. With this plugin, you need to create a cron-job to generate backup files. Run job and download results.

## Configuration

Clone this repository to the desired folder using the command below. 
```bash
git clone git@github.com:bogkonstantin/wordpress-docker.git
```

Change PHP version in `docker/php/Dockerfile` if needed. Change MySQL version in `docker-compose.yml` if needed.  

Copy website files to the `wp` folder.  

Add to `wp-config.php` local database connection values. See it in the `docker-compose.yml` or override using the `.env` file.  

Default parameters:
```php
define( 'DB_NAME', "db" );
define( 'DB_USER', "dbuser" );
define( 'DB_PASSWORD', "pass" );
define( 'DB_HOST', "db" );
```

Set domain to localhost in `wp-config.php`:
```php
define('WP_HOME','http://localhost');
define('WP_SITEURL','http://localhost');
``` 

Copy database dump to `db_init` folder.

Override config values in `.env` files if needed. See the list of available variables in the `docker-compose.yml` file.  

## Usage

Use it with docker-compose commands. For example, start the application with the command:
```bash
docker-compose up -d
```

Stop application (containers) with the command:
```bash
docker-compose down
```

Now you can open your website locally using the link http://localhost

Config Xdebug in your IDE if necessary.

## Other

Feel free to contribute to this repository.

And don't forget to check your website availability with [uptime.onl](https://uptime.onl).
