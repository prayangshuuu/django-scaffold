# django-scaffold

A minimal, clean, and reusable Django boilerplate configured with uv, Docker, and PostgreSQL.

## Requirements

- [Docker](https://docs.docker.com/get-docker/) and [Docker Compose](https://docs.docker.com/compose/)
- [uv](https://docs.astral.sh/uv/) (optional for local non-Docker development)

## Getting Started (Docker)

1. Copy the environment file:
   ```bash
   cp .env.example .env
   ```

2. Build and start containers:
   ```bash
   docker-compose up --build
   ```

3. Run database migrations:
   ```bash
   docker-compose exec web uv run python manage.py migrate
   ```

4. Access the application at `http://localhost:8000`.

## Local Development (with uv)

1. Set up dependencies:
   ```bash
   uv sync
   ```

2. Run migrations:
   ```bash
   uv run python manage.py migrate
   ```

3. Start development server:
   ```bash
   uv run python manage.py runserver
   ```
