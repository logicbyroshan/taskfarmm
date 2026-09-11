<div align="center">

# 🏛️ TaskFarmm Architecture & Codebase Structure

### *System Design, Directory Hierarchy, and Module Responsibilities*

[![Django 5.2](https://img.shields.io/badge/Django-5.2+-092E20?style=flat-square&logo=django&logoColor=white)](https://www.djangoproject.com/)
[![REST API v1](https://img.shields.io/badge/API-REST_v1_%2B_JWT-blue?style=flat-square)](API.md)
[![Voice AI Engine](https://img.shields.io/badge/Engine-Voice_Automation-2563eb?style=flat-square)](#-domain-services-todo)

</div>

---

## 📁 Repository Overview

```
TaskFarmm/
├── .github/                         # GitHub Community, CI & Issue Templates
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md           # Bug report template
│   │   └── feature_request.md      # Feature proposal template
│   └── pull_request_template.md     # Pull request checklist
├── config/                          # Django Core Project Configuration
│   ├── asgi.py                      # ASGI entry point for asynchronous servers
│   ├── settings.py                  # Production & Development environment settings
│   ├── urls.py                      # Master URL routing (/api/v1/, admin, session app)
│   └── wsgi.py                      # Production WSGI entry point (Gunicorn)
├── static/                          # Pure CSS Design System & JavaScript
│   └── todo/
│       ├── css/
│       │   ├── base.css             # Root variables, reset, zero-scrollbar engine
│       │   ├── style.css            # Dark mode tokens, headers, dropdown stacking
│       │   ├── my-tasks.css         # Task card styling & filter layout
│       │   ├── task-categories.css  # Project board cards & progress metrics
│       │   └── settings.css         # Profile & preferences forms
│       ├── js/
│       │   ├── script.js            # 60fps Wave canvas, modals, search, voice controller
│       │   └── sw.js                # Service worker for offline asset caching
│       └── images/
│           └── logo.png             # TaskFarmm brand mark
├── templates/                       # HTML5 Django Semantic Templates
│   ├── todo/
│   │   ├── base.html                # Master layout, navbar, ambient canvas, drawer
│   │   ├── index.html               # Main dashboard with live status grid & metrics
│   │   ├── kanban.html              # 6-column drag-and-drop Kanban board
│   │   ├── manage-projects.html     # Project workspace management
│   │   ├── manage_team.html         # Sub-user team accounts management
│   │   ├── ai_assistant.html        # ChatGPT-style AI Workspace
│   │   ├── settings.html            # Profile, notification switches, JSON/CSV export
│   │   ├── auth/                    # Dedicated OLED login, register, Google SSO
│   │   └── components/              # Modular templates (task_card, project_card, modals)
│   └── emails/                      # Responsive OLED HTML Email Templates
│       ├── base_email.html          # Email shell with glowing sapphire CTA button
│       ├── task_assigned.html       # Task assignment alert
│       ├── task_comment.html        # Comment notification
│       ├── task_due_soon.html       # Deadline reminder
│       ├── task_completed.html      # Completion confirmation
│       ├── project_shared.html      # Project invitation
│       └── welcome.html             # Onboarding email
├── todo/                            # Core Application Package
│   ├── admin.py                     # Django admin registrations
│   ├── autocorrect.py               # OpenHinglish multi-lingual spell correction pipeline
│   ├── context_processors.py        # Template context injectors
│   ├── forms.py                     # ModelForms for Tasks, Projects, and Users
│   ├── google_auth.py               # RFC 6749 Google OAuth 2.0 & GIS handler
│   ├── middleware.py                # Security & session bridge middleware
│   ├── models.py                    # Task, Attachment, Comment, Category, Notification, UserProfile
│   ├── notifications.py             # Enterprise Notification & Exponential Backoff Queue
│   ├── services.py                  # Domain business logic & data aggregation services
│   ├── serializers.py               # DRF Serializers for REST API v1
│   ├── api_auth.py                  # JWT session bridge & verification
│   ├── urls.py                      # Web application routes
│   ├── api/                         # REST API v1 Package (DRF ViewSets & Routers)
│   └── tests/                       # Automated Test Suite (89 tests)
├── .env.example                     # Environment configuration template
├── API.md                           # Complete REST API v1 reference
├── CONTRIBUTING.md                  # Contribution guidelines
├── LICENSE                          # MIT License
├── README.md                        # Flagship visual open-source documentation
└── SETUP.md                         # Deployment and setup guide
```

---

## 🧩 Architectural Layers

| Layer | Technologies | Responsibilities |
| :--- | :--- | :--- |
| **Presentation (UI/UX)** | Vanilla CSS, HTML5, Alpine.js, HTMX | Pure OLED Black theme, live drag-and-drop, zero-scrollbar viewport, ambient wave animation. |
| **Voice & NLP Pipeline** | Web Speech API, OpenHinglish | Real-time voice-to-task recognition, Hinglish normalization, entity extraction (priority, due dates). |
| **API & Controllers** | Django 5.2, Django REST Framework | REST API v1 with JWT authentication, throttling, search, session views, OAuth callback. |
| **Domain Services** | Python 3.11+ Service Classes | Task lifecycle orchestration, project analytics, sub-user permissions, email delivery. |
| **Persistence & Queue** | PostgreSQL / SQLite, Notification Queue | Relational schema, attachment storage, exponential backoff notification dispatch. |
