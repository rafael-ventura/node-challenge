# Node Challenge

Full Stack technical assessment for **+A Educação** ("Brazil's largest education platform"):
build a student-enrollment system — register students, then enroll them in an online class.

## Stack

- **Backend:** Node.js + TypeScript, Express, Clean Architecture, PostgreSQL (Sequelize), JWT auth, Jest
- **Frontend:** Nuxt 3 + TypeScript + Vuetify

## Architecture

Backend follows Clean Architecture: controllers → use cases (business rules) → repositories
(Sequelize/PostgreSQL), with domain models kept separate from infrastructure. JWT auth and a
global error-handling middleware round it out. Every use case has unit tests (Jest), with the
database mocked so tests stay isolated.

Frontend components are kept single-purpose, with composables centralizing API calls and form
validation.

Full write-up — decisions, libraries, and what I'd improve with more time — in
[`comments.md`](comments.md).

## How to run

```bash
cd backend && npm install && npm run dev
cd frontend && npm install && npm run dev
```
