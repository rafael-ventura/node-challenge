# +A Educação Challenge

## Architecture decisions

### Backend

Follows **Clean Architecture** principles, separating responsibilities for modularity:

- **API (Controllers)**: defines endpoints, delegates logic to use cases.
- **Use Cases**: business rules, keeping the application flow well defined.
- **Infrastructure**: repository implementations for **PostgreSQL**, via **Sequelize**.
- **Domain**: entity models representing the core business concepts.
- **Middlewares**:
  - **Auth**: JWT-based authentication.
  - **Error handling**: a global middleware to standardize error messages and avoid
    boilerplate try/catch blocks.
  - **Async handler**: reduces boilerplate for async calls.

#### Unit tests

- Every use case is covered by unit tests (Jest), tested in isolation with the database mocked
  so tests stay independent of infrastructure.

#### Postman

- Full endpoint collection: [postman.com/warped-eclipase-340486/a-educacao](https://www.postman.com/warped-eclipase-340486/a-educacao/overview)

#### Database

![schema](mockups/img.png)

- `users`: administrative users of the system, with `created_at`/`updated_at` for auditing.
- `students`: registered students, with `created_at`/`updated_at` for auditing.

### Frontend

Built with **Nuxt 3 + TypeScript + Vuetify**.

- **Components**: each isolated to a single responsibility.
- **Composables**: centralize API communication logic.
- **SCSS**: global definitions in `app.scss` for consistent colors/styles.
- **Validation**: form validation logic centralized in a single file.

---

## Libraries used

**Backend:** `express` · `sequelize` + `pg` · `jest` · `jsonwebtoken` · `bcryptjs` · `dotenv`

**Frontend:** `nuxt` · `vuetify` · `sass` · `vue-router` · `axios`

---

## What I'd improve with more time

1. **Frontend polish** — reusable button/input components, more centralized validation, richer
   feedback (loaders, detailed error messages).
2. **Authorization** — auth is implemented, but permission checks aren't yet enforced on the
   backend (the frontend hides some actions from unauthenticated users, but the API doesn't
   verify that itself).
3. **Data layer** — repository interfaces to make swapping the database easier, plus a shared
   base class to reduce duplication across repositories.
4. **Tests** — unit tests already cover all backend business logic; with more time I'd add
   integration tests (API + database + auth) and frontend component tests.
5. **Performance & UX** — pagination/filters on the student list, a metrics dashboard using the
   audit timestamps, and a "remember me" login option.
6. **Infrastructure** — a CI/CD pipeline for tests and deploys, plus using the audit timestamps
   to track all operations performed in the system.
