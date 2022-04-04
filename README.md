# FastAPI + SQLModel + Alembic

Sample FastAPI project that uses async SQLAlchemy, SQLModel, Postgres, Alembic, and Docker.

## Want to learn how to build this?

Check out the [post](https://testdriven.io/blog/fastapi-sqlmodel/).

## Want to use this project?

```sh
$ docker-compose up -d --build
$ docker-compose up
$ docker-compose exec web alembic upgrade head
```

Sanity check: [http://localhost:8004/ping](http://localhost:8004/ping)

Add a song:

```sh
$ curl -d '{"name":"Midnight Fit", "artist":"Mogwai", "year":"2021"}' -H "Content-Type: application/json" -X POST http://localhost:8004/songs
```

Get all songs: [http://localhost:8004/songs](http://localhost:8004/songs)

создание миграции
```sh
docker-compose exec web alembic revision --autogenerate -m "init"
alembic revision --autogenerate -m "add_unique_name_in_film"
```

применение миграции
```sh
docker-compose exec web alembic upgrade head
alembic upgrade head
```
downgrade
```sh
docker-compose exec web alembic downgrade head
alembic downgrade head
```