# The Asterisk(R) Open Source PBX with Docker

## Setup

clone the repository

```shell
git clone https://github.com/paxha/astdoc.git
```

Modify/Add your configuration files you needed and

```shell
docker-compose up -d --build
```

If you need shell execution

```shell
docker exec -it asterisk.test bash
```

asterisk.test is your container name

