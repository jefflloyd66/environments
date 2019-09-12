docker build -t php:7.3-dev .

docker run --rm -d -p 80:80 -v $PWD:/var/www php:7.3-dev