# Full Stack Trivia API Backend

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing
purposes.

### Installing Dependencies

#### Python 3.7
#### Python 3.9 last version 

Follow instructions to install the latest version of python for your platform in the
[python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

#### Virtual Environment

It is preferred if you run this in a virtual environment for python. If you are using `pipenv`, virtual environment
would be taken care of by `pipenv`. Instructions for setting up a virtual environment for your platform can be found in
the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/).

#### PIP Dependencies

Once you have your virtual environment setup and running, install dependencies by running:

```bash
pipenv install
```
or if you are not using `pipenv`:
```bash
pip install -r requirements.txt
```

This will install all of the required packages we selected within the `requirements.txt` file.

#### pycodeStyle 
  ```bash
pip install pycodestyle
```
pycodestyle is a tool to check your Python code against some of the style conventions in PEP 8.

##### Features
  - Plugin architecture: Adding new checks is easy.
  - Parseable output: Jump to error location in your editor.
  - Small: Just one Python file, requires only stdlib. You can use just the pycodestyle.py file for this purpose.
  - Comes with a comprehensive test suite.

#### Key Dependencies

- [Flask](http://flask.pocoo.org/)  is a lightweight backend micro-services framework. Flask is required to handle
requests and responses.
- [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use handle the lightweight sqlite
database. You'll primarily work in app.py and can reference models.py.
- [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross origin requests
from our frontend server.

## Database Setup (_Important_)
Install and setup "PostgreSQL" on the system and create a database named `trivia` in the Postgres server.
```bash
createdb trivia
```

Instructions (macOS): https://www.codementor.io/engineerapart/getting-started-with-postgresql-on-mac-osx-are8jcopb

With Postgres running, restore a database using the trivia.psql file provided. From the backend folder in terminal run:
```bash
cd database
psql trivia < database/trivia.psql
```

## Running the server

Ensure you are working using your created virtual environment.

To run the server, execute:
```bash
export FLASK_APP=flaskr
flask run --reload
```

The `--reload` flag will detect file changes and restart the server automatically.
The application will be served on **http://localhost:5000**

## Testing
```bash
createdb trivia_test
```

To run the flask tests, run the following command:
```bash
python -m unittest discover -t ../
```
_NOTE_: Make sure you create a database named `trivia_test` in the PostgreSQL server before running the tests.

## API Documentation
* GET "/categories"
    - Fetches a dictionary of categories in which the keys are the ids and the value is the corresponding string of the category
    - Request Parameters: None
    - Response Body:
    
    `categories`: Dictionary of *Category ID* <-> *Category Type*
```json
{
  "categories": {
    "1": "Science",
    "2": "Art"
  } 
}
```

* GET "/questions?page=1"
    - Fetches the questions to be displayed on the page using page number
    - Request Parameters: `page`: Page number
    - Response Body:

    `questions`: List of questions

    `categories`: Dictionary of *Category ID* <-> *Category Type*

    `total_questions`: Total number of  questions
```json
{
  "questions": [{
    "id": 1,
    "question": "",
    "answer": "",
    "category": 1,
    "difficulty": 1
  }],
  "categories": {
    "1": "Science",
    "2": "Art"
  },
  "total_questions": 1
}
```

* DELETE "/questions/<int:question_id>"
    - Deletes a question from the database
    - Request Parameters: `question_id`: Question ID to delete
    - Response Body:

    `deleted`: Question ID that is deleted
```json
{
  "deleted": 20
}
```

* POST "/questions"
    - Adds a questions to the database
    - Request Body:
    
    `question`: Question statement
    
    `answer`: Answer statement
    
    `category`: Category ID
    
    `difficulty`: Difficulty Level
    - Response Body:
    
    `question`: Question object that is created
```json
{
  "question": {
    "id": 1,
    "question": "",
    "answer": "",
    "category": 1,
    "difficulty": 1
  }
}
```

* POST "/search"
    - Fetches questions based on the search term
    - Request Body:
    
    `searchTerm`: Search term
    - Response Body:
    
    `questions`: List of questions found in search
    
    `total_questions`: Total number of  questions
```json
{
  "questions": [{
    "id": 1,
    "question": "",
    "answer": "",
    "category": 1,
    "difficulty": 1
  }],
  "total_questions": 1
}
```

* GET "/categories/<int:category_id>/questions"
    - Fetches questions for the requested category
    - Request Parameters: `category_id`: Category ID for questions
    - Response Body:

    `questions`: List of category questions

    `total_questions`: Total number of  questions
    
    `current_category`: Current category ID
```json
{
  "questions": [{
    "id": 1,
    "question": "",
    "answer": "",
    "category": 1,
    "difficulty": 1
  }],
  "total_questions": 1,
  "current_category": 1
}
```

* POST "/quizzes"
    - Fetches a unique question for the quiz on selected category
    - Request Body:
    
    `previous_questions`: List of previously answered questions

    `quiz_category`: Category object of the quiz
    - Response Body:
    
    `question`: Random question of requested category
```json
{
  "question": {
    "id": 1,
    "question": "",
    "answer": "",
    "category": 1,
    "difficulty": 1
  }
}
```
