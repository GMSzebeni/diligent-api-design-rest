# API design

## Resources
actors
movies

## URIs
/movies
/movies/{id}
/movies/{id}/actors

/actors
/actors/{id}
/actors/{id}/movies

/search=?title={title}&genre={genre}&name={name}

## Resource representations

movies collection:
{
    "id": 5,
    "title": "The Matrix",
    "releaseDate": "1999-10-24",
    "_links": {
        "self": "/movies/5",
        "actors": "movies/5/actors"
    }
}

actors collection:
{
    "name": "Lessie",
    "height": 120,
    "_links": {
        "self": "/actors/4",
        "actors": "actors/4/movies"
    }
}

movie:
{
    "id": 1,
    "title": "Lessie hazatér",
    "genre": ["családi", "kutyás"],
    "plot": "Lessie megtalálja az útját haza.",
    "releaseDate": 1994-12-10,
    "actors": [{
        "name": "Lessie",
        "height": 120
    },
    {
        "name": "XY",
        "height": 180
    }]
}

actor:
{
    "id": 1,
    "name": "Lessie",
    "birthDate": 1992-05-12,
    "birthLocation": "Los Angeles",
    "height": 120,
    "movies": [{
        "title": "Lessie hazatér",
        "releaseDate": 1994-12-10
    }]
}

## Assigned HTTP methods

###
GET {{host}}/movies
List a movie collection

###
GET {{host}}/movies/{id}
Fetch a concrete movie

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
PUT {{host}}/movies/{movieId}/actors/{actorId}
Connects an actor to the movie

###
DELETE {{host}}/movies/{id}
Removes a movie from a collection

###
GET {{host}}/movies/?title={title}&genres={genres}

###
GET {{host}}/actors

###
GET {{host}}/actors/{id}

###
POST {{host}}/actors/{id}

###
PUT {{host}}/actors/{id}

###
PATCH {{host}}/actors/{id}

###
DELETE {{host}}/actors/{id}

###
GET {{host}}/actors/?name={name}



