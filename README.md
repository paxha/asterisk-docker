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

## Testing

login any softphone e.g. zoiper or linphone with these credentials.

```text
username: `6001`
password: `6001`
host: YOUR_IP_ADDRESS
```

and dial `100` you will get `demo-congrats`.
