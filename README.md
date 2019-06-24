# pretix 4 Jugend hackt

This is a fork with custom templates and locale for Jugend hackt events.

The custom templates are located in `src/jugendhackt/templates`, they are mostly used to overwrite `pretixpresale` app templates.

The locale is located in `src/pretix/locale/de_jugendhackt` and contains a merged .po file with some custom translation strings, based on `de_Informal`.

With this, we only touch the upstream code in 2 places in `src/pretix/settings.py`
[INSTALLED_APPS](https://github.com/okfde/pretix/blob/master/src/pretix/settings.py#L258) and [ALL_LANGUAGES](https://github.com/okfde/pretix/blob/master/src/pretix/settings.py#L258). That should keep merge conflicts while updating to a minimum. Please check if these are still in place after updating, since this is where the overall app is notified of our own changes.

## Local setup

Follow the pretix [developer documentation](https://docs.pretix.eu/en/latest/development/setup.html).

You can ignore your own venv in `.git/info/exclude`.


## Update code from upstream

First, set `pretix/pretix` as upstream git remote. This is where we get the updates from

```bash
$ git remote add upstream https://github.com/pretix/pretix.git
```

Then fetch remote master, this will get all information from upstream, but not merge it yet.

```bash
$ git fetch upstream
```

Next, merge upstream master (or a specific release tag) into our master.

``` bash
$ git merge upstream master
```

Then you can push to our origin master. On the server pull from origin and rebuild the docker container.

## Update locale

Workflow described here https://hackmd.okfn.de/5G3L7O5HSQ2NCmV7yjQ38A#Workflow-%C3%9Cbersetzung-erstellen-und-wieder-mergen

and here https://hackmd.okfn.de/5G3L7O5HSQ2NCmV7yjQ38A#Was-passiert-wenn-sich-durch-ein-pretix-Update-etwas-%C3%A4ndert

Afterwards run  `$ make localecompile`, commit the changes and push to origin master. On the server pull from origin and rebuild the docker container.


## Docker compose

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
