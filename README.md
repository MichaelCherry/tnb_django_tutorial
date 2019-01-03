# tnb_django_tutorial
Django tutorial based on playlist from thenewboston ( https://www.youtube.com/playlist?list=PL6gx4Cwl9DGBlmzzFcLgDhKTTfNLfX1IK )

## Run the Webpage (example from part 8)

To start the webpage, run
```shell
$python manage.py runserver
```

## Migrate the Database

Change the models.py file

($ is the command, the rest is the output)
```shell
$ python manage.py makemigrations music
Migrations for 'music':
  music\migrations\0001_initial.py
    - Create model Album
    - Create model Song
```

```shell
$ python manage.py sqlmigrate music 0001
BEGIN;
--
-- Create model Album
--
CREATE TABLE "music_album" ("id" integer NOT NULL PRIMARY KEY AUTOINCREMENT, "artist" varchar(250) NOT NULL, "album_title" varchar(500) NOT NULL, "genre" varchar(100) NOT NULL, "album_logo" varchar(1000) NOT NULL);
--
-- Create model Song
--
CREATE TABLE "music_song" ("id" integer NOT NULL PRIMARY KEY AUTOINCREMENT, "file_type" varchar(10) NOT NULL, "song_title" varchar(250) NOT NULL, "album_id" integer NOT NULL REFERENCES "music_album" ("id") DEFERRABLE INITIALLY DEFERRED);
CREATE INDEX "music_song_album_id_62a413c8" ON "music_song" ("album_id");
COMMIT;
```

```shell
$ python manage.py migrate
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, music, sessions
Running migrations:
  Applying music.0001_initial... OK
```


CONTINUE FROM
https://www.youtube.com/watch?v=uYTiPwEGKyQ&index=9&list=PL6gx4Cwl9DGBlmzzFcLgDhKTTfNLfX1IK


NOTE: this is using Django 2.4.1. There are some minor syntax differences between this version and the version in TheNewBoston's tutorial.