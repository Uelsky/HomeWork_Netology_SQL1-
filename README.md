# Домашнее задание к лекции «Работа с SQL. Создание БД»

### Студент: Максимов Сергей Алексеевич
## Задание
### Обязательная часть
Будем развивать схему для музыкального сервиса.

Ранее существовало ограничение, что каждый исполнитель поёт строго в одном жанре, пора его убрать. Исполнители могут петь в разных жанрах, как и одному жанру могут принадлежать несколько исполнителей.

Аналогичное ограничение было и с альбомами у исполнителей — альбом мог выпустить только один исполнитель. Теперь альбом могут выпустить несколько исполнителей вместе. Как и исполнитель может принимать участие во множестве альбомов.

С треками ничего не меняем, всё так же трек принадлежит строго одному альбому.

Но появилась новая сущность — сборник. Сборник имеет название и год выпуска. В него входят различные треки из разных альбомов.

Обратите внимание: один и тот же трек может присутствовать в разных сборниках.

Задание состоит из двух частей

1. Спроектировать и нарисовать схему, как в первой домашней работе. Прислать изображение со схемой.
2. Написать SQL-запросы, создающие спроектированную БД. Прислать ссылку на файл, содержащий SQL-запросы.

## Решение
![Схема](/images/image.png)
```
CREATE TABLE Genres
(
    'id' SERIAL INTEGER PRIMARY KEY,
    'genre_name' VARCHAR(60) NOT NULL
);


CREATE TABLE Bands
(
    'id' SERIAL INTEGER PRIMARY KEY,
    'band_name' VARCHAR(60) NOT NULL
);


CREATE TABLE Albums
(
    'id' SERIAL INTEGER PRIMARY KEY,
    'album_name' VARCHAR(60) NOT NULL,
    'release_year' INTEGER NOT NULL
);


CREATE TABLE Songs
(
    'id' SERIAL INTEGER PRIMARY KEY,
    'song_name' VARCHAR(60) NOT NULL,
    'timing' INTEGER NOT NULL
    'id_album' INTEGER PEFERENCE Albums(id)
);


CREATE TABLE Collections
(
    'id' SERIAL INTEGER PRIMARY KEY,
    'collection_name' VARCHAR(60) NOT NULL,
    'release_year' INTEGER NOT NULL
);


CREATE TABLE Genres_and_bands
(
    'id' SERIAL INTEGER PRIMARY KEY,
    'id_genre' INTEGER PEFERENCE Genres(id),
    'id_band' INTEGER PEFERENCE Bands(id)
);


CREATE TABLE Albums_and_bands
(
    'id' SERIAL INTEGER PRIMARY KEY,
    'id_band' INTEGER PEFERENCE Bands(id),
    'id_album' INTEGER PEFERENCE Albums(id)
);


CREATE TABLE Collections_and_songs
(
    'id' SERIAL INTEGER PRIMARY KEY,
    'id_song' INTEGER PEFERENCE Songs(id),
    'id_collection' INTEGER PEFERENCE Collections(id)
);
```