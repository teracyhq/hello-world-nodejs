# hello-world-nodejs

This is a basic example for a hello world nodejs app with Docker workflow running on teracy-dev v0.5.0


## Getting Started

- Set up the latest stable version of teracy-dev v0.5.0 from: https://github.com/teracyhq/dev with the
  following custom configuration (`vagrant_config_override.json`):

```json
{
  "provisioners": [{
    "_id": "0",
    "json": {
      "teracy-dev": {
        "env_vars": [{
          "_id": "1",
          "key": "DOCKER_HIDE_LEGACY_COMMANDS",
          "value": "true",
          "action": "add"
        }],
        "proxy": {
          "container": {
            "enabled": true
          }
        }
      }
    }
  }],
  "plugins": [{
    "_id": "2",
    "options": {
      "aliases": ["hello-d.teracy.dev", "hello.teracy.dev"]
    }
  }]
}

```

After `$ vagrant up` successfully, clone this repo into the `~/teracy-dev/workspace` directory:

```
$ cd ~/teracy-dev/workspace
$ git clone https://github.com/teracyhq/hello-world-nodejs.git
```

## Running on dev mode

`ssh` into the teracy-dev VM to execute the following commands:

```
$ vagrant ssh
$ ws
$ cd hello-world-nodejs
$ docker-compose up -d
```

After that, open hello-d.teracy.dev on your browser to see the app on the dev mode.

## Running on prod mode

`ssh` into the teracy-dev VM to execute the following commands:

```
$ vagrant ssh
$ ws
$ cd hello-world-nodejs
$ docker-compose -f docker-compose.prod.yml up -d
```

After that, open hello.teracy.dev on your browser to see the app on the prod mode.

