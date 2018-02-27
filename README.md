# Docker-compose - Laravel Development Lamp
I going to use this with Laravel, but it's the same process for any composer installed framework - or no framework.

## Installation

### **Step 1) Install Laravel**

```
In an empty directory...

docker run --rm -v $(pwd):/app jamesway/php71-cli-dev composer create-project --prefer-dist laravel/laravel .
```

### **Step 2) Docker-compose**

Clone this repo and extract the contents to the root directory.


### **Step 3) Append .dev.env to Laravel's .env**
*Note: This is for development, but .env files with actual secrets, should NEVER be version controlled.*

```
cat .dev.env >> .env
```

### **Step 4) Fire up the stack**
```
docker-compose up -d
```

### **Step 5) Composer dump**
```
docker-compose run --rm jamesway/php71-cli-dev composer dump-autoload
```


## Usage

Laravel http://192.168.99.100:8080 - http://your-docker-ip:8080

phpMyAdmin http://192.168.99.100:8081 - http://your-docker-ip:8081


## Notes

*OS X and docker-sync*
If you find volume syncs are slow, docker-sync is a workaround for the underlying INotify problem on OS X.
- Install docker sync https://github.com/Jamesway/docker-cheatsheet
- Rename \_docker-compose-override.yml to docker-compose-override.yml (remove the underscore) to enable the docker-sync compose config.

*docker-compose > docker*
A cool side benefit of using compose - the flags are baked into the compose file so your commands are simpler:
```
docker-compose run --rm [service_name_in_compose]
docker-compose exec [service_name_in_compose]

eg.
docker run --rm -v $(pwd):/app jamesway/php71-cli-dev composer dump-autoload

vs

docker-compose run --rm pjamesway/php71-cli-dev dump-autoload

ehh, I guess the docker command in this example isn't so bad, but let's say you have some ENVs...
```


*Named Volumes*
Named volumes persist after their container is removed which makes them ideal for data storage containers.
When making changes to a service config (eg. mariadb) that uses "dbdata", or if mariadb becomes corrupted, remove the named volume and start fresh before bringing the stack up.
