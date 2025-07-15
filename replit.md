# Canteeno - Restaurant Ordering System

## Overview

This is a modern full-stack restaurant ordering application built for a campus canteen. The system allows users to browse menu items, add them to a cart, place orders, and track order status. It features a mobile-first design with a clean, intuitive interface optimized for quick ordering.

## Recent Changes (January 2025)
- ✓ Added PostgreSQL database integration with Neon serverless
- ✓ Enhanced menu item UI with quantity controls and visual feedback
- ✓ Implemented persistent order storage and history
- ✓ Added toast notifications for better user experience
- ✓ Seeded database with authentic Indian canteen menu items

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Styling**: Tailwind CSS with shadcn/ui component library
- **State Management**: React Context for cart state, TanStack React Query for server state
- **Routing**: Wouter (lightweight routing library)
- **Build Tool**: Vite with custom configuration for monorepo structure

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript with ES modules
- **Database**: PostgreSQL with Drizzle ORM
- **Database Provider**: Neon Database (serverless PostgreSQL)
- **Storage**: Database-backed storage with seeded sample data

### Project Structure
- **Monorepo**: Single repository with separate client, server, and shared directories
- **Client**: React frontend located in `/client`
- **Server**: Express backend located in `/server`
- **Shared**: Common schemas and types in `/shared`

## Key Components

### Database Schema (Drizzle ORM)
- **menu_items**: Stores restaurant menu with prices, categories, images, ratings
- **orders**: Stores customer orders with items (JSON), totals, status tracking
- **Schema Validation**: Zod schemas for type-safe data validation

### Frontend Features
- **Menu Browsing**: Category-based filtering, search functionality
- **Shopping Cart**: Persistent cart using localStorage, quantity management
- **Order Placement**: Form validation, order confirmation
- **Order Tracking**: Real-time status updates, estimated delivery times
- **Mobile-First UI**: Responsive design optimized for mobile devices

### Backend API Endpoints
- `GET /api/menu-items` - Retrieve all menu items
- `GET /api/menu-items/category/:category` - Filter by category
- `GET /api/menu-items/search` - Search menu items
- `POST /api/orders` - Create new order
- `GET /api/orders` - Retrieve order history

### UI Components
- **shadcn/ui**: Comprehensive component library with Radix UI primitives
- **Custom Components**: Menu-specific components for cart, order status, navigation
- **Toast Notifications**: User feedback for actions and errors
- **Loading States**: Skeleton loaders and loading indicators

## Data Flow

1. **Menu Loading**: Client fetches menu items from API, cached with React Query
2. **Cart Management**: Items added to cart, persisted in localStorage, managed via React Context
3. **Order Placement**: Cart contents validated, sent to API, order created in database
4. **Order Tracking**: Order status displayed, updates shown to user
5. **State Synchronization**: React Query handles cache invalidation and background updates

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: Serverless PostgreSQL client
- **drizzle-orm**: Type-safe SQL ORM
- **@tanstack/react-query**: Server state management
- **wouter**: Lightweight routing
- **zod**: Schema validation

### UI Dependencies
- **@radix-ui/***: Accessible UI primitives
- **tailwindcss**: Utility-first CSS framework
- **class-variance-authority**: Component variant management
- **lucide-react**: Icon library

### Development Tools
- **vite**: Build tool and dev server
- **typescript**: Type safety
- **tsx**: TypeScript execution for development

## Deployment Strategy

### Development
- **Vite Dev Server**: Hot module replacement for frontend
- **tsx**: Direct TypeScript execution for backend
- **Concurrent Development**: Frontend and backend run simultaneously

### Production Build
- **Frontend**: Vite builds optimized static assets
- **Backend**: esbuild bundles server code for Node.js
- **Static Serving**: Express serves built frontend assets
- **Environment Variables**: Database URL and other config via environment

### Database Management
- **Migrations**: Drizzle Kit handles schema migrations
- **Schema**: PostgreSQL tables for menu items and orders
- **Data**: Seeded with sample Indian canteen menu items
- **Connection**: Neon Database serverless PostgreSQL

The application is designed to be easily deployable to platforms like Replit, with automatic database provisioning and environment setup.