## Benchmarking using the supplied Docker Stack

Use the supplied Docker Stack in order to automatically set up the following benchmarking environments:

* Ubuntu 15.04 64bit (Docker)
  * PHP-FPM 5.6.4
    * Zend OPcache 7.0.4-dev
    * PhalconPHP 2.0.9
  * HHVM 3.10.1

By sharing underlying software stacks, the benchmark results vary only according to the host machine's hardware specs and ORM implementations.

### Getting Started

Install [Docker Toolbox](https://www.docker.com/docker-toolbox).

Cd into the `.docker-stack` directory of this repo and make sure that docker toolbox is available:
```
cd .docker-stack
eval "$(docker-machine env default)"
```

Start the supplied docker shell:
```
docker-compose run shell
```

Run benchmarks using PHP 5.6.4:
```
php TestRunner.php
```

Run benchmarks using HHVM 3.10.1:
```
/usr/bin/update-alternatives --install /usr/bin/php php /repo/.docker-stack/stack/php/hhvm-jit.sh 60
php TestRunner.php
```

To return to using PHP 5.6.4, simply exit the Docker shell and enter it again.
