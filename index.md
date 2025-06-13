---
layout: home
title: Home
nav_order: 1
permalink: /
---

# Story Flow Typer
{: .fs-9 }

A typing practice app that combines creative storytelling with skill development, using a felt board/puppet show aesthetic where users write continuously as visual scenes evolve around them.
{: .fs-6 .fw-300 }

[Project Summary]({{ '/docs/project-summary' | relative_url }}){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[View Requirements]({{ '/docs/requirements' | relative_url }}){: .btn .fs-5 .mb-4 .mb-md-0 .mr-2 }

---

## What Makes Story Flow Typer Different
{: .fs-7 }

Unlike traditional typing trainers that rely on repetitive drills, Story Flow Typer transforms practice into **continuous creative writing** sessions. Users type stories while beautiful scenes evolve around them, naturally incorporating skill practice elements like punctuation, numbers, and special characters.

### Key Features
{: .fs-5 }

**🎭 Theatrical Experience**
: Sessions follow narrative arc pacing with natural scene transitions and break points

**📱 Cross-Platform Sharing**  
: Stories are encoded in shareable URLs - no login required for mobile replay

**📊 Smart Progress Tracking**
: Focus on WPM improvement, accuracy trends, and targeted skill development

**🎨 Felt Board Aesthetic**
: Warm, engaging visuals that feel creative rather than clinical

---

## Current Project Status
{: .fs-6 }

**Phase:** Requirements & Architecture Complete ✅  
**Next:** Sprint 1 Implementation (Google OAuth + Basic Sessions)  
**Tech Stack:** Expo + Gel + Zustand + TypeScript  

### Architecture Highlights
- **Browser:** Full typing experience with authentication and progress tracking
- **Mobile:** Story replay/sharing viewer (no authentication required) 
- **Data:** Binary animation format in 8KB shareable URLs
- **Testing:** TDD methodology (mocks → local Gel → production)

[View Detailed Requirements]({{ '/docs/project-requirements' | relative_url }}){: .btn .btn-outline .fs-4 .mb-4 .mb-md-0 .mr-2 }

---

## Documentation Overview
{: .fs-6 }

This documentation chronicles the collaborative development of Story Flow Typer, showcasing AI-assisted application design and implementation.

### 📋 Project Documentation
{: .fs-5 }

<div class="code-example" markdown="1">

| Document | Purpose | Status |
|:---------|:--------|:-------|
| [Project Summary]({{ '/docs/project-summary' | relative_url }}) | Core concept, tech stack, and feature overview | ✅ Complete |
| [User Stories]({{ '/docs/user-stories' | relative_url }}) | Detailed user experience requirements | ✅ Complete |
| [Project Requirements]({{ '/docs/project-requirements' | relative_url }}) | Technical specifications and sprint planning | ✅ Complete |
| [Project Plan & Status]({{ '/docs/project-plan-and-status' | relative_url }}) | Current progress and milestones | 🚧 In Progress |

</div>

### 🏗️ Technical Foundation
{: .fs-5 }

**Target Audience:** Keyboard-literate users wanting to break through speed plateaus  
**Session Structure:** 5-25 minutes with adaptive storytelling and skill integration  
**Data Philosophy:** Minimal storage, maximum user control over their creative output  

---

## Latest Development Update
{: .fs-6 }

{% assign latest_entry = site.html_pages | where: "parent", "journal" | sort: "date" | reverse | first %}
{% if latest_entry %}

### [{{ latest_entry.title }}]({{ latest_entry.url | relative_url }})
{: .fs-5 }

**{{ latest_entry.date | date: "%B %d, %Y" }}**
{: .fs-3 .text-grey-dk-000 }

Today we took the Story Flow Typer concept from brainstorming and transformed it into a concrete, actionable project plan with comprehensive technical architecture and sprint-by-sprint implementation roadmap.

**Key Accomplishments:**
- ✅ Google OAuth authentication strategy with Gel Auth
- ✅ Zustand state management architecture  
- ✅ Binary animation format for 8KB URL sharing
- ✅ TDD testing strategy (mocks → local → production)
- ✅ Cross-platform deployment pipeline design

[Read Full Update]({{ latest_entry.url | relative_url }}){: .btn .btn-primary .fs-4 .mb-4 .mb-md-0 .mr-2 }

{% else %}

### Development Journal Coming Soon
{: .fs-5 }

Development journal entries will appear here as the project progresses, documenting the AI-assisted development process and technical decisions.

{% endif %}

[View All Journal Entries]({{ '/docs/journal' | relative_url }}){: .btn .fs-4 .mb-4 .mb-md-0 .mr-2 }

---

## Quick Navigation
{: .fs-6 }

<div class="code-example" markdown="1">

**🚀 Get Started**
- [Project Summary]({{ '/docs/project-summary' | relative_url }}) - Understand the vision
- [User Stories]({{ '/docs/user-stories' | relative_url }}) - See user experience flows  
- [Technical Requirements]({{ '/docs/project-requirements' | relative_url }}) - Review implementation plan

**📊 Track Progress**  
- [Journal]({{ '/docs/journal' | relative_url }}) - Development updates and insights
- [Project Status]({{ '/docs/project-plan-and-status' | relative_url }}) - Current milestones

**🛠️ Technical Details**
- Authentication: Gel Auth with Google OAuth
- Frontend: Expo (React Native) with TypeScript
- State: Zustand for lightweight state management
- Testing: Jest + React Native Testing Library (TDD)

</div>

---

## About This Documentation
{: .fs-5 .text-grey-dk-000 }

This site documents the collaborative development of Story Flow Typer between a human developer and AI assistant, demonstrating modern application architecture, test-driven development, and AI-assisted software design. The project showcases how thoughtful requirements gathering and systematic technical questioning can transform creative concepts into production-ready applications.

**Development Philosophy:** Build something unique that respects users' creativity and intelligence, solving real problems through engaging experiences rather than repetitive drill work.