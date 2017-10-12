docker build -t dev_laravel:5.5 .

docker run --rm -it --name laravel_5.5 -v "$PWD":/project -w /project dev_laravel:5.5 /bin/bash
