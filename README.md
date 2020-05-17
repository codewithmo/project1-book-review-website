# Project 1

Web Programming with Python and JavaScript

# Book Review Website
## Overview
This is a book review website. Users will be able to register for your website and then log in using their username and password. Once they log in, they will be able to search for books, leave reviews for individual books, and see the reviews made by other people. I have also used the third-party API by Goodreads, another book review website, to pull in ratings from a broader audience. Finally, users will be able to query for book details and book reviews programmatically via this website’s API.


---

## Getting Started
Make sure you have the following set-ups to run this application successfully.
1. PostgreSQl database URI
2. Goodreads API key
3. Python and Flask

### **PostgreSQL**
For this project, you’ll need to set up a PostgreSQL database to use with our application. It’s possible to set up PostgreSQL locally on your own computer, but for this project, we’ll use a database hosted by Heroku, an online web hosting service.

1. Navigate to [https://www.heroku.com/](https://www.heroku.com/), and create an account if you don’t already have one.
2. On Heroku’s Dashboard, click “New” and choose “Create new app.”
3. Give your app a name, and click “Create app.”
4. On your app’s “Overview” page, click the “Configure Add-ons” button.
5. In the “Add-ons” section of the page, type in and select “Heroku Postgres.”
6. Choose the “Hobby Dev - Free” plan, which will give you access to a free PostgreSQL database that will support up to 10,000 rows of data. Click “Provision.”
7. Now, click the “Heroku Postgres :: Database” link.
8. You should now be on your database’s overview page. Click on “Settings”, and then “View Credentials.” This is the information you’ll need to log into your database. You can access the database via Adminer, filling in the server (the “Host” in the credentials list), your username (the “User”), your password, and the name of the database, all of which you can find on the Heroku credentials page.
Alternatively, if you install PostgreSQL on your own computer, you should be able to run `psql URI` on the command line, where the _URI_ is the link provided in the Heroku credentials list.

`Note:` Follow this DB Schema to properly run this project, run the following commands in your terminal
```
psql URI            #URI is the link provided in the Heroku credentials list

>>>into your database

CREATE TABLE books(
    id SERIAL PRIMARY KEY, 
    isbn VARCHAR NOT NULL, 
    title VARCHAR NOT NULL, 
    author VARCHAR NOT NULL, 
    year INTEGER NOT NULL
    );
CREATE TABLE users(
    id SERIAL PRIMARY KEY, 
    fullname VARCHAR(50) NOT NULL, 
    username VARCHAR(50) NOT NULL, 
    email VARCHAR(100), 
    password VARCHAR(300) NOT NULL
    );
CREATE TABLE reviews(
    id SERIAL PRIMARY KEY, 
    review TEXT, 
    rating VARCHAR, 
    book_id INTEGER REFERENCES books, 
    user_id INTEGER REFERENCES users
    );

```
`Note:`After Creating tables it is important to import the data to database

**Import:** Provided for you in this project is a file called `books.csv`, which is a spreadsheet in CSV format of 5000 different books. Each one has an ISBN number, a title, an author, and a publication year. In a Python file called `import.py` separate from your web application. Run this program by running `python3 import.py` to import the books into your database.
 

### **Goodreads API**
Goodreads is a popular book review website, and we’ll be using their API in this project to get access to their review data for individual books.

1. Go to [https://www.goodreads.com/api](https://www.goodreads.com/api) and sign up for a Goodreads account if you don’t already have one.
2. Navigate to [https://www.goodreads.com/api/keys](https://www.goodreads.com/api/keys) and apply for an API key. For “Application name” and “Company name” feel free to just write “project1,” and no need to include an application URL, callback URL, or support URL.
3. You should then see your API _key_ . (For this project, we’ll care only about the “key”, not the “secret”.)

### **Python and Flask**
1. First, make sure you install a copy of Python. For this course, you should be using Python version 3.6 or higher.
2. You’ll also need to install `pip`. If you downloaded Python from Python’s website, you likely already have `pip` installed (you can check by running `pip` in a terminal window). If you don’t have it installed, be sure to install it before moving on!

***

Now its time to run the application by following the below given details:
1. ### **Clone** the `cs50wp-project1` repository from [https://github.com/codewithmo/cs50wp-project1.git](https://github.com/codewithmo/cs50wp-project1.git)
2. In a terminal window, navigate into your `cs50wp-project1` directory.
3. Run `pip3 install -r requirements.txt` in your terminal window to make sure that all of the necessary Python packages (Flask and SQLAlchemy, for instance) are installed.
4. Set the environment variable `FLASK_APP` to be `application.py`. On a Mac or on Linux, the command to do this is `export FLASK_APP=application.py.` On Windows, the command is instead `set FLASK_APP=application.py`. You may optionally want to set the environment variable `FLASK_DEBUG` to `1`, which will activate Flask’s debugger and will automatically reload your web application whenever you save a change to a file.
5. Set the environment variable `DATABASE_URL` to be the URI of your database, which you should be able to see from the credentials page on Heroku.
6. Set the environment variable `GOODREADS_KEY` to be the _key_ of your Goodreads API.
7. Run `flask run` to start up your Flask application.
If you navigate to the URL provided by `flask`, you should see home page. Below I am attaching my screencast of this project1

**Screencast of this project-** [https://youtu.be/CzS5XHnmkRA](https://youtu.be/CzS5XHnmkRA)




