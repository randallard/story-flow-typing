---
layout: page
title: Project Plan & Status
nav_order: 2
permalink: /docs/project-plan-and-status/
---

# Story Flow Typer: Project Plan & Status

This document serves as a living record of our project plan, current status, and progress towards completing the Story Flow Typer application with Expo, Gel, and cross-platform deployment.

## Current Status

**Phase**: Development Environment Setup  
**Current Task**: Planning project initialization  
**Last Updated**: June 13, 2025

## Project Vision

To create a typing practice app that combines creative storytelling with skill development, using a felt board/puppet show aesthetic where users write continuously as visual scenes evolve around them. Unlike traditional typing trainers, Story Flow Typer transforms practice into engaging creative writing sessions.

## Architecture Overview

### Technical Stack
- **Frontend**: Expo (React Native) with TypeScript for cross-platform development
- **Database & Auth**: Gel (EdgeDB-based graph-relational) with Google OAuth
- **State Management**: Zustand for lightweight, TypeScript-friendly state handling
- **Development**: WSL2 + Ubuntu with VS Code and Expo CLI
- **Animation**: Binary format encoded in shareable URLs (<8KB)
- **Testing**: TDD with 4-stage pipeline (mocks → local Gel → staging → production)

### Key Design Decisions
- **Cross-platform asymmetry**: Browser for full typing experience, mobile for story replay/sharing
- **URL-based sharing**: Binary animation format in 8KB URLs eliminates server storage complexity
- **TDD methodology**: Red-green-refactor cycles with comprehensive testing at each stage
- **Gel Cloud environments**: Local → staging → production deployment pipeline
- **Minimal data storage**: Privacy-first approach with user-controlled story sharing

## Development Approach

This project follows **Test-Driven Development (TDD)** with:
- **Red-Green-Refactor cycles** for all features
- **4-stage testing pipeline** ensuring quality at each level
- **2-week sprint cadence** for consistent delivery
- **Binary animation innovation** as core technical differentiator
- **Cross-platform sharing** without authentication barriers

## User Flow

1. **Authentication**: Users sign in via Google OAuth through Gel Auth
2. **Session Setup**: Choose 5-25 minute typing session with felt board scenes
3. **Creative Typing**: Write continuously as scenes evolve, with optional skill practice hints
4. **Story Sharing**: Generate <8KB URL containing full animation + text for cross-platform replay
5. **Progress Tracking**: WPM, accuracy, and session endurance improvements over time

## Development Roadmap

### Phase 1: Development Environment Setup (3-4 days)

#### 1.1 WSL2 + Core Tools ⬜
- [ ] Verify WSL2 with Ubuntu 24.04 LTS installation
- [ ] Install Node.js via nvm (LTS version)
- [ ] Configure Git with proper line ending handling
- [ ] Install VS Code extensions for WSL2 development

#### 1.2 Expo Development Environment ⬜
- [ ] Install Expo CLI and EAS CLI globally
- [ ] Configure WSL2 networking for iPhone testing
- [ ] Set up Windows Firewall rules for Expo ports
- [ ] Create port forwarding scripts for device connectivity
- [ ] Test basic Expo app on iPhone via Expo Go

#### 1.3 Gel Database Setup ⬜
- [ ] Install Gel CLI in WSL2 environment
- [ ] Create local Gel project and configure schema
- [ ] Set up Gel Auth extension for Google OAuth
- [ ] Configure local, staging, and production environments
- [ ] Test database connectivity and basic queries

#### 1.4 Project Structure & Testing Foundation ⬜
```
~/projects/story-flow-typer/
├── mobile-app/           # Expo + React Native + TypeScript
├── gel-backend/          # Gel database schema and migrations
├── shared-types/         # TypeScript type definitions
├── testing/              # Test utilities and mocks
└── docs/                 # Project documentation
```
- [ ] Initialize Expo project with TypeScript template
- [ ] Configure Jest and React Native Testing Library
- [ ] Set up Zustand store structure
- [ ] Create basic project documentation

#### 1.5 TDD Workflow Setup ⬜
- [ ] Configure 4-stage testing environments
- [ ] Create mock services for offline development
- [ ] Set up local Gel instance for integration tests
- [ ] Configure GitHub Actions for staging deployment
- [ ] Document TDD red-green-refactor process

### Phase 2: Sprint 1 - Foundation & Authentication (2 weeks)

#### Sprint 1 Goal
Working Google OAuth authentication, basic 5-minute typing sessions, and URL-based story sharing with binary animation format.

#### 2.1 Authentication System (Days 1-3) ⬜

**TDD Cycle 1: Auth Store (Mocks)**
- [ ] **Red**: Write failing tests for Zustand auth store
- [ ] **Green**: Implement auth store with mock Google OAuth
- [ ] **Refactor**: Optimize state management and type safety

