---
layout: page
title: Requirements
nav_order: 2
permalink: /docs/requirements/
---
# Story Flow Typer - Project Requirements

## Project Overview

**Story Flow Typer** is a typing practice app that combines creative storytelling with skill development using a felt board/puppet show aesthetic. Users write continuously as visual scenes evolve around them, making typing practice engaging rather than repetitive.

### Core Architecture
- **Browser**: Full typing experience with authentication, sessions, and progress tracking
- **Mobile**: Story replay/sharing viewer (no authentication required)
- **Database**: Gel (graph-relational database) with built-in authentication
- **State Management**: Zustand for lightweight, TypeScript-friendly state handling
- **Framework**: Expo for cross-platform development
- **Data Sharing**: Binary animation format encoded in URLs (8KB limit)

## Technical Stack

### Frontend
- **Framework**: Expo (React Native for cross-platform)
- **Language**: TypeScript
- **State Management**: Zustand
- **Navigation**: React Navigation
- **Animation**: React Native Animated API / Lottie
- **Testing**: Jest + React Native Testing Library

### Backend & Database
- **Database**: Gel (EdgeDB-based graph-relational database)
- **Authentication**: Gel Auth with Google OAuth
- **Cloud**: Gel Cloud for staging/production
- **Local Development**: Local Gel instance via CLI

### Development & Deployment
- **Version Control**: Git with GitHub
- **Development Environment**: WSL2 + Expo CLI
- **Testing Strategy**: TDD (Red-Green-Refactor)
- **Deployment**: 
  - Browser: Vercel (integrated with Gel Cloud)
  - Mobile: Expo EAS (for app stores eventually)
- **CI/CD**: GitHub Actions

## Sprint 1: Foundation & Google OAuth

### User Stories

**Authentication**
- As a new user, I want to sign in with Google so I can quickly start practicing without creating another account
- As a returning user, I want automatic login so I can resume my typing practice immediately
- As a user, I want to see Gel's built-in auth UI initially, with plans for custom styling

**Core Typing Experience**
- As a user, I want to start a basic 5-minute typing session so I can begin practicing
- As a user, I want to see my WPM and accuracy in real-time so I know how I'm performing
- As a user, I want simple scene transitions so I can experience the felt board aesthetic

**Story Sharing**
- As a user, I want to get a shareable URL after my session so others can watch my typing story
- As a mobile user, I want to open shared URLs and watch typing stories without needing an account

### Technical Requirements

#### Authentication Setup
- Configure Gel Auth extension in schema
- Set up Google OAuth provider in Gel Auth admin UI
- Implement Zustand auth store with token management
- Create auth navigation flow (signed in/out states)

#### Database Schema (Initial)
```edgeql
# Initial Gel Auth setup
using extension auth;

type User {
  required property email -> str;
  property created_at -> datetime {
    default := datetime_current();
  }
}

type TypingSession {
  required property duration -> duration;
  required property wpm -> int16;
  required property accuracy -> float32;
  required property created_at -> datetime {
    default := datetime_current();
  }
  required link user -> User;
}
```

#### State Management Structure
```typescript
// Auth Store
interface AuthState {
  token: string | null;
  user: User | null;
  isAuthenticated: boolean;
  login: (token: string) => void;
  logout: () => void;
}

// Session Store
interface SessionState {
  currentSession: TypingSession | null;
  isActive: boolean;
  startTime: Date | null;
  animationData: Uint8Array;
  wpm: number;
  accuracy: number;
}
```

#### Animation Data Format
- **Binary Structure**: Fixed header + variable animation events
- **Compression**: Target <8KB per 5-10 minute session
- **Encoding**: Base64 for URL embedding
- **Format**:
  ```
  Header (32 bytes):
  - Version (4 bytes)
  - Duration (4 bytes) 
  - Event count (4 bytes)
  - Text length (4 bytes)
  - Reserved (16 bytes)
  
  Events (variable):
  - Timestamp (4 bytes)
  - Event type (1 byte)
  - Data (variable)
  ```

#### Testing Requirements

**Unit Tests (Mocks)**
- Auth store actions and state updates
- Animation data encoding/decoding
- URL generation and parsing
- Session calculations (WPM, accuracy)

**Integration Tests (Local Gel)**
- Google OAuth flow end-to-end
- Database operations (create user, save session)
- Auth token refresh and validation

**E2E Tests (Production)**
- Complete user journey: login → session → share
- Cross-platform URL sharing (browser → mobile)
- Performance testing with 8KB URL limits

### Acceptance Criteria

#### Authentication
- [ ] User can sign in with Google using Gel's built-in UI
- [ ] App remembers authentication state between sessions
- [ ] User can sign out and clear all local data
- [ ] Auth errors are handled gracefully with user feedback

#### Typing Experience
- [ ] User can start a 5-minute typing session
- [ ] Real-time WPM and accuracy calculations are accurate
- [ ] Basic scene transitions work smoothly (placeholder animations)
- [ ] Session ends automatically after 5 minutes

#### Story Sharing
- [ ] Session generates shareable URL under 8KB
- [ ] URL contains all data needed for replay
- [ ] Mobile app can parse URL and replay session
- [ ] Shared stories play without authentication

