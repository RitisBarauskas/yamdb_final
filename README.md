![example workflow](https://github.com/RitisBarauskas/yamdb_final/actions/workflows/yamdb_workflow.yaml/badge.svg)


# YaMDb API
API queries: [yatube.website:8001/api/v1/](http://yatube.website:8001/api/v1/)


## Description 
The YaMDb project collects user reviews of works.
The works are divided into categories: Books, Movies, Music.

## User registration algorithm

1. User sends a request with the `email` parameter to `/auth/email/`.
2. YaMDB sends an email with a `confirmation_code` to the `email` address.
3. User sends request with `email` and `confirmation_code` to `/auth/token/`, user receives a `token` (JWT token) in response.
4. If desired, the user sends a `PATCH` request to `/users/me/` and completes the fields in their profile (see documentation for description of fields).

## User roles

* **Anonymous** - can browse descriptions, read reviews and comments.
* **Authenticated User** - may, like Anonymous, read anything, in addition may post reviews and rate works (movies/books/songs), may comment on others' reviews and rate them; may edit and delete their own reviews and comments.
* **Moderator** - the same rights as an Authenticated User plus the right to remove any reviews and comments.
* **Administrator** - full rights to manage the project and all its contents. Can create and delete categories and works. Can assign roles to users.
* **Django Administrator** - The same rights as the Administrator role.

## Install

 1. Install docker and docker-compose on your server
 2. Copy `docker-compose.yaml` and `nginx/default` on you directory with your settings
 3. Create secrets in repository GITHUB
 ```
USERNAME_DOCKER # Pass Docker Hub
PASSWORD_DOCKER # Login от Docker Hub
HOST_SERVER # Public IP your server
USERUSER_SERVER # Server user
SSH_KEY # Private SSH-KEY 
PASSPHRASE # Password for SSH-KEY
TELEGRAM_TO # ID your telegram
TELEGRAM_TOKEN # Token TG bot
```
 4. PUSH on Github

 ## First settings
 1. Connect to your server
 2. Run:  
 * `sudo docker-compose exec web bash`
 * `python manage.py makemigrations api`
 * `python manage.py makemigrations`
 * `python manage.py migrate`
 * `python manage.py collectstatic`
 * `python manage.py loaddata fixtures.json` - if your needs default data
 * `python manage.py createsuperuser`
 * `exit`
3. Test your API-service

## Author
Ritis Barauskas, fullstack developer
+79526578502 (tel, WA, TG)


