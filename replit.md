# AI4u - University of Utah AI Community Platform

## Overview

AI4u is a web application for the University of Utah's AI community club. It serves as an informational platform showcasing the club's mission, activities, events, and membership opportunities. The application provides a single-page experience with smooth scrolling navigation between sections, featuring details about weekly meetings, workshops, speaker series, and the club's interdisciplinary approach to AI education.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework & Build System**
- React 18 with TypeScript for type-safe component development
- Vite as the build tool and development server for fast HMR and optimized production builds
- Single-page application (SPA) using Wouter for lightweight client-side routing
- Component architecture follows a modular pattern with reusable UI components

**UI Component System**
- Shadcn/ui component library (New York style variant) for consistent, accessible UI elements
- Radix UI primitives as the foundation for complex interactive components
- Tailwind CSS for utility-first styling with CSS variables for theming
- Custom design tokens defined in CSS variables for colors, spacing, and shadows

**State Management**
- TanStack Query (React Query) for server state management and data fetching
- Custom query client configuration with disabled refetching for stable data display
- Local component state using React hooks for UI interactions

### Backend Architecture

**Server Framework**
- Express.js server with TypeScript for API endpoints
- RESTful API design for event management operations (GET, POST, PATCH, DELETE)
- Middleware for JSON parsing, URL encoding, and request logging
- Custom error handling middleware for consistent error responses

**Development Setup**
- Vite middleware integration in development mode for seamless full-stack development
- Static file serving for production builds
- Request/response logging with duration tracking for API endpoints

**Data Layer**
- In-memory storage implementation (MemStorage class) for development/demo purposes
- Storage interface (IStorage) defines contracts for data operations
- Pre-populated default events for demonstration purposes
- Schema validation using Zod for runtime type safety

### Database Schema

**PostgreSQL with Drizzle ORM**
- Configured for PostgreSQL dialect with Neon serverless driver
- Schema defined in TypeScript using Drizzle ORM's table definitions
- Two main tables:
  - **users**: id (UUID), username (unique), password
  - **events**: id (UUID), title, description, date (timestamp), location, speaker, eventType
- Drizzle-Zod integration for automatic schema validation from database types
- Migration files managed in `/migrations` directory

**Data Validation**
- Insert schemas generated from Drizzle table definitions
- Zod validation on API endpoints for type safety
- Partial schema support for PATCH operations

### External Dependencies

**UI & Styling Libraries**
- Radix UI component primitives (accordion, dialog, dropdown, toast, etc.)
- Tailwind CSS with PostCSS for processing
- Class Variance Authority (CVA) for variant-based component styling
- CLSX and Tailwind Merge for conditional class name management

**Data Management**
- TanStack Query v5 for async state management
- React Hook Form with Hookform Resolvers for form handling
- Drizzle ORM for database operations
- Zod for schema validation

**Database & Infrastructure**
- Neon Database serverless PostgreSQL driver
- Drizzle Kit for schema migrations and database operations
- Connect-pg-simple for PostgreSQL session storage (configured but not actively used)

**Development Tools**
- Replit-specific plugins for development (cartographer, dev-banner, runtime error overlay)
- ESBuild for server-side code bundling in production
- TSX for TypeScript execution in development

**Utilities**
- date-fns for date manipulation and formatting
- nanoid for unique ID generation
- embla-carousel-react for carousel functionality (imported but not actively used in main pages)
- cmdk for command menu functionality (imported but not actively used)

**Build Configuration**
- TypeScript with strict mode and ESNext module resolution
- Path aliases configured: `@/` (client), `@shared/` (shared), `@assets/` (assets)
- Separate build outputs: client to `dist/public`, server to `dist`