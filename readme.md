# Laravel Heroku Deployment Tutorial

## Creating a Procfile

```bash
$ echo web: vendor/bin/heroku-php-apache2 public/ > Procfile
```

## Create or Link Heroku

Create a Heroku App:

```bash
$ heroku create
```

Or link project to existing Heroku App:

```bash
$ git remote add heroku git@heroku.com:<app-name>.git
```

Change `<app-name>` to your Heroku App name

## Setup Database

Add a PostgreSQL Database

```bash
$ heroku addons:create heroku-postgresql:hobby-dev
```

## Add database credentials to the Heroku App

Go to https://dashboard.heroku.com/apps and click on your Application.

Click on the `Installed add-ons` -> `Heroku Postgres` 

From the new website, click on `Settings` -> `View Credentials` to see database credentials

Go back to the website https://dashboard.heroku.com/apps/<your-app> and click on `Settings` -> `Reveal Config Vars`

Add the following to the config vars:

`DB_CONNECTION` -> `pgsql`

`DB_DATABASE` -> `Database from Database Credentials`

`DB_HOST` -> `Host from Database Credentials`

`DB_PASSWORD` -> `Password from Database Credentials`

`DB_PORT` -> `Port from Database Credentials`

`DB_USERNAME` -> `User from Database Credentials`

## Migrate

Run php migrations

```bash
$ heroku run php /app/artisan migrate
```

Or you can use heroku bash to migrate

```bash
$ heroku run bash
```

```bash
$ php artisan migrate
```

## Reference

[Getting Started with Laravel on Heroku](https://devcenter.heroku.com/articles/getting-started-with-laravel)
