# TRD (Technical Requirement Document) - Complete Guide

## Table of Contents
1. What is TRD?
2. Purpose & Importance
3. Who Creates It?
4. When to Create It?
5. Complete Structure & Components
6. Real Examples & Code
7. Best Practices
8. Template & Checklist

---

## 1. WHAT IS TRD?

**TRD (Technical Requirement Document)** is a comprehensive specification that defines:
- **HOW** the system will be built technically
- **WHAT** architecture pattern will be used
- **WHICH** technologies will be used and why
- **HOW** components interact
- **WHAT** APIs will be exposed
- **HOW** data flows through system
- **WHAT** performance targets must be met

### Key Characteristics:
- **Architecture-focused** - system design and structure
- **Detailed** - implementation-level specifications
- **Technical audience** - for engineers, not stakeholders
- **Measurable** - includes performance targets, SLAs
- **Complete** - covers entire system top to bottom
- **Implementation-ready** - teams can code from this

### Who Reads TRD?
- Backend Engineers ✓
- Frontend Engineers ✓
- DevOps Engineers ✓
- Database Administrators ✓
- Security Engineers ✓
- QA Engineers ✓
- Solutions Architects ✓

---

## 2. PURPOSE & IMPORTANCE

### Why Is TRD Important?

**Technical Alignment:**
- All engineers understand system design
- Prevents miscommunication about how components interact
- Reduces rework and refactoring
- Enables parallel work on different components

**Quality & Performance:**
- Sets clear performance targets
- Enables testing strategy planning
- Identifies bottlenecks early
- Ensures non-functional requirements are met

**Scalability Planning:**
- Anticipates growth challenges
- Designs for scale from the beginning
- Reduces costly refactoring later
- Enables capacity planning

**Risk Mitigation:**
- Identifies technical risks early
- Plans for failure scenarios
- Ensures security by design
- Prevents architectural mistakes

**Knowledge Base:**
- Documents why decisions were made
- Helps onboard new team members
- Serves as reference during incidents
- Records historical technical context

**Resource Planning:**
- Helps estimate engineering effort
- Identifies skill requirements
- Enables timeline planning
- Supports budget allocation

---

## 3. WHO CREATES IT?

### Primary Owner: **Tech Lead / Solution Architect**

**Responsibilities:**
- Leads technical design process
- Evaluates technology options
- Documents architecture decisions
- Ensures alignment with business requirements
- Maintains and updates TRD

### Contributors:

**Senior Engineers:**
- Provide implementation insights
- Identify edge cases and gotchas
- Validate feasibility
- Suggest optimizations

**Database Architect:**
- Designs data model
- Plans indexing and optimization
- Defines replication strategy
- Plans for scale

**DevOps/Infrastructure:**
- Designs deployment architecture
- Plans infrastructure as code
- Defines CI/CD pipeline
- Plans monitoring and logging

**Security Engineer:**
- Defines authentication/authorization
- Plans encryption strategy
- Identifies security risks
- Plans security testing

**QA Lead:**
- Defines testing strategy
- Identifies test scenarios
- Plans performance testing
- Defines quality metrics

### Sign-off Required From:
- Tech Lead ✓
- Engineering Manager ✓
- Security Engineer ✓ (if security critical)
- DevOps Lead ✓ (if infrastructure critical)

---

## 4. WHEN TO CREATE IT?

### Timeline in Product Development:

```
PRD Approved → TRD Creation → Design Phase → Engineering → Testing

Week 3-4:       Week 4-6:        Week 7:      Week 8-12:    Week 12+:
- Tech lead     - Architecture   - Detailed   - Coding       - QA/Testing
- Evaluates    - API specs       design      - Unit tests   - Integration
  PRD           - Database       - Mockups    - Integration     tests
- Identifies     design          - Prototypes    tests      - Performance
  options       - Security       - Review         testing
- Drafts         design          - Approval
  TRD           - Approval
```

### Trigger Points for TRD Creation:

✅ **After PRD approval** (before design phase)
✅ **Before engineering starts coding**
✅ **For major new systems**
✅ **For significant architectural changes**
✅ **When scaling existing system**
✅ **For security-critical features**
✅ **For performance-sensitive systems**

### Timeline Considerations:

- **Simple feature:** 1-2 weeks TRD creation
- **Medium system:** 2-4 weeks TRD creation
- **Complex system:** 4-8 weeks TRD creation
- **Critical deadline:** Compress to 1-2 weeks (less detail)

---

## 5. COMPLETE STRUCTURE & COMPONENTS

### Section 1: COVER PAGE & METADATA

```markdown
# TECHNICAL REQUIREMENT DOCUMENT

**System/Feature:** [System Name]
**Version:** 1.0
**Document Owner:** [Tech Lead Name]
**Created Date:** [Date]
**Last Updated:** [Date]
**Status:** Draft / In Review / Approved / Active

**Key Stakeholders:**
- Tech Lead: [Name]
- Backend Lead: [Name]
- Frontend Lead: [Name]
- DevOps Lead: [Name]
- Security Lead: [Name]

**Approval Sign-off:**
- Tech Lead: [Signature] Date: ___
- Engineering Manager: [Signature] Date: ___
- Security: [Signature] Date: ___

**Distribution:**
- Internal: Engineering, DevOps, Security
- External: [External teams if applicable]

**Related Documents:**
- PRD: [Link to PRD]
- UI/UX: [Link to design]
- Backend Schema: [Link to database design]
```

---

### Section 2: EXECUTIVE SUMMARY

**Purpose:** 
Brief technical overview for busy engineering leaders

**Length:** 
1-2 pages

**Components:**

```markdown
## Executive Summary

### System Overview
[2-3 sentence description of system architecture]

"AutoReview is a web-based service that analyzes GitHub pull requests 
using machine learning to detect code quality, security, and performance 
issues. It's built as a microservices architecture with a React frontend, 
Node.js backend, Python ML service, and PostgreSQL database."

### Technology Stack
- **Frontend:** React 18, TypeScript, Tailwind CSS
- **Backend:** Node.js (Express), TypeScript
- **ML Service:** Python (PyTorch, FastAPI)
- **Database:** PostgreSQL 14 (primary), Redis (cache)
- **Infrastructure:** AWS (ECS, RDS, S3)
- **DevOps:** Docker, Kubernetes, GitLab CI/CD

### Architecture Pattern
- **Style:** Microservices (3 services)
- **Communication:** REST APIs + Message Queue (SQS)
- **Deployment:** Containerized (Docker) on Kubernetes

### Key Technical Decisions
1. **Microservices over Monolith**
   - Reason: ML service has different scaling needs than API
   - Trade-off: Complexity of distributed system

2. **PostgreSQL for primary data**
   - Reason: ACID compliance, complex queries needed
   - Trade-off: Scaling limited to read replicas

3. **Python for ML, Node.js for API**
   - Reason: Best-in-class libraries for each
   - Trade-off: Multiple languages to maintain

### Performance Targets
- API latency: < 200ms (p95)
- ML model inference: < 15 seconds (p95)
- Page load time: < 2 seconds
- Database query: < 100ms (p95)
- System uptime: 99.9% (< 45 min/month downtime)

### Scalability Approach
- Frontend: CDN + auto-scaling
- Backend API: Horizontal scaling (load balanced)
- ML service: Batch processing queue
- Database: Read replicas + caching

### Security Approach
- OAuth2 for authentication
- JWT tokens for authorization
- AES-256 encryption at rest
- TLS 1.3 encryption in transit
- WAF (Web Application Firewall) for DDoS protection

### Development Timeline
- Phase 1 (4 weeks): Core API + GitHub integration
- Phase 2 (4 weeks): ML model integration
- Phase 3 (2 weeks): Frontend + admin dashboard
- Phase 4 (2 weeks): Testing, optimization, deployment

### Key Risks
- ML model accuracy might not meet targets
- GitHub API rate limiting could be issue
- Scaling PostgreSQL might become bottleneck
- Security vulnerabilities in dependencies

### Resource Requirements
- Backend Engineers: 2 FTE
- ML Engineers: 1 FTE
- Frontend Engineers: 1 FTE
- DevOps: 0.5 FTE
- QA: 0.5 FTE
- Total: 5 FTE for 12 weeks

### Next Steps
1. Get approval from tech lead and security
2. Begin detailed API specification
3. Start database schema design
4. Set up development environment
5. Create spike tasks for risky areas
```

