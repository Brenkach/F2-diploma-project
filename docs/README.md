# Документація проєкту «Сусід»

Веб-платформа локальних послуг із районним рейтингом довіри, стійким до накрутки відгуків.

## Навігація

| Документ | Опис |
|---|---|
| [Розділ 1 (локальний .docx)](./F2_Diploma_Chapter1_Brenkach.docx) | Аналіз предметної області та постановка задачі |
| Розділ 1 (хмарний файл, режим «Can comment») | https://docs.google.com/document/d/1vxf4DWT1cBav3a8jCheDgw9I5ZYqvONBCZMfsg6z8GY/edit?usp=sharing |
| [1_analysis.md](./1_analysis.md) | Аналіз аналогів, модель To-Be, Core Features, NFRs у Markdown |
| [srs.md](./srs.md) | Специфікація вимог (ISO/IEC/IEEE 29148): функціональні вимоги SRS-FUN, нефункціональні SRS-NFR, критерії верифікації, глосарій |
| [2_design.md](./2_design.md) | Архітектура: C4 Level 1-3 (Mermaid) із трасуванням на вимоги |
| [adr/](./adr/) | Architecture Decision Records |
| [adr/0001-choice-of-technology.md](./adr/0001-choice-of-technology.md) | ADR-001: Transactional Outbox у PostgreSQL + Celery + Redis |

## Календарний план

| Етап | Статус |
|---|---|
| Аналіз предметної області та вимоги (Розділ 1) | Done |
| Проєктування архітектури (Розділ 2) | In Progress |
| Реалізація (Розділ 3) | Planned |
| Тестування та експерименти | Planned |
| Підготовка до захисту | Planned |

## Ключові архітектурні обмеження

- Модульний моноліт на Python/Flask, PostgreSQL як єдине джерело істини.
- Transactional Outbox, асинхронні worker-процеси Celery з брокером Redis ([ADR-001](./adr/0001-choice-of-technology.md)).
- Розгортання на одному вузлі (4 vCPU, 8 ГБ RAM) через Docker Compose; масштабування вертикальне.
- Повна матриця нефункціональних вимог з числовими значеннями та інструментами перевірки: [srs.md, розділ 3](./srs.md#3-non-functional-requirements-нефункціональні-вимоги).
