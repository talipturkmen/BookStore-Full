# BookStore-Full

> **Archived.** This is a 2018 course/learning project and is no longer maintained. Dependencies are outdated and contain known vulnerabilities; do not deploy as-is.

A server-rendered bookstore with two Spring Boot applications that share one MySQL database. The customer application (`Bookstore/`) provides a book catalog, shopping cart, checkout, order history, and user accounts with password reset by email. The admin application (`adminportal/`) manages books and orders.

## Tech stack

- Java 1.8
- Spring Boot 1.4.3 (Spring Security, Spring Data JPA / Hibernate, Thymeleaf, `thymeleaf-extras-springsecurity4`)
- MySQL (`mysql-connector-java`)
- Maven (wrapper included)
- Bootstrap and jQuery (bundled as static files)

## Repository structure

- `Bookstore/`: customer-facing Spring Boot application (default port 8080)
- `adminportal/`: admin Spring Boot application (port 8081)
- Each application has `src/main/java/...` (controllers, services, repositories, domain), `src/main/resources/templates/` (Thymeleaf), and `src/main/resources/static/` (assets).

## Running it

This is best-effort documentation; the project was not re-run during the cleanup.

1. Install JDK 8 and MySQL, and start MySQL on `localhost:3306`.
2. Create a database named `bookstoredatabase`. Both applications use `ddl-auto=update`.
3. Check the datasource settings in each `src/main/resources/application.properties` (the defaults are `root` / `sesame`).
4. To send password-reset and account emails, set `spring.mail.*` in the properties file. The mail password was removed from this repository, so it must be supplied locally.
5. From `Bookstore/` run `./mvnw spring-boot:run` (http://localhost:8080). From `adminportal/` run `./mvnw spring-boot:run` (http://localhost:8081).

## Known issues

- Database credentials and the BCrypt salt (`"salt"`) are hard-coded in the source.
- The admin application and the customer application use the same database and have separate copies of the domain classes.
- This code is not suitable for real use. See the archive note above.