---

### Section 3: SYSTEM ARCHITECTURE

**Purpose:** 
Define overall system structure and how components interact

**Length:** 
2-3 pages with diagrams

**Components:**

```markdown
## System Architecture

### 3.1 High-Level Architecture Diagram

```
┌─────────────────────────────────────────────────────────────┐
│                        GitHub                                 │
│                     (External API)                            │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
    ┌────────────────────────────────────────────────────────┐
    │                   AWS CloudFront                        │
    │                   (CDN / Content)                       │
    └────────────────────┬───────────────────────────────────┘
                         │
    ┌────────────────────┴───────────────────────────────────┐
    │                   Application Tier                     │
    │  ┌──────────────────────────────────────────────────┐ │
    │  │  Load Balancer (AWS ALB)                         │ │
    │  └────────────────────┬─────────────────────────────┘ │
    │                       │                                │
    │  ┌────────────────────┴─────────────────────────────┐ │
    │  │  API Service Cluster (ECS, 3-10 instances)      │ │
    │  │  - Node.js / Express                            │ │
    │  │  - GitHub webhooks + REST API                   │ │
    │  │  - User management                              │ │
    │  └────────────────────┬─────────────────────────────┘ │
    │                       │                                │
    └───────────────────────┼────────────────────────────────┘
                            │
                ┌───────────┼───────────┐
                ▼           ▼           ▼
    ┌──────────────────┐  ┌────────────────────┐  ┌──────────────┐
    │   ML Service     │  │   Data Tier        │  │   Cache      │
    │ (ECS, Python)    │  │  (PostgreSQL)      │  │  (Redis)     │
    │ - PyTorch model  │  │  - Primary DB      │  │  - Sessions  │
    │ - Inference API  │  │  - Read replicas   │  │  - Cache     │
    │ - Async jobs     │  │  - Backups         │  │  - Queues    │
    └──────────────────┘  └────────────────────┘  └──────────────┘
                │
                ▼
    ┌──────────────────────────────────────────────────────┐
    │              Message Queue (SQS)                     │
    │  - PR analysis jobs                                  │
    │  - Webhook processing                               │
    │  - Slack notifications                              │
    └──────────────────────────────────────────────────────┘
```

### 3.2 Component Descriptions

**Frontend (React SPA)**
- Single-page application
- Served via CDN for fast load times
- Communicates with API via REST
- Handles authentication with OAuth2

**API Service (Node.js)**
- Exposes REST API for frontend
- Handles GitHub webhooks
- User management and authentication
- Configuration management
- Horizontal scaling via load balancer

**ML Service (Python)**
- Performs code analysis
- Uses trained PyTorch model
- Processes PRs asynchronously
- Returns findings to API service

**Database (PostgreSQL)**
- Primary relational database
- Read replicas for scaling reads
- Handles all structured data
- ACID compliance required

**Cache Layer (Redis)**
- Session storage
- Frequently accessed data caching
- Job queue for async processing
- Real-time notifications

**Message Queue (AWS SQS)**
- Decouples services
- Handles async processing
- Retries and dead-letter handling
- Enables scaling of ML service

### 3.3 Architecture Pattern: Microservices

**Pattern Choice:** Microservices

**Rationale:**
1. ML service has different scaling profile (compute-heavy)
2. API service is I/O heavy (network, database)
3. Can scale independently based on demand
4. Easier to iterate on ML service separately

**Tradeoff:**
- Complexity: Distributed systems are harder to debug
- Latency: Network calls between services
- Operational overhead: More containers to manage

**Alternative Considered: Monolith**
- Reason not chosen: ML inference would slow down API
- Would need to process code sequentially
- Would require threading or async within single process
- Harder to scale just the inference service

### 3.4 Data Flow Through System

```
USER FLOW:
1. Developer pushes code to GitHub
2. GitHub webhook → API Service
3. API stores PR metadata in PostgreSQL
4. API publishes job to SQS queue
5. ML Service picks up job from queue
6. ML Service analyzes code
7. ML Service stores findings in PostgreSQL
8. API sends GitHub comment with findings
9. User sees findings in GitHub PR UI

TIMING:
Step 1: Instant (developer action)
Steps 2-3: < 100ms
Step 4: < 50ms
Steps 5-6: 10-30 seconds (queue latency + ML processing)
Step 7: < 100ms
Step 8: < 500ms (GitHub API call)
Step 9: Instant (GitHub UI refresh)
Total End-to-End: 10-30 seconds ✓ (within 30-second target)
```

### 3.5 Deployment Architecture

```
DEVELOPMENT
  └─ Local machine (Docker Compose)

STAGING
  └─ AWS (same as production, different data)

PRODUCTION
  ├─ Region: us-east-1
  ├─ Availability Zones: us-east-1a, us-east-1b, us-east-1c
  ├─ Services:
  │  ├─ API Service: 3-10 instances (auto-scaling)
  │  ├─ ML Service: 2-5 instances (auto-scaling)
  │  ├─ Database: 1 primary + 2 read replicas
  │  ├─ Cache: 1 cluster (3-node sharded)
  │  └─ Load Balancer: Multi-AZ
  └─ Backup: Daily automated backups, geo-replicated

DISASTER RECOVERY
  ├─ Primary: us-east-1
  ├─ Secondary: us-west-2 (read-only replica)
  ├─ RTO (Recovery Time Objective): 1 hour
  ├─ RPO (Recovery Point Objective): 15 minutes
  └─ Failover: Manual (automated in future)
```

### 3.6 Design Decisions & Rationale

| Decision | Choice | Reason | Alternative | Trade-off |
|---|---|---|---|---|
| Language | Node.js + Python | Best libraries per task | Go/Rust | More languages |
| Database | PostgreSQL | ACID, complex queries | MongoDB | Scaling limits |
| Caching | Redis | Fast, versatile | Memcached | Requires VM |
| Queue | AWS SQS | Managed, reliable | RabbitMQ | Less control |
| Hosting | AWS ECS | Managed K8s alternative | On-prem | Vendor lock-in |
| Frontend | React | Rich ecosystem | Vue | Team familiar |

---

### Section 4: TECHNOLOGY STACK

**Purpose:** 
Detailed explanation of every technology and why it was chosen

**Length:** 
3-4 pages

**Components:**

```markdown
## Technology Stack

### 4.1 Frontend Stack

**Framework: React 18**
- Why: Largest ecosystem, best libraries, team expertise
- Version: 18.2.0 (LTS)
- Why not: Vue (smaller ecosystem), Angular (overkill)

**Language: TypeScript**
- Why: Type safety, better IDE support, catches errors early
- Why not: Plain JavaScript (no type safety)

**Build Tool: Vite**
- Why: Lightning-fast dev server, optimized builds
- Alternative: Webpack (older, slower), Next.js (adds BE)

**Styling: Tailwind CSS**
- Why: Utility-first, fast development, consistent design
- Alternative: CSS Modules (verbose), Styled Components

