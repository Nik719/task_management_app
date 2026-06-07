# Task Manager API

A RESTful Task Management API built with **Python**, **Django**, and **Django Rest Framework (DRF)**. Features JWT authentication, role-based permissions, and full task lifecycle management.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Language | Python |
| Framework | Django, Django Rest Framework (DRF) |
| Authentication | Django SimpleJWT |
| Database | PostgreSQL / MySQL |
| Background Tasks | Celery + Redis *(optional)* |

---

## Features

### Authentication & Authorization
- JWT-based authentication via `djangorestframework-simplejwt`
- - Role-based access control with DRF permissions
  - - Secure token refresh and token blacklisting support
   
    - ### Task CRUD
    - - Full Create, Read, Update, Delete operations via RESTful endpoints
      - - DRF serializers and viewsets for clean, consistent API design
       
        - ### User-Specific Task Visibility
        - - Tasks are scoped to the authenticated user
          - - Queryset-level filtering ensures users only see their own data
           
            - ### Priority & Status
            - - **Status:** `Todo` | `In Progress` | `Done`
              - - **Priority:** `Low` | `Medium` | `High`
                - - Implemented using Django model enums / `choices`
                 
                  - ---

                  ## Getting Started

                  ### Prerequisites

                  - Python 3.9+
                  - - PostgreSQL or MySQL
                    - - Redis *(if using Celery)*
                     
                      - ### Installation
                     
                      - ```bash
                        # 1. Clone the repository
                        git clone https://github.com/Nik719/task_management_app.git
                        cd task_management_app

                        # 2. Create and activate a virtual environment
                        python -m venv venv
                        source venv/bin/activate  # On Windows: venv\Scripts\activate

                        # 3. Install dependencies
                        pip install -r requirements.txt

                        # 4. Configure environment variables
                        cp .env.example .env
                        # Edit .env with your database credentials and secret key

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

                        | Method | Endpoint | Description |
                        |---|---|---|
                        | `POST` | `/api/auth/register/` | Register a new user |
                        | `POST` | `/api/auth/login/` | Obtain JWT access & refresh tokens |
                        | `POST` | `/api/auth/token/refresh/` | Refresh access token |

                        ### Tasks

                        | Method | Endpoint | Description |
                        |---|---|---|
                        | `GET` | `/api/tasks/` | List all tasks for the authenticated user |
                        | `POST` | `/api/tasks/` | Create a new task |
                        | `GET` | `/api/tasks/{id}/` | Retrieve a specific task |
                        | `PUT` | `/api/tasks/{id}/` | Update a task |
                        | `PATCH` | `/api/tasks/{id}/` | Partially update a task |
                        | `DELETE` | `/api/tasks/{id}/` | Delete a task |

                        ---

                        ## Environment Variables

                        Create a `.env` file in the project root:

                        ```env
                        SECRET_KEY=your-django-secret-key
                        DEBUG=True
                        DATABASE_URL=postgres://user:password@localhost:5432/taskdb

                        # Optional – Celery
                        CELERY_BROKER_URL=redis://localhost:6379/0
                        ```

                        ---

                        ## Running Background Tasks (Optional)

                        If Celery is configured:

                        ```bash
                        # Start the Celery worker
                        celery -A task_management_app worker --loglevel=info
                        ```

                        ---

                        ## Project Structure

                        ```
                        task_management_app/
                        ├── task_app/                # Core app – models, views, serializers
                        │   ├── models.py
                        │   ├── serializers.py
                        │   ├── views.py
                        │   └── urls.py
                        ├── task_management_app/     # Project settings & configuration
                        │   ├── settings.py
                        │   └── urls.py
                        ├── manage.py
                        ├── requirements.txt
                        └── docker-compose.yml
                        ```

                        ---

                        ## License

                        This project is open-source and available under the [MIT License](LICENSE).
