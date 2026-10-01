# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

A small Spring Boot 2.4.4 (Java 11, Gradle 6.8.3 wrapper) scratch project. Gradle's `rootProject.name` is `acko`. Declared starters: Web, WebFlux, JDBC, Data MongoDB, Kafka, MySQL driver, Lombok.

- `com.AckoApplication` — the Spring Boot entry point. Because it sits in package `com`, component scanning covers every `com.*` package.
- `com.controller.PostData` — **not** a Spring bean. It has its own `main` and builds a bare `JdbcTemplate` with no `DataSource`, so running it fails until a DataSource is wired in (see the commented-out code).
- The test class lives in package `com.acko`, which differs from the main package `com`.

`src/main/resources/application.properties` points at a local MySQL database `twitter` on `localhost:3306` and sets `server.port=8085`.

## Commands

```bash
./gradlew build
./gradlew bootRun
./gradlew test --tests 'com.acko.AckoApplicationTests'
```
