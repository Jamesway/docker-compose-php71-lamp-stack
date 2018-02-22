# Docker-compose - php71 Development Lamp Stack
I going to use this with Laravel, but the stack works with no frameworks.

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
```

## Usage

Laravel http://192.168.99.100:8080/ - http://your-docker-ip:80**80**

phpMyAdmin http://192.168.99.100:8081/ - http://your-docker-ip:80**81**


## Notes

The .dev.env is for development and is fine to keep in version control. An .env with actual secrets should NEVER be version controlled.

If no .dev.env, docker-compose expects the environment variables to passed on the command line.
