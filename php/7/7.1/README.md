docker build -t devenv-php:7.1 .

docker run --rm -it --name devenv-php_7.1 -v "$PWD":/project -w /project devenv-php:7.1 /bin/bash
