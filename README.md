# keycloak-security-example

[![MIT License](https://img.shields.io/apm/l/atomic-design-ui.svg?)](https://github.com/tterb/atomic-design-ui/blob/master/LICENSEs) [![Main Branch workflow](https://github.com/wkrzywiec/keycloak-security-example/actions/workflows/main.yaml/badge.svg?branch=main)](https://github.com/wkrzywiec/keycloak-security-example/actions/workflows/main.yaml)


* *Keycloak* (authorization server) - open-source tool for identity and access management,

This project was created for learning purposes, if you would like to know more about OAuth 2.0 in general go check my blog posts listed below.

## Prerequisites

To run all necessary applications first you need to install Docker with Docker Compose (for Windows and MacOS it's already bundled with Docker). Instructions can be found on the official website:

* [Ubuntu (Linux)](https://docs.docker.com/install/linux/docker-ce/ubuntu/),
* [Windows](https://docs.docker.com/docker-for-windows/install/),
* [MacOS](https://docs.docker.com/docker-for-mac/install/).

Instructions for installing Docker Compose on Linux can be found [here](https://docs.docker.com/compose/install/).

### Edit hosts file

Apart from installing Docker you also need to edit **hosts** file of your OS.

JWT's payload contains a field **iss** (issuer). It's an URL of an authorization server, in our case Keycloak. In the backend application we need to provide exactly the same URL to the keycloak. But here is the problem that a Docker network and machine's hosts are not the same. From point of view of a backend service a keycloak will have different URL than from point of view of a user! 

To mitigate this problem you need to add following lines to the *hosts* file:
```
127.0.0.1	keycloak
```

Location of *hosts* file on different OS:
* [Linux (Ubuntu)](http://manpages.ubuntu.com/manpages/trusty/man5/hosts.5.html)
* [Windows 10](https://www.groovypost.com/howto/edit-hosts-file-windows-10/)
* [Mac](https://www.imore.com/how-edit-your-macs-hosts-file-and-why-you-would-want#page1)

## Usage

To run all apps just run following command in a terminal

```bash
> docker-compose up -d
```
docker logs --follow keycloak

It will spin up all necessary parts like Keycloak with its database.
Also first startup of all Docker containers might take awhile, especially a Keycloak container, because it not only run it but also it's applying an initial configuration like a predefined Keycloak realm, users, roles and clients.



KeyCloak admin console: http://localhost:8080
to login:
username: admin
password: admin

## Keycloak Client id, secret
There is a client called "test_client". To see this client, on the admin console,
 you can go to Clients on the left6 hand side menu. Select test_client from the list
 Once you select test_client, go to Credentials and there you will see secret. This secret can be used \
 in requests to keycloak


