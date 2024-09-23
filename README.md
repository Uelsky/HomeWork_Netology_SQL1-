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
![Схема](/images/Снимок%20экрана%202024-09-23%20153130.png)
```
CREATE TABLE Genres
(
    'id' INTEGER PRIMARY KEY AUTO_INCREMENT,
    'genre_name' VARCHAR(60) NOT NULL
);


CREATE TABLE Bands
(
    'id' INTEGER PRIMARY KEY AUTO_INCREMENT,
    'band_name' VARCHAR(60) NOT NULL
);


CREATE TABLE Albums
(
    'id' INTEGER PRIMARY KEY AUTO_INCREMENT,
    'album_name' VARCHAR(60) NOT NULL,
    'release_year' INTEGER NOT NULL
);


CREATE TABLE Collection
(
    'id' INTEGER PRIMARY KEY AUTO_INCREMENT,
    'collection_name' VARCHAR(60) NOT NULL,
    'release_year' INTEGER NOT NULL
);


CREATE TABLE Songs
(
    'id' INTEGER PRIMARY KEY AUTO_INCREMENT,
    'song_name' VARCHAR(60) NOT NULL,
    'timing' TIME NOT NULL
);


CREATE TABLE Union_table
(
    'id' INTEGER PRIMARY KEY AUTO_INCREMENT,
    'id_genre' INTEGER REFERENCE Genres(id),
    'id_band' INTENGER REFERENCE Bands(id),
    'id_album' INTENGER REFERENCE Albums(id),
    'id_collection' INTENGER REFERENCE Collection(id),
    'id_song' INTENGER REFERENCE Songs(id)
);
```