# API design

## Resources
actors
movies

## URIs
/movies
/movies/{id}
/movies/{id}/actors
/movies/{movieId}/actors/{actorId}

/actors
/actors/{id}
/actors/{id}/movies

/search=?title={title}&genre={genre}&name={name}

## Resource representations

movies collection:
{
    "title": "The Matrix",
    "releaseDate": "1999-10-24"
}

actors collection:
{
    "name": "Lessie",
    "height": 120
}

actors for post:
{
    "name": "Lessie",
    "birthDate": "1992-05-12",
    "birthLocation": "Los Angeles",
    "height": 120,
    "_links": {
        "self": "/actors/4"
    }
}

movies for post:
{
    "title": "Lessie hazatér",
    "genre": ["családi", "kutyás"],
    "plot": "Lessie megtalálja az útját haza.",
    "releaseDate": 1994-12-10,
    "_links": {
        "self": "/movies/5",
    }
}

movie:
{
    "id": 1,
    "title": "Lessie hazatér",
    "genre": ["családi", "kutyás"],
    "plot": "Lessie megtalálja az útját haza.",
    "releaseDate": 1994-12-10,
    "_links": {
        "self": "/movies/5",
        "actors": "movies/5/actors"
    }
}

actor:
{
    "id": 1,
    "name": "Lessie",
    "birthDate": "1992-05-12",
    "birthLocation": "Los Angeles",
    "height": 120,
    "_links": {
        "self": "/actors/4",
        "actors": "actors/4/movies"
    }
}

## Assigned HTTP methods

###
GET {{host}}/movies
List a movie collection

###
GET {{host}}/movies/{id}
Fetch a specific movie

###
POST {{host}}/movies
Create single movie resource

###
PUT {{host}}/movies/{id}
Replace the representation of the movie

###
PATCH {{host}}/movies/{id}
Partially update the movie

###
DELETE {{host}}/movies/{id}
Removes the movie

###
PUT {{host}}/movies/{movieId}/actors/{actorId}
Associates an actor to the movie

###
DELETE {{host}}/movies/{movieId}/actors/{actorId}
Dissosiates an actor from the movie

###
GET {{host}}/movies/?title={title}&genres={genres}
Search for movies by title or genre

###
GET {{host}}/actors
Lists all actors

###
GET {{host}}/actors/{id}
Fetch a specific actor

###
POST {{host}}/actors/{id}
Adds an actor to the collection

###
PUT {{host}}/actors/{id}
Updates a specific actor

###
PATCH {{host}}/actors/{id}
Partially updates a specific actor

###
DELETE {{host}}/actors/{id}
Removes an actor form the collection

###
GET {{host}}/actors/?name={name}
Search for actors by name