**TDD Cycle 2: Google OAuth Integration (Local Gel)**
- [ ] **Red**: Write failing integration tests for OAuth flow
- [ ] **Green**: Implement Gel Auth with Google OAuth provider
- [ ] **Refactor**: Handle auth errors and token refresh

**TDD Cycle 3: Auth UI (Staging)**
- [ ] **Red**: Write E2E tests for complete auth flow
- [ ] **Green**: Build login/logout screens with Gel's built-in UI
- [ ] **Refactor**: Improve UX and error handling

**TDD Cycle 4: Production Deploy (Production)**
- [ ] **Red**: Write production verification tests
- [ ] **Green**: Deploy auth system to production
- [ ] **Refactor**: Monitor and optimize performance

#### 2.2 Core Typing Experience (Days 4-8) ⬜

**TDD Cycle 1: Session Management (Mocks)**
- [ ] **Red**: Write failing tests for typing session state
- [ ] **Green**: Implement 5-minute session timer and WPM calculation
- [ ] **Refactor**: Optimize real-time metrics and accuracy tracking

**TDD Cycle 2: Basic Animation System (Local Gel)**
- [ ] **Red**: Write failing tests for scene transitions
- [ ] **Green**: Create placeholder felt board animations
- [ ] **Refactor**: Smooth animation performance and timing

**TDD Cycle 3: Session Storage (Staging)**
- [ ] **Red**: Write failing tests for session persistence
- [ ] **Green**: Save basic session data to Gel database
- [ ] **Refactor**: Optimize database queries and data structure

#### 2.3 Binary Animation & URL Sharing (Days 9-14) ⬜

**TDD Cycle 1: Binary Format (Mocks)**
- [ ] **Red**: Write failing tests for animation encoding/decoding
- [ ] **Green**: Implement binary format with <8KB target
- [ ] **Refactor**: Optimize compression and data structure

**TDD Cycle 2: URL Generation (Local Gel)**
- [ ] **Red**: Write failing tests for URL sharing
- [ ] **Green**: Generate shareable URLs with animation data
- [ ] **Refactor**: Handle edge cases and validation

**TDD Cycle 3: Mobile Replay (Staging)**
- [ ] **Red**: Write failing tests for cross-platform replay
- [ ] **Green**: Build mobile replay without authentication
- [ ] **Refactor**: Optimize mobile performance and UX

**TDD Cycle 4: Production Sharing (Production)**
- [ ] **Red**: Write failing tests for production URL sharing
- [ ] **Green**: Deploy complete sharing system
- [ ] **Refactor**: Monitor URL performance and user feedback

#### Sprint 1 Acceptance Criteria
- [ ] Google OAuth authentication working in production
- [ ] 5-minute typing sessions with real-time WPM/accuracy
- [ ] Basic felt board scene transitions (placeholder animations)
- [ ] Binary animation format generating URLs <8KB
- [ ] Mobile replay of shared stories without login
- [ ] All tests passing at each TDD stage
- [ ] Production deployment pipeline functional

### Phase 3: Sprint 2 - Enhanced UI & Rich Animations (2 weeks)

#### Sprint 2 Goal
Custom felt board authentication UI, richer scene animations, variable session lengths, and story snippet curation.

#### 3.1 Custom Felt Board UI (Days 1-5) ⬜
- [ ] Design felt board component library
- [ ] Replace Gel's built-in auth UI with custom styling
- [ ] Implement animated scene transitions
- [ ] Create rich visual storytelling elements

#### 3.2 Enhanced Session Experience (Days 6-10) ⬜
- [ ] Variable session lengths (5-25 minutes)
- [ ] Break reminders with theatrical transitions
- [ ] Skill practice hints (punctuation, numbers, special chars)
- [ ] Improved binary format for richer animations

#### 3.3 Story Management (Days 11-14) ⬜
- [ ] Story snippet highlights on welcome screen
- [ ] Basic curation system for favorite moments
- [ ] Enhanced replay experience with better UX
- [ ] Performance optimization for longer sessions

#### Sprint 2 Acceptance Criteria
- [ ] Custom felt board aesthetic throughout app
- [ ] Variable session lengths with break management
- [ ] Rich scene animations within 8KB URL limit
- [ ] Story highlight system functional
- [ ] Staging environment fully operational

### Phase 4: Sprint 3 - Advanced Features & Production Polish (2 weeks)

#### Sprint 3 Goal
Sophisticated skill practice integration, progress analytics, full CI/CD pipeline, and production-ready performance.

#### 4.1 Advanced Skill Practice (Days 1-5) ⬜
- [ ] Smart skill practice suggestions in scenes
- [ ] Targeted improvement tracking
- [ ] Adaptive difficulty based on user performance
- [ ] Session endurance building features

