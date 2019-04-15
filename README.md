# Table of Contents

This container contains the confluence server installation based on Linux Centos 7 & puppet.


For previous versions or newest releases see other branches.

## Introduction


Dockerfiles to build [Confluence](https://www.atlassian.com/software/confluence)


### Version
* Version: `6.15.2.5` - Latest: Fix base.pp 2
* Version: `6.15.2.2` - Fix base.pp
* Version: `6.15.2.1` - Upgrade to 6.15.2
* Version: `6.2.1.1`
* Version: `5.10.8.2` - First version


## Installation

Pull the image from docker hub.

```bash
docker pull ffquintella/docker-confluence
```

Alternately you can build the image locally.

```bash
git clone https://github.com/ffquintella/docker-confluence.git
cd docker-confluence
./build.sh
```

## Quick Start

Just create a volume or share a host directory for /opt/confluence-home and (optionaly) for the configuration dir
confluence uses.

You can also use the pre_run_cmd variable to determine commands to be pre-runned


## Configuration

### Data Store

This image doesn't use data volumes by default but you should configure /opt/jira-home to point to a data volume or to point to a folder in the local disk

### User

No special users

### Ports

Next ports are exposed

* `8080/tcp` - default port


### Entrypoint

We use puppet as the default entry point to manage the environment

*Confluence is launched in background. Which means that is possible to restart confluence without restarting the container.*

### Hostname

It is recommended to specify `hostname` for this image, so if you will recreate confluence instance you will keep the same hostname.

### SSL certs
The image is configured to use /etc/pki/tls/certs as the base ssl cert configuration. Java will use /etc/pki/tls/certs/java/cacerts as it's keychain.

If you want to add more certs to it ou can mount this file.

### Basic configuration using Environment Variables

> Some basic configurations are allowed to configure the system and make it easier to change at docker command line


## Upgrade from previous version

Basically stop your running container;

Docker pull latest version

Start a new instance with the new image (backup your data dir)

## Credits

My thanks to the following

- Atlassian for the great KM tool
- Every one who worked building docker
- Github for the dvcs support
- Puppet guys for the great tool
- The guys at Voxpupuli for the [great puppet module](https://github.com/voxpupuli/puppet-jira) witch made this image so easier to create
