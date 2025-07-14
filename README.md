# RevReq.com
## AI-Powered Feedback to Requirements Platform

RevReq is an AI-powered SaaS platform that automatically transforms customer feedback into actionable product requirements with success predictions. This repository contains the starter template for building the full RevReq platform.

## 🚀 Vision
Turn feedback noise into product clarity by automatically converting scattered customer feedback into prioritized, actionable requirements.

## 🛠️ Tech Stack

### Core Technologies
- **[TypeScript](https://www.typescriptlang.org/)** - Type safety across the entire codebase
- **[Bun](https://bun.sh/)** - Fast all-in-one JavaScript runtime and package manager
- **[Turborepo](https://turbo.build/)** - High-performance build system for monorepos

### Frontend
- **[React](https://react.dev/)** - UI library
- **[TanStack Router](https://tanstack.com/router)** - Type-safe file-based routing
- **[TailwindCSS](https://tailwindcss.com/)** - Utility-first CSS framework
- **[shadcn/ui](https://ui.shadcn.com/)** - High-quality React components
- **[Vite](https://vitejs.dev/)** - Fast build tool and dev server

### Backend
- **[Hono](https://hono.dev/)** - Lightweight, fast web framework
- **[tRPC](https://trpc.io/)** - End-to-end type-safe APIs
- **[Drizzle ORM](https://orm.drizzle.team/)** - TypeScript-first SQL ORM
- **[PostgreSQL](https://www.postgresql.org/)** - Primary database
- **[Better Auth](https://www.better-auth.com/)** - Secure authentication system

### Infrastructure (Planned)
- **[Upstash Redis](https://upstash.com/)** - Serverless Redis for caching and queues
- **[Bull/BullMQ](https://bullmq.io/)** - Background job processing
- **[Resend](https://resend.com/)** - Email service
- **[Vercel](https://vercel.com/)** - Deployment platform

### Developer Tools
- **[Biome](https://biomejs.dev/)** - Fast formatter and linter
- **[Husky](https://typicode.github.io/husky/)** - Git hooks
- **[Astro Starlight](https://starlight.astro.build/)** - Documentation framework

## 📋 Prerequisites

- [Bun](https://bun.sh/) v1.0 or higher
- [PostgreSQL](https://www.postgresql.org/) v14 or higher
- [Git](https://git-scm.com/)

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/yourusername/revreq.git
cd revreq
```

### 2. Install dependencies
```bash
bun install
```

### 3. Database Setup

1. Create a PostgreSQL database for the project
2. Copy the environment variables template:
```bash
cp apps/server/.env.example apps/server/.env
```
3. Update `apps/server/.env` with your database credentials:
```env
DATABASE_URL="postgresql://user:password@localhost:5432/revreq"
BETTER_AUTH_SECRET="your-secret-key-min-32-chars"
```
4. Push the database schema:
```bash
bun db:push
```

### 4. Start the development servers
```bash
bun dev
```

This will start:
- 🌐 Web app: [http://localhost:3001](http://localhost:3001)
- 🔧 API server: [http://localhost:3000](http://localhost:3000)
- 📚 Docs (optional): `cd apps/docs && bun dev` → [http://localhost:4321](http://localhost:4321)

## 📁 Project Structure

```
revreq/
├── apps/
│   ├── web/         # Frontend application
│   │   ├── src/
│   │   │   ├── components/   # React components
│   │   │   ├── routes/       # TanStack Router pages
│   │   │   ├── lib/          # Utilities and helpers
│   │   │   └── utils/        # tRPC client setup
│   │   └── package.json
│   │
│   ├── server/      # Backend API
│   │   ├── src/
│   │   │   ├── db/           # Database schema & config
│   │   │   ├── routers/      # tRPC routers
│   │   │   └── lib/          # Server utilities
│   │   └── package.json
│   │
│   └── docs/        # Documentation site
│       └── src/
│           └── content/      # Markdown docs
│
├── plans/           # Project planning documents
│   ├── prd.md       # Product Requirements Document
│   └── tasks.md     # Development tasks breakdown
│
├── turbo.json       # Turborepo configuration
├── package.json     # Root package.json
└── CLAUDE.md        # AI assistant context file
```

## 📝 Available Scripts

### Development
- `bun dev` - Start all apps in development mode
- `bun dev:web` - Start only the frontend
- `bun dev:server` - Start only the backend
- `bun build` - Build all apps for production

### Database
- `bun db:push` - Push schema changes to database
- `bun db:studio` - Open Drizzle Studio GUI
- `bun db:generate` - Generate database migrations
- `bun db:migrate` - Run database migrations

### Code Quality
- `bun check` - Run Biome linter and formatter
- `bun check-types` - TypeScript type checking
- `bun prepare` - Setup git hooks with Husky

### Documentation
- `cd apps/docs && bun dev` - Start docs dev server
- `cd apps/docs && bun build` - Build docs for production

## 🔧 Configuration

### Environment Variables

Create `.env` files in the respective app directories:

#### `apps/server/.env`
```env
# Database
DATABASE_URL="postgresql://user:password@localhost:5432/revreq"

# Authentication
BETTER_AUTH_SECRET="your-secret-key-min-32-chars" # Generate with: openssl rand -base64 32

# AI/LLM APIs (for future use)
OPENAI_API_KEY="sk-..."
ANTHROPIC_API_KEY="sk-ant-..."

# Redis (for future use)
UPSTASH_REDIS_URL="https://..."
UPSTASH_REDIS_TOKEN="..."

# Email (for future use)
RESEND_API_KEY="re_..."
```

## 🏗️ Architecture Overview

### Frontend (React + TanStack Router)
- **File-based routing** with full type safety
- **Server-state management** via tRPC + React Query
- **Component library** using shadcn/ui
- **Styling** with TailwindCSS
- **Authentication** integrated with Better Auth

### Backend (Hono + tRPC)
- **Type-safe API** endpoints with automatic client types
- **Database access** via Drizzle ORM
- **Authentication** with Better Auth
- **Middleware** for logging, CORS, auth guards
- **Background jobs** ready with Bull/BullMQ integration

### Database (PostgreSQL)
- **Schema management** with Drizzle
- **Migrations** tracked in source control
- **pgvector** extension for AI embeddings
- **Optimized indexes** for performance

## 🚢 Deployment

### Vercel (Recommended)
The project is optimized for deployment on Vercel:

1. Connect your GitHub repository to Vercel
2. Configure environment variables
3. Deploy with automatic preview environments

### Docker (Alternative)
```dockerfile
# Coming soon
```

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Workflow
- Code is auto-formatted on commit via Husky + Biome
- TypeScript must pass type checking
- Follow the established patterns in the codebase

## 📚 Documentation

- [Product Requirements Document](./plans/prd.md) - Full product vision and specifications
- [Development Tasks](./plans/tasks.md) - Detailed implementation roadmap
- [API Documentation](http://localhost:3000/docs) - Auto-generated from tRPC (when running)

## 🎯 Product Roadmap

### Phase 1: Foundation (Months 1-8)
- ✅ Core architecture setup
- ⏳ Zendesk integration
- ⏳ AI analysis engine
- ⏳ Requirements generation
- ⏳ Jira integration

### Phase 2: Expansion (Months 9-16)
- Additional integrations (Intercom, Freshdesk, etc.)
- PM tool suite expansion
- Public API v1
- Team collaboration features

### Phase 3: Enterprise (Months 17-24)
- SSO/SAML authentication
- Advanced RBAC
- Multi-workspace support
- SOC 2 compliance

## 📄 License

This project is proprietary software. All rights reserved.

## 🙋‍♀️ Support

- **Documentation**: Check the [docs site](http://localhost:4321) when running locally
- **Issues**: Use GitHub Issues for bug reports
- **Discussions**: Use GitHub Discussions for questions

---

Built with ❤️ using modern web technologies
