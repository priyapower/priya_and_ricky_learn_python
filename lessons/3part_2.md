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

[Get your Root endpoint Exposed](#get-your-root-endpoint-exposed)

[Let's get an index of movies returned](#lets-get-an-index-of-movies-returned)

[CRUD - It's what you do](#crud-its-what-you-do)

[Test CRUD out with Postman](#test-crud-with-postman)

[](#)

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
- blarg
