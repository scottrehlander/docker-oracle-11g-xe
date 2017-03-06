docker-oracle-xe-11g
============================

## Oracle XE - Dockerfile

This repository uses Oracle Express Edition 11g Release 2 and Ubuntu 14.04 LTS (Trusty)


### How-To: Install and Use

Download the contents of the repository and cd to the base directory then execute:

```
docker build -t <insert desired docker container name here> .
```
**Note:** The Oracle installation may ask you to confirm that it should run on OS startup, choose yes.
**Note:** It's important to run Oracle XE with >1GB shared memory.

### Start Oracle XE
Running Oracle XE in `detached` mode with `1521` and `8080` ports opened and `2GB` shared memory:

```
docker run -d --shm-size=2g -p 1521:1521 -p 8080:8080 <insert docker container name here>
```

### You can optionally start Oracle XE and execute SQL on startup

Put your `*.sql` files for database init into some local folder and mount this folder during container startup to `/etc/entrypoint-initdb.d` volume.

```
docker run -d --shm-size=1g -p 8080:8080 -p 1521:1521 -v /local-initdb:/etc/entrypoint-initdb.d <insert docker container name here>
```

### Connect

Connect database with following setting:
```
hostname: localhost
port: 1521
sid: xe
username: system
password: oracle
```

Password for **SYS** user
```
oracle
```

Connect to Oracle Application Express web management console with following settings:
```
url: http://localhost:8080/apex
workspace: internal
user: admin
password: oracle
```

Do not forget to change `admin` password!
