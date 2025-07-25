# Quiz Application - replit.md

## Overview

This is a modern quiz application built with React and Express, featuring a full-stack architecture with TypeScript. The application allows users to take quizzes across different categories (GATE Computer Science, Data Analytics, UPSC, etc.) with real-time scoring, question navigation, and results tracking.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **UI Library**: Radix UI components with shadcn/ui design system
- **Styling**: Tailwind CSS with custom design tokens
- **State Management**: React hooks and TanStack Query for server state
- **Routing**: Wouter for lightweight client-side routing

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Database**: PostgreSQL with Drizzle ORM
- **Database Provider**: Neon Database (@neondatabase/serverless)
- **Session Storage**: PostgreSQL database storage (migrated from in-memory)
- **API Design**: RESTful endpoints with proper error handling

### Development Tools
- **TypeScript**: Full type safety across frontend and backend
- **ESBuild**: Fast backend bundling for production
- **Hot Reload**: Vite HMR for frontend, tsx for backend development

## Key Components

### Database Schema (shared/schema.ts)
- **Users Table**: Basic user authentication with username/password
- **Quiz Sessions Table**: Stores completed quiz attempts with scores, answers, and metadata
- **Zod Validation**: Type-safe schema validation for all data structures

### Frontend Pages
- **Home**: Category selection dashboard
- **Gate Sections**: GATE exam subcategories
- **Quiz**: Interactive quiz interface with timer and navigation
- **Results**: Detailed score breakdown and performance analysis

### Backend Services
- **Storage Layer**: Abstracted storage interface with PostgreSQL database implementation
- **Question Service**: JSON-based question loading with category filtering
- **Session Management**: Quiz session creation and retrieval with persistent storage

### UI Components
- **Question Card**: Quiz question display with answer selection
- **Quiz Navigation**: Visual question progress and direct navigation
- **Comprehensive UI Kit**: 30+ Radix UI components for consistent UX

## Data Flow

### Quiz Taking Flow (Updated January 2025)
1. User selects category from home page
2. User enters their name before starting quiz
3. System randomly selects one of 5 predefined question sets (A-E) for the chosen paper
4. Each set contains exactly 5 questions, one from each subject within the paper
5. Quiz runs for 1 minute with immediate answer feedback and subject tags
6. Navigation includes Next/Previous/Submit buttons for better user control
7. Real-time progress tracking and question navigation
8. Session saved to database with player name upon completion
9. Results page shows performance analysis and leaderboard link

### Recent Improvements
- ✓ Added name entry screen before quiz starts
- ✓ Reduced to 5 questions with 1-minute time limit
- ✓ Immediate visual feedback (green/red) on answer selection
- ✓ Explanation display after selecting answers
- ✓ Leaderboard system showing scores and completion times
- ✓ Removed skip button, simplified navigation
- ✓ Database integration: Migrated from in-memory to PostgreSQL storage (January 2025)
- ✓ Expanded question bank: 20 questions per category with proper Fisher-Yates shuffling (January 2025)
- ✓ Restructured to 5 different question sets per paper with subject-specific organization (January 2025)
- ✓ Added Next/Previous/Submit navigation buttons in quiz interface (January 2025)
- ✓ Each question now belongs to a specific subject within the paper (January 2025)

### Data Storage
- **Question Sets**: Organized in `server/data/question-sets.json` with 5 predefined sets per paper
- **Subject Organization**: Each question belongs to a specific subject within the paper
- **Set Structure**: Each paper has 5 different question sets (A, B, C, D, E) with unique sequences
- **Subject Coverage**: Every set contains exactly 5 questions, one from each subject area
- Quiz sessions with player names persisted to PostgreSQL database
- Leaderboard API endpoint with category filtering
- PostgreSQL database with Drizzle ORM for production
- Shared TypeScript types ensure consistency

## External Dependencies

### Core Libraries
- **React Ecosystem**: React 18, React DOM, React Hook Form
- **UI Framework**: Radix UI primitives, shadcn/ui components
- **Database**: Drizzle ORM, Neon Database serverless driver
- **Utilities**: Zod validation, date-fns, class-variance-authority

### Development Dependencies
- **Build Tools**: Vite, ESBuild, TypeScript compiler
- **Styling**: Tailwind CSS, PostCSS, Autoprefixer
- **Replit Integration**: Runtime error overlay, cartographer plugin

## Deployment Strategy

### Development Environment
- Frontend: Vite dev server with HMR
- Backend: tsx with hot reload
- Database: Environment-based DATABASE_URL configuration

### Production Build
- Frontend: Vite build to dist/public
- Backend: ESBuild bundle to dist/index.js
- Database: Drizzle migrations via drizzle-kit push
- Single Node.js process serving both static files and API

### Environment Configuration
- Development: NODE_ENV=development with local database
- Production: NODE_ENV=production with Neon Database
- Database migrations handled via Drizzle Kit
- Static file serving integrated into Express server

### Key Architectural Decisions
- **Monorepo Structure**: Single repository with client/server/shared folders for code reuse
- **Type Safety**: Shared TypeScript types between frontend and backend
- **Database Abstraction**: Storage interface allows switching between in-memory and PostgreSQL
- **Static Questions**: JSON files for questions enable easy content management
- **Component Architecture**: Radix UI + shadcn/ui for accessible, customizable components