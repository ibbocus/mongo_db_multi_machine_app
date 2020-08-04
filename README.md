# Sparta App
This app includes 3 pages
- The home page showing you have connected to the sparta app
- A page allowing you to see a number at a specific position within the fibonacci sequence
- A page which pulls from a randomly formed database to produce a page of posts

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

What things you need to install the software and how to install them

```
Ruby
  - Bundler
Virtual Box
Vagrant
```

### Installing

Within the directory containing Vagrantfile
``` /mongodb-multi-machine/solution-code ```

Run:
```
vagrant up
```

This will result in the app automatically initialising.

To obtain further information run:

``` 
vagrant ssh app
```

Then once inside the vm

```
cd /home/ubuntu/app
pm2 status
```

This will allow you to troubleshoot whether the app is running
## Running the tests

Within the directory named tests
``` /mongodb-multi-machine/solution-code/tests ```

Run the following line:
```
rake spec
```

This will test whether all the dependencies have been properly installed

## Authors

* **Ibrahim Bocus** - *Initial work* - [SpartaGlobal](www.spartaglobal.com)


## Acknowledgments
* Thank you to Sparta Global for providing the base code to produce this app

## Additional Information

# Nginx Reverse Proxy 

# What is Nginx?
- Nginx is an open source high performance web server (stores, processes and delivers web pages to users) that powers many modern web applications. 

## What is a reverse proxy?
- A server that sits in front of web servers and forwards clients requests (e.g. web browser) to those web servers.
- Reverse proxies are typically implemented to help increase security, performance and reliability.

## What is a proxy server?
- A forward proxy, often called a proxy, proxy server, web proxy, is a server that sits in front of a group of client machines
- When those computers make requests to sites and services on the Internet, the proxy server intercepts those requests and then communicates with web servers on behalf of those clients, like an intermediary. 



## Reverse Proxy
- A reverse proxy is a server that sits in front of one or more web servers, intercepting requests from clients



### Changes to the proxy config file
```bash
sudo unlink /etc/nginx/sites-enabled/default
cd /etc/nginx/sites-available
sudo touch reverse-proxy.conf
sudo chmod 666 reverse-proxy.conf
echo "server{
  listen 80;
  location / {
      proxy_pass http://192.168.10.100:3000;
  }
}" >> reverse-proxy.conf
sudo ln -s /etc/nginx/sites-available/reverse-proxy.conf /etc/nginx/sites-enabled/reverse-proxy.conf
sudo service nginx restart

```



# Restart `NGINX` in order to effect changes
```bash
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx
```


Due to the provisions.sh running during the vagrant up process the app will automaticall run due to pm2 start app.js
Therefore nothing has to be done once vagrant up is run

