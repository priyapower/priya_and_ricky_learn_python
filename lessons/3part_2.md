# Part 2 Practice
Keyword - REST
![rest](https://static.onecms.io/wp-content/uploads/sites/35/2017/04/03204310/fb-lazy-cat-rest-day-gif.gif)
## With Python, MongoDB, and Flask (No testing)

## What is on this page

Ricky/Windows/Beginner:
- [Ricky's Practice](#rickys-practice)
- Goal is to create a number guessing game
- Product: [Finished Product]()

Priya/Mac/Intermediate:
- [Priya's Practice](#priyas-practice)
- Goal is to build a a RESTful api with Flask and MongoDB
- Product: [Finished Product]()

## Ricky's Practice
Goal is to create a number guessing game

(more coming soon...)

- theory part 2 notes
- notes on how he completed this project

## Priya's Practice
Goal is to build a a RESTful api with Flask and MongoDB

[Setup](#setup)

[Get your Root Endpoint Exposed](#get-your-root-endpoint-exposed)

[Let's Get an Index of Movies Returned](#lets-get-an-index-of-movies-returned)

[CRUD - It's What You Do](#crud-its-what-you-do)

[Test CRUD out with Postman](#test-crud-with-postman)

[Installing Mongodb and Understanding the Library We Will Use](#installing-mongodb-and-understanding-the-library-we-will-use)

[Getting Started with the Database](#getting-started-with-the-database)

[Connect Your Database with Your App](#connect-your-database-with-your-app)

[Make Our API Endpoints More Robust](#make-our-api-endpoints-more-robust)

[Run the Server and Test in Postman](#run-the-server-and-test-in-postman)

[Add Data to Database](#add-data-to-database)

[Best Practices for Organizing Code](#best-practices-for-organizing-code)

[Blueprints](#blueprints)

[Flask RESTful](#flask-restful)

[Authentication and Authorization](#Authentication-and-Authorization)

[Blarg](#blarg)

#### Setup
  - Following [this tutorial](https://dev.to/paurakhsharma/flask-rest-api-part-0-setup-basic-crud-api-4650)
  - Create your project folder/directory: `mkdir practice_api_movies`
  - `cd practice_api_movies`
  - Create a new virtual environment
  - Successful installation of pipenv, includes errors
    - tried `pip install --user pipenv`, error = 'no command pip'
    - tried `pip3 install --user pipenv` and got a correct sequence, however, could not use `pipenv` still
    - Finally tried `sudo -H pip install -U pipenv` ([source](https://stackoverflow.com/questions/46391721/pipenv-command-not-found))
  - Use `pipenv install flask` to install flask
  - The following prints out
      ```console
      Creating a virtualenv for this project...
      Pipfile: /Users/priyapower/Coding/learning/python/practice_api_movies/Pipfile
      Using /usr/local/bin/python3 (3.9.1) to create virtualenv...
      ⠋ Creating virtual environment...created virtual environment CPython3.9.1.final.0-64 in 627ms
        creator CPython3Posix(dest=/Users/priyapower/.local/share/virtualenvs/practice_api_movies-8EKfv0js, clear=False, no_vcs_ignore=False, global=False)
        seeder FromAppData(download=False, pip=bundle, setuptools=bundle, wheel=bundle, via=copy, app_data_dir=/Users/priyapower/Library/Application Support/virtualenv)
          added seed packages: pip==20.3.1, setuptools==51.0.0, wheel==0.36.1
        activators BashActivator,CShellActivator,FishActivator,PowerShellActivator,PythonActivator,XonshActivator
      ✔ Successfully created virtual environment!
      Virtualenv location: /Users/priyapower/.local/share/virtualenvs/practice_api_movies-8EKfv0js
      Creating a Pipfile for this project...
      Installing flask...
      Adding flask to Pipfile's [packages]...
      ✔ Installation Succeeded
      Pipfile.lock not found, creating...
      Locking [dev-packages] dependencies...
      Locking [packages] dependencies...
      Building requirements...
      Resolving dependencies...
      ✔ Success!
      Updated Pipfile.lock (9536c4)!
      Installing dependencies from Pipfile.lock (9536c4)...
        🐍   ▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉ 0/0 — 00:00:00
      To activate this project's virtualenv, run pipenv shell.
      Alternatively, run a command inside the virtualenv with pipenv run.
      ```
  - There should be **2** new files in your project directory, `Pipfile` and `Pipfile.lock` (confirmed)
  - My `Pipfile` contains the packages (**flask** package is on ln 7) - which means if someone else downloads this code and uses `pipenv install` they should get **flask** as well, similar to a `requirements.txt` file:
      ```console
      [[source]]
      url = "https://pypi.org/simple"
      verify_ssl = true
      name = "pypi"

      [packages]
      flask = "*"

      [dev-packages]

      [requires]
      python_version = "3.9"
      ```

- #### Get your Root endpoint Exposed
  - Make a file for our rest api: `touch app.py`
  - Code for the app file:
      ```python
      # imports the flask class from the flask package
      from flask import Flask

      app = Flask(__name__)

      # Defines the root endpoint (@app.route == decorator)
      @app.route('/')
      # When '/' endpoint is called, it returns this function, hello()
      def hello():
          # which returns {'hello': 'world'}
          return {'hello': 'world'}

      # This line starts the flask server
      app.run()
      ```
  - To **RUN** the app, you first enable the virtual environment with `pipenv shell`
  - Response:
      ```console
      /Users/priyapower/Coding/learning/python/practice_api_movies  $🐧pipenv shell
        Launching subshell in virtual environment...
          . /Users/priyapower/.local/share/virtualenvs/practice_api_movies-8EKfv0js/bin/activate
      /Users/priyapower/Coding/learning/python/practice_api_movies  $🐧
        . /Users/priyapower/.local/share/virtualnvs/practice_api_movies-8EKfv0js/bin/activate
      (practice_api_movies) /Users/priyapower/Coding/learning/python/practice_api_movies  $🐧
      ```
  - Run with `python app.py`
  - Response:
      ```console
      * Serving Flask app "app" (lazy loading)
      * Environment: production
       WARNING: This is a development server. Do not use it in a production deployment.
       Use a production WSGI server instead.
      * Debug mode: off
      * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
      ```
  - Checked at http://localhost:5000 OR http://127.0.0.1:5000/
  - Confirmed site response was `{'hello': 'world'}`
  - Yay! Everything is up an running
  - ![round_of_applause](https://media0.giphy.com/media/PkXrOxe77MbmavlfWa/giphy.gif)

- #### Let's get an index of movies returned
  - Time to update our `app.py` "runner" file:
      ```python
      # Imports jsonify from flask package. This converts our data into proper JSON responses
      from flask import Flask, jsonify

      app = Flask(__name__)

      #  creates a data set called movie which is an array. Each element in the array represents a movie data record that is a hash/dict datatype. Name datatype is string. Casts and Genres datatypes are arrays of strings.
      movies = [
          {
              "name": "The Shawshank Redemption",
              "casts": ["Tim Robbins", "Morgan Freeman", "Bob Gunton", "William Sadler"],
              "genres": ["Drama"]
          },
          {
             "name": "The Godfather ",
             "casts": ["Marlon Brando", "Al Pacino", "James Caan", "Diane Keaton"],
             "genres": ["Crime", "Drama"]
          }
      ]

      # Updates the endpoint beyond just / and now has a declared endpoint /movies
      @app.route('/movies')
      def hello():
          # returns the JSON version of the movie data set from line 7
          return jsonify(movies)

      app.run()
      ```
  - Tested at http://127.0.0.1:5000/movies and http://localhost:5000/movies
    - From this point, all testing will be done directly through localhost since 127.0.0.1 represents localhost
  - Now that we know our endpoint is exposing data correctly and through JSON, time to check it with **Postman**
  ![Get on Postman](https://user-images.githubusercontent.com/49959312/103389126-2e907380-4aca-11eb-8949-9ea100449747.png)
  - Woo! It works

- #### CRUD - It's what you do
  - Time to work on that CRUD (create, read, update, and destroy, see this [article](https://trendintech.com/2018/01/19/why-is-crud-so-important-in-computer-programming/) for more information on CRUD)
  - Updates to code:
      ```python
      # Imports request object from flask, see here(https://flask.palletsprojects.com/en/1.1.x/reqcontext/)
      from flask import Flask, jsonify, request

      app = Flask(__name__)

      @app.route('/')
      def hello():
          return {'hello': 'world'}

      # This is called a list in python (array in ruby/js)
      movies = [
          {
              "name": "The Shawshank Redemption",
              "casts": ["Tim Robbins", "Morgan Freeman", "Bob Gunton", "William Sadler"],
              "genres": ["Drama"]
          },
          {
             "name": "The Godfather ",
             "casts": ["Marlon Brando", "Al Pacino", "James Caan", "Diane Keaton"],
             "genres": ["Crime", "Drama"]
          }
      ]

      @app.route('/movies')
      def get_all_movies():
          return jsonify(movies)

      # CREATE
      # @app.route can take 2 arguments, the first being the endpoint, the second is the API verb (get, post, put, delete, etc). I assume without the second arg, the default is GET since the beginning of this tutorial worked :)
      @app.route('/movies', methods=['POST'])
      # New method/function name
      def add_movie():
          # set block variable movie equal to the json input (from user/client)
          movie = request.get_json()
          # Takes the movies list(what I know as array from ruby) from line 10 and adds an item (in this case, the block variable movie which has saved the user/client input in json format) to end of the list (https://www.programiz.com/python-programming/methods/list/append)
          movies.append(movie)
          # returns dict/hash of id which is set to calling the length of the list (https://www.w3schools.com/python/ref_func_len.asp) && returns a status code of 200 - successful
          return {'id': len(movies)}, 200

      # UPDATE
      # endpoint now has an integer index value it is assuming exists in the list
      @app.route('/movies/<int:index>', methods=['PUT'])
      def update_movie(index):
          movie = request.get_json()
          # replaces what is saved at the index value with the information from user/client input
          movies[index] = movie
          # returns the json version of the record at that index spot && status code 200
          return jsonify(movies[index]), 200

      # DESTROY
      @app.route('/movies/<int:index>', methods=['DELETE'])
      def delete_movie(index):
          #  removes element at index (https://www.w3schools.com/python/ref_list_pop.asp)
          movies.pop(index)
          # returns an string of none with 200 status code
          return 'None', 200

      app.run()
      ```

- #### Test CRUD out with Postman
  - Create/Post:
    - Post verb
    - Body tab = raw & JSON
    - Put user/client info for a NEW movie record in the body input section
    - Hit Send
    - VOILA! - You can confirm with /movies as a GET to see all 3 movie records
    - ![image](https://user-images.githubusercontent.com/49959312/103389125-2e907380-4aca-11eb-9f11-c0c748ada3b8.png)
  - Update/Put:
    - Put verb
    - Body tab = raw & JSON
    - Paste new info
    - Hit send
    - **ERROR** - I attempted to do /movies/3, since there are 3 records, however, it is technically id=2 because it begins at 0. Is there a discrepancy in the code? Why does POST show id=3?
    - VOILA!
    - ![image](https://user-images.githubusercontent.com/49959312/103389124-2df7dd00-4aca-11eb-8eb4-41ebb4b3fa2f.png)
  - Destroy/Delete:
    - Ensure correct id in endpoint uri
    - Delete verb
    - Hit send
    - VOILA!
    - ![image](https://user-images.githubusercontent.com/49959312/103389122-2d5f4680-4aca-11eb-99d0-0f3abee0cf08.png)

- Final Code for this section:
  ```py
  Part 0 Final product
  from flask import Flask, jsonify, request

  app = Flask(__name__)

  @app.route('/')
  def hello():
      return {'hello': 'world'}

  movies = [
      {
          "name": "The Shawshank Redemption",
          "casts": ["Tim Robbins", "Morgan Freeman", "Bob Gunton", "William Sadler"],
          "genres": ["Drama"]
      },
      {
         "name": "The Godfather ",
         "casts": ["Marlon Brando", "Al Pacino", "James Caan", "Diane Keaton"],
         "genres": ["Crime", "Drama"]
      }
  ]

  @app.route('/movies')
  def get_all_movies():
      return jsonify(movies)

  @app.route('/movies', methods=['POST'])
  def add_movie():
      movie = request.get_json()
      movies.append(movie)
      return {'id': len(movies)}, 200

  @app.route('/movies/<int:index>', methods=['PUT'])
  def update_movie(index):
      movie = request.get_json()
      movies[index] = movie
      return jsonify(movies[index]), 200

  @app.route('/movies/<int:index>', methods=['DELETE'])
  def delete_movie(index):
      movies.pop(index)
      return 'None', 200

  app.run()
  ```

- #### Installing Mongodb and Understanding the library we will use
  - The docs for installing on [mac](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/)
  - Prereqs: xcode command-line & homebrew
  - "Tap" the homebrew mongodb by running `brew tap mongodb/brew`
  - My terminals output:
  ```console
  ==> Tapping mongodb/brew
  Cloning into '/usr/local/Homebrew/Library/Taps/mongodb/homebrew-brew'...
  remote: Enumerating objects: 1, done.
  remote: Counting objects: 100% (1/1), done.
  remote: Total 504 (delta 0), reused 0 (delta 0), pack-reused 503
  Receiving objects: 100% (504/504), 106.55 KiB | 1.13 MiB/s, done.
  Resolving deltas: 100% (238/238), done.
  Tapped 11 formulae (39 files, 179.2KB).
  ```
  - We need to download the community edition, so first check system reqs by running `brew tap | grep mongodb`
  - I confirmed in my terminal that I see `mongodb/brew`
  - Install the community edition (latest version is at 4.4) by running `brew install mongodb-community@4.4`
  - See lots of output including:
  ```console
  ==> Installing mongodb/brew/mongodb-community
  ==> Caveats
  To have launchd start mongodb/brew/mongodb-community now and restart at login:
    brew services start mongodb/brew/mongodb-community
  Or, if you don't want/need a background service you can just run:
    mongod --config /usr/local/etc/mongod.conf
  ==> Summary
  🍺  /usr/local/Cellar/mongodb-community/4.4.3: 11 files, 156.8MB, built in 4 seconds
  ```
  - Popular Libraries:
    - [Pymongo](https://pymongo.readthedocs.io/en/stable/index.html) - connects Mongo and Python
      - Allows you to use the schemaless nature of MongoDB
    - [MongoEngine](http://docs.mongoengine.org) - creates a _document_ based schema that connects Python and Mongo
      - This will **restrict** our access to the schemaless nature of MongoDB
      - We will utilize an extension for flask called [Flask-MongoEngine](http://docs.mongoengine.org/projects/flask-mongoengine/en/latest/)
  - Installing the libraries and the Flask extension
    - Since MongoEngine relies on PyMongo, if you [install](http://docs.mongoengine.org/guide/installing.html) engine, it brings pymongo along with it
    - And guess what?? Since flask-mongoengine relies on mongoengine, when you install flask you get mongoengine!
    - So we really only need to start with the extension since the rest come with it
    - Run `pipenv install flask-mongoengine`
    - To confirm pymongo installed, I ran `pip freeze | grep pymongo`, which returned `pymongo==3.11.2`
    - To confirm mongoengine installed, I ran `pip freeze | grep mongoengine` , which returned `mongoengine==0.22.1`
    - To confirm the extension installed, I ran `pip freeze | grep flask-mongoengine` , which returned `flask-mongoengine==1.0.0`

- #### Getting started with the database
  - First we begin my updating our file tree
    - `mkdir database`
    - `cd database`
    - `touch db.py`
    - `touch models.py`
  - We need to activate the database
    - Inside `db.py`, add the following code:
    ```py
    # imports flask_mongoengine from mongoengine
    from flask_mongoengine import MongoEngine
    # sets a variable called db to the engine
    db = MongoEngine()
    # Function will initialize the database using the app (app.py) as its arg
    def initialize_db(app):
      # initializes the database with the app
        db.init_app(app)
    ```
  - We need to add a Movie model
    - Inside `models.py`, add the following code:
    ```py
    # This is a 'document'
    # This defines the schema and users/clients cannot work outside these constraints
    from .db import db
    # Makes a Movie document
    class Movie(db.Document):
        # has three fields
        # name is a string datatype that is required and must be unique
        name = db.StringField(required=True, unique=True)
        # casts is a list datatype; has a subfield of string that is required
        casts = db.ListField(db.StringField(), required=True)
        # genres is a list datatype; has a subfield of string that is required
        genres = db.ListField(db.StringField(), required=True)
    ```

- #### Connect your database with your app
  - Update  `app.py` to use the database and not hardcoded data && change the view functions
    ```py
    # remove jsonify from flask imports and add a Response import
    from flask import Flask, request, Response
    # Brings in the function we just wrote in db.py
    from database.db import initialize_db
    # Brings in the class (document) we just wrote in models.py
    from database.models import Movie
    import json

    app = Flask(__name__)
    # Sets up configuration for mongodb
    app.config['MONGODB_SETTINGS'] = {
        # declare the host in the format <host-url>/<database-name> (see http://docs.mongoengine.org/projects/flask-mongoengine/en/latest/#configuration)
        'host': 'mongodb://localhost/practice-api-movies'
    }

    # initialize the database
    initialize_db(app)

    @app.route('/movies')
    def get_movies():
        # calls all the objects from the Movie document & converts to json
        movies = Movie.objects().to_json()
        # returns a response object, response type is defined as application/json
        return Response(movies, mimetype="application/json", status=200)

    @app.route('/movies', methods=['POST'])
    def add_movie():
        # gets the json from the body in post
        body = request.get_json()
        # loads the Movie document with the fields in the request
        # the ** is a spread operator (in this case it will spread the dict object)
        # After it will save
        movie =  Movie(**body).save()
        # block variable id is set to movie.id
        id = movie.id
        # returns block variable of string of the id and status 200
        return {'id': str(id)}, 200

    @app.route('/movies/<id>', methods=['PUT'])
    def update_movie(id):
        body = request.get_json()
        # First get the movie object by id, THEN update with spread
        Movie.objects.get(id=id).update(**body)
        # Returns empty string and 200 status
        return '', 200

    @app.route('/movies/<id>', methods=['DELETE'])
    def delete_movie(id):
        # First get the movie object by id, THEN delete
        movie = Movie.objects.get(id=id).delete()
        return '', 200

    app.run()
    ```
- #### Make our API endpoints more robust
  - We forgot a CRUD endpoint. We have Create (Post), Read/Retrieve (GET), Update (Put), and Destroy (Delete). HOWEVER, Read/Retrieve technically has 2! GET single movie (in rails this is Show) and GET all movies (in rails this is Index). We are missing our GET single (get by id)
  - Add the following _above_ `app.run()`
  ```py
  @app.route('/movies/<id>')
  def get_movie(id):
      movies = Movie.objects.get(id=id).to_json()
      return Response(movies, mimetype="application/json", status=200)
  ```
- The Final code:
  ```py
  from flask import Flask, request, Response
  from database.db import initialize_db
  from database.models import Movie
  import json

  app = Flask(__name__)

  app.config['MONGODB_SETTINGS'] = {
      'host': 'mongodb://localhost/practice-api-movies'
  }

  initialize_db(app)

  @app.route('/')
  def hello():
      return {'hello': 'world'} # Left this for an browser confirmation that localhost is connected correctly

  @app.route('/movies')
  def get_movies():
      movies = Movie.objects().to_json()
      return Response(movies, mimetype="application/json", status=200)

  @app.route('/movies', methods=['POST'])
  def add_movie():
      body = request.get_json()
      movie =  Movie(**body).save()
      id = movie.id
      return {'id': str(id)}, 200

  @app.route('/movies/<id>', methods=['PUT'])
  def update_movie(id):
      body = request.get_json()
      Movie.objects.get(id=id).update(**body)
      return '', 200

  @app.route('/movies/<id>', methods=['DELETE'])
  def delete_movie(id):
      movie = Movie.objects.get(id=id).delete()
      return '', 200

  @app.route('/movies/<id>')
  def get_movie(id):
      movies = Movie.objects.get(id=id).to_json()
      return Response(movies, mimetype="application/json", status=200)

  app.run()
  ```

- #### Run the server and test in Postman
  - If you are outside of the virtual environment, first run `pipenv shell`
  - Otherwise, just run `python app.py`
  - If there are no typos, you should see your server start
  - To continue testing, we may need to ensure database is connected and loaded with data (see next section)

- #### Add data to database
<!-- - [source](https://github.com/pkosiec/mongo-seeding) -->
  - Exit the server (CTRL + C on Mac)
  - First, we need to see if we have truly started mongodb.
    - Run `brew services list`.
    - Is `mongodb-community` labeled as _started_ or _stopped_?
      - If started, great, move to next bullet.
      - If not, run `brew services start mongodb-community@4.4` (change version if need to, or use without version)
  - Now that mongodb is started:
    - I ran my server first (In terminal `python app.py`)
    - And confirmed my Postman could "hit" the endpoints
    - I ran POST with faker data and then ran GET to confirm at least 2 endpoints were exposed and working correctly
  - We can always interact with the database using Postman, **but what if I want to interact with the db using my terminal?**
    - In terminal, run `mongo` to enter the database shell
    - Run `show dbs` to see your databases (_my project db didn't show up until I had run the server and connected via Postman - maybe this was a fluke or a misconception on my part_)
    - Run `use <project-db-name>`; for me this was `use practice-api-movies`
    - The response from terminal was `switched to db practice-api-movies`
    - FUN FACT ABOUT MONGO: _If this db didn't exist before, it will create it right here!_
    - Commands:
      - db is a command
      - foo = <collection-name> (in our example it would be movie)
      - DROP: `db.dropDatabase()`
      - INSERT single:

        ```
        db.foo.insert({
          "attribute": "information",
          "attribute": "information"
        })
        ```
      - INSERT multi:
        ```
        db.foo.insert([
          {
            "attribute": "information"
          },
          {
            "attribute2": "information2"
          }
        ])
        ```
      - GET all: `db.foo.find()`
      - GET all, pretty: `db.foo.find().pretty()`
      - See all collections: `show collections`
      - GET single record `db.foo.findOne()`
      - REMOVE single record: `db.foo.remove({"id": "id object"})`
      - UPDATE single record:
      ```
      db.foo.update({"id": "id object"}, {"name": "NEW NAME"} )
      ```
      - [Looking for more commands?](https://docs.mongodb.com/manual/crud/#create-operations)

- At this point you have successfully added data to your database using mongo shell (terminal) or using Postman and can test each of your CRUD endpoints via Postman! Celebrate!
- ![celebrate with birds](https://media.giphy.com/media/B81XkL3dtnWTe/giphy.gif)

- #### Best Practices for Organizing Code
  - See [here](https://exploreflask.com/en/latest/organizing.html) for official Flask documentation on organizing code
  - [Flask Community](https://github.com/pallets/flask/issues/2626) conversation on MVC, factory patterns, and folder/tree structure
  - [Blue Ocean Tutorial](https://www.digitalocean.com/community/tutorials/how-to-structure-large-flask-applications) on flask structures (though, take this with a grain of salt)

- #### Blueprints
  - What are [blueprints](https://stackoverflow.com/questions/24420857/what-are-flask-blueprints-exactly) in flask?
    - [Official Flask Documentation](https://flask.palletsprojects.com/en/1.1.x/blueprints/)
    - Simply put, it is a way to structure your code; a method of encapsulating code into separate components; a chance for Single-Responsibility Principle patterns to emerge!
      - Why is SRP important - smaller chunks of code that only do "one thing" makes code easier to read, easier to understand and implement. It allows us to test easier since each "chunk of code" won't have too much logic or know too much about other parts of code.
      - What is encapsulation? We hide the code/data; The only access to this code will be through our other bits of code (in this project, we will pull the routes information for Movie into it's own file and the only only "public" file that has access will be our `app.py`, aka our runner file)
  - So let's take our project code and encapsulate the code!
  - From the root of the project folder:
    - `mkdir resources`
    - `cd resources`
    - `touch movie.py`
  - Update `movie.py` with all the movie routes
    ```py
    @app.route('/movies/<id>')
    def get_movie(id):
        movies = Movie.objects.get(id=id).to_json()
        return Response(movies, mimetype="application/json", status=200)

    @app.route('/movies')
    def get_movies():
        movies = Movie.objects().to_json()
        return Response(movies, mimetype="application/json", status=200)

    @app.route('/movies', methods=['POST'])
    def add_movie():
        body = request.get_json()
        movie =  Movie(**body).save()
        id = movie.id
        return {'id': str(id)}, 200

    @app.route('/movies/<id>', methods=['PUT'])
    def update_movie(id):
        body = request.get_json()
        Movie.objects.get(id=id).update(**body)
        return '', 200

    @app.route('/movies/<id>', methods=['DELETE'])
    def delete_movie(id):
        movie = Movie.objects.get(id=id).delete()
        return '', 200
    ```
  - Your clean `app.py` now looks like:
    ```py
    from flask import Flask, request, Response
    from database.db import initialize_db
    from database.models import Movie
    import json

    app = Flask(__name__)

    app.config['MONGODB_SETTINGS'] = {
        'host': 'mongodb://localhost/practice-api-movies'
    }

    initialize_db(app)

    @app.route('/')
    def hello():
        return {'hello': 'world'}

    app.run()
    ```
  - **HOWEVER**, we aren't quite finished. The routes are encapsulated in their own file, but our `app.py` file has no way of accessing it or understanding what the `movie.py` file is.
  - Update `movie.py` to import Blueprints for flask and update code for use of blueprint:
    ```py
    # gets Blueprint (the new package) as well as Response and request from Flask
    from flask import Blueprint, Response, request
    # Pulls in the class Movie from our models file
    from database.models import Movie

    # creates a local variable movies which will be a blueprint
    # Blueprint has 2 arguments: Blueprint(name, import_name); where import_name is typically `_name_` because this is a special Python variable that represents the name of the current module
    movies = Blueprint('movies', _name_)

    # We no longer call @app.route, but use movies.route (our blueprint)
    movies.route('/movies/<id>')
    def get_movie(id):
        movies = Movie.objects.get(id=id).to_json()
        return Response(movies, mimetype="application/json", status=200)

    movies.route('/movies')
    def get_movies():
        movies = Movie.objects().to_json()
        return Response(movies, mimetype="application/json", status=200)

    movies.route('/movies', methods=['POST'])
    def add_movie():
        body = request.get_json()
        movie =  Movie(**body).save()
        id = movie.id
        return {'id': str(id)}, 200

    movies.route('/movies/<id>', methods=['PUT'])
    def update_movie(id):
        body = request.get_json()
        Movie.objects.get(id=id).update(**body)
        return '', 200

    movies.route('/movies/<id>', methods=['DELETE'])
    def delete_movie(id):
        movie = Movie.objects.get(id=id).delete()
        return '', 200
    ```
  - Now that our encapsulated file of `movie.py` is officially a blueprint, we can update our runner (`app.py`) to access the blueprint for Movie
  - Update `app.py` to register the Blueprint:
    ```py
    # We no longer need request and Response (since this is inside movie.py)
    from flask import Flask
    # We still need our database
    from database.db import initialize_db
    # We no longer call our model directly (since this is inside movie.py), instead, we call on movies variable from the resource file movie.py
    from resources.movie import movies

    app = Flask(__name__)

    app.config['MONGODB_SETTINGS'] = {
        'host': 'mongodb://localhost/practice-api-movies'
    }

    initialize_db(app)

    @app.route('/')
    def hello():
        return {'hello': 'world'}

    # We use a blueprint for the movies routes
    app.register_blueprint(movies)

    app.run()
    ```
  - Now, it looks much cleaner and feels closer to single-responsibility principle patterns

- #### Flask RESTful
  - We aren't quite finished though
  - [Official Extension Documentation](https://flask-restful.readthedocs.io/en/latest/)
  - This extension encourages best practices in RESTful design
  - Install in virtual environment, `pipenv install flask-restful`
  - Terminal response:
    ```console
    Installing flask-restful...
    Adding flask-restful to Pipfile's [packages]...
    ✔ Installation Succeeded
    Pipfile.lock (cb5958) out of date, updating to (b8315d)...
    Locking [dev-packages] dependencies...
    Locking [packages] dependencies...
    Building requirements...
    Resolving dependencies...
    ✔ Success!
    Updated Pipfile.lock (b8315d)!
    Installing dependencies from Pipfile.lock (b8315d)...
      🐍   ▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉ 0/0 — 00:00:00
    ```
  - Fix the blueprint (`movie.py`) to consume _flask-restful_:
    ```py
    # remove blueprint because flask-restful will accomplish what we need
    from flask import Response, request
    from database.models import Movie
    # Bring in Resouce from flask_restful
    from flask_restful import Resource

    # Adds a restful class for single movie records (retrieve by id, update, and destroy)
    class MovieApi(Resource):
        # function name is HTTP verb
        # In this class, this will take 2 arguments: (self, id)
        def get(self, id):
            movie = Movie.objects.get(id=id).to_json()
            return Response(movies, mimetype="application/json", status=200)

        def put(self, id):
            body = request.get_json()
            Movie.objects.get(id=id).update(**body)
            return '', 200

        def delete(self, id):
            movie = Movie.objects.get(id=id).delete()
            return '', 200

    # Adds a restful class for all movie records (retrieve all, create new)
    class MoviesApi(Resource):
        # function name is HTTP verb
        # In this class, the argument will be only be (self)
        def get(self):
            movies = Movie.objects().to_json()
            return Response(movies, mimetype="application/json", status=200)

        def post(self):
            body = request.get_json()
            movie =  Movie(**body).save()
            id = movie.id
            return {'id': str(id)}, 200
    ```
  - How do we register these endpoints? We will need a new file
    - From directory `resources`
    - `touch routes.py`
    - Add this code:
      ```py
      # Imports from relative file movie.py the classes MovieApi and MoviesApi
      from .movie import MovieApi, MoviesApi

      def initialize_routes(api):
          # Defines the routes for movies that need an id
          api.add_resource(MovieApi, '/movies/<id>')
          # Defines the routes for movies that don't need an id
          api.add_resource(MoviesApi, '/movies')
      ```
  - But our runner/index, `app.py`, does not know about these routes yet. Let's update that:
    ```py
    from flask import Flask
    from database.db import initialize_db
    # Import Api package from flask-restful
    from flask_restful import Api
    # Import function initialize_routes from the routes.py file under resources
    from resources.routes import initialize_routes

    app = Flask(__name__)
    # Creates an instance of Api (from flask-restful)
    api = Api(app)

    app.config['MONGODB_SETTINGS'] = {
        'host': 'mongodb://localhost/practice-api-movies'
    }

    initialize_db(app)

    @app.route('/')
    def hello():
        return {'hello': 'world'}

    # Initializes the routes file as an Api (replaced the blueprint registration of movies)
    initialize_routes(api)

    app.run()
    ```
  - SUCCESS! But wait, our URL is... okay. But it doesn't tell a user/client that it is an api or account for versioning. What if we updated our `routes.py` to account for that:
    ```py
    from .movie import MovieApi, MoviesApi

    def initialize_routes(api):
        api.add_resource(MovieApi, '/api/v1/movies/<id>')
        api.add_resource(MoviesApi, '/api/v1/movies')
    ```
  - Don't forget to test in Postman (I like to test GET, GET by id, POST, PUT, and DELETE) (it is a great thing I did, because there were a couple typos!! See final code for updates)
    - _Troubleshooting tip: When updating your code, stop and restart server to see affects in Postman_
  - Final code:
    ```py
    # app.py
    from flask import Flask
    from database.db import initialize_db
    from flask_restful import Api
    from resources.routes import initialize_routes

    app = Flask(__name__)
    api = Api(app)

    app.config['MONGODB_SETTINGS'] = {
        'host': 'mongodb://localhost/practice-api-movies'
    }

    initialize_db(app)

    @app.route('/')
    def hello():
        return {'hello': 'world'}

    initialize_routes(api)

    app.run()

    # resources/movie.py
    from flask import Response, request
    from database.models import Movie
    from flask_restful import Resource

    class MovieApi(Resource):
        def get(self, id):
            movie = Movie.objects.get(id=id).to_json()
            return Response(movie, mimetype="application/json", status=200)

        def put(self, id):
            body = request.get_json()
            Movie.objects.get(id=id).update(**body)
            return '', 200

        def delete(self, id):
            movie = Movie.objects.get(id=id).delete()
            return '', 200

    class MoviesApi(Resource):
        def get(self):
            movies = Movie.objects().to_json()
            return Response(movies, mimetype="application/json", status=200)

        def post(self):
            body = request.get_json()
            movie =  Movie(**body).save()
            id = movie.id
            return {'id': str(id)}, 200

    # resources/routes.py
    from .movie import MovieApi, MoviesApi

    def initialize_routes(api):
        api.add_resource(MoviesApi, '/api/v1/movies')
        api.add_resource(MovieApi, '/api/v1/movies/<id>')
    ```
  - Take a moment to appreciate your clean and pretty code!
  - ![moment](https://i.pinimg.com/originals/4a/3e/d6/4a3ed62b7a158d34a37d8c53595b445f.gif)

- #### Authentication and Authorization
  - Authentication vs Authorization:
    - Authentication: You are who you say you are; _Logging into an application_
    - Authorization: You are allowed to do the things you are trying to do; _An admin is authorized to see all users and delete/update/create users, whereas a user is only authorized to update their own records_
  - Let's implement authentication into our backend server
  - Let's implement authorization into our backend server

- #### Blarg
