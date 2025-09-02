# Student Portal SaaS

A comprehensive multi-tenant web-based platform designed for small universities and colleges to manage student academic life, administrative processes, and communication.

## Architecture

This is a monorepo containing:

- **Frontend** (`apps/frontend`): React application with TypeScript and Tailwind CSS
- **Backend** (`apps/backend`): Node.js/Express API with TypeScript
- **Shared** (`packages/shared`): Common types, utilities, and validation schemas

## Prerequisites

- Node.js 18+ and npm 9+
- Docker and Docker Compose
- PostgreSQL 15+ (or use Docker)
- Redis 7+ (or use Docker)

## Quick Start

1. **Clone and install dependencies:**
   ```bash
   git clone <repository-url>
   cd student-portal-saas
   npm install
   ```

2. **Set up environment variables:**
   ```bash
   cp .env.example .env
   # Edit .env with your configuration
   ```

3. **Start with Docker (recommended for development):**
   ```bash
   npm run docker:up
   ```

4. **Or start services manually:**
   ```bash
   # Start PostgreSQL and Redis (if not using Docker)
   # Then run:
   npm run dev
   ```

5. **Access the application:**
   - Frontend: http://localhost:3000
   - Backend API: http://localhost:3001
   - Health check: http://localhost:3001/health

## Development

### Available Scripts

- `npm run dev` - Start both frontend and backend in development mode
- `npm run build` - Build all packages
- `npm run test` - Run tests for all packages
- `npm run lint` - Lint all code
- `npm run format` - Format code with Prettier

### Docker Commands

- `npm run docker:up` - Start all services with Docker Compose
- `npm run docker:down` - Stop all Docker services
- `npm run docker:build` - Rebuild Docker images

### Project Structure

```
student-portal-saas/
├── apps/
│   ├── backend/          # Express.js API server
│   └── frontend/         # React application
├── packages/
│   └── shared/           # Shared types and utilities
├── docker/               # Docker configuration files
├── docker-compose.yml    # Docker Compose configuration
└── package.json          # Root package.json with workspaces
```

## Multi-Tenant Architecture

The platform uses a tenant-per-schema approach:

- **Tenant Identification**: Subdomain-based routing (e.g., `university1.studentportal.com`)
- **Data Isolation**: Each tenant has a dedicated database schema
- **Shared Resources**: Application code, infrastructure, and common services
- **Customization**: Per-tenant configuration, branding, and feature flags

## Technology Stack

- **Frontend**: React 18, TypeScript, Tailwind CSS, Vite
- **Backend**: Node.js, Express.js, TypeScript
- **Database**: PostgreSQL with tenant-specific schemas
- **Cache**: Redis for session management and caching
- **Authentication**: JWT tokens with refresh token rotation
- **Testing**: Jest (backend), Vitest (frontend)
- **Code Quality**: ESLint, Prettier, TypeScript

## Contributing

1. Follow the existing code style and conventions
2. Write tests for new features
3. Run linting and formatting before committing
4. Use conventional commit messages

## License

[Add your license here]