---
name: test-writing
description: Writing unit, integration and e2e tests for Spring Boot services following the style of the current repository. Use when new tests are needed or existing tests must be extended.
---

# Skill: Writing tests for Spring Boot services

## Основной принцип
Всегда сначала анализируй существующие тесты в текущем репозитории и копируй их стиль.

Если тесты уже существуют:
- следуй их структуре
- используй те же аннотации
- используй те же библиотеки
- копируй naming conventions

Если стиль тестов неоднозначен — задай вопрос пользователю.

---

# Технологии тестирования

## Unit тесты
Используй:

- JUnit 5
- Mockito
- AssertJ

Примерная структура:

- у класса теста тот же пакет что и у тестируемого класса 
- моки через Mockito
- assertions через AssertJ
- не используем spring context
- fixtures, mock данные выносим в отдельный утилитный/билдер класс
---

## Интеграционные тесты

Используй:

@SpringBootTest

Следуй стилю существующих integration тестов в проекте.

---

## E2E тесты

Используй:

Testcontainers через библиотеку команды:

testImplementation(“company:testing-sb3:1.2.0”)

Не подключай Testcontainers напрямую.

---

## REST API тесты

Если тестируется REST API:

используй:

RestAssured

---

## Моки внешних сервисов

Для внешних HTTP вызовов используй:

WireMock

---

# Процесс написания теста

Перед написанием теста:

1. Найди существующие тесты в проекте.
2. Определи:
    - какие аннотации используются
    - как создаются моки
    - какой стиль assertions
3. Скопируй структуру существующего теста.

---

# Когда тестов нет

Если в модуле нет тестов:

### Unit тест

Используй:

- JUnit 5
- Mockito
- AssertJ

### Integration тест

Используй:

@SpringBootTest

### E2E тест

Используй:

- Testcontainers через `testing-sb3`
- RestAssured
- WireMock при необходимости
- Подниммай контекст spring полностью

---

# Ограничения

- Не переписывай существующие тесты без необходимости.
- Перепись существующих тестов только с подтверждения
- Не меняй стиль тестов, принятый в текущем репозитории.
- Если есть несколько стилей тестов — сначала спроси пользователя.