# School Manager

A Django web application for managing a three-level school hierarchy: **School → Classroom → Student**.

## Live App

**https://main-bvxea6i-y4ssttyekx4hq.us.platformsh.site/**

## Project Structure

```
school\_manager/          <- top-level Django config package
    \_\_init\_\_.py
    settings.py
    urls.py
    wsgi.py
schools/                 <- app package with all models, views, and templates
    \_\_init\_\_.py
    admin.py
    apps.py
    models.py
    urls.py
    views.py
    migrations/
    templates/schools/
manage.py
requirements.txt
.platform.app.yaml
.platform/
    services.yaml
    routes.yaml
```

## Models

|Model|Key Fields|
|-|-|
|School|name, address, principal, founded|
|Classroom|name, subject, teacher, room\_number, FK→School|
|Student|first\_name, last\_name, student\_id, email, enrolled, FK→Classroom|

## Local Setup

```bash
python -m venv venv
source venv/bin/activate       
pip install -r requirements.txt
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

Visit `http://127.0.0.1:8000/` in your browser.

## Deploy to Platform.sh

Install the Platform.sh CLI:

```bash
curl -fsSL https://cli.platform.sh/installer | bash
```

Log in and deploy:

```bash
platform login
platform project:create --title "School Manager" --region
git init
git add .
git commit -m "Initial commit"
platform push
```

After the first deploy, create a superuser on the live server:

```bash
platform ssh -- python manage.py createsuperuser
```

## GitHub

```bash
git remote add origin https://github.com/YOUR\_USERNAME/school-manager.git
git push -u origin main
```

