# Technical Task - Developer, Platform team, ReedPop

Hello,

In this task you will set up a working copy of a very simple news/reviews website.

The site is built in Python and uses the Django framework (v2.2).

You will be asked to:

  - Extend the basic `Post` model and render some new data
  - Modify how the `Post` is rendered to include a new automatically inserted element
  - Add a test case to ensure the `Post` model works in the expected way.

The task is designed to demonstrate your ability to use new technology, to interpret specifications, solve programming problems, and show an understanding of test coverage.

The task is intended to take no more than 2 or 3 hours. If you overrun significantly then please get in touch to discuss - we may have misjudged the timing of the task.

## Getting set up

Install **Python 3** if you don't already have it (should be fine on OSX and Linux).

Then, in a shell, run the following to set up the project:

```bash
git clone https://github.com/gamernetwork/tech-task-platform-2021.5.git
cd tech-task-platform-2021.5

# set up a python virtual environment
python3 -m venv .env

# install Django into this environment
.env/bin/pip install -r requirements.txt

# set up the database
.env/bin/python manage.py migrate
```

You will now have a `db.sqlite3` file in your project directory. This is your database.

```
# import 3 starting articles
.env/bin/python manage.py loaddata youreagamer_starting_articles

# set yourself up as a user for the backend of this site
.env/bin/python manage.py createsuperuser
```

You can now start a local development server (errors and access logs will show here) and get hacking

```
.env/bin/python manage.py runserver
```

Point your browser at http://127.0.0.1:8000 and you should see a list of 3 posts, which can be clicked.

The data for the site can be modified using the backend available here: http://127.0.0.1:8000/admin/ (log in using the superuser account you created.)

### Note regarding database

If you get into a mess with migrations, etc, you can just move/delete the `db.sqlite3` file and re-run the `migrate`, `loaddata` and `createsuperuser` steps again to get back to a fresh install.

## Tasks

Please do the following:

  1. Add the following fields to the `Post` model:
     1. datetime (mandatory, default to now)
     2. a subheading (not mandatory, max 200 characters)
  2. Populate the new fields using the admin site.
  3. Add a new test case that checks if `str(post)` returns the post title for a Post object.
  4. Add a second test case that creates a Post, then checks if the index view of the application contains a post title.

Refer to https://docs.djangoproject.com/en/1.11/topics/migrations/#workflow for steps to get your model changes into the database.

Refer to https://docs.djangoproject.com/en/3.2/intro/tutorial05/#writing-our-first-test for information about writing and running tests.

Refer to https://docs.djangoproject.com/en/3.2/topics/testing/tools/#the-test-client for information about using the test client to write your second test.

## Submitting your completed task

You should submit your work by email either as a zip of code, or as a patch against the original repo.

Please do not file a pull request against the original repo - other candidates will see your work!

Feel free to provide any explanatory notes in along with you submission.

If anything is unclear, please do no hesitate to get in touch!