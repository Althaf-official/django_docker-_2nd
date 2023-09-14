our Django Project.
1. Create a virtual environment with pipenv
Open up terminal (Mac) or PowerShell (Windows)

Copy
cd path/to/your/dev/folder/

Copy
mkdir simple_django_docker
cd simple_dj_docker
pipenv install django==2.2.4 gunicorn --python 3.6
pipenv shell


2. Create a Django project
Copy
django-admin startproject cfehome .


3. Local DB & Migrations
Copy
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser

4. Update Django settings.py
CopyCopyCopy
# DEBUG can be True/False or 1/0
DEBUG = int(os.environ.get('DEBUG', default=1)) 

5. Create .env
CopyCopyCopy
DEBUG=1

6. Test Gunicorn
CopyCopyCopy
gunicorn cfehome.wsgi:application --bind 0.0.0.0:8000
Your Docker File, Image, & Container.
1. Create your Dockerfile
CopyCopyCopy
$ cd path/to/your/dev/folder
$ cd simple_dj_docker
$ touch Dockerfile
$ ls
Dockerfile

2. Build your Docker Image
docker build -t simple_django_docker -f Dockerfile .