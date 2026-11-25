# Meal Rater API

A REST API for rating meals from 1 to 5 stars, built with Django REST Framework. Each meal shows how many ratings it has and its average score.

## Features

- **Meals** with a title and description, plus `no_of_ratings` and `avg_rating` computed from their ratings
- **Rate a meal** with one call: creates your rating or updates it if you already rated that meal
- One rating per user per meal, limited to 1–5 stars
- **Users:** sign up and get an auth token back right away
- Token authentication for meals and ratings

## API

| Method | Endpoint | Description |
| --- | --- | --- |
| POST | `/api/users/` | Sign up, returns a token |
| POST | `/tokenrequest/` | Get a token with username and password |
| GET, POST | `/api/meals/` | List or create meals |
| GET, PUT, DELETE | `/api/meals/<id>/` | Read, update or delete a meal |
| POST | `/api/meals/<id>/rate_meal/` | Rate a meal (`{"stars": 4}`) |
| GET | `/api/ratings/` | List ratings |

Send the token as `Authorization: Token <token>`.

## Built with

- Python 3, Django, Django REST Framework
- SQLite

## Run it locally

```bash
git clone https://github.com/hamzakhalem/Django-meals-rates.git
cd Django-meals-rates
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install django djangorestframework
export DJANGO_SECRET_KEY="any-long-random-string"   # PowerShell: $env:DJANGO_SECRET_KEY="..."
cd MealRater
python manage.py migrate
python manage.py runserver
```

## Project structure

```
MealRater/
  MealRater/   Settings and root URLs
  api/         Meal and rating models, serializers, viewsets
```
