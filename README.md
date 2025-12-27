# 🚀 Express TypeScript Backend Template

A production-ready backend template built with **Express.js**, **TypeScript**, **Prisma ORM**, and **PostgreSQL**. This template follows clean architecture principles with a well-organized folder structure for scalable and maintainable applications.

## ✨ Features

- ⚡ **Express 5** - Fast, unopinionated, minimalist web framework
- 🔷 **TypeScript** - Type-safe development with the latest ES features
- 🗃️ **Prisma ORM** - Next-generation ORM for Node.js and TypeScript
- 🐘 **PostgreSQL** - Powerful, open-source relational database
- 🔐 **JWT Authentication** - Secure authentication with access & refresh tokens
- 🔒 **Bcrypt** - Password hashing for enhanced security
- ✅ **Zod Validation** - TypeScript-first schema validation
- 🔄 **CORS** - Cross-Origin Resource Sharing enabled
- 🌱 **Environment Validation** - Type-safe environment variables with Zod
- 🔥 **Hot Reload** - Development with Nodemon & TSX

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- [Node.js](https://nodejs.org/) (v18 or higher recommended)
- [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/) or [pnpm](https://pnpm.io/)
- [PostgreSQL](https://www.postgresql.org/) database

## 🛠️ Installation

### 1. Clone the repository

```bash
git clone <repository-url>
cd template-setup-be
```

### 2. Install dependencies

```bash
npm install
# or
yarn install
# or
pnpm install
```

### 3. Environment Setup

Create a `.env` file in the root directory:

```env
# Application
NODE_ENV=development
HOST=localhost
PORT=3000

# CORS
CORS_ORIGIN=http://localhost:3000

# Database
DATABASE_URL=postgresql://username:password@localhost:5432/database_name

# JWT Secrets
ACCESS_TOKEN_SECRET=your-super-secret-access-token-key
REFRESH_TOKEN_SECRET=your-super-secret-refresh-token-key
```

### 4. Database Setup

Generate Prisma Client:

```bash
npx prisma generate
```

Run database migrations:

```bash
npx prisma migrate dev --name init
```

(Optional) Open Prisma Studio to view your database:

```bash
npx prisma studio
```

### 5. Start Development Server

```bash
npm run dev
```

The server will start at `http://localhost:3000` (or your configured PORT).

## 📁 Project Structure

```
├── prisma/
│   └── schema.prisma       # Prisma schema definition
├── src/
│   ├── controllers/        # Route handlers / Controllers
│   │   └── nameController.ts
│   ├── lib/                # Library configurations
│   │   ├── env.ts          # Environment variables validation
│   │   └── prisma.ts       # Prisma client instance
│   ├── middlewares/        # Express middlewares
│   │   └── authMiddleware.ts
│   ├── repositories/       # Data access layer
│   │   └── nameRepository.ts
│   ├── routes/             # API route definitions
│   │   └── nameRoute.ts
│   ├── seeds/              # Database seeders
│   │   └── seeder.ts
│   ├── services/           # Business logic layer
│   │   └── nameService.ts
│   ├── types/              # TypeScript type definitions
│   │   └── nameType.ts
│   ├── utils/              # Utility functions
│   │   ├── errorResponse.ts
│   │   ├── successResponse.ts
│   │   └── index.ts
│   ├── validators/         # Request validation schemas
│   │   └── nameValidation.ts
│   └── index.ts            # Application entry point
├── nodemon.json            # Nodemon configuration
├── package.json            # Project dependencies
├── prisma.config.ts        # Prisma configuration
└── tsconfig.json           # TypeScript configuration
```

## 🏗️ Architecture Overview

This template follows the **Clean Architecture** pattern with separation of concerns:

| Layer            | Description                                |
| ---------------- | ------------------------------------------ |
| **Controllers**  | Handle HTTP requests and responses         |
| **Services**     | Contain business logic                     |
| **Repositories** | Data access and database operations        |
| **Validators**   | Request validation using Zod schemas       |
| **Middlewares**  | Authentication, logging, error handling    |
| **Types**        | TypeScript interfaces and type definitions |
| **Utils**        | Reusable utility functions                 |

### Request Flow

```
Request → Route → Middleware → Controller → Service → Repository → Database
```

## 📜 Available Scripts

| Command       | Description                              |
| ------------- | ---------------------------------------- |
| `npm run dev` | Start development server with hot reload |

## 🔧 Configuration Files

### TypeScript (`tsconfig.json`)

- Target: ESNext
- Module: NodeNext
- Path aliases: `@/*` maps to `src/*`
- Strict mode enabled

### Nodemon (`nodemon.json`)

- Watches: `.ts`, `.js`, `.json` files
- Uses TSX for TypeScript execution

### Prisma (`prisma.config.ts`)

- Schema location: `prisma/schema.prisma`
- Migrations: `prisma/migrations`
- Database: PostgreSQL

## 🛡️ API Response Format

### Success Response

```json
{
	"status": 200,
	"success": true,
	"message": "Operation successful",
	"data": {}
}
```

### Error Response

```json
{
	"success": false,
	"status": 400,
	"code": "BAD_REQUEST",
	"message": "Error message",
	"errors": [
		{
			"field": "fieldName",
			"message": "Validation error message"
		}
	]
}
```

### Error Codes

| Code                    | Status | Description             |
| ----------------------- | ------ | ----------------------- |
| `BAD_REQUEST`           | 400    | Invalid request data    |
| `UNAUTHORIZED`          | 401    | Authentication required |
| `FORBIDDEN`             | 403    | Access denied           |
| `NOT_FOUND`             | 404    | Resource not found      |
| `INTERNAL_SERVER_ERROR` | 500    | Server error            |

## 🌱 Environment Variables

| Variable               | Required | Default       | Description                  |
| ---------------------- | -------- | ------------- | ---------------------------- |
| `NODE_ENV`             | No       | `development` | Environment mode             |
| `HOST`                 | No       | `localhost`   | Server host                  |
| `PORT`                 | No       | `8000`        | Server port                  |
| `CORS_ORIGIN`          | Yes      | -             | Allowed CORS origin URL      |
| `DATABASE_URL`         | Yes      | -             | PostgreSQL connection string |
| `ACCESS_TOKEN_SECRET`  | Yes      | -             | JWT access token secret      |
| `REFRESH_TOKEN_SECRET` | Yes      | -             | JWT refresh token secret     |

## 📦 Dependencies

### Production

| Package              | Description                   |
| -------------------- | ----------------------------- |
| `express`            | Web framework                 |
| `@prisma/client`     | Prisma ORM client             |
| `@prisma/adapter-pg` | PostgreSQL adapter for Prisma |
| `pg`                 | PostgreSQL client             |
| `bcrypt`             | Password hashing              |
| `jsonwebtoken`       | JWT implementation            |
| `zod`                | Schema validation             |
| `cors`               | CORS middleware               |
| `dotenv`             | Environment variables         |

### Development

| Package      | Description                      |
| ------------ | -------------------------------- |
| `typescript` | TypeScript compiler              |
| `tsx`        | TypeScript execution             |
| `ts-node`    | TypeScript execution for Node.js |
| `nodemon`    | File watcher for development     |
| `prisma`     | Prisma CLI                       |
| `@types/*`   | TypeScript type definitions      |

## 🚀 Deployment

### Build for Production

```bash
# Generate Prisma Client
npx prisma generate

# Compile TypeScript
npx tsc

# Run migrations
npx prisma migrate deploy
```

### Production Start

```bash
node dist/index.js
```

## 📝 Usage Examples

### Creating a New Module

1. **Define the Prisma model** in `prisma/schema.prisma`
2. **Create types** in `src/types/`
3. **Create validation schemas** in `src/validators/`
4. **Create repository** in `src/repositories/`
5. **Create service** in `src/services/`
6. **Create controller** in `src/controllers/`
7. **Define routes** in `src/routes/`
8. **Register routes** in `src/index.ts`

### Example Controller Usage

```typescript
import { Request, Response } from "express";
import { successRes, errBadRequest, errInternalServer } from "@/utils";

export const getItems = async (req: Request, res: Response) => {
	try {
		const items = await itemService.findAll();
		return successRes(res, items, "Items retrieved successfully");
	} catch (error) {
		return errInternalServer(res, error);
	}
};
```

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request


<p align="center">
  Made with ❤️ using Express.js & TypeScript
</p>
