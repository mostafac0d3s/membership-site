# membership-site

A framework for launching new Django membership site quickly on to an **Ubuntu 18.04** LTS instance using [Amazon Lightsail](https://aws.amazon.com/lightsail/) or [Amazon EC2](https://aws.amazon.com/ec2/). Comes with a complete user authentication flow, custom user model, environment variables, and social authentication options via Gmail, Facebook, Twitter, etc.

## Features

- Django 2.1 and Python 3.7
- PostgreSQL database
- [Django-allauth](https://django-allauth.readthedocs.io/en/latest/installation.html)
- Dockerized containers
- Environment variables
- **NGINX** and **Gunicorn** for production

## Required

Get the right flavor of Docker for your OS...
- [Docker for Mac](https://docs.docker.com/docker-for-mac/install/)
- [Docker for Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
- [Docker for Windows](https://docs.docker.com/docker-for-windows/install/)

**Note:** The minimum building requirement for deployment of this project is 4 GB RAM.
For Docker for Mac, this can be set by following these steps:

Open Docker > Preferences > Advanced tab, then set memory to 4.0 GiB

## Setup:

### local:

Use pipenv
- `cd membership-site && pipenv install`
- `pipenv shell`
- `cd site`
- `./manage.py migrate`
- `./manage.py collectstatic`
- `./manage.py runserver`

### production:

steps to deploy to production:
- `cd membership-site && sudo chmod u+x ubuntu-start.sh`
- `echo -e "yes\nyes\nyes" | ./ubuntu-start.sh`

**note: log out & back in to remove the need for sudo**

- `cd membership-site`

migrate & collectstatic
- `sudo chmod u+x site/deploy-tasks.sh`
- `./site/deploy-tasks.sh`

run server
- `docker-compose up --build -d`

### delete database data
- `docker volume ls`
- `docker volume rm <name_of_volume>`
