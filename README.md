

# Development

## Build & Up

docker-compose up -d --build

docker-compose down -v

## Database operations

docker-compose exec web python manage.py flush --no-input
docker-compose exec web python manage.py migrate
docker-compose exec db psql --username=hello_django --dbname=hello_django_dev
docker-compose exec db psql --username=hello_django --dbname=hello_django_prod

docker-compose logs -f

# Production

## Build & Up

docker-compose -f docker-compose.prod.yml up -d --build

docker-compose -f docker-compose.prod.yml down -v

## Database operations

docker-compose -f docker-compose.prod.yml exec web python manage.py migrate --noinput

## Logs

docker-compose -f docker-compose.prod.yml logs -f

## Tests

hey -z 10s -z 3m http://localhost:1337