**State Management: Redux Toolkit**
- Why: Predictable state, good for complex app
- Alternative: Context API (simpler for small apps)

**HTTP Client: Axios**
- Why: Clean API, good error handling
- Alternative: Fetch API (more verbose)

**Testing: Vitest + React Testing Library**
- Why: Fast unit tests, realistic component testing
- Alternative: Jest (older), Cypress (E2E only)

**Dependencies:**
```json
{
  "react": "^18.2.0",
  "react-dom": "^18.2.0",
  "typescript": "^5.0.0",
  "vite": "^4.0.0",
  "tailwindcss": "^3.3.0",
  "@reduxjs/toolkit": "^1.9.0",
  "axios": "^1.4.0",
  "react-router-dom": "^6.0.0"
}
```

### 4.2 Backend Stack

**Runtime: Node.js**
- Version: 18 LTS (must be latest LTS)
- Why: JavaScript ecosystem, fast I/O, good for APIs

**Framework: Express.js**
- Version: 4.18.0
- Why: Minimal, flexible, well-known
- Alternative: Fastify (faster but less mature)

**Language: TypeScript**
- Why: Type safety, better IDE, early error detection

**Database Driver: pg (node-postgres)**
- Why: Most popular, well-maintained, pool support

**Request Validation: Joi**
- Why: Comprehensive validation, good error messages
- Alternative: Zod (newer, simpler)

**Authentication: Passport.js + JWT**
- Why: Industry standard, many strategies
- Alternative: Custom auth (not recommended)

**Logging: Winston**
- Why: Multiple transports, structured logging
- Alternative: Pino (faster but less features)

**Testing: Jest + Supertest**
- Why: Comprehensive, good for API testing
- Alternative: Mocha (older)

**API Documentation: Swagger/OpenAPI**
- Why: Auto-generates docs from code
- Tool: swagger-jsdoc + swagger-ui-express

**Dependencies:**
```json
{
  "express": "^4.18.0",
  "typescript": "^5.0.0",
  "pg": "^8.10.0",
  "joi": "^17.0.0",
  "passport": "^0.6.0",
  "jsonwebtoken": "^9.0.0",
  "winston": "^3.8.0",
  "jest": "^29.0.0",
  "supertest": "^6.3.0"
}
```

### 4.3 ML Service Stack

**Language: Python**
- Version: 3.10+ (must be 3.8+)
- Why: Best ML libraries available

**Web Framework: FastAPI**
- Why: Modern, fast, async support
- Alternative: Flask (simpler but slower)

**ML Framework: PyTorch**
- Version: 2.0+
- Why: Most flexible, good for research, Transformers support
- Alternative: TensorFlow (overkill for this use case)

**Transformers: Hugging Face Transformers**
- Model: CodeBERT or CodeT5 (code understanding)
- Why: Pre-trained on code, good accuracy
- Fine-tuning: Yes, on project-specific data

**Task Queue: Celery + Redis**
- Why: Distributed task processing, good for long-running jobs
- Alternative: Direct queue consumption (less flexible)

**Database: SQLAlchemy ORM**
- Why: Database-agnostic, good migrations
- Alternative: Raw queries (error-prone)

**Testing: Pytest**
- Why: Powerful, good fixtures
- Alternative: Unittest (verbose)

**Dependencies:**
```
fastapi==0.95.0
uvicorn==0.21.0
torch==2.0.0
transformers==4.30.0
sqlalchemy==2.0.0
celery==5.2.0
redis==4.5.0
pytest==7.3.0
```

### 4.4 Database Stack

**Primary Database: PostgreSQL 14**
- Why: ACID, advanced features, excellent for complex queries
- Alternative: MySQL (simpler but fewer features)

**Object-Relational Mapping: SQLAlchemy**
- Used in: Backend service
- Why: Database-agnostic, good migrations

**Migration Tool: Flyway or Alembic**
- Choice: Alembic (Python-native)
- Why: Version control for schema
- How: Manual migrations reviewed before applying

**Backup: AWS RDS Automated Backups**
- Retention: 30 days
- Frequency: Daily automated + hourly snapshots
- Geographic: Multi-region replication

**Monitoring: AWS CloudWatch**
- Metrics: CPU, connections, query performance
- Alarms: Alert on 80%+ CPU or slow queries
- Logs: Query logs for slow query analysis

### 4.5 Infrastructure & DevOps

**Container Orchestration: AWS ECS**
- Why: Managed service, less operational overhead
- Alternative: Kubernetes (more control but complex)

**Containerization: Docker**
- Base image: node:18-alpine (minimal)
- Multi-stage builds: Separate build and runtime
- Registry: AWS ECR (private container registry)

**CI/CD Pipeline: GitHub Actions**
- Trigger: On push to main, pull request
- Steps:
  1. Lint (ESLint, Prettier)
  2. Unit tests (Jest)
  3. Build image (Docker)
  4. Push to ECR
  5. Deploy to staging
  6. Run integration tests
  7. Deploy to production

**Infrastructure as Code: Terraform**
- State management: S3 backend with locking
- Version control: All .tf files in Git
- Approval: Code review before apply

**Monitoring: CloudWatch + Datadog**
- CloudWatch: AWS native metrics
- Datadog: Application performance monitoring (APM)
- Metrics tracked:
  - Request latency (p50, p95, p99)
  - Error rates
  - Database connections
  - Cache hit rate
  - ML inference time

**Logging: CloudWatch Logs + Splunk**
- Centralized log aggregation
- Retention: 30 days in CloudWatch, 1 year in Splunk
- Log level: INFO in production, DEBUG in development

**Secrets Management: AWS Secrets Manager**
- All API keys, passwords, credentials stored here
- Rotation: Automatic for some (DB passwords)
- Access: Via IAM roles (no hardcoding)

### 4.6 Version Constraints

**Minimum Required Versions:**
```
Node.js: 18.0.0 (must be LTS)
Python: 3.8.0 (latest 3.x preferred)
PostgreSQL: 12.0 (latest version preferred)
Docker: 20.10.0
Kubernetes/ECS: Latest stable

CRITICAL SECURITY VERSIONS:
React: Must have latest patch
Express: Must have latest patch
PyTorch: Must have latest patch
PostgreSQL: Security updates within 1 month
```

---

### Section 5: API SPECIFICATIONS

**Purpose:** 
Complete definition of all API endpoints and contracts

**Length:** 
4-6 pages with examples

**Components:**

```markdown
## API Specifications

### 5.1 API Overview

**API Type:** REST (HTTP/JSON)

**Base URL:**
```
Development: http://localhost:3000/api/v1
Staging: https://api-staging.autoreview.dev/api/v1
Production: https://api.autoreview.dev/api/v1
```

**Authentication:** OAuth2 + JWT

**Rate Limiting:** 1000 requests per minute per user

**API Versioning:** URL-based (v1, v2, etc.)

### 5.2 Authentication & Authorization

**OAuth2 Flow:**
```
1. User clicks "Connect GitHub"
2. Redirect to GitHub OAuth URL
3. GitHub redirects back with code
4. Backend exchanges code for token
5. Backend stores GitHub token (encrypted)
6. Backend issues JWT token to frontend
7. Frontend uses JWT for API calls
```

**JWT Token Structure:**
```json
Header:
{
  "alg": "HS256",
  "typ": "JWT"
}

Payload:
{
  "sub": "user_123",
  "email": "user@example.com",
  "role": "admin",
  "iat": 1640000000,
  "exp": 1640086400  // 24-hour expiry
}

