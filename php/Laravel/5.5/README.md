docker build -t dev_laravel:5.5 .

docker run --rm -it --name laravel_5.5 -v "$PWD":/project -w /project -p 8000:8000 dev_laravel:5.5 /bin/bash

### Starting a new project
* start container
* laravel new project-name --dev
* php artisan key:generate
* serve (to view on web browser http://localhost:8000)
