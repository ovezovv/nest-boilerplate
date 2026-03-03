# 🚀 NestJS Boilerplate --- GraphQL + Prisma + PostgreSQL

A production-ready NestJS boilerplate using:

- ⚡ NestJS 11
- 🧠 GraphQL (Apollo Driver, Code-First)
- 🛢 PostgreSQL
- 🔷 Prisma ORM v7
- 🧩 Express 5
- 🔐 Environment-based configuration

This project is designed to be clean, modern, and aligned with the
latest stable ecosystem.

---

## 📌 Tech Stack & Versions

Package Version

---

Node.js 24.x LTS
NestJS \^11.x
@nestjs/graphql \^13.x
@nestjs/apollo \^13.x
GraphQL \^16.x
Prisma \^7.x
PostgreSQL 14+
Express 5.x
@as-integrations/express5 \^1.x

---

## 📁 Project Structure

    backend/
    ├── prisma/
    │   ├── schema.prisma
    │   └── migrations/
    ├── src/
    │   ├── prisma/
    │   │   └── prisma.service.ts
    │   ├── app.module.ts
    │   ├── app.resolver.ts
    │   └── main.ts
    ├── prisma.config.ts
    ├── .env
    ├── .env.example
    └── package.json

---

## ⚙️ Environment Setup

Create your environment file:

```bash
cp .env.example .env
```

### `.env.example`

```env
PORT=3000
DATABASE_URL="postgresql://{db_user}:{db_user_password}@localhost:5432/{database_name}?schema=public"
```

---

## 🛢 PostgreSQL Setup

You can use:

- Local PostgreSQL installation
- Remote PostgreSQL server
- Cloud PostgreSQL provider (Neon, Supabase, RDS, etc.)

Make sure:

- Database exists
- User has full privileges
- `DATABASE_URL` is correct

Example:

```env
DATABASE_URL="postgresql://app:securepassword@localhost:5432/app_db?schema=public"
```

---

## 📦 Installation

```bash
npm install
```

---

## 🧬 Prisma Setup (v7)

This boilerplate uses Prisma v7 with adapter-based configuration.

### Generate Prisma Client

```bash
npx prisma generate
```

### Run Initial Migration

```bash
npx prisma migrate dev --name init
```

### Open Prisma Studio

```bash
npx prisma studio
```

---

## ▶️ Run Development Server

```bash
npm run start:dev
```

Server:

http://localhost:3000

GraphQL Playground:

http://localhost:3000/graphql

Test query:

```graphql
query {
  health
}
```

---

## 🏗 Architecture Notes

### Prisma v7 Adapter-Based Client

This project uses Prisma's new driver adapter system:

```ts
import { PrismaPg } from '@prisma/adapter-pg';
import { Pool } from 'pg';

const pool = new Pool({ connectionString: process.env.DATABASE_URL });
const adapter = new PrismaPg(pool);

super({ adapter });
```

This avoids deprecated configuration patterns and aligns with Prisma v7
best practices.

---

## 🔐 Production Recommendations

For production deployments:

- Use managed PostgreSQL (Neon, Supabase, AWS RDS, etc.)
- Disable GraphQL Playground in production
- Enable:
  - Helmet
  - CORS configuration
  - Global validation pipes
- Add structured logging (Winston or Pino)
- Use environment-based configs
- Enable graceful shutdown hooks
- Add rate limiting
- Use proper CI/CD workflow

---

## 📜 Available Scripts

```bash
npm run start:dev      # Development mode
npm run build          # Build production bundle
npm run start:prod     # Start production build

npm run prisma:generate
npm run prisma:migrate
npm run prisma:studio
```

---

## 🎯 Ideal For

- CMS backends
- SaaS APIs
- Admin dashboards
- Multi-language content APIs
- Scalable GraphQL backends
- Clean architecture starters

---

## 📄 License

MIT

---

## ⭐ Contributing

Feel free to fork, improve, and submit pull requests.

If this boilerplate helps you, consider giving it a star ⭐