Signature: HMAC-SHA256(header.payload, SECRET_KEY)
```

**Authorization Levels:**
```
Public: No authentication required (health check)
User: Must have valid JWT
Admin: Must have admin role in JWT
Team: Must belong to team and have permission
```

### 5.3 Detailed Endpoint Specifications

---

**ENDPOINT 1: GitHub OAuth Callback**

```
POST /auth/github/callback

Description: GitHub OAuth callback after user authorization

Request:
{
  "code": "abc123def456"  // Code from GitHub
}

Response (200 OK):
{
  "success": true,
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "id": "user_123",
    "email": "john@example.com",
    "name": "John Doe",
    "avatarUrl": "https://...",
    "githubUsername": "johndoe"
  }
}

Response (400 Bad Request):
{
  "success": false,
  "error": "INVALID_CODE",
  "message": "GitHub authorization code is invalid or expired"
}

Response (500 Internal Server Error):
{
  "success": false,
  "error": "GITHUB_API_ERROR",
  "message": "Failed to contact GitHub API"
}

Headers:
Authorization: None (this is the login endpoint)
Content-Type: application/json

Latency Target: < 1000ms (includes GitHub API call)
```

---

**ENDPOINT 2: GitHub Webhook for PR Events**

```
POST /webhooks/github

Description: Receives GitHub PR events and triggers analysis

Triggering Events:
- pull_request.opened
- pull_request.synchronize (new commits)

Payload (from GitHub):
{
  "action": "opened" | "synchronize",
  "pull_request": {
    "id": 1,
    "number": 123,
    "head": {
      "sha": "abc123def456",
      "ref": "feature/new-feature"
    },
    "base": {
      "sha": "main_commit_sha",
      "ref": "main"
    },
    "repository": {
      "id": 12345,
      "full_name": "company/repo",
      "private": false
    },
    "owner": {
      "login": "company"
    }
  }
}

Processing:
1. Validate webhook signature (GitHub secret)
2. Store PR metadata in database
3. Publish analysis job to SQS
4. Return 202 Accepted immediately
5. ML service processes asynchronously

Response (202 Accepted):
{
  "success": true,
  "jobId": "job_abc123",
  "message": "Analysis queued"
}

Security:
- Signature validation: HMAC-SHA256(payload, GITHUB_SECRET)
- Only process authenticated webhooks
- Idempotent: Same webhook processed multiple times = same result

Latency Target: < 500ms (should respond quickly, processing async)
```

---

**ENDPOINT 3: Get PR Analysis Findings**

```
GET /repositories/{repoId}/pulls/{pullNumber}/findings

Description: Get all findings for a specific pull request

Parameters:
- repoId (path): Repository identifier
- pullNumber (path): Pull request number
- severityLevel (query): Filter by severity (critical, warning, info)
  Values: "critical" | "warning" | "info" | undefined (all)
  Optional, default: undefined

Headers:
Authorization: Bearer {JWT_TOKEN}
Content-Type: application/json

Response (200 OK):
{
  "success": true,
  "pullNumber": 123,
  "findings": [
    {
      "id": "finding_123",
      "type": "security",
      "category": "sql_injection",
      "severity": "critical",
      "file": "src/db/queries.js",
      "line": 45,
      "column": 12,
      "message": "Potential SQL injection vulnerability",
      "description": "User input is concatenated into SQL query without parameterization",
      "suggestion": "Use parameterized queries instead of string concatenation",
      "code": "const query = `SELECT * FROM users WHERE id = ${userId}`;",
      "correctCode": "const query = 'SELECT * FROM users WHERE id = $1';",
      "documentationUrl": "https://owasp.org/www-community/SQL_Injection",
      "dismissed": false,
      "dismissedAt": null,
      "dismissedReason": null
    },
    {
      "id": "finding_124",
      "type": "performance",
      "category": "n_plus_one",
      "severity": "warning",
      "file": "src/services/user.js",
      "line": 78,
      "message": "N+1 database query pattern detected",
      "description": "Loop contains database query - will execute once per item",
      "suggestion": "Use batch query or JOIN instead",
      "code": "for (const userId of userIds) { db.query('SELECT * FROM user_roles WHERE user_id = ?', userId); }",
      "correctCode": "db.query('SELECT * FROM user_roles WHERE user_id = ANY($1)', [userIds]);",
      "documentationUrl": "https://use-the-index-luke.com/",
      "dismissed": false
    }
  ],
  "summary": {
    "totalFindings": 2,
    "byType": {
      "security": 1,
      "performance": 1,
      "quality": 0
    },
    "bySeverity": {
      "critical": 1,
      "warning": 1,
      "info": 0
    }
  }
}

Response (404 Not Found):
{
  "success": false,
  "error": "PULL_REQUEST_NOT_FOUND",
  "message": "Pull request #123 not found in repository"
}

Response (401 Unauthorized):
{
  "success": false,
  "error": "UNAUTHORIZED",
  "message": "User does not have access to this repository"
}

Latency Target: < 200ms (should be from cache if possible)
```

---

**ENDPOINT 4: Dismiss Finding**

```
POST /findings/{findingId}/dismiss

Description: User indicates finding is false positive or not applicable

Parameters:
- findingId (path): Finding to dismiss

Request Body:
{
  "reason": "false_positive" | "not_applicable" | "will_fix_later",
  "comment": "Optional explanation from user"
}

Response (200 OK):
{
  "success": true,
  "finding": {
    "id": "finding_123",
    "dismissed": true,
    "dismissedAt": "2024-01-20T10:30:00Z",
    "dismissedReason": "false_positive",
    "dismissedBy": {
      "id": "user_123",
      "name": "John Doe"
    }
  }
}

Response (404 Not Found):
{
  "success": false,
  "error": "FINDING_NOT_FOUND"
}

Idempotency: 
- Same request twice = same result (idempotent)
- Use Idempotency-Key header for safety

Latency Target: < 100ms
```

---

**ENDPOINT 5: List Team Configuration**

```
GET /teams/{teamId}/configuration

Description: Get code review rules configured for team

Parameters:
- teamId (path): Team identifier

Response (200 OK):
{
  "success": true,
  "teamId": "team_123",
  "configuration": {
    "rules": {
      "security": {
        "enabled": true,
        "severity": "critical",
        "categories": {
          "sql_injection": { "enabled": true, "severity": "critical" },
          "xss": { "enabled": true, "severity": "critical" },
          "hardcoded_secrets": { "enabled": true, "severity": "critical" },
          "weak_crypto": { "enabled": true, "severity": "warning" }
        }
      },
      "performance": {
        "enabled": true,
        "severity": "warning",
        "categories": {
          "n_plus_one": { "enabled": true, "severity": "warning" },
          "unbounded_loops": { "enabled": true, "severity": "warning" },
          "inefficient_algorithms": { "enabled": false }
        }
      },
      "quality": {
        "enabled": true,
        "severity": "info"
      }
    },
    "exclusions": {
      "directories": ["node_modules/", "build/", "dist/"],
      "files": ["*.test.js", "*.spec.js"]
    },
    "languages": ["javascript", "python", "java"]
  },
  "updatedAt": "2024-01-20T10:30:00Z",
  "updatedBy": {
    "id": "user_456",
    "name": "Jane Smith"
  }
}

