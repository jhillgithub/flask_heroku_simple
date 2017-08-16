# flask_heroku_simple
Example of Deploying a Simple Flask App to Heroku

## App Setup

### Create, Clone, and CD into your repo

```
git clone https://github.com/jhillgithub/<your_repo>.git
cd <your_repo>
```

### Create Conda Environment

```
conda create -n myflaskapp python=3.6
source activate myflaskapp
```

### Install Flask and Gunicorn Dependencies

1. Activate your Environment (if you didn't do it above)

```
source activate myflaskapp 
```

2. Install Flask and Gunicorn

```
pip install Flask==0.12.2
pip install gunicorn==19.7.1
```

3. Create a `requirements.txt` file

```
pip freeze > requirements.txt
```

### Create a runtime file to specify the version of Python to use

1. Create a file called runtime.txt

``` 
touch runtime.txt
```

2. Open `runtime.txt` with a text editor and add the python version

``` 
python-3.6.2
```

### Create a Procfile for the server

1. Create a file called `Procfile`

```
touch Procfile
```

2. Open `Procfile` with a text editor and add the following

```
web: gunicorn app:app
```

### Create the Flask App

1. Create a file called `app.py`

```
touch app.py
```

2. Open `app.py` with a text editor and add the following code 

```python
from flask import Flask
app = Flask(__name__)


@app.route('/')
def hello():
    return "Hello World!"

if __name__ == '__main__':
    app.run()

```

### Test the app

1. Launch the app

```
python app.py
```

2. View the app in the browser at `http://127.0.0.1:5000`


3. `ctrl-c` to quit

## Heroku Setup

### Login to heroku

``` 
heroku login
```

### Create the heroku app


```
cd /path/to/app
heroku create
```

Note: Make sure that you are inside of the app repo folder before running `heroku create`

