# docker-apache2-reverse-proxy
Dockerized apache2 reverse proxy service.

<img width="200" src="https://www.docker.com/sites/default/files/Whale%20Logo332_5.png"/><img width="300" src="https://www.apache.org/foundation/press/kit/asf_logo.png"/>

# Building
Clone the project to your directory
```bash
git clone https://github.com/Ismail-AlJubbah/docker-apache2-reverse-proxy
```
Edit the file `config\a.conf` to add your localhost url (ex: google.local) and target URL (ex: google.nl)
```
ServerName google.local
...
ProxyPass / https://www.google.nl/
ProxyPassReverse / https://www.google.nl/
```
Then build the image
```bash
docker build -t jubba/apache2-reverse-proxy:latest .
```

# Running
Run this command to run the container 
```bash
docker run -d -p 8088:80 -u=root --name apache2-reverse-proxy -v /REPLACE-WITH-FULL-PATH/config:/etc/apache2/sites-enabled -v /REPLACE-WITH-FULL-PATH/log:/var/log/apache2  jubba/apache2-reverse-proxy
```
# Test
Edit your /etc/hosts and add this line.
```
127.0.0.1  google.local
```
Then go to [google.local](http://google.local:8088) on your browser and you will access https://google.nl

# Links
More information can be found on the following links:

1. [Original Repo by jmferrer](https://github.com/jmferrer/docker-apache2-reverse-proxy)
 
   
