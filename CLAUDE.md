# RevReq - AI-Powered Feedback to Requirements Platform

## Project Overview
RevReq is an AI-powered SaaS platform that automatically transforms customer feedback into actionable product requirements with success predictions. The platform aggregates feedback from support tickets and app reviews, uses advanced LLMs with intelligent routing to analyze and deduplicate insights, and generates ready-to-use requirements that integrate bidirectionally with popular project management tools.

## Key Business Context
- **Target Market**: B2B SaaS companies (50-500 employees)
- **Core Value Prop**: Reduce feedback analysis time by 80%
- **Delivery Timeline**: 24-month full product build
- **Budget**: ~$15.4M total investment
- **Team Size**: 31 people by Month 24

## Technical Architecture

### Tech Stack
- **Frontend**: React with TanStack Router, TypeScript, TailwindCSS, shadcn/ui, Vite
- **Backend**: Hono, tRPC, Drizzle ORM
- **Database**: PostgreSQL with pgvector for embeddings
- **Runtime**: Bun
- **Authentication**: Better Auth
- **Documentation**: Astro Starlight
- **Background Jobs**: Bull/BullMQ with Upstash Redis
- **Caching & Queues**: Upstash Redis
- **File Storage**: Vercel Blob Storage
- **Email**: Resend
- **Deployment**: Vercel
- **Monorepo**: Turborepo
- **Code Quality**: Biome (linting/formatting), Vitest (testing), Playwright (E2E)

### Architecture Principles
1. **Monorepo Structure**: All apps and packages in a single repository
2. **Type Safety**: End-to-end type safety with TypeScript and tRPC
3. **File-based Routing**: TanStack Router for type-safe routing
4. **Modern Runtime**: Bun for fast development and deployment
5. **Security First**: Enterprise-grade security from Day 1

## Core Features

### Phase 1: Foundation & Core (Months 1-8)
- Zendesk integration (support tickets)
- Apple App Store & Google Play Store reviews
- AI analysis with smart LLM routing
- Requirements generation
- Jira Cloud integration
- Basic analytics dashboard

### Phase 2: Expansion (Months 9-16)
- Additional integrations: Intercom, Freshdesk, Trustpilot, Google Business
- Full PM tool suite: GitHub Issues, Linear, Asana, Monday.com
- Team collaboration features
- API v1 release

### Phase 3: Enterprise (Months 17-24)
- SSO/SAML support
- Advanced RBAC
- Multi-workspace support
- API v2 with SDKs
- SOC 2 compliance

## AI/LLM Strategy
- **Smart Routing**: 
  - GPT-4o mini for simple categorization ($2.50/MTok)
  - Claude 3.5 Sonnet for complex analysis
  - Claude Opus 4 for requirement generation ($15/MTok)
- **Cost Optimization**: Caching, batch processing, customer API keys
- **Target**: Keep LLM costs <5% of revenue

## Integration Specifications
- **Input Sources** (7 total): Zendesk, App Store, Play Store, Intercom, Freshdesk, Trustpilot, Google Business
- **Output Destinations** (5 total): Jira, GitHub, Linear, Asana, Monday.com
- **Architecture**: Pull from sources, push-only to PM tools (no reverse sync)

## Development Guidelines

### Code Organization
```
/apps
  /web          # Frontend application (React + TanStack Router)
  /docs         # Documentation site (Astro Starlight)
  /server       # Backend API (Hono, tRPC)
```

### Key Conventions
1. **API Server**: Hono framework in `/apps/server`
2. **Type-safe APIs**: tRPC for end-to-end type safety
3. **Authentication**: Use Better Auth for all auth needs
4. **Database**: Use Drizzle ORM for all database operations
5. **Frontend Routing**: TanStack Router with file-based routing
6. **Testing**: Write tests for all critical paths

### Environment Variables
```
DATABASE_URL          # PostgreSQL connection
BETTER_AUTH_SECRET    # Auth secret (min 32 chars)
UPSTASH_REDIS_URL    # Redis for cache/queues
UPSTASH_REDIS_TOKEN  # Redis auth token
ANTHROPIC_API_KEY    # For Claude models
OPENAI_API_KEY       # For GPT models
RESEND_API_KEY       # Email service
```

## Commands & Scripts
```bash
# Development
bun install          # Install dependencies
bun dev             # Start all apps (web on :3001, server on :3000)
bun build           # Build all apps
bun dev:web         # Start only the web application
bun dev:server      # Start only the server

# Database
bun db:push         # Push schema changes to database
bun db:studio       # Open database studio UI

# Code Quality
bun check           # Run Biome formatting and linting
bun check-types     # Check TypeScript types across all apps

# Documentation
cd apps/docs && bun dev    # Start documentation site
cd apps/docs && bun build  # Build documentation site
```

## Testing Strategy
- **Unit Tests**: Vitest for business logic
- **Component Tests**: React Testing Library
- **E2E Tests**: Playwright for critical user flows
- **Coverage Target**: 80%+ for critical paths

## Security Requirements
- SOC 2 Type II compliance
- GDPR & CCPA compliance
- End-to-end encryption
- API rate limiting
- OWASP Top 10 compliance

## Performance Targets
- API response time: <200ms (P95)
- Frontend Core Web Vitals: All green
- Uptime: 99.9% SLA
- LLM processing: <5s for requirement generation

## Success Metrics (Month 24)
- 800+ total customers (480+ paying)
- $3.6M ARR
- 85% gross retention
- 110% net revenue retention
- <7 days to value
- NPS > 50

## Helpful Resources
- [Project Tasks](/plans/tasks.md) - Detailed implementation plan
- [Product Requirements](/plans/prd.md) - Full PRD with market analysis
- [TanStack Router Docs](https://tanstack.com/router/latest)
- [Hono Docs](https://hono.dev)
- [tRPC Docs](https://trpc.io)
- [Drizzle ORM Docs](https://orm.drizzle.team)
- [Bun Docs](https://bun.sh)

## Common Tasks

### Adding a New Integration
1. Create integration class extending base `Integration` class
2. Implement OAuth flow and data fetching
3. Add to integration registry
4. Create UI configuration wizard
5. Add to background sync jobs
6. Test rate limits and error handling

### Creating a New API Endpoint
1. Define tRPC router in `/apps/server/src/routers`
2. Add procedure with input validation using Zod
3. Implement business logic
4. Add auth middleware if needed
5. Export from main router
6. Frontend will have full type safety automatically

### Deploying to Production
1. All merges to `main` auto-deploy
2. Preview deployments for all PRs
3. Use feature flags for gradual rollouts
4. Monitor Vercel Analytics after deploy
5. Check error rates in Vercel Logs

## Contact & Support
- **Tech Lead**: [Your Name]
- **Product Manager**: [PM Name]
- **Slack Channel**: #revreq-dev
- **Documentation**: Internal wiki

---

*Last Updated: July 14, 2025*
*This file helps AI assistants understand the RevReq codebase. Keep it updated as the project evolves.*