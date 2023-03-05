## Generating certs
Inside traefik/certs:
```
mkcert -install
mkcert -cert-file certs/local-cert.pem -key-file certs/local-key.pem "docker.localhost" "*.docker.localhost"
```

On local machine:
```
choco install mkcert
mkcert -install
mkcert "docker.localhost" "*.docker.localhost"
```

## Setting up smtp
[Sign in with App Passwords](https://support.google.com/mail/answer/185833?hl=en)

Inside ./docer/ssmtp/ssmtp.conf

For your safety use trash account (in case you accidently push it into repo). App password works the same as regular password, it gives full access to account.
```
AuthUser=example@gmail.com
AuthPass=app_password
```

## Setting up project
Inside .env

This needs to be unique!
```
APP_NAME=project_name
```

## Switching mysql versions
Just use mysql8 or mysql57 as hostname

## Switching php versions
Change php-fpm image inside Dockerfile

## Installing php extensions
Uncomment extension name in Dockerfile

## Enabling php extensions
Uncomment extension name in php.ini

## Browsing ngnix error & access logs
Logs will appear in .docker/logs directory

## Excluding docker files from git tracking
edit .git/info/exclude

add this files at the bottom
```
.docker
.env
Dockerfile
docker-compose.yml
```