Latency Target: < 50ms (cached data)
```

### 5.4 Error Handling

**Error Response Format:**

```json
{
  "success": false,
  "error": "ERROR_CODE",
  "message": "Human-readable error message",
  "details": {
    "field": "optional field-specific info"
  }
}
```

**HTTP Status Codes:**

| Code | Meaning | When |
|---|---|---|
| 200 | OK | Request succeeded |
| 201 | Created | Resource created |
| 202 | Accepted | Request accepted for async processing |
| 400 | Bad Request | Invalid input/validation failure |
| 401 | Unauthorized | Authentication required or failed |
| 403 | Forbidden | Authenticated but not authorized |
| 404 | Not Found | Resource doesn't exist |
| 409 | Conflict | State conflict (e.g., already exists) |
| 429 | Too Many Requests | Rate limit exceeded |
| 500 | Internal Server Error | Unexpected error |
| 502 | Bad Gateway | Dependency unavailable |
| 503 | Service Unavailable | Temporary service issue |

**Common Error Codes:**

```
AUTH_REQUIRED - Authentication token missing or invalid
AUTHORIZATION_FAILED - User lacks required permissions
VALIDATION_ERROR - Request validation failed
NOT_FOUND - Resource not found
GITHUB_API_ERROR - GitHub API call failed
DATABASE_ERROR - Database operation failed
INTERNAL_ERROR - Unexpected server error
RATE_LIMIT_EXCEEDED - Too many requests
```

### 5.5 Rate Limiting

**Strategy:**
- Limit: 1000 requests per minute per authenticated user
- Limit: 100 requests per minute per IP (unauthenticated)
- Webhooks: Unlimited (from GitHub servers only)

**Response Headers:**
```
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 987
X-RateLimit-Reset: 1640086400
```

**When Limit Exceeded:**
```
HTTP 429 Too Many Requests

{
  "error": "RATE_LIMIT_EXCEEDED",
  "message": "API rate limit exceeded",
  "retryAfter": 60  // Seconds
}
```

---

### Section 6: DATABASE SCHEMA

**Purpose:** 
Detailed database design including all tables and relationships

**Length:** 
3-4 pages

```markdown
## Database Schema

### 6.1 Overview

**Database:** PostgreSQL 14
**Design:** Normalized (3NF)
**Total Tables:** 12
**Total Relations:** 15

### 6.2 User Management Tables

**TABLE: users**
```sql
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  email VARCHAR(255) NOT NULL UNIQUE,
  github_username VARCHAR(255) NOT NULL UNIQUE,
  github_id INTEGER NOT NULL UNIQUE,
  github_token_encrypted TEXT NOT NULL,  -- Encrypted with KMS
  first_name VARCHAR(100),
  last_name VARCHAR(100),
  avatar_url TEXT,
  is_active BOOLEAN DEFAULT true,
  role VARCHAR(50) DEFAULT 'user',  -- user, admin
  created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  
  CONSTRAINT check_valid_email CHECK (email ~ '^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}$'),
  CONSTRAINT check_valid_role CHECK (role IN ('user', 'admin'))
);

CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_users_github_id ON users(github_id);
CREATE INDEX idx_users_is_active ON users(is_active) WHERE is_active = true;
```

**TABLE: teams**
```sql
CREATE TABLE teams (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  name VARCHAR(255) NOT NULL,
  owner_id UUID NOT NULL REFERENCES users(id) ON DELETE CASCADE,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  
  CONSTRAINT check_name_not_empty CHECK (length(trim(name)) > 0)
);

CREATE INDEX idx_teams_owner ON teams(owner_id);
```

**TABLE: team_members**
```sql
CREATE TABLE team_members (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  team_id UUID NOT NULL REFERENCES teams(id) ON DELETE CASCADE,
  user_id UUID NOT NULL REFERENCES users(id) ON DELETE CASCADE,
  role VARCHAR(50) NOT NULL DEFAULT 'developer',  -- admin, developer
  joined_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  
  UNIQUE(team_id, user_id),
  CONSTRAINT check_valid_role CHECK (role IN ('admin', 'developer'))
);

CREATE INDEX idx_team_members_team ON team_members(team_id);
CREATE INDEX idx_team_members_user ON team_members(user_id);
```

### 6.3 Repository Tables

**TABLE: repositories**
```sql
CREATE TABLE repositories (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  github_repo_id INTEGER NOT NULL UNIQUE,
  team_id UUID NOT NULL REFERENCES teams(id) ON DELETE CASCADE,
  name VARCHAR(255) NOT NULL,
  full_name VARCHAR(255) NOT NULL,  -- owner/repo
  url TEXT NOT NULL,
  is_private BOOLEAN DEFAULT true,
  language VARCHAR(50),
  created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  
  UNIQUE(team_id, github_repo_id)
);

CREATE INDEX idx_repos_team ON repositories(team_id);
CREATE INDEX idx_repos_github_id ON repositories(github_repo_id);
```

**TABLE: pull_requests**
```sql
CREATE TABLE pull_requests (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  github_pr_number INTEGER NOT NULL,
  repository_id UUID NOT NULL REFERENCES repositories(id) ON DELETE CASCADE,
  author_id UUID REFERENCES users(id) ON DELETE SET NULL,
  title VARCHAR(500) NOT NULL,
  description TEXT,
  head_sha VARCHAR(40) NOT NULL,  -- Commit SHA
  base_sha VARCHAR(40) NOT NULL,  -- Base commit SHA
  status VARCHAR(50),  -- open, merged, closed
  created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  analyzed_at TIMESTAMP WITH TIME ZONE,
  
  UNIQUE(repository_id, github_pr_number)
);

CREATE INDEX idx_prs_repo ON pull_requests(repository_id);
CREATE INDEX idx_prs_analyzed_at ON pull_requests(analyzed_at);
CREATE INDEX idx_prs_status ON pull_requests(status);
```

### 6.4 Findings Tables

**TABLE: findings**
```sql
CREATE TABLE findings (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  pull_request_id UUID NOT NULL REFERENCES pull_requests(id) ON DELETE CASCADE,
  type VARCHAR(50) NOT NULL,  -- security, performance, quality
  category VARCHAR(100) NOT NULL,  -- sql_injection, n_plus_one, etc.
  severity VARCHAR(50) NOT NULL,  -- critical, warning, info
  file_path VARCHAR(500) NOT NULL,
  line_number INTEGER NOT NULL,
  column_number INTEGER,
  message TEXT NOT NULL,
  description TEXT,
  suggestion TEXT,
  code_snippet TEXT,
  correct_code_snippet TEXT,
  documentation_url TEXT,
  ml_confidence_score DECIMAL(3,2),  -- 0.00 to 1.00
  dismissed BOOLEAN DEFAULT false,
  dismissed_at TIMESTAMP WITH TIME ZONE,
  dismissed_reason VARCHAR(100),
  dismissed_by_id UUID REFERENCES users(id),
  github_comment_id BIGINT,  -- GitHub comment ID for linking
  created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  
  CONSTRAINT check_valid_type CHECK (type IN ('security', 'performance', 'quality')),
  CONSTRAINT check_valid_severity CHECK (severity IN ('critical', 'warning', 'info')),
  CONSTRAINT check_confidence CHECK (ml_confidence_score IS NULL OR (ml_confidence_score >= 0 AND ml_confidence_score <= 1))
);

CREATE INDEX idx_findings_pr ON findings(pull_request_id);
CREATE INDEX idx_findings_type ON findings(type);
CREATE INDEX idx_findings_severity ON findings(severity);
CREATE INDEX idx_findings_file ON findings(file_path);
CREATE INDEX idx_findings_dismissed ON findings(dismissed) WHERE dismissed = false;
```

### 6.5 Configuration Tables

**TABLE: team_configuration**
```sql
CREATE TABLE team_configuration (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  team_id UUID NOT NULL UNIQUE REFERENCES teams(id) ON DELETE CASCADE,
  rules JSONB NOT NULL,  -- JSON structure of enabled rules
  exclusions JSONB,  -- Directories/files to exclude
  supported_languages TEXT[] DEFAULT ARRAY['javascript', 'python', 'java'],
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  updated_by_id UUID REFERENCES users(id)
);

CREATE INDEX idx_team_config_team ON team_configuration(team_id);
```

