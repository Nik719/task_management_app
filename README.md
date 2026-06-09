# Task Manager API

A RESTful Task Management API built with **Python**, **Django**, and **Django Rest Framework (DRF)**. Features JWT authentication, role-based permissions, and full task lifecycle management.

---

## Tech Stack

| Layer            | Technology                          |
| ---------------- | ----------------------------------- |
| Language         | Python                              |
| Framework        | Django, Django Rest Framework (DRF) |
| Authentication   | Django SimpleJWT                    |
| Database         | PostgreSQL / MySQL                  |
| Background Tasks | Celery + Redis (Optional)           |

---

## Features

### Authentication & Authorization

* JWT-based authentication using `djangorestframework-simplejwt`
* Role-based access control with DRF permissions
* Secure token refresh mechanism
* Token blacklisting support for enhanced security

### Task CRUD Operations

* Create, Read, Update, and Delete tasks through RESTful APIs
* DRF serializers for data validation and transformation
* ViewSets and routers for clean API architecture

### User-Specific Task Visibility

* Tasks are scoped to authenticated users
* Queryset-level filtering ensures users only access their own tasks

### Task Status & Priority Management

#### Status Options

* Todo
* In Progress
* Done

#### Priority Levels

* Low
* Medium
* High

Implemented using Django model `choices` for consistency and validation.

---

## Getting Started

### Prerequisites

* Python 3.9+
* PostgreSQL or MySQL
* Redis (Optional, for Celery)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/Nik719/task_management_app.git
cd task_management_app

# 2. Create and activate a virtual environment
python -m venv venv

# Linux / macOS
source venv/bin/activate

# Windows
venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Configure environment variables
cp .env.example .env

# 5. Apply migrations
python manage.py migrate

# 6. Create a superuser
python manage.py createsuperuser

# 7. Run the development server
python manage.py runserver
```

---

## API Endpoints

### Authentication

| Method | Endpoint                   | Description                          |
| ------ | -------------------------- | ------------------------------------ |
| POST   | `/api/auth/register/`      | Register a new user                  |
| POST   | `/api/auth/login/`         | Obtain JWT access and refresh tokens |
| POST   | `/api/auth/token/refresh/` | Refresh access token                 |

### Tasks

| Method | Endpoint           | Description                               |
| ------ | ------------------ | ----------------------------------------- |
| GET    | `/api/tasks/`      | List all tasks for the authenticated user |
| POST   | `/api/tasks/`      | Create a new task                         |
| GET    | `/api/tasks/{id}/` | Retrieve a specific task                  |
| PUT    | `/api/tasks/{id}/` | Update a task                             |
| PATCH  | `/api/tasks/{id}/` | Partially update a task                   |
| DELETE | `/api/tasks/{id}/` | Delete a task                             |

---

## Environment Variables

Create a `.env` file in the project root:

```env
SECRET_KEY=your-django-secret-key
DEBUG=True
DATABASE_URL=postgres://user:password@localhost:5432/taskdb

# Optional - Celery
CELERY_BROKER_URL=redis://localhost:6379/0
```

---

## Running Background Tasks (Optional)

If Celery is configured:

```bash
celery -A task_management_app worker --loglevel=info
```

---

## Project Structure

```text
task_management_app/
├── task_app/
│   ├── models.py
│   ├── serializers.py
│   ├── views.py
│   └── urls.py
├── task_management_app/
│   ├── settings.py
│   └── urls.py
├── manage.py
├── requirements.txt
└── docker-compose.yml
```

---

## Future Enhancements

* Email notifications and reminders
* Task categories and tagging
* File attachments
* Team collaboration features
* Activity logging and audit trails
* Docker deployment support
* CI/CD pipeline integration
* Swagger / OpenAPI documentation

---

## License

This project is licensed under the MIT License. See the LICENSE file for details.

---

## Author

**Nikhil**

* GitHub: https://github.com/Nik719
* LinkedIn: https://linkedin.com/in/nikhilsaha719

⭐ If you found this project useful, consider starring the repository.
