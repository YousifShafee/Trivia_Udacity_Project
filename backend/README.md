# Full Stack Trivia API Backend

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

## Database Setup
With Postgres running, restore a database using the trivia.psql file provided. From the backend folder in terminal run:
```bash
psql trivia < trivia.psql
```

## Running the server

From within the `backend` directory first ensure you are working using your created virtual environment.

To run the server, execute:

```bash
export FLASK_APP=flaskr
export FLASK_ENV=development
flask run
```

Setting the `FLASK_ENV` variable to `development` will detect file changes and restart the server automatically.

Setting the `FLASK_APP` variable to `flaskr` directs flask to use the `flaskr` directory and the `__init__.py` file to find the application. 

## Tasks

One note before you delve into your tasks: for each endpoint you are expected to define the endpoint and response data. The frontend will be a plentiful resource because it is set up to expect certain endpoints and response data formats already. You should feel free to specify endpoints in your own way; if you do so, make sure to update the frontend or you will get some unexpected behavior. 

1. Use Flask-CORS to enable cross-domain requests and set response headers. 
2. Create an endpoint to handle GET requests for questions, including pagination (every 10 questions). This endpoint should return a list of questions, number of total questions, current category, categories. 
3. Create an endpoint to handle GET requests for all available categories. 
4. Create an endpoint to DELETE question using a question ID. 
5. Create an endpoint to POST a new question, which will require the question and answer text, category, and difficulty score. 
6. Create a POST endpoint to get questions based on category. 
7. Create a POST endpoint to get questions based on a search term. It should return any questions for whom the search term is a substring of the question. 
8. Create a POST endpoint to get questions to play the quiz. This endpoint should take category and previous question parameters and return a random questions within the given category, if provided, and that is not one of the previous questions. 
9. Create error handlers for all expected errors including 400, 404, 422 and 500. 

REVIEW_COMMENT
```
This README is missing documentation of your endpoints. Below is an example for your endpoint to get all categories. Please use it as a reference for creating your documentation and resubmit your code. 

Endpoints
GET '/categories'
GET '/questions'
POST '/questions/create'
DELETE '/questions/<int:question_id>'
POST '/questions/search'
GET '/categories/<int:category_id>'
POST '/quiz'

GET '/categories'
- Fetches a dictionary of categories have a list of cotegories type.
- Request Arguments: None
- Returns: An object with a single key, categories, that contains a array of categories type (if there one category)
        or return 404 exception. 

"categories": [
    "First thing",
    "Second Categories",
    "Third Categories"
]

GET '/questions'
- Fetches a dictionary of categories, questions and number of questions
- Request Arguments: None
- Returns: An object with a three kies, categories which contains as GET '/categories', questions which a list 
    of questions data and total_questions is the number of questions(if there one question)
        or return 404 exception.  

"categories": [
    "Any thing",
    "Second Categories",
    "Third Categories"
],
"questions": [
    {
        "answer": "second answer",
        "category": 1,
        "difficulty": 2,
        "id": 7,
        "question": "second question"
    }
],
"total_questions": 1

POST '/questions/create'
- Create new question and commit in database. 
- Request Arguments: {'question': string, 'answer': string, 'difficulty': integer, 'category': integer}
- Returns: An object with a tow kies success and the value is True, question id (if there is no required missing)
    or return 422 exception.
{"success": True, "question_id": question.id}

DELETE '/questions/<int:question_id>'
- Delete question by id and commit in database .
- Request Arguments: None
- Returns: An object with a tow kies success and the value is True, question id (if nothing wrong)
    or return 422 exception.
{"success": True, "question_id": question.id}

POST '/questions/search'
- Search in questions by substring of the question and return the question.
- Request Arguments: {'searchTerm': string}
- Returns: An object with a tow kies ,questions, contain list of question data ,number of questions (if nothing missing)
    or return 404 exception.
{"questions": [
    {
        "answer": "second answer",
        "category": 1,
        "difficulty": 2,
        "id": 7,
        "question": "second question"
    }
],
"total_questions": 1
}

GET '/categories/<int:category_id>'
- Fetch single category by id.
- Request Arguments: None
- Returns: An object with a three kies ,questions, contain list of question data ,number of questions and 
    current category contain category type (if id valid) or return 404 exception.
{
"current_category": "First Category",
"questions": [
    {
        "answer": "second answer",
        "category": 1,
        "difficulty": 2,
        "id": 7,
        "question": "second question"
    }
],
    "total_questions": 1
}

POST '/quiz'
- get 5 random questinos separately and without repeating when choose between all categories questions or one 
    category questions.
- Request Arguments: {'previous_questions': [], 'quiz_category': {'type': 'category_type', 'id': integer}}
- Returns: An object with a single key ,question, contain question data (if stil questions in chosen category) 
    or return 404 exception.
{"question":
    "answer": "second answer",
    "category": 1,
    "difficulty": 2,
    "id": 7,
    "question": "second question"
}

Errors Handle
    404 -- Not found
    422 -- Not processable
    500 -- Internal Server Error

404 Return 404 status code and
{
    "error": 404,
    "message": "Not found"
}

422 Return 422 status code and
{
    "error": 422,
    "message": "Un processable"
}

500 Return 500 status code and (Not Used In Code)
{
    "error": 500,
    "message": "Internal Server Error"
}
```


## Testing
To run the tests, run
```
dropdb trivia_test
createdb trivia_test
psql trivia_test < trivia.psql
python test_flaskr.py
```