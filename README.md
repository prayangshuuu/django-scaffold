# django-scaffold

A minimal, clean, and reusable Django boilerplate configured with uv, Docker, and PostgreSQL.

## Requirements

- [Docker](https://docs.docker.com/get-docker/) and [Docker Compose](https://docs.docker.com/compose/)
- [uv](https://docs.astral.sh/uv/) (optional for local non-Docker development)

## Features

- **Authentication:** Custom User model configured with email login (via Django-allauth)
- **Role-Based Access Control (RBAC):** Users can have roles such as `admin` and `user`. 
  - `admin`: Has `is_staff` and `is_superuser` privileges for access to Django admin and protected areas.
  - `user`: Default role for regular users.
- **Mixins & Decorators:** Reusable components like `@role_required(['admin'])`, `@admin_required`, `RoleRequiredMixin`, and `AdminRequiredMixin` for protecting views.

## Getting Started (Docker)

1. Copy the environment file:
   ```bash
   cp .env.example .env
   ```

2. Build and start containers:
   ```bash
   docker-compose up --build -d
   ```

3. Run database migrations:
   ```bash
   docker-compose exec web uv run python manage.py migrate
   ```

4. Seed the database with initial users:
   ```bash
   docker-compose exec web uv run python manage.py seed
   ```

5. Access the application at `http://localhost:8000`.

## Local Development (with uv)

1. Set up dependencies:
   ```bash
   uv sync
   ```

2. Run migrations:
   ```bash
   uv run python manage.py migrate
   ```

3. Seed the database:
   ```bash
   uv run python manage.py seed
   ```

4. Start development server:
   ```bash
   uv run python manage.py runserver
   ```

## Seed Data

The project includes a seed command that creates two default accounts:
- One `admin` user
- One `user` (regular user)

You can customize the seeded accounts using the following environment variables in your `.env` file:
```env
SEED_ADMIN_EMAIL=admin@example.com
SEED_ADMIN_PASSWORD=adminpass
SEED_USER_EMAIL=user@example.com
SEED_USER_PASSWORD=userpass
```