Example JSONB structure:
```json
{
  "rules": {
    "security": {
      "enabled": true,
      "severity": "critical",
      "categories": {
        "sql_injection": { "enabled": true, "severity": "critical" },
        "xss": { "enabled": true, "severity": "critical" }
      }
    },
    "performance": {
      "enabled": true,
      "severity": "warning"
    }
  },
  "exclusions": {
    "directories": ["node_modules/", "build/"],
    "files": ["*.test.js", "*.spec.js"]
  }
}
```

### 6.6 Data Relationships Diagram

```
users (1)
  ├─── (∞) teams (as owner)
  ├─── (∞) team_members
  ├─── (∞) pull_requests (as author)
  └─── (∞) findings (as dismissed_by)

teams (1)
  ├─── (∞) team_members
  ├─── (∞) repositories
  └─── (1) team_configuration

repositories (1)
  └─── (∞) pull_requests

pull_requests (1)
  └─── (∞) findings

team_members:
  user_id → users.id
  team_id → teams.id
```

---

### Section 7: SECURITY ARCHITECTURE

**Purpose:** 
Define security measures and compliance requirements

**Length:** 
3 pages

```markdown
## Security Architecture

### 7.1 Authentication

**OAuth2 Flow:**
- Use GitHub as identity provider (OAuth2)
- Redirect flow: User → GitHub → Callback
- Token storage: Encrypted in database
- Token refresh: Automatic before expiry

**JWT for API:**
- Issued on login
- Stored in HTTP-only cookie (not localStorage)
- 24-hour expiry
- Signed with HS256 algorithm
- Contains: user_id, email, role

**Session Management:**
- Server-side sessions in Redis
- Session timeout: 30 days
- Session invalidation on logout
- Clear on browser close option

### 7.2 Authorization

**Role-Based Access Control (RBAC):**

```
ROLE: User
- Can access own profile
- Can create team
- Can submit PRs

ROLE: Team Admin
- Can manage team members
- Can configure team rules
- Can view team analytics
- Can delete team

ROLE: Platform Admin
- Can access all teams
- Can modify any configuration
- Can view all analytics
- Can manage users
```

**Permission Matrix:**
```
Action                      User    TeamAdmin   Admin
View own profile            ✓       ✓           ✓
View team profile           ✓       ✓           ✓
Add team member             -       ✓           ✓
Remove team member          -       ✓           ✓
Configure team rules        -       ✓           ✓
View team findings          ✓       ✓           ✓
Dismiss findings            ✓       ✓           ✓
Delete team                 -       ✓           ✓
View all teams              -       -           ✓
Modify any config           -       -           ✓
```

### 7.3 Data Protection

**Encryption in Transit:**
- TLS 1.3 for all HTTP traffic
- Certificate: AWS Certificate Manager
- Cipher suites: Modern (no RC4, DES, etc.)

**Encryption at Rest:**
```
GitHub Token: AES-256 (AWS KMS)
User Passwords: Not stored (OAuth2)
Code Snippets: AES-256 (in database)
API Keys: AES-256 (AWS Secrets Manager)
Session Data: Redis (in-memory, ephemeral)
Backups: AES-256 (AWS managed)
```

**Key Management:**
- AWS KMS for key storage
- Keys rotated annually
- Separate keys per environment
- Access logging for all key operations

### 7.4 Input Validation & Sanitization

**API Input Validation:**
```javascript
// Example: Email validation
const emailSchema = Joi.string()
  .email()
  .max(255)
  .required();

// Example: File path validation
const pathSchema = Joi.string()
  .regex(/^[a-zA-Z0-9_\-/.]+$/)
  .max(500)
  .required();
```

**SQL Injection Prevention:**
- Always use parameterized queries
- Never concatenate user input into SQL
- Prepared statements for all queries

**XSS Prevention:**
- Sanitize all user input
- Use Content-Security-Policy headers
- React escapes by default
- DOMPurify for HTML content

**CSRF Protection:**
- CSRF token for state-changing requests
- Same-site cookies
- Verify origin/referer headers

### 7.5 Security Headers

```
Strict-Transport-Security: max-age=31536000; includeSubDomains
Content-Security-Policy: default-src 'self'; script-src 'self' 'unsafe-inline'
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: geolocation=(), microphone=()
```

### 7.6 Vulnerability Management

**Dependency Scanning:**
- npm audit (weekly)
- Dependabot (automated)
- OWASP Top 10 scanning
- Critical vulnerabilities: Fixed within 24 hours

**Code Analysis:**
- Static code analysis: SonarQube
- SAST: Snyk
- Secrets scanning: GitGuardian
- All committed on every PR

**Penetration Testing:**
- Annual external pentest
- Quarterly internal security reviews
- Bug bounty program
- Incident response plan

### 7.7 Compliance

**Standards:**
- GDPR (General Data Protection Regulation)
- CCPA (California Consumer Privacy Act)
- SOC 2 Type 2
- ISO 27001 (planned)

**Data Processing:**
- GDPR Data Processing Agreement (DPA)
- Data residency: US/EU options
- CCPA compliance: Opt-out capability
- Consent management: Explicit opt-in

**Audit Logging:**
```
Log all:
- User authentication events
- Team configuration changes
- Data access (who viewed what)
- Administrative actions
- API key creation/rotation
- Security rule changes

Retention: 7 years for compliance
Access: Restricted to compliance/security team
Immutable: Logs cannot be deleted
```
```

---

### Section 8: PERFORMANCE & OPTIMIZATION

**Purpose:** 
Define performance targets and optimization strategies

**Length:** 
2-3 pages

```markdown
## Performance & Optimization

### 8.1 Performance Targets

**Frontend:**
- Page load time: < 2 seconds (Lighthouse)
- First contentful paint: < 1 second
- Time to interactive: < 3 seconds
- Largest contentful paint: < 2.5 seconds
- Cumulative layout shift: < 0.1

**Backend API:**
- API latency: < 200ms (p95)
- API latency: < 500ms (p99)
- Error rate: < 0.1%
- Availability: 99.9% (45 minutes downtime/month max)

**ML Service:**
- Inference latency: < 15 seconds (p95)
- Model accuracy: > 90%
- Throughput: > 100 PRs/minute

**Database:**
- Query latency: < 100ms (p95)
- Connection pool: 50-100 connections
- Read replica lag: < 100ms

### 8.2 Caching Strategy

**Frontend Caching:**
- Browser cache: Static assets (1 year)
- CDN cache: HTML/images (1 hour)
- Service worker: Offline capability
- Redux store: State caching

**Backend Caching:**
- Redis: Session data (30 day TTL)
- Redis: Frequently accessed data (1 hour TTL)
- Redis: Query results (5 minute TTL)
- Database query cache: N/A (keep fresh)

**Cache Key Strategy:**
```javascript
// User data cache
`user:${userId}` -> TTL: 1 hour

// Team configuration cache
`team:${teamId}:config` -> TTL: 24 hours

// PR findings cache
`pr:${prId}:findings` -> TTL: 10 minutes

// Analytics cache
`analytics:${teamId}:${metric}` -> TTL: 1 hour
```

**Cache Invalidation:**
- Time-based expiry (TTL)
- Event-based invalidation (when data changes)
- Manual invalidation (admin override)

### 8.3 Database Optimization

**Indexing Strategy:**
- Index foreign keys: team_id, user_id, repository_id
- Index frequently filtered columns: status, type, severity
- Composite index: (pull_request_id, dismissed) for common query
- Partial index: findings WHERE dismissed = false
- Full-text index: message, description for search

**Query Optimization:**
```sql
-- SLOW (N+1 query problem)
SELECT pr.id FROM pull_requests pr;
FOR EACH pr:
  SELECT findings FROM findings WHERE pr_id = pr.id;