#### Quality & Performance
- [ ] All tests pass (unit, integration, E2E)
- [ ] App deploys successfully to production
- [ ] URLs work across different browsers and mobile apps
- [ ] Session data encoding/decoding is under 100ms

## Sprint 2: Custom UI & Enhanced Sessions

### User Stories

**Enhanced Authentication UI**
- As a user, I want the login screen to match the felt board aesthetic so the experience feels cohesive
- As a user, I want smooth transitions from auth screens to the main app

**Improved Typing Experience**
- As a user, I want richer scene animations so the experience feels more engaging
- As a user, I want to choose session length (5-25 minutes) so I can practice according to my available time
- As a user, I want break reminders during longer sessions so I can practice safely

**Story Management**
- As a user, I want to see highlights of my recent stories on the welcome screen so I feel motivated
- As a user, I want basic story snippet curation so I can appreciate my creative output

### Technical Requirements

#### Custom Authentication UI
- Design felt board-themed login components
- Implement custom Google OAuth button with Gel Auth backend
- Create animated transitions between auth states
- Maintain accessibility standards

#### Enhanced Animation System
- Expand binary format for richer scene data
- Implement scene transition engine
- Create felt board visual components library
- Optimize animations for mobile replay

#### Staging Environment Setup
- Configure Gel Cloud staging branch
- Set up GitHub Actions for staging deployments
- Implement environment-specific configurations
- Create staging-to-production promotion workflow

## Sprint 3: Full Pipeline & Advanced Features

### User Stories

**Production-Ready Experience**
- As a user, I want sophisticated scene changes that inspire my storytelling
- As a user, I want smart skill practice suggestions integrated naturally into scenes
- As a user, I want progress tracking across multiple sessions

**Team Collaboration**
- As a developer, I want full CI/CD pipeline so deployments are safe and automated
- As a team member, I want staging environment for testing before production

### Technical Requirements

#### Complete Testing Pipeline
- Comprehensive mock suite for all user interactions
- Local Gel integration tests with realistic data
- Staging environment validation
- Production deployment verification

#### Advanced Features
- Skill practice integration (punctuation, numbers, special characters)
- Progress tracking and analytics
- Session endurance building
- Story snippet curation and highlights

## Development Environment Setup

### Prerequisites
- WSL2 with Ubuntu
- Node.js 18+ and npm/yarn
- Expo CLI
- Gel CLI
- Git and GitHub CLI

### Initial Setup Commands
```bash
# Project initialization
git clone <repository>
cd story-flow-typer
npm install

# Gel setup
npx gel project init
npx gel ui  # Configure auth in admin panel

# Development
npm run dev          # Start Expo dev server
npm run test         # Run test suite
npm run test:watch   # Run tests in watch mode

# Database
npx gel migrate      # Apply migrations
npx gel ui           # Open database admin
```

### Environment Variables
```bash
# .env.local
EXPO_PUBLIC_GEL_DSN=<gel-connection-string>
EXPO_PUBLIC_GOOGLE_OAUTH_CLIENT_ID=<client-id>
```

## Deployment Strategy

### Environments
1. **Local**: Developer machines with local Gel instances
2. **Staging**: Gel Cloud staging branch for integration testing
3. **Production**: Gel Cloud main branch for live users

### Deployment Pipeline
```yaml
# GitHub Actions workflow
name: Deploy
on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  test:
    - Unit tests with mocks
    - Integration tests with local Gel
    
  staging-deploy:
    if: branch == 'develop'
    - Deploy to Gel Cloud staging
    - Run E2E tests
    
  production-deploy:
    if: branch == 'main'
    - Deploy to Gel Cloud production
    - Post-deployment verification
```

## Data Privacy & Performance

### Privacy Considerations
- Minimal data storage (only auth and basic session metrics)
- Story content in URLs (user controls sharing)
- GDPR compliance through data minimization
- Clear data retention policies

### Performance Targets
- Session start: <2 seconds
- URL generation: <100ms
- Mobile replay startup: <1 second
- Animation playback: 60fps
- URL size: <8KB for 10-minute sessions

## Success Metrics

### Sprint 1 Goals
- [ ] Working authentication with Google OAuth
- [ ] Basic typing sessions with sharing
- [ ] Production deployment pipeline
- [ ] Test-driven development established

### Future Metrics
- User session completion rate >80%
- Average session length progression
- Story sharing engagement
- Cross-platform replay success rate

## Risk Mitigation

### Technical Risks
- **8KB URL Limit**: Fallback to cloud storage for longer sessions
- **Mobile Performance**: Progressive enhancement for older devices
- **Gel Learning Curve**: Start with simple queries, expand gradually

### Business Risks
- **User Adoption**: Focus on seamless onboarding experience
- **Development Velocity**: Maintain test coverage to prevent regressions
- **Scope Creep**: Stick to MVP features for initial sprints

---

## Next Steps

1. **Sprint Planning**: Break down Sprint 1 stories into detailed tasks
2. **Technical Setup**: Initialize Expo project with Gel integration
3. **Design System**: Create felt board component library
4. **Testing Framework**: Establish TDD workflow and CI/CD pipeline

This requirements document serves as the foundation for Story Flow Typer development, ensuring we maintain focus on user value while building robust, testable, and scalable architecture.