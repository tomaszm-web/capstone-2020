### Casting Agency Capstone Project 

This is my final project for the Udacity Full Stack Nanodegree. I created a RESTful API for performing CRUD operations for Actor and Movie models stored in a Postgresql database. This API is designed to simplify and streamline process occuring in casting agency. The process involves creating movies, managing and assigning actors to those movies.

### Installing Dependencies

#### Python 3.7

Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

#### Virtual Enviornment

We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organaized. Instructions for setting up a virual enviornment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)

#### PIP Dependencies

Once you have your virtual environment setup and running, install dependencies by naviging to the `/capstone-2020` directory and running:

```bash
pip install -r requirements.txt
```

This will install all of the required packages we selected within the `requirements.txt` file.

##### Key Dependencies
- [Heroku] This is a cloud platform where this Git repository was pushed to and built from. The following files were used to setup the app on Heroku:
1. requirements.txt contains all required Python libraries which were installed  
2. Procfile contains instructions to start up  Gunicorn web server
3. manage.py is used to run all migrations to Postgres dabase hoseted on Heroku platform

The Capstone Application is live at: https://capstone-2020.herokuapp.com

- [Flask](http://flask.pocoo.org/)  is a lightweight backend microservices framework. Flask is required to handle requests and responses.

- [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use handle the lightweight sqlite database. You'll primarily work in app.py and can reference models.py. 

- [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross origin requests from our frontend server. 

- [Postman] is a development tool used to write and run tests to ensure that the API is working as intended.

- [Auth0](https://auth0.com/) is a service which is used for authentication and authorization.
##### How to set up authentication and authorization on Auth0:

1. Sign up for an Auth0 account at https://auth0.com/. You can either use username and password or log in with a social
provider (such as Facebook, Google, or Apple).Once you create your account you will be asked to create a tenant.
2. When you create an application in the Dashboard, choose application type: Single-Page App.
3. Create a new API - in API Settings:
        Enable RBAC
        Enable Add Permissions in the Access Token
   Create new API permissions:
        get:actors
        get:movies
        post:actors
        post:movies
        patch:actors
        patch:movies
        delete:actors
        delete:movies
4. Go to Users & Roles/Roles to create the following roles:
        Casting Assistant
        - can get:actors and get: movies
        Casting Director
        - can perform all actions of Casting Assistant
        - can post:actor and delete:actor
        - can patch:actor and patch:movie
        Executive Producer
        - can perform all actions
5. Go to Users & Roles/Users and create 3 users.
6. Assign one role to each user.
   
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
Example response:
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
{
  "id": 3,
  "success": true
}

POST '/movies'
Request body: {title:string, release_year:int}
- Creates a new movie using the submitted title and release_year. 
- Returns movie id as an object together with the success value. 
Example response:
{
  "id": 3,
  "success": true
}

PATCH '/actors/<int:id>'
- Updates actor information related to a given id. Name, role or gender can be updated.
Example response:
{
  "id": 2,
  "success": true
}

PATCH '/movies/<int:id>'
- Updates movie information related to a given id. Title or release_year can be updated.
Example response:
{
  "id": 2,
  "success": true
}

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