-- FAST (Single query)
SELECT pr.id, f.* FROM pull_requests pr
LEFT JOIN findings f ON pr.id = f.pull_request_id
WHERE pr.repository_id = $1;

-- FAST (Using array aggregation)
SELECT pr.id, array_agg(f.id) as finding_ids
FROM pull_requests pr
LEFT JOIN findings f ON pr.id = f.pull_request_id
GROUP BY pr.id;
```

**Connection Pooling:**
- Pool size: 50 connections minimum
- Max: 100 connections
- Queue timeout: 30 seconds
- Idle timeout: 10 minutes

### 8.4 Load Testing & Capacity Planning

**Load Test Targets:**
- Concurrent users: 10,000
- Requests per second: 1,000
- Duration: 30 minutes sustained
- Latency must remain < 200ms at load

**Capacity Planning:**
- Database: Monitor CPU, memory, disk I/O
- API servers: Monitor CPU, memory, network
- Cache: Monitor hit rate (target 80%+)
- Queue: Monitor depth (target < 100 jobs)

**Scaling Thresholds:**
```
Metric              Threshold    Action
API CPU             70%         Spin up new instance
API Memory          80%         Alert ops
Database CPU        75%         Add read replica
Cache Hit Rate      < 70%       Increase cache size
Queue Depth         > 500       Scale ML workers
API Latency p95     > 300ms     Investigate bottleneck
Error Rate          > 0.2%      Page on-call engineer
```

---

### Section 9: TESTING STRATEGY

**Purpose:** 
Define how the system will be tested and validated

**Length:** 
2-3 pages

```markdown
## Testing Strategy

### 9.1 Testing Pyramid

```
        △
       /|\
      / | \
     /  |  \ E2E Tests (10%)
    /   |   \ - Full user flows
   /    |    \----
  /     |         \
 /      |          \ Integration Tests (30%)
/       |           \ - API + DB
---------|----------- - Service interactions
|       |        |
| Unit Tests (60%)   |
| - Individual functions |
| - Edge cases        |
| - Mocks            |
```

### 9.2 Unit Tests

**Coverage Target:** 80%+

**Testing Framework:** Jest

**Example:**
```javascript
describe('Finding Detection', () => {
  it('should detect SQL injection', () => {
    const code = "SELECT * FROM users WHERE id = " + userId;
    const findings = detectIssues(code);
    expect(findings).toContainEqual(
      expect.objectContaining({
        type: 'security',
        category: 'sql_injection'
      })
    );
  });

  it('should not flag parameterized queries', () => {
    const code = "SELECT * FROM users WHERE id = $1";
    const findings = detectIssues(code);
    expect(findings).not.toContainEqual(
      expect.objectContaining({
        category: 'sql_injection'
      })
    );
  });
});
```

### 9.3 Integration Tests

**Testing Framework:** Supertest + Jest

**Example:**
```javascript
describe('POST /repositories/:id/analyze', () => {
  it('should create analysis job', async () => {
    const res = await request(app)
      .post(`/repositories/${repoId}/analyze`)
      .set('Authorization', `Bearer ${token}`)
      .send({ pullNumber: 123 })
      .expect(202);

    expect(res.body.jobId).toBeDefined();
    
    // Verify job was created in database
    const job = await Job.findById(res.body.jobId);
    expect(job).toBeDefined();
  });
});
```

### 9.4 E2E Tests

**Testing Framework:** Cypress

**Coverage:** Critical user paths only

**Example:**
```javascript
describe('Complete PR Analysis Flow', () => {
  it('should analyze PR and show findings', () => {
    cy.login('user@example.com');
    cy.navigateToDashboard();
    cy.selectRepository('test-repo');
    
    // Trigger analysis via GitHub webhook
    triggerGithubWebhook({ action: 'opened' });
    
    cy.waitForAnalysis(30000);  // Max 30 seconds
    cy.seeFindingsInPR();
    cy.verifyFindingDetails();
  });
});
```

### 9.5 Performance Tests

**Load Test Tool:** Apache JMeter

**Test Scenarios:**
```
Scenario 1: Normal Load
- 100 concurrent users
- 10 PRs analyzed per user
- Duration: 10 minutes

Scenario 2: Peak Load
- 1000 concurrent users
- 100 PRs analyzed per user
- Duration: 30 minutes

Scenario 3: Stress Test
- Gradually increase to 5000 users
- Measure breaking point
- Verify recovery after load reduction
```

### 9.6 Security Testing

**Static Analysis:** SonarQube + Snyk

**Dependency Scanning:** npm audit (weekly)

**Penetration Testing:**
- Annual external pentest
- Quarterly internal security review
- OWASP Top 10 testing

**Manual Testing:**
```
- SQL injection attempts
- XSS payload testing
- CSRF attacks
- Authentication bypass
- Authorization flaws
- Sensitive data exposure
```
```

---

### Section 10: DEPLOYMENT & OPERATIONS

**Purpose:** 
How the system will be deployed and operated

**Length:** 
2-3 pages

```markdown
## Deployment & Operations

### 10.1 Deployment Strategy

**Approach:** Blue-Green Deployment

```
Current (Blue):        New (Green):
- v1.2.3 (Current)    - v1.2.4 (Testing)
- Production traffic   - Canary traffic (10%)
- 3 instances         - 3 instances
                       
If v1.2.4 healthy:
1. Route 50% traffic to Green
2. Monitor metrics
3. Route 100% traffic to Green
4. Blue becomes standby (rollback)
5. After 24 hours, decommission Blue

If v1.2.4 fails:
1. Route traffic back to Blue
2. Investigate issue
3. Fix and redeploy
```

**Rollout Frequency:** Multiple times per day

**Rollback Time:** < 5 minutes

### 10.2 Release Management

**Version Format:** Semantic Versioning (major.minor.patch)

**Release Timeline:**
```
Monday:   Feature freeze
Tuesday:  Release candidate testing
Wednesday: Deploy to staging
Thursday:  Final validation
Friday:    Deploy to production
```

**Release Approval:**
- Engineering lead approval
- Ops approval (deployment readiness)
- Product sign-off (feature completeness)

### 10.3 Infrastructure Management

**Infrastructure as Code:** Terraform

**Version Control:** All .tf files in Git

**State Management:**
- S3 backend with DynamoDB locking
- Backup: Daily snapshots
- Access: IAM role restricted

**Change Process:**
1. Make .tf changes
2. `terraform plan` - review changes
3. Code review by ops engineer
4. Approval in Terraform Cloud
5. `terraform apply` automatically

### 10.4 Monitoring & Alerting

**Metrics Collected:**
```
Application:
- Request latency (p50, p95, p99)
- Error rates
- Throughput (requests/second)
- Database query latency
- Cache hit rate
- ML inference latency

Infrastructure:
- CPU usage
- Memory usage
- Disk I/O
- Network bandwidth
- Database connections

Business:
- Users analyzed (PRs)
- Findings generated
- API calls made
- Revenue (if tracked)
```

**Alert Thresholds:**
```
CRITICAL (Page on-call):
- API latency > 500ms (p95)
- Error rate > 1%
- Database connection pool exhausted
- ML service down
- Disk space < 10%

WARNING (Slack notification):
- API latency > 300ms (p95)
- Error rate > 0.1%
- Cache hit rate < 70%
- Database CPU > 80%
- Slow query detected (> 1 second)
```

### 10.5 Disaster Recovery

