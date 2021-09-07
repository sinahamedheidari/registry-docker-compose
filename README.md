# registry-docker-compose
Simple docker-composes for creating a private docker registry with and without authentication

To create htpasswd file you need to use `htpasswd`.

To install on Ubuntu/Debian:
```
sudo apt install apache2-utils -y
```

Create a new user:
```
htpasswd -u admin
```

Then insert the new encrypted password in the file