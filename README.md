# Kittygram

<img width="2233" height="1284" alt="image" src="https://github.com/user-attachments/assets/91ba5837-8240-4491-a4cb-e4164cff5b06" />
<img width="1095" height="1220" alt="image" src="https://github.com/user-attachments/assets/206f2f36-7c0e-4979-a244-ab7ccba668a9" />

## About Kittygram

Kittygram is a simple social network where you can share your cat with the internet :3

The list of features:
- Post your cat: choose name, color, birth date upload an image and add some achievements.
- Edit your cat: change information or delete the post entirely.
- View other people's cats and leave some comments.

## Tech Stack

- **Frontend**: React.js
- **Backend**: Django (Python)
- **Database**: PostgreSQL
- **Server**: Nginx (reverse proxy & static file serving)
- **API**: RESTful API architecture

## Setup & Installation

### Prerequisites
- Docker Engine (v20.10+)
- Docker Compose (v2.10+)

### Environment Configuration

1. **Create `.env` file** in the project root:
    ```bash
    cp .env.example .env
    ```

2. **Place your secrets in `.env` file**. Optionally: change the Django `settings.py` file: remove `DEBUG = True` and add `ALLOWED_HOSTS = ['your_domain.com', 'www.your_domain.com']` if you want a production build.

3. **Build the images and start the servers**:
    ```bash
    docker-compose -f docker-compose.production.yml up --build
    ```

4. **Apply database migrations**:
    ```bash
    docker-compose -f docker-compose.production.yml exec backend python manage.py migrate
    ```

5. **Create yourself a superuser** (Optional):
    ```bash
    docker-compose -f docker-compose.production.yml exec backend python manage.py createsuperuser
    ```

6. **Collect Django static files**:
    ```bash
    docker-compose -f docker-compose.production.yml exec backend python manage.py collectstatic --noinput
    ```

7. **Visit `http://localhost:8000/`**

