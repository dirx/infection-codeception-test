# Testing infection with codeception

Based on: 

* Feature branch: https://github.com/infection/infection/tree/feature/codeception
* PR: https://github.com/infection/infection/pull/800

Build image with xdebug & composer

```bash
docker-compose build --pull php
```

Update dependencies

```bash
docker-compose run php composer
```

Run tests

```bash
docker-compose run php vendor/bin/codecept run
```

Run infection (first time - will fail)

```bash
docker-compose run php vendor/bin/infection
```

Run codeception tests with initial infection based config (wail fail):

```bash
docker-compose run php vendor/bin/codecept run --config /app/./infection/codeception.initial.infection.yml --coverage-phpunit codeception-coverage-xml --xml /app/./infection/junit.xml
```

Change dump configuration in [tests/integration.suite.yml#L10](./tests/integration.suite.yml) to ```'../tests/_data/stuff.sql'```.

Run infection again (now ok)

```bash
docker-compose run php vendor/bin/infection
```