#### 4.2 Progress Analytics (Days 6-10) ⬜
- [ ] Comprehensive WPM and accuracy tracking
- [ ] Session completion rate analytics
- [ ] Skill-specific improvement metrics
- [ ] Visual progress charts and motivation

#### 4.3 Production Pipeline (Days 11-14) ⬜
- [ ] Complete CI/CD with automated testing
- [ ] Performance optimization and monitoring
- [ ] User feedback collection system
- [ ] Production deployment verification

#### Sprint 3 Acceptance Criteria
- [ ] Advanced skill practice seamlessly integrated
- [ ] Comprehensive progress tracking system
- [ ] Full automated deployment pipeline
- [ ] Production performance targets met (<2s session start, <100ms URL generation)

## Development Methodology: TDD Guidance

### Red-Green-Refactor Cycle
1. **Red**: Write a failing test that describes desired behavior
2. **Green**: Write minimal code to make the test pass
3. **Refactor**: Improve code quality while keeping tests green

### 4-Stage Testing Pipeline
1. **Mocks**: Fast unit tests with mocked dependencies
2. **Local Gel**: Integration tests with local database
3. **Staging**: E2E tests in staging environment
4. **Production**: Verification tests in production

### TDD Best Practices
- Write tests first, then implement features
- Keep test cycles short (15-30 minutes)
- Refactor frequently to maintain code quality
- Use descriptive test names that explain behavior
- Mock external dependencies for unit tests

*Ask for clarification on TDD practices, testing setup, or specific implementation details as needed.*

## Current Focus

Setting up the complete development environment including WSL2, Expo, and Gel CLI. This foundation is critical for enabling the TDD workflow and cross-platform development throughout the project.

### Immediate Next Steps
1. Complete WSL2 and Expo development environment setup
2. Install and configure Gel CLI with local database
3. Initialize Expo project with TypeScript and testing framework
4. Set up Zustand store structure and basic auth flow
5. Create project structure and TDD workflow documentation

## Estimated Timeline

**Total Duration**: 6-7 weeks
- Environment Setup: 3-4 days
- Sprint 1 (Auth + Basic Sessions): 2 weeks
- Sprint 2 (Enhanced UI + Rich Animations): 2 weeks  
- Sprint 3 (Advanced Features + Production): 2 weeks

## Success Metrics

### Sprint 1 Success Criteria
- TDD workflow established and documented
- Google OAuth working in production
- 5-minute typing sessions functional
- URL sharing with binary animation format
- <8KB URL generation verified
- Mobile replay without authentication

### Overall Project Success
- Cross-platform app working on browser and mobile
- Real-time typing metrics with <100ms accuracy
- Binary animation URLs consistently <8KB
- Story sharing engagement >70% success rate
- User session completion rate >80%
- Production deployment pipeline 99.9% reliable

## Technology Migration Notes

### From Gaming App to Story Flow Typer
- **Database**: Supabase → Gel (EdgeDB) for better TypeScript integration
- **State Management**: Various → Zustand for lightweight performance
- **Authentication**: Supabase Auth → Gel Auth with Google OAuth
- **Data Sharing**: Traditional → Binary format in URLs for privacy
- **Testing**: Basic → Comprehensive TDD with 4-stage pipeline

### Preserved Concepts
- WSL2 + Expo development environment
- Cross-platform React Native architecture
- TypeScript-first development approach
- Mobile-first responsive design
- User-centric experience design

## Risk Mitigation

### Technical Risks
- **8KB URL Limit**: Progressive fallback to cloud storage for complex sessions
- **Gel Learning Curve**: Start simple, extensive documentation, community support
- **Binary Format Complexity**: Iterative development with format versioning
- **Cross-platform Performance**: Early testing on multiple devices

### Development Risks
- **TDD Adoption**: Pair programming sessions, clear examples, incremental adoption
- **Sprint Scope**: Regular scope review, prioritize core features first
- **Environment Complexity**: Comprehensive setup documentation, automation scripts

## Open Questions

- How to handle offline typing sessions and sync when reconnected?
- Should we implement progressive enhancement for slower mobile devices?
- What analytics should we collect while respecting privacy-first approach?
- How to optimize binary format for different story types and lengths?
- Should we add collaborative features (shared stories, competitions)?

---

## Sprint Planning Notes

### Sprint 1 Focus Areas
- **Week 1**: Authentication system with TDD workflow
- **Week 2**: Typing sessions and binary animation sharing

### Sprint 2 Focus Areas  
- **Week 1**: Custom UI and enhanced animations
- **Week 2**: Variable sessions and story management

### Sprint 3 Focus Areas
- **Week 1**: Advanced features and skill practice
- **Week 2**: Production polish and deployment automation