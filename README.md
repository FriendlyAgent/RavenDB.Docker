# RavenDB.Docker
This repo contains the base dockerfiles for building RavenDB(Server) Images.

[![Docker Stars](https://img.shields.io/docker/stars/friendlyagent/ravendb.svg?style=flat)](https://hub.docker.com/r/friendlyagent/ravendb/)
[![Docker Pulls](https://img.shields.io/docker/pulls/friendlyagent/ravendb.svg?style=flat)](https://hub.docker.com/r/friendlyagent/ravendb/)
[![Docker build](https://img.shields.io/docker/automated/friendlyagent/ravendb.svg?style=flat)](https://hub.docker.com/r/friendlyagent/ravendb/)

# Supported tags and respective `Dockerfile` links
|Version|Build|Tags|Base|Git|
|:------------|:-------------|:-------------|:-------------|:-------------|
|4.0.0-alpha|40012 |**40012**, **4.0.0-alpha-40012**, **latest**|ubuntu:xenial|[RavenDB.Docker](https://github.com/FriendlyAgent/RavenDB.Docker/tree/master/40012/ubuntu "40012")|
|4.0.0-alpha|40010 |**40010**, **4.0.0-alpha-40010**|ubuntu:xenial|[RavenDB.Docker](https://github.com/FriendlyAgent/RavenDB.Docker/tree/master/40010/ubuntu "40010")|
|4.0.0-alpha|40009 |**40009**, **4.0.0-alpha-40009**|ubuntu:xenial|[RavenDB.Docker](https://github.com/FriendlyAgent/RavenDB.Docker/tree/master/40009/ubuntu "40009")|
|4.0.0-alpha|40008 |**40008**, **4.0.0-alpha-40008**|ubuntu:xenial|[RavenDB.Docker](https://github.com/FriendlyAgent/RavenDB.Docker/tree/master/40008/ubuntu "40008")|
|4.0.0-alpha|40005 |**40005**, **4.0.0-alpha-40005**|ubuntu:xenial|[RavenDB.Docker](https://github.com/FriendlyAgent/RavenDB.Docker/tree/master/40005/ubuntu "40005")|

# How to use this image
`docker run -p 8080:8080 friendlyagent/ravendb`
This will store the workspace in `/var/lib/ravendb` all RavenDB data is contained within that workspace. **RavenDB will store the system and subsequent database(s) there.**

>**Note:** You will probably want to make that a persistent volume (recommended).


`docker run -p 8080:8080 -v /your/home:/var/lib/ravendb friendlyagent/ravendb`
This will store the RavenDB data in `/your/home` on the host.

## You can also use a volume container
`docker run --name myravendb -p 8080:8080 -v /var/lib/ravendb friendlyagent/ravendb`
Then myravendb container has the volume (please do read about docker volume handling to find out more).

## Environment Variables
You can use environment properties to manipulate the container (Example: `-e RAVEN_ServerUrl='http://0.0.0.0:9090'`)

* RAVEN_Port: The port to use when creating the http listener.
* RAVEN_ServerUrl: The URLs which the server should listen to.
* RAVEN_DataDir: The directory for the RavenDB resource.
* RAVEN_EverybodyAsAdmin: When set to true, exposes the database to the world.

# User Feedback

## Issues

If you have any problems with or questions about this image, please contact us through a [GitHub issue](https://github.com/FriendlyAgent/RavenDB.Docker/issues).