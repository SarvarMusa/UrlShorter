# URL Shortener API

[![CI](https://github.com/SarvarMusa/UrlShorter/actions/workflows/ci.yml/badge.svg)](https://github.com/SarvarMusa/UrlShorter/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Description: A clean RESTful API that solves the problem of managing long, unwieldy URLs by generating short, unique codes that redirect users to the original destination. Built with Spring Boot and backed by an H2 in-memory database for easy setup with zero configuration.

## Tech Stack
- **Framework:** Spring Boot 2.7.x
- **Language:** Java 11
- **Database:** H2 (in-memory) & Spring Data JPA
- **Tools:** Maven, Lombok, ModelMapper, Spring Validation

## Setup instructions

1. Clone the repository:
   ```bash
   git clone https://github.com/SarvarMusa/UrlShorter.git
   cd UrlShorter
   ```

2. Run the application (no database setup required — H2 is embedded):
   ```bash
   ./mvnw spring-boot:run
   ```

3. The API will be available at `http://localhost:8080/api/v1`.

## Environment variables
No mandatory environment variables are required. The application uses an H2 in-memory database out of the box.

Optional overrides in `application.properties`:
- `server.port` (default: `8080`)
- `spring.h2.console.enabled` (default: `true`, access at `/h2-console`)

## Usage examples

**Shorten a URL:**
```bash
curl -X POST http://localhost:8080/api/v1/create \
  -H "Content-Type: application/json" \
  -d '{"url": "https://www.example.com/some/very/long/path"}'
```

**Redirect using a short code:**
```bash
curl -L http://localhost:8080/api/v1/{code}
```

## API endpoints

| Method | Endpoint               | Description                         |
|--------|------------------------|-------------------------------------|
| `GET`  | `/api/v1/all`          | Retrieve all shortened URLs         |
| `GET`  | `/api/v1/getCode/{code}` | Get details of a specific short URL |
| `GET`  | `/api/v1/{code}`       | Redirect to the original URL        |
| `POST` | `/api/v1/create`       | Create a new short URL              |
