Casting Agency Capstone Project

## Getting Started

### Installing Dependencies

#### Python 3.7

Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

#### Virtual Enviornment

We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organaized. Instructions for setting up a virual enviornment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)

#### PIP Dependencies

Once you have your virtual environment setup and running, install dependencies by naviging to the `/backend` directory and running:

```bash
pip install -r requirements.txt
```

This will install all of the required packages we selected within the `requirements.txt` file.

##### Key Dependencies

- [Flask](http://flask.pocoo.org/)  is a lightweight backend microservices framework. Flask is required to handle requests and responses.

- [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use handle the lightweight sqlite database. You'll primarily work in app.py and can reference models.py. 

- [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross origin requests from our frontend server. 

- [Auth0](https://auth0.com/) is the service we'll be using for proper authentication and authorization.

## Running the server

To run the server, execute:

```bash
export FLASK_APP=app
export FLASK_ENV=development
flask run
```

Setting the `FLASK_ENV` variable to `development` will detect file changes and restart the server automatically.

Setting the `FLASK_APP` variable to `app` directs flask to use the `app` directory and the `__init__.py` file to find the application. 

## Endpoints
The API will return four error types when requests fail:

    400: Bad Request
    404: Resource Not Found
    422: Not Processable
    405: Method not allowed

ENDPOINTS:
GET '/actors'
GET '/movies'
POST '/actors'
POST '/movies'
PATCH '/actors/<int:id>'
PATCH '/movies/<int:id>'
DELETE '/actors/<int:id>'
DELETE '/movies/<int:id>'

GET '/actors'
 - Returns a list of actors.
{
  "actors": [
    {
      "gender": "male",
      "name": "Tom Hanks",
      "role": "runner"
    },
    {
      "gender": "male",
      "name": "Marlon Brando",
      "role": "runner"
    }
  ],
  "success": true
}

GET '/movies'
 - Returns a list of movies.
Example response:
{
  "movies": [
    {
      "release_year": 2019,
      "title": "Raging Bull"
    },
    {
      "release_year": 2015,
      "title": "Cast Away"
    }
  ],
  "success": true
}

POST '/actors'
Request body: {name:string, role:string, gender:string, movie_id:int}
- Creates a new actor using the submitted name, role, gender and movie_id. 
- Returns actor id as an object together with the success value. 
Example response:
post
{
  "id": 3,
  "success": true
}

POST '/movies'
Request body: {title:string, release_year:int}
- Creates a new movie using the submitted title and release_year. 
- Returns movie id as an object together with the success value. 

Example response:
post
{
  "id": 3,
  "success": true
}

PATCH '/actors/<int:id>'
PATCH '/movies/<int:id>'

DELETE '/actors/<int:id>'
- Deletes the actor of the given ID if it exists. Returns the id of the deleted actor and success value.
- Request Arguments: id <int:id>

{
  "deleted": 3, 
  "success": true
}

DELETE '/movies/<int:id>'
- Deletes the movie of the given ID if it exists. Returns the id of the deleted movie and success value.
- Request Arguments: id <int:id>

{
  "deleted": 3, 
  "success": true
}
