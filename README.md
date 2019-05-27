# pretix 4 Jugend hackt

[![Build Status](https://travis-ci.com/okfde/pretix.svg?branch=master)](https://travis-ci.com/okfde/pretix)


This is a fork with custom templates for Jugend hackt events.



## Local setup

Follow the pretix dev `developer documentation`_

You can ignore your venv in `.git/info/exclude`

## Update the fork

First, set `pretix.pretix` as upstream repo.

```bash
$ git remote add upstream https://github.com/pretix/pretix.git
```

Then fetch remote master and rebase onto it.

```bash
$ git fetch upstream master && git rebase upstream/master
```

### Docker compose

`docker-compose.yml` contains our Docker production setup.

It'll read config values from the environment. See `env.sample` for variables needed.
On the server (or wherever) `$ cp env.sample .env` and adjust your values.
Then you can `$ docker-compose up` that stuff.

## Contributing

tbd

## Code of Conduct

We have a [Code of Conduct](CODE_OF_CONDUCT.md) in place that applies to all project contributions,
including issues, pull requests, etc.

## License

The code in this repository is published under the terms of the Apache License.
See the LICENSE file for the complete license text.

Big thanks to Raphael Michel mail@raphaelmichel.de, pretix' main developer, and the folks listed in the  AUTHORS file  who contributed to the project.
