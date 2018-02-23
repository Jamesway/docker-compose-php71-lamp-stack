# Docker-compose - Laravel Development Lamp Stack
I going to use this with Laravel, but the stack works with any or no frameworks.

## Installation

**Step 1) Install Laravel**

```
In an empty directory...

docker run --rm -v $(pwd):/app jamesway/php71-cli-dev composer create-project --prefer-dist laravel/laravel .
```

**Step 2) Docker-compose**

Clone this repo and extract the contents to the root directory.


**Step 3) Fire up the stack**
```
docker-compose up -d
...
docker-compose down
```

*Note: a cool side benefit of using compose - the flags are baked into the compose file so you can:*
```
docker-compose run --rm [service_name_in_compose]
docker-compose exec [service_name_in_compose]

eg.

docker-compose run --rm php-cli composer dump-autoload
```

## Usage

Laravel http://192.168.99.100:8080 - http://your-docker-ip:8080

phpMyAdmin http://192.168.99.100:8081 - http://your-docker-ip:8081


## Notes

The .dev.env is for development and is ok to keep in version control BUT an .env with actual secrets should NEVER be version controlled.

If no .dev.env, docker-compose expects the environment variables to passed on the command line.