**RTO (Recovery Time Objective):** 1 hour
**RPO (Recovery Point Objective):** 15 minutes

**Backup Strategy:**
- Daily automated backups (AWS RDS)
- Hourly incremental snapshots
- Geo-replicated to secondary region
- Test restore monthly

**Failover Process:**
1. Detect primary unavailable (5-minute timeout)
2. Promote read replica to primary (2 minutes)
3. Update DNS (propagation: 5 minutes)
4. Validate data integrity
5. Notify stakeholders

### 10.6 Incident Response

**Runbook for Common Incidents:**

**Incident: API Service Down**
1. Check service status dashboard
2. Check AWS CloudWatch alarms
3. Restart ECS tasks (auto-restarts)
4. If not resolved: Roll back last deployment
5. Investigate root cause post-incident
6. Runbook: https://internal-wiki/incidents/api-down

**Incident: Database Slow**
1. Check active connections
2. Check slow query log
3. Identify blocking query
4. Kill long-running query (if safe)
5. Check for indexes
6. Escalate to DBA

**Incident: ML Model Not Responding**
1. Check ML service logs
2. Check queue depth
3. Restart ML workers
4. If not resolved: Use fallback (basic linting)
5. Notify users of degraded service
6. Investigate root cause

---

### Section 11: DEVELOPMENT ENVIRONMENT

**Purpose:** 
How developers set up and use local environment

**Length:** 
2 pages

```markdown
## Development Environment Setup

### 11.1 Local Development Setup

**Prerequisites:**
- Node.js 18 LTS
- Python 3.10+
- PostgreSQL 14
- Redis 6.0+
- Docker & Docker Compose

**Quick Start:**
```bash
# Clone repository
git clone https://github.com/company/autoreview.git
cd autoreview

# Install dependencies
npm install              # Frontend + API
cd ml_service && pip install -r requirements.txt

# Start services
docker-compose up -d

# Run database migrations
npm run migrate

# Seed test data
npm run seed

# Start dev servers
npm run dev:all

# Access application
Frontend: http://localhost:3000
API: http://localhost:3001/api/v1
```

**Environment Configuration:**
```
.env.local (local development):
REACT_APP_API_URL=http://localhost:3001/api/v1
REACT_APP_GITHUB_CLIENT_ID=<github-app-id>
DATABASE_URL=postgresql://user:pass@localhost/autoreview_dev
REDIS_URL=redis://localhost:6379
GITHUB_WEBHOOK_SECRET=test_secret
JWT_SECRET=dev_secret

NEVER commit .env files (in .gitignore)
Use .env.example as template
```

### 11.2 Database Migrations

**Tool:** Alembic

**Workflow:**
```bash
# Create migration after schema change
alembic revision --autogenerate -m "Add findings table"

# Review generated migration file
cat alembic/versions/abc123_add_findings_table.py

# Apply migration
alembic upgrade head

# Rollback if needed
alembic downgrade -1

# Version control
git add alembic/versions/
git commit -m "Add database migration: findings table"
```

### 11.3 Code Quality Tools

**Linting:** ESLint
```bash
npm run lint              # Check for issues
npm run lint:fix         # Auto-fix issues
```

**Formatting:** Prettier
```bash
npm run format           # Auto-format code
```

**Type Checking:** TypeScript
```bash
npm run type-check      # Check types without building
```

**Testing:**
```bash
npm test                # Run all tests
npm test -- --coverage  # With coverage
npm test -- --watch     # Watch mode
```

### 11.4 Git Workflow

**Branch Naming:**
```
feature/pr-analysis       - New feature
bugfix/fix-sql-detection  - Bug fix
chore/update-deps         - Maintenance
docs/api-docs            - Documentation
```

**Commit Message Format:**
```
<type>(<scope>): <subject>

feat(api): add webhook endpoint for GitHub
fix(ml): improve SQL injection detection
docs(api): update endpoint documentation
chore(deps): upgrade React to 18.2.0
```

**PR Requirements:**
- ✓ All tests passing
- ✓ Code coverage > 80%
- ✓ No linting errors
- ✓ At least 1 approval
- ✓ Signed commits (git -S)
```

---

## BEST PRACTICES FOR TRD WRITING

✅ **DO:**
- Be specific with versions (not "latest")
- Include rationale for every decision
- Provide code examples
- Document trade-offs
- Update as implementation reveals issues
- Include diagrams and visual explanations
- Specify performance targets with metrics
- Document security measures explicitly
- Include deployment procedures
- Make it searchable and well-organized

❌ **DON'T:**
- Be vague about technology choices
- Skip performance considerations
- Ignore security concerns
- Write without consulting engineering team
- Make assumptions without testing
- Skip error handling specifications
- Forget about edge cases
- Make the document too long
- Introduce new tech without strong reason
- Leave it unmaintained after launch

---

## TEMPLATE CHECKLIST

```markdown
## TRD Completion Checklist

### Section 1: Cover Page
- [ ] Document title and version
- [ ] Owner name and contact
- [ ] Key stakeholder list
- [ ] Approval signatures
- [ ] Status clearly indicated

### Section 2: Executive Summary
- [ ] System overview (2-3 sentences)
- [ ] Technology stack listed
- [ ] Architecture pattern explained
- [ ] Performance targets defined
- [ ] Resource requirements stated
- [ ] Key risks identified
- [ ] Development timeline provided

### Section 3: System Architecture
- [ ] High-level architecture diagram
- [ ] Component descriptions
- [ ] Architecture pattern justified
- [ ] Data flow diagrams
- [ ] Deployment architecture
- [ ] Design decisions documented

### Section 4: Technology Stack
- [ ] Frontend tech stack with versions
- [ ] Backend tech stack with versions
- [ ] Database technology justified
- [ ] Infrastructure tech specified
- [ ] Version constraints clear
- [ ] Rationale for each choice

### Section 5: API Specifications
- [ ] All endpoints documented
- [ ] Request/response examples
- [ ] Error handling specified
- [ ] Rate limiting defined
- [ ] Authentication approach
- [ ] Status codes listed

### Section 6: Database Schema
- [ ] All tables documented
- [ ] Column types specified
- [ ] Primary/foreign keys defined
- [ ] Indexes planned
- [ ] Relationships shown
- [ ] Sample data provided

### Section 7: Security Architecture
- [ ] Authentication method defined
- [ ] Authorization approach specified
- [ ] Encryption at rest/transit
- [ ] Input validation rules
- [ ] Security headers listed
- [ ] Compliance requirements noted

### Section 8: Performance & Optimization
- [ ] Performance targets defined
- [ ] Caching strategy
- [ ] Database optimization
- [ ] Load testing plan
- [ ] Scalability approach

### Section 9: Testing Strategy
- [ ] Unit test targets
- [ ] Integration test plan
- [ ] E2E test scenarios
- [ ] Performance test approach
- [ ] Security test plan

### Section 10: Deployment & Operations
- [ ] Deployment strategy
- [ ] Release process
- [ ] Monitoring approach
- [ ] Alerting thresholds
- [ ] Disaster recovery plan
- [ ] Incident response runbooks

### Section 11: Development Environment
- [ ] Setup instructions
- [ ] Environment configuration
- [ ] Database migration process
- [ ] Code quality tools
- [ ] Git workflow

### General
- [ ] Document is well-organized
- [ ] Includes diagrams and visuals
- [ ] Code examples provided
- [ ] All decisions explained
- [ ] Stakeholders reviewed
- [ ] Sign-off obtained
```

---

**Final Notes:**
- A good TRD prevents 90% of engineering issues
- Share regularly - get feedback from team
- Update as implementation reveals new insights
- This is a living document - adapt to your needs
- Keep it focused and readable
