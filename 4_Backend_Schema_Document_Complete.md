# BACKEND SCHEMA DOCUMENT - Complete Guide

## Table of Contents
1. What is Backend Schema Document?
2. Purpose & Importance
3. Who Creates It?
4. When to Create It?
5. Complete Structure & Components
6. Real Examples & SQL
7. Database Design Patterns
8. Performance Optimization
9. Data Management
10. Best Practices
11. Template & Checklist

---

## 1. WHAT IS BACKEND SCHEMA DOCUMENT?

**Backend Schema Document** is a comprehensive specification that defines:
- **WHAT** data the system stores
- **HOW** data is organized and structured
- **WHICH** relationships exist between data
- **HOW** data is accessed and queried
- **WHAT** constraints and rules apply
- **HOW** data scales and performs
- **WHAT** backup and recovery strategy exists

### Key Characteristics:
- **Data-centric** - focuses on data structure
- **Detailed** - every table, column, relationship specified
- **Performance-focused** - indexes and optimization planned
- **Scalability-conscious** - designed for growth
- **Complete** - all data requirements documented
- **Technical** - for database architects and engineers
- **Maintainable** - clear structure for future changes

### Who Reads Backend Schema Document?
- Database Architects ✓
- Backend Engineers ✓
- DevOps Engineers ✓
- Data Analysts ✓
- QA Engineers (test data) ✓
- Security Engineers ✓

---

## 2. PURPOSE & IMPORTANCE

### Why Is Backend Schema Important?

**Data Integrity:**
- Ensures data consistency and accuracy
- Prevents invalid data entry
- Maintains referential integrity
- Reduces data quality issues

**Performance:**
- Proper indexing strategy
- Optimized query performance
- Reduced database load
- Better response times

**Scalability:**
- Plans for growth
- Identifies partitioning strategy
- Enables replication and sharding
- Anticipates bottlenecks

**Security:**
- Encryption specifications
- Access control design
- Data masking for sensitive data
- Audit trail capabilities

**Development Efficiency:**
- Clear contracts for API responses
- Consistent data structure
- Easier migrations
- Better onboarding

**Maintainability:**
- Historical context for changes
- Clear understanding of relationships
- Documentation for future developers
- Reference for troubleshooting

**Compliance:**
- GDPR data retention rules
- HIPAA encryption requirements
- SOC 2 audit logging
- PCI-DSS security measures

---

## 3. WHO CREATES IT?

### Primary Owner: **Database Architect / Senior Backend Engineer**

**Responsibilities:**
- Designs overall data model
- Evaluates database technology
- Plans for scale and performance
- Documents schema
- Reviews migrations
- Maintains schema evolution

### Contributors:

**Backend Engineers:**
- Provide implementation insights
- Identify access patterns
- Suggest optimizations
- Validate feasibility

**Data Analysts:**
- Define reporting requirements
- Identify analytical queries
- Plan data warehouse schema
- Suggest denormalization opportunities

**DevOps Engineer:**
- Plans replication strategy
- Designs backup procedures
- Plans monitoring
- Ensures recovery procedures work

**Security Engineer:**
- Specifies encryption
- Defines access controls
- Plans audit logging
- Reviews data retention

**Product Manager:**
- Provides business requirements
- Identifies data needs
- Explains data relationships
- Reviews data retention needs

### Sign-off Required From:
- Database Architect ✓
- Engineering Lead ✓
- Security Engineer ✓
- DevOps Lead ✓

---

## 4. WHEN TO CREATE IT?

### Timeline in Product Development:

```
Requirements → Schema Design → TRD → Development → Testing

Week 2-3:     Week 3-4:      Week 4-5:   Week 6-12:   Week 12+:
- Review     - Design       - Finalize - Implement  - Test
  PRD/TRD      tables        in TRD      migrations
- Identify   - Define       - Get      - Write SQL
  entities     relations      approval   - Verify
- Map data   - Plan         - Document - Create
  flows       indexes         migrations  tests
- Early      - Consider     - Plan DRI
  draft       scale
```

### Trigger Points for Schema Document:

✅ **During TRD creation** (parallel with architecture design)
✅ **Before backend development starts**
✅ **For new systems with significant data**
✅ **For redesigns of existing schemas**
✅ **When data volumes exceed current capacity**

### Timeline Considerations:

- **Simple feature (few tables):** 3-5 days schema design
- **Medium system (10-20 tables):** 1-2 weeks design
- **Complex system (50+ tables):** 2-4 weeks design
- **Must be complete:** Before first migration runs

---

## 5. COMPLETE STRUCTURE & COMPONENTS

### Section 1: COVER PAGE & METADATA

```markdown
# BACKEND SCHEMA DOCUMENT

**System/Database:** [Database Name]
**Version:** 1.0
**Document Owner:** [Database Architect]
**Created Date:** [Date]
**Last Updated:** [Date]
**Status:** Draft / In Review / Approved / Active

**Key Stakeholders:**
- Database Architect: [Name]
- Backend Lead: [Name]
- DevOps Lead: [Name]
- Security Lead: [Name]

**Database Details:**
- Technology: PostgreSQL 14
- Environment: Production (us-east-1)
- Region: AWS US East 1
- Replicas: 2 read replicas
- Backup: Daily automated + hourly snapshots

**Approval Sign-off:**
- Database Architect: [Signature] Date: ___
- Engineering Lead: [Signature] Date: ___
- Security: [Signature] Date: ___
- DevOps: [Signature] Date: ___

**Related Documents:**
- TRD: [Link to TRD]
- API Spec: [Link to API docs]
- Deployment Guide: [Link]
```

---

### Section 2: EXECUTIVE SUMMARY

**Purpose:** 
Brief overview of data model and key decisions

**Length:** 
1-2 pages

**Components:**

```markdown
## Executive Summary

### 2.1 Data Model Overview

**Database Type:** PostgreSQL (Relational)

**Total Tables:** 15
**Total Relationships:** 22
**Total Indexes:** 35
**Estimated Data Size:** 50GB (year 1)

**Technology Choice Rationale:**
PostgreSQL chosen for:
- ACID compliance (data consistency critical)
- Complex queries needed (user analysis)
- Advanced features (JSONB, full-text search)
- Open source (no licensing costs)
- Excellent performance (well-optimized)

Alternative Considered: MongoDB
- Reason not chosen: Needs ACID transactions
- Would need complex application logic

### 2.2 Key Entities

```
Users           - Account and authentication data
Teams           - Group management
Repositories    - GitHub repositories
Pull Requests   - Code review requests
Findings        - Analysis results
Configurations  - Team settings
Audit Logs      - Security tracking
```

### 2.3 Design Principles

1. **Normalization** - Eliminate redundancy (3NF)
   - Data stored once
   - Referenced via foreign keys
   - Reduces storage
   - Maintains consistency

2. **Performance-First** - Strategic denormalization where needed
   - Aggregate columns for common queries
   - Cached computed values
   - Trade-off: Storage for query speed

3. **Scalability** - Design for growth
   - Indexing strategy for large data
   - Partitioning when needed
   - Read replicas for scaling reads

4. **Security** - Protect sensitive data
   - Encrypt sensitive columns
   - Audit all access
   - Separate permissions per table

5. **Maintainability** - Clear structure
   - Consistent naming
   - Clear relationships
   - Well-documented

### 2.4 Growth Projections

| Year | Users | PRs/Day | Storage |
|------|-------|---------|---------|
| 1 | 10,000 | 10,000 | 50GB |
| 2 | 50,000 | 50,000 | 250GB |
| 3 | 200,000 | 200,000 | 1TB |

**Scaling Plan:**
- Year 1: Single PostgreSQL + 2 read replicas
- Year 2: Vertical scaling + partitioning of PR data
- Year 3: Horizontal sharding by organization ID

---

### Section 3: ENTITY RELATIONSHIP DIAGRAM (ERD)

**Purpose:** 
Visual representation of all tables and relationships

**Length:** 
2-3 pages with diagrams

**Components:**

```markdown
## Entity Relationship Diagram

### 3.1 ERD Visual

```
┌─────────────┐         ┌──────────────┐
│   users     │────1────│   teams      │
│             │    ∞    │              │
│ id (PK)     │         │ id (PK)      │
│ email       │         │ name         │
│ username    │         │ owner_id (FK)│
│ password    │         │ created_at   │
│ created_at  │         └──────────────┘
└─────────────┘              │
      │                      │ 1
      │ 1                    │
      │                      ├─ (∞) team_members
      │ ∞                    │
      └─ (1) team_members    │
                             │
                    ┌────────┴──────────┐
                    │                   │
            ┌───────────────┐   ┌──────────────┐
            │ repositories  │   │ pull_requests│
            │               │   │              │
            │ id (PK)       │   │ id (PK)      │
            │ team_id (FK)  │   │ repo_id (FK) │
            │ github_repo_id│   │ pr_number    │
            │ name          │   │ created_at   │
            └───────────────┘   └──────────────┘
                    │                   │
                    │ 1                 │ 1
                    │                   │
                    │ ∞                 │ ∞
                    └───────┬───────────┘
                            │
                    ┌───────────────┐
                    │   findings    │
                    │               │
                    │ id (PK)       │
                    │ pr_id (FK)    │
                    │ type          │
                    │ severity      │
                    │ message       │
                    └───────────────┘
```

### 3.2 Relationship Types

**One-to-Many (1:∞):**
```
users 1 ──── ∞ teams
- One user owns many teams
- Foreign key: teams.owner_id → users.id
- Cascading delete: If user deleted, teams deleted
```

**Many-to-Many (∞:∞):**
```
users ∞ ──── ∞ teams
        via team_members

team_members table:
- user_id (FK)
- team_id (FK)
- role (admin/developer)
- joined_at

Junction table stores the relationship
```

**One-to-One (1:1):**
```
users 1 ──── 1 user_profiles
- One user has one profile
- Foreign key: user_profiles.user_id → users.id (UNIQUE)
```

---

### Section 4: DATABASE DESIGN APPROACH

**Purpose:** 
Explain design decisions and rationale

**Length:** 
1-2 pages

```markdown
## Database Design Approach

### 4.1 Normalization Level

**Choice: Third Normal Form (3NF)**

**What is 3NF?**
1. Atomic values (no multi-valued attributes)
2. Depends on primary key (no partial dependencies)
3. No transitive dependencies (non-key attributes depend on other non-keys)

**Example (Bad - Not 3NF):**
```
users table:
- id
- email
- team_name          ❌ (depends on team, not user)
- team_creation_date ❌ (depends on team, not user)
```

**Example (Good - 3NF):**
```
users table:
- id
- email

teams table:
- id
- name
- created_at

team_members table:
- user_id (FK)
- team_id (FK)
```

**Benefits:**
- No data duplication
- Consistent data
- Easy to maintain
- Efficient storage

**Trade-off:**
- More joins needed for queries
- Slightly slower complex queries
- Mitigated with proper indexing

### 4.2 Strategic Denormalization

**Where We Denormalize (for performance):**

```
pull_requests table:
- pr_number
- author_id
- author_name ← DENORMALIZED
  (could get from users table, but access pattern frequent)
- author_avatar_url ← DENORMALIZED
  (displayed on every PR list item)

Reason:
- Every PR list shows author name + avatar
- Joining to users table for this adds latency
- We update author info rarely
- Trade-off: Storage + update complexity for query speed

Update Strategy:
- When user updates name, update all denormalized copies
- Trigger in database maintains consistency
```

### 4.3 Data Type Decisions

| Column | Type | Why |
|--------|------|-----|
| user.id | UUID | Globally unique, not guessable (vs auto-increment) |
| user.email | VARCHAR(255) | Fixed max length for emails |
| user.created_at | TIMESTAMP WITH TIME ZONE | Store timezone, consistent comparisons |
| findings.ml_confidence | DECIMAL(3,2) | Precise decimal (0.00-1.00), not float |
| pr_data | JSONB | Flexible structure, queryable JSON |
| tags | TEXT[] | Array of strings for PostgreSQL |

### 4.4 Constraint Strategy

**Primary Keys:**
- UUID (not auto-increment)
- Why: Globally unique, safe for sharding, not guessable

**Foreign Keys:**
- All relationships have explicit FKs
- Enforce referential integrity
- Cascade on delete (if appropriate)

**Unique Constraints:**
- Email (users table) - no duplicate emails
- GitHub ID + Team (repositories) - no duplicate repos per team
- User + Team (team_members) - no duplicate memberships

**Check Constraints:**
- Role IN ('admin', 'developer')
- Severity IN ('critical', 'warning', 'info')
- Email format validation (regex in code, not DB)

**Not Null Constraints:**
- Applied when column always has value
- Enforced at DB level
- Prevents NULL bugs

---

### Section 5: COMPLETE TABLE DEFINITIONS

**Purpose:** 
Detailed specification of every table

**Length:** 
6-8 pages with SQL

**Components:**

```markdown
## Complete Table Definitions

### 5.1 Users Table

**Purpose:** Store user accounts and authentication data

**SQL Definition:**
```sql
CREATE TABLE users (
  -- Primary Key
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  
  -- Authentication
  email VARCHAR(255) NOT NULL UNIQUE,
  password_hash VARCHAR(255) NOT NULL,
  github_id INTEGER NOT NULL UNIQUE,
  github_username VARCHAR(255) NOT NULL UNIQUE,
  github_token_encrypted TEXT NOT NULL,  -- Encrypted with KMS
  
  -- Profile
  first_name VARCHAR(100),
  last_name VARCHAR(100),
  avatar_url TEXT,
  
  -- Status
  is_active BOOLEAN DEFAULT true,
  role VARCHAR(50) DEFAULT 'user',
  
  -- Timestamps
  created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  
  -- Constraints
  CONSTRAINT check_valid_email CHECK (
    email ~ '^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}$'
  ),
  CONSTRAINT check_valid_role CHECK (role IN ('user', 'admin')),
  CONSTRAINT check_password_not_empty CHECK (length(password_hash) > 0)
);

-- Indexes
CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_users_github_id ON users(github_id);
CREATE INDEX idx_users_is_active ON users(is_active) WHERE is_active = true;
CREATE INDEX idx_users_created_at ON users(created_at);

-- Enable password hash function
CREATE OR REPLACE FUNCTION update_users_timestamp()
RETURNS TRIGGER AS $$
BEGIN
  NEW.updated_at = CURRENT_TIMESTAMP;
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER users_update_timestamp
BEFORE UPDATE ON users
FOR EACH ROW
EXECUTE FUNCTION update_users_timestamp();
```

**Column Details:**

| Column | Type | Constraints | Notes |
|--------|------|-----------|-------|
| id | UUID | PK | gen_random_uuid() generates on insert |
| email | VARCHAR(255) | NOT NULL, UNIQUE | Email validation in constraint |
| password_hash | VARCHAR(255) | NOT NULL | bcrypt hash, never plain text |
| github_id | INTEGER | NOT NULL, UNIQUE | From GitHub API |
| github_username | VARCHAR(255) | NOT NULL, UNIQUE | Display name, lowercase |
| github_token_encrypted | TEXT | NOT NULL | Encrypted with AWS KMS |
| first_name | VARCHAR(100) | NULLABLE | Optional, from GitHub profile |
| last_name | VARCHAR(100) | NULLABLE | Optional, from GitHub profile |
| avatar_url | TEXT | NULLABLE | URL to GitHub avatar |
| is_active | BOOLEAN | DEFAULT true | Soft delete flag |
| role | VARCHAR(50) | DEFAULT 'user' | user or admin role |
| created_at | TIMESTAMP TZ | DEFAULT NOW() | Account creation time |
| updated_at | TIMESTAMP TZ | DEFAULT NOW() | Last profile update |

**Indexes Rationale:**

| Index | Reason |
|-------|--------|
| email | Email used for login frequently |
| github_id | Used to find user on GitHub callback |
| is_active | Filter active users in queries |
| created_at | Sort by newest users, time-range queries |

**Example Rows:**
```json
{
  "id": "550e8400-e29b-41d4-a716-446655440000",
  "email": "john@example.com",
  "password_hash": "$2b$12$R9h7cIPz0gi.URNNGH3j6OPST9/PgBkqquzi.Ss7KIUgO2t0jKMm",
  "github_id": 12345678,
  "github_username": "johndoe",
  "github_token_encrypted": "enc_...",
  "first_name": "John",
  "last_name": "Doe",
  "avatar_url": "https://avatars.githubusercontent.com/u/12345678",
  "is_active": true,
  "role": "user",
  "created_at": "2024-01-15T10:30:00+00:00",
  "updated_at": "2024-01-15T10:30:00+00:00"
}
```

---

### 5.2 Teams Table

**Purpose:** Store team/organization information

**SQL Definition:**
```sql
CREATE TABLE teams (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  
  name VARCHAR(255) NOT NULL,
  description TEXT,
  owner_id UUID NOT NULL REFERENCES users(id) ON DELETE CASCADE,
  
  -- GitHub Integration
  github_org_id INTEGER,
  github_org_name VARCHAR(255),
  
  -- Settings
  is_active BOOLEAN DEFAULT true,
  
  -- Timestamps
  created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  
  CONSTRAINT check_name_not_empty CHECK (length(trim(name)) > 0)
);

CREATE INDEX idx_teams_owner ON teams(owner_id);
CREATE INDEX idx_teams_github_org ON teams(github_org_id);
CREATE INDEX idx_teams_created_at ON teams(created_at);

CREATE TRIGGER teams_update_timestamp
BEFORE UPDATE ON teams
FOR EACH ROW
EXECUTE FUNCTION update_teams_timestamp();
```

---

### 5.3 Team Members Table

**Purpose:** Manage team membership and roles (junction table for many-to-many)

**SQL Definition:**
```sql
CREATE TABLE team_members (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  
  team_id UUID NOT NULL REFERENCES teams(id) ON DELETE CASCADE,
  user_id UUID NOT NULL REFERENCES users(id) ON DELETE CASCADE,
  
  role VARCHAR(50) NOT NULL DEFAULT 'developer',
  
  joined_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  
  UNIQUE(team_id, user_id),
  CONSTRAINT check_valid_role CHECK (role IN ('admin', 'developer'))
);

CREATE INDEX idx_team_members_team ON team_members(team_id);
CREATE INDEX idx_team_members_user ON team_members(user_id);
CREATE INDEX idx_team_members_role ON team_members(role);
```

**Use Cases:**
- Find all teams a user belongs to: `SELECT team_id FROM team_members WHERE user_id = $1`
- Find all members of a team: `SELECT user_id FROM team_members WHERE team_id = $1`
- Check if user is team admin: `SELECT role FROM team_members WHERE team_id = $1 AND user_id = $2`

---

### 5.4 Repositories Table

**Purpose:** Store integrated GitHub repositories per team

**SQL Definition:**
```sql
CREATE TABLE repositories (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  
  -- Reference
  team_id UUID NOT NULL REFERENCES teams(id) ON DELETE CASCADE,
  github_repo_id INTEGER NOT NULL,
  
  -- GitHub Data
  name VARCHAR(255) NOT NULL,
  full_name VARCHAR(255) NOT NULL,  -- owner/repo
  url TEXT NOT NULL,
  description TEXT,
  
  is_private BOOLEAN DEFAULT true,
  language VARCHAR(50),
  
  -- Configuration
  is_active BOOLEAN DEFAULT true,
  
  -- Timestamps
  created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  
  UNIQUE(team_id, github_repo_id)
);

CREATE INDEX idx_repos_team ON repositories(team_id);
CREATE INDEX idx_repos_github_id ON repositories(github_repo_id);
CREATE INDEX idx_repos_is_active ON repositories(is_active);
```

---

### 5.5 Pull Requests Table

**Purpose:** Store analyzed pull requests

**SQL Definition:**
```sql
CREATE TABLE pull_requests (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  
  -- Reference
  repository_id UUID NOT NULL REFERENCES repositories(id) ON DELETE CASCADE,
  github_pr_number INTEGER NOT NULL,
  
  -- Authorship
  author_id UUID REFERENCES users(id) ON DELETE SET NULL,
  author_name VARCHAR(255),  -- DENORMALIZED for display
  author_avatar_url TEXT,    -- DENORMALIZED for display
  
  -- PR Data
  title VARCHAR(500) NOT NULL,
  description TEXT,
  
  -- Git References
  head_sha VARCHAR(40) NOT NULL,  -- Commit SHA being reviewed
  base_sha VARCHAR(40) NOT NULL,  -- Base commit SHA
  
  -- Status
  status VARCHAR(50) DEFAULT 'open',  -- open, merged, closed
  
  -- Analysis
  analyzed_at TIMESTAMP WITH TIME ZONE,
  analysis_status VARCHAR(50) DEFAULT 'pending',  -- pending, completed, failed
  
  -- Timestamps
  created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  
  UNIQUE(repository_id, github_pr_number),
  CONSTRAINT check_valid_status CHECK (status IN ('open', 'merged', 'closed')),
  CONSTRAINT check_valid_analysis_status CHECK (analysis_status IN ('pending', 'completed', 'failed'))
);

CREATE INDEX idx_prs_repo ON pull_requests(repository_id);
CREATE INDEX idx_prs_analyzed_at ON pull_requests(analyzed_at);
CREATE INDEX idx_prs_status ON pull_requests(status);
CREATE INDEX idx_prs_analysis_status ON pull_requests(analysis_status);
CREATE INDEX idx_prs_created_at ON pull_requests(created_at);

-- For finding recent PRs that need analysis
CREATE INDEX idx_prs_analysis_pending ON pull_requests(created_at DESC) 
WHERE analysis_status = 'pending';
```

---

### 5.6 Findings Table

**Purpose:** Store code review findings/issues

**SQL Definition:**
```sql
CREATE TABLE findings (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  
  -- Reference
  pull_request_id UUID NOT NULL REFERENCES pull_requests(id) ON DELETE CASCADE,
  
  -- Classification
  type VARCHAR(50) NOT NULL,          -- security, performance, quality
  category VARCHAR(100) NOT NULL,     -- sql_injection, n_plus_one, etc
  severity VARCHAR(50) NOT NULL,      -- critical, warning, info
  
  -- Location
  file_path VARCHAR(500) NOT NULL,
  line_number INTEGER NOT NULL,
  column_number INTEGER,
  
  -- Content
  message TEXT NOT NULL,
  description TEXT,
  suggestion TEXT,
  code_snippet TEXT,
  correct_code_snippet TEXT,
  
  -- External Reference
  documentation_url TEXT,
  
  -- ML Confidence
  ml_confidence_score DECIMAL(3,2),   -- 0.00 to 1.00
  
  -- Dismissal
  dismissed BOOLEAN DEFAULT false,
  dismissed_at TIMESTAMP WITH TIME ZONE,
  dismissed_reason VARCHAR(100),      -- false_positive, will_fix_later, etc
  dismissed_by_id UUID REFERENCES users(id),
  
  -- Integration
  github_comment_id BIGINT,            -- Link to GitHub comment
  
  -- Timestamps
  created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  
  CONSTRAINT check_valid_type CHECK (type IN ('security', 'performance', 'quality')),
  CONSTRAINT check_valid_severity CHECK (severity IN ('critical', 'warning', 'info')),
  CONSTRAINT check_confidence CHECK (ml_confidence_score IS NULL OR (ml_confidence_score >= 0 AND ml_confidence_score <= 1)),
  CONSTRAINT check_not_empty_message CHECK (length(trim(message)) > 0)
);

CREATE INDEX idx_findings_pr ON findings(pull_request_id);
CREATE INDEX idx_findings_type ON findings(type);
CREATE INDEX idx_findings_severity ON findings(severity);
CREATE INDEX idx_findings_file ON findings(file_path);
CREATE INDEX idx_findings_dismissed ON findings(dismissed);

-- For finding undismissed issues for a PR
CREATE INDEX idx_findings_active ON findings(pull_request_id, dismissed)
WHERE dismissed = false;

-- For finding critical security issues
CREATE INDEX idx_findings_critical_security ON findings(severity, type)
WHERE type = 'security' AND severity = 'critical';
```

---

### 5.7 Team Configuration Table

**Purpose:** Store team-specific configuration and rules

**SQL Definition:**
```sql
CREATE TABLE team_configuration (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  
  team_id UUID NOT NULL UNIQUE REFERENCES teams(id) ON DELETE CASCADE,
  
  -- Configuration as JSON (flexible structure)
  rules JSONB NOT NULL DEFAULT '{}',
  
  -- Exclusions
  exclusions JSONB,  -- Files/directories to exclude
  
  -- Supported Languages
  supported_languages TEXT[] DEFAULT ARRAY['javascript', 'python', 'java'],
  
  -- Metadata
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  updated_by_id UUID REFERENCES users(id),
  
  CONSTRAINT check_team_id_not_empty CHECK (team_id IS NOT NULL)
);

CREATE INDEX idx_team_config_team ON team_configuration(team_id);
```

**Example JSONB Structure:**
```json
{
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
        "unbounded_loops": { "enabled": true, "severity": "warning" }
      }
    },
    "quality": {
      "enabled": true,
      "severity": "info"
    }
  },
  "exclusions": {
    "directories": ["node_modules/", "build/", "dist/"],
    "files": ["*.test.js", "*.spec.js", "*.min.js"]
  }
}
```

---

### 5.8 Audit Logs Table

**Purpose:** Track all administrative actions for compliance

**SQL Definition:**
```sql
CREATE TABLE audit_logs (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  
  -- Actor
  user_id UUID REFERENCES users(id) ON DELETE SET NULL,
  
  -- Action
  action VARCHAR(100) NOT NULL,     -- user_created, config_updated, etc
  entity_type VARCHAR(50),           -- users, teams, findings, etc
  entity_id UUID,
  
  -- Change Details
  old_values JSONB,                 -- Previous values (before update)
  new_values JSONB,                 -- New values (after update)
  
  -- IP & User Agent (for security)
  ip_address INET,
  user_agent TEXT,
  
  -- Timestamp (immutable)
  created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  
  CONSTRAINT check_action_not_empty CHECK (length(trim(action)) > 0)
);

CREATE INDEX idx_audit_logs_user ON audit_logs(user_id);
CREATE INDEX idx_audit_logs_action ON audit_logs(action);
CREATE INDEX idx_audit_logs_entity ON audit_logs(entity_type, entity_id);
CREATE INDEX idx_audit_logs_created_at ON audit_logs(created_at);

-- Never allow updates/deletes on audit logs
ALTER TABLE audit_logs ENABLE ROW LEVEL SECURITY;
CREATE POLICY audit_logs_immutable ON audit_logs 
  USING (true) 
  WITH CHECK (false);
```

**Example Entries:**
```json
{
  "user_id": "550e8400-e29b-41d4-a716-446655440000",
  "action": "config_updated",
  "entity_type": "team",
  "entity_id": "team_123",
  "old_values": { "rules.security.enabled": false },
  "new_values": { "rules.security.enabled": true },
  "ip_address": "192.168.1.1",
  "created_at": "2024-01-20T10:30:00+00:00"
}
```

---

### Section 6: RELATIONSHIPS & CONSTRAINTS

**Purpose:** 
Document all foreign keys and their behavior

**Length:** 
1-2 pages

```markdown
## Relationships & Constraints

### 6.1 Relationship Map

**One-to-Many Relationships:**

```
users 1 ──────── ∞ teams
- Foreign key: teams.owner_id → users.id
- Delete behavior: CASCADE (delete team if owner deleted)
- Update behavior: CASCADE (update team if user ID changes - rare)
- Usage: Find all teams owned by user

users 1 ──────── ∞ team_members
- Foreign key: team_members.user_id → users.id
- Delete behavior: CASCADE (remove user from all teams if user deleted)
- Update behavior: CASCADE
- Usage: Find all team memberships for user

teams 1 ──────── ∞ team_members
- Foreign key: team_members.team_id → teams.id
- Delete behavior: CASCADE (remove all members if team deleted)
- Update behavior: CASCADE
- Usage: Find all members of a team

teams 1 ──────── ∞ repositories
- Foreign key: repositories.team_id → teams.id
- Delete behavior: CASCADE (delete repos if team deleted)
- Usage: Find all repositories in a team

repositories 1 ──────── ∞ pull_requests
- Foreign key: pull_requests.repository_id → repositories.id
- Delete behavior: CASCADE (delete PRs if repo deleted)
- Usage: Find all PRs in a repository

pull_requests 1 ──────── ∞ findings
- Foreign key: findings.pull_request_id → pull_requests.id
- Delete behavior: CASCADE (delete findings if PR deleted)
- Usage: Find all findings for a PR

teams 1 ──────── 1 team_configuration
- Foreign key: team_configuration.team_id → teams.id
- Delete behavior: CASCADE
- Usage: Get configuration for team
```

**Many-to-Many Relationships:**

```
users ∞ ──────── ∞ teams
(via team_members junction table)

team_members.user_id → users.id
team_members.team_id → teams.id

Allows:
- User to belong to multiple teams
- Team to have multiple members
```

---

### 6.2 Referential Integrity

**On Delete Behaviors:**

```
CASCADE:
- Delete parent record → also delete child records
- Example: Delete user → delete all team memberships

SET NULL:
- Delete parent record → set foreign key to NULL
- Example: Delete finding author → set author_id to NULL
- Requires: Foreign key column is nullable

RESTRICT:
- Cannot delete if children exist
- Example: Cannot delete team if repositories exist
- Requires: Check children first before deleting

NO ACTION:
- Same as RESTRICT but checked at end of transaction
```

**Configuration by Relationship:**

| Parent | Child | Behavior | Reason |
|--------|-------|----------|--------|
| users | teams | CASCADE | Can delete user (team goes with) |
| users | team_members | CASCADE | Remove from all teams |
| users | pull_requests | SET NULL | Keep PR history, unassign author |
| teams | repositories | CASCADE | Delete team deletes repos |
| repositories | pull_requests | CASCADE | Delete repo deletes PRs |
| pull_requests | findings | CASCADE | Delete PR deletes findings |

---

### Section 7: INDEXES & QUERY OPTIMIZATION

**Purpose:** 
Define indexing strategy for performance

**Length:** 
2-3 pages

```markdown
## Indexes & Query Optimization

### 7.1 Indexing Strategy

**When to Create Index:**
1. Foreign key columns (for joins)
2. Frequently filtered columns (WHERE clauses)
3. Frequently sorted columns (ORDER BY)
4. Frequently searched columns
5. High-cardinality columns (many unique values)

**When NOT to Index:**
1. Nullable columns (unless frequently queried)
2. Low-cardinality columns (few unique values)
3. Rarely used columns
4. Small tables (< 1000 rows)
5. Update-heavy tables (indexes slow writes)

### 7.2 Index Types & Examples

**Single Column Index (B-Tree):**

```sql
-- Used for simple lookups
CREATE INDEX idx_users_email ON users(email);

Query benefit:
SELECT * FROM users WHERE email = 'john@example.com';
-- Without index: Full table scan
-- With index: Direct lookup (~1ms)
```

**Composite Index (Multi-column):**

```sql
-- Used for queries filtering on multiple columns
CREATE INDEX idx_findings_pr_dismissed ON findings(pull_request_id, dismissed);

Query benefit:
SELECT * FROM findings 
WHERE pull_request_id = $1 AND dismissed = false;

-- PostgreSQL can use this index for both columns
-- Or just the first column (pull_request_id)
```

**Partial Index:**

```sql
-- Only index active records (most common case)
CREATE INDEX idx_users_active ON users(id) 
WHERE is_active = true;

-- Smaller index, faster inserts of deleted records
```

**Full-Text Search Index:**

```sql
-- For text searching
CREATE INDEX idx_findings_text ON findings 
USING GIN(to_tsvector('english', message || ' ' || description));

Query benefit:
SELECT * FROM findings 
WHERE to_tsvector('english', message || ' ' || description) 
  @@ to_tsquery('english', 'sql injection');
```

**Unique Index (also ensures uniqueness):**

```sql
CREATE UNIQUE INDEX idx_users_email_unique ON users(email);

-- This is both an index AND a constraint
-- Faster than UNIQUE constraint alone
```

### 7.3 Index Performance Metrics

**Monitoring Indexes:**

```sql
-- Find unused indexes (candidates for deletion)
SELECT schemaname, tablename, indexname, idx_scan
FROM pg_stat_user_indexes
ORDER BY idx_scan ASC;

-- Find slow queries
SELECT query, mean_exec_time, calls
FROM pg_stat_statements
ORDER BY mean_exec_time DESC;

-- Find missing indexes (queries doing seq scans)
SELECT * FROM pg_stat_user_tables
WHERE seq_scan > 0
ORDER BY seq_scan DESC;
```

**Index Statistics:**

```
Index Size: Monitor growing indexes
Index Fragmentation: Rebuild if > 30% bloated
Index Scan Count: Should be non-zero for indexed columns
```

### 7.4 Query Optimization Patterns

**Pattern 1: N+1 Query Problem**

❌ **SLOW (N+1 queries):**
```sql
-- First query: Get PRs
SELECT id FROM pull_requests WHERE repository_id = $1;

-- Then N queries: Get findings for each PR
FOR EACH pr_id:
  SELECT * FROM findings WHERE pull_request_id = pr_id;
-- Total: 1 + N queries
```

✓ **FAST (Single query with JOIN):**
```sql
SELECT pr.id, f.* 
FROM pull_requests pr
LEFT JOIN findings f ON pr.id = f.pull_request_id
WHERE pr.repository_id = $1
ORDER BY pr.created_at DESC;
-- Total: 1 query
```

---

**Pattern 2: Avoiding SELECT ***

❌ **SLOW:**
```sql
SELECT * FROM findings WHERE pull_request_id = $1;
-- Fetches all columns, wastes bandwidth/memory
```

✓ **FAST:**
```sql
SELECT id, message, severity, file_path, line_number 
FROM findings 
WHERE pull_request_id = $1;
-- Fetches only needed columns
```

---

**Pattern 3: Using Covering Index**

❌ **SLOW (index and table lookup):**
```sql
CREATE INDEX idx_findings_pr ON findings(pull_request_id);

SELECT message, severity FROM findings 
WHERE pull_request_id = $1;
-- Index returns PR IDs, must look up table for data
```

✓ **FAST (everything in index):**
```sql
CREATE INDEX idx_findings_pr_covering ON findings(pull_request_id) 
INCLUDE (message, severity);

-- Index contains all needed data, no table lookup
```

---

**Pattern 4: Batch Operations**

❌ **SLOW (multiple queries):**
```sql
FOR EACH user_id:
  INSERT INTO team_members (team_id, user_id) VALUES ($1, $2);
-- Slow, many round-trips
```

✓ **FAST (single batch insert):**
```sql
INSERT INTO team_members (team_id, user_id) 
VALUES 
  ($1, $2),
  ($1, $3),
  ($1, $4),
  ...
  ($1, $N);
-- Single query, much faster
```

---

### 7.5 Slow Query Monitoring

**PostgreSQL Slow Query Log:**

```sql
-- Enable slow query logging
ALTER SYSTEM SET log_min_duration_statement = 1000;  -- 1 second
ALTER SYSTEM SET log_statement = 'all';

-- View slow queries
SELECT query, mean_exec_time, calls
FROM pg_stat_statements
WHERE mean_exec_time > 1000
ORDER BY mean_exec_time DESC;

-- Clear statistics
SELECT pg_stat_statements_reset();
```

---

### Section 8: DATA TYPES & STORAGE

**Purpose:** 
Explain data types and storage requirements

**Length:** 
1-2 pages

```markdown
## Data Types & Storage

### 8.1 Data Type Selection

**String Types:**

```sql
CHAR(n)         -- Fixed length (pad with spaces)
  Size: Always n bytes
  Use case: Codes (status codes, roles)
  
VARCHAR(n)      -- Variable length up to n
  Size: Actual length + 1-4 bytes overhead
  Use case: Names, emails, short text
  
TEXT            -- Unlimited length
  Size: Actual length + overhead
  Use case: Long text (descriptions, code)
  
UUID            -- Universally unique identifier
  Size: 16 bytes (vs 4 bytes for auto-increment)
  Use case: Primary keys, security
```

**Numeric Types:**

```sql
INTEGER (INT)   -- Whole numbers: -2B to 2B
  Size: 4 bytes
  Use case: Counts, IDs
  
BIGINT          -- Large whole numbers: -9E18 to 9E18
  Size: 8 bytes
  Use case: GitHub IDs, timestamps
  
DECIMAL(p, s)   -- Exact decimal
  Size: Variable (1-9 bytes)
  Precision p: Total digits
  Scale s: Decimal places
  Use case: Money, scores (0.00-1.00)
  
FLOAT/DOUBLE    -- Approximate decimal
  Size: 4-8 bytes
  Use case: Scientific data (not money!)
```

**Temporal Types:**

```sql
DATE            -- Date only (2024-01-15)
  Size: 4 bytes
  
TIME            -- Time only (14:30:00)
  Size: 8 bytes
  
TIMESTAMP       -- Date + time (2024-01-15 14:30:00)
  Size: 8 bytes
  Issue: No timezone info
  
TIMESTAMP WITH TIME ZONE -- Date + time + timezone
  Size: 8 bytes
  Best for: Global applications
  ALWAYS use this for user-visible timestamps
```

**Boolean Type:**

```sql
BOOLEAN         -- true/false
  Size: 1 byte
  Use case: Flags (is_active, is_admin)
```

**JSON Types:**

```sql
JSON            -- Text-based JSON
  Size: Variable, text format
  Use case: Flexible data
  
JSONB           -- Binary JSON
  Size: Variable, binary format
  Use case: Queryable JSON (better for PostgreSQL)
  Faster for: Queries, operations
  Slower for: Insertion (parsing overhead)
  Recommended: Use JSONB for new code
```

**Array Types:**

```sql
TEXT[]          -- Array of strings
  Size: Variable
  Use case: Tags, supported languages
  
INTEGER[]       -- Array of numbers
  Use case: IDs, scores
```

### 8.2 Storage Calculation

**Example: Expected storage for users table**

```
Columns per row:
- id (UUID): 16 bytes
- email (VARCHAR): avg 30 bytes
- password_hash (VARCHAR): 60 bytes
- github_id (INTEGER): 4 bytes
- github_username (VARCHAR): avg 15 bytes
- first_name (VARCHAR): avg 15 bytes
- last_name (VARCHAR): avg 15 bytes
- avatar_url (TEXT): avg 100 bytes
- is_active (BOOLEAN): 1 byte
- role (VARCHAR): 10 bytes
- created_at (TIMESTAMP TZ): 8 bytes
- updated_at (TIMESTAMP TZ): 8 bytes
- Overhead: ~24 bytes (PostgreSQL per-row overhead)

Total per row: ~306 bytes

For 100,000 users:
100,000 × 306 bytes = 30.6 MB (plus indexes)
```

---

### Section 9: SECURITY & ENCRYPTION

**Purpose:** 
Document security measures for sensitive data

**Length:** 
1-2 pages

```markdown
## Security & Encryption

### 9.1 Sensitive Data Classification

**Level 1 (Highly Sensitive):**
- GitHub tokens
- Password hashes
- API keys
- Encryption keys
- User IP addresses

**Level 2 (Sensitive):**
- Email addresses
- Names
- Avatar URLs
- Configuration settings

**Level 3 (Non-sensitive):**
- Pull request numbers
- Finding messages
- Public code snippets

### 9.2 Encryption at Rest

**GitHub Token Encryption:**

```sql
-- Don't store plaintext GitHub tokens
github_token_encrypted TEXT NOT NULL,

-- Encryption approach: AWS KMS
-- Application code encrypts before INSERT
-- Application code decrypts after SELECT

-- How it works:
1. User authenticates with GitHub
2. GitHub returns access token
3. Application encrypts token with AWS KMS
4. Stores encrypted blob in database
5. On use: Decrypt token, use, discard

-- Never log tokens
-- Never display tokens in UI
-- Rotate tokens annually
```

**Password Hash Storage:**

```sql
password_hash VARCHAR(255) NOT NULL,

-- Must use bcrypt, not plaintext
-- Cost factor: 12 (2^12 iterations)
-- Never store plaintext password

-- Generation (Node.js example):
const bcrypt = require('bcrypt');
const salt = await bcrypt.genSalt(12);
const hash = await bcrypt.hash(password, salt);

-- Verification:
const match = await bcrypt.compare(password, hash);
```

### 9.3 Encryption in Transit

**TLS Requirements:**
- All database connections: TLS 1.3 minimum
- All API responses: TLS 1.3 minimum
- Certificate verification: Always enabled

### 9.4 Access Control

**Column-Level Security:**

```sql
-- Restrict access to sensitive columns
CREATE POLICY github_token_secret ON users
  FOR SELECT
  USING (
    current_user = 'system_user'  -- Only app user can see
    OR auth.uid() = id            -- Or the user themselves
  );

-- Apply to sensitive columns
ALTER TABLE users ENABLE ROW LEVEL SECURITY;
ALTER TABLE users FORCE ROW LEVEL SECURITY;
```

### 9.5 Audit Logging

```sql
-- Trigger to log all changes
CREATE OR REPLACE FUNCTION audit_changes()
RETURNS TRIGGER AS $$
BEGIN
  INSERT INTO audit_logs (user_id, action, entity_type, entity_id, old_values, new_values)
  VALUES (current_user, TG_OP, TG_TABLE_NAME, NEW.id, row_to_json(OLD), row_to_json(NEW));
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;

-- Apply to all sensitive tables
CREATE TRIGGER audit_users_changes AFTER INSERT OR UPDATE OR DELETE ON users
  FOR EACH ROW EXECUTE FUNCTION audit_changes();
CREATE TRIGGER audit_config_changes AFTER UPDATE ON team_configuration
  FOR EACH ROW EXECUTE FUNCTION audit_changes();
```

---

### Section 10: PERFORMANCE & SCALING

**Purpose:** 
Plan for growth and performance optimization

**Length:** 
1-2 pages

```markdown
## Performance & Scaling

### 10.1 Performance Targets

**Query Performance:**

| Query Type | Target | Actual Target |
|-----------|--------|--------------|
| Lookup (by PK) | < 10ms | < 5ms |
| Filter (indexed) | < 100ms | < 50ms |
| Join (2 tables) | < 200ms | < 100ms |
| Aggregate | < 500ms | < 200ms |
| Complex query | < 1000ms | < 500ms |

**Database Performance:**

```
- Query latency p95: < 100ms
- Query latency p99: < 500ms
- Connection pool: 50-100 connections
- CPU usage: < 70% (alert at 80%)
- Memory usage: < 80%
- Disk I/O: Monitor IOPs
```

### 10.2 Scalability Strategy

**Year 1 (0-50GB):**
- Single PostgreSQL instance
- 2 read replicas
- No special partitioning

**Year 2 (50-250GB):**
- Partition pull_requests and findings by date
- Add more read replicas
- Optimize queries

**Year 3 (250GB-1TB):**
- Consider sharding by organization
- Separate reporting database
- Archive old data

### 10.3 Partitioning Strategy

**Partition pull_requests by month:**

```sql
CREATE TABLE pull_requests_2024_01 PARTITION OF pull_requests
  FOR VALUES FROM ('2024-01-01') TO ('2024-02-01');

CREATE TABLE pull_requests_2024_02 PARTITION OF pull_requests
  FOR VALUES FROM ('2024-02-01') TO ('2024-03-01');

-- Benefits:
-- - Faster queries on recent data
-- - Faster archival of old data
-- - Easier maintenance
```

### 10.4 Connection Pooling

**PgBouncer Configuration:**

```ini
[databases]
autoreview = host=db.example.com port=5432 dbname=autoreview

[pgbouncer]
pool_mode = transaction  -- Connection per query
max_client_conn = 1000   -- Max client connections
default_pool_size = 25   -- Connections per client
reserve_pool_size = 5    -- Emergency connections
reserve_pool_timeout = 3
max_idle = 600
```

---

### Section 11: DATA MIGRATION & VERSIONING

**Purpose:** 
Track schema changes over time

**Length:** 
1-2 pages

```markdown
## Data Migrations & Versioning

### 11.1 Migration Strategy

**Tool:** Alembic (for Python) or Flyway (SQL-based)

**Workflow:**

```
1. Make code changes
2. Create migration: alembic revision --autogenerate -m "message"
3. Review migration file
4. Test locally
5. Code review approval
6. Apply to staging
7. Test thoroughly
8. Apply to production
9. Monitor for issues
10. Roll back if problems (if possible)
```

### 11.2 Migration Examples

**Migration 001: Initial Schema**

```sql
-- file: 001_create_initial_schema.sql
-- status: Applied (2024-01-01)

CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  email VARCHAR(255) NOT NULL UNIQUE,
  password_hash VARCHAR(255) NOT NULL,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE teams (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  name VARCHAR(255) NOT NULL,
  owner_id UUID NOT NULL REFERENCES users(id),
  created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP
);

-- Status: ✓ Applied
-- Duration: 50ms
-- Downtime: None
```

**Migration 002: Add GitHub Integration**

```sql
-- file: 002_add_github_integration.sql
-- status: Applied (2024-01-10)

-- Add GitHub fields to users
ALTER TABLE users ADD COLUMN github_id INTEGER;
ALTER TABLE users ADD COLUMN github_username VARCHAR(255);
ALTER TABLE users ADD COLUMN github_token_encrypted TEXT;

-- Create unique constraint
ALTER TABLE users ADD CONSTRAINT unique_github_id UNIQUE(github_id);

-- Create index
CREATE INDEX idx_users_github_id ON users(github_id);

-- Status: ✓ Applied
-- Duration: 120ms
-- Downtime: None (alter table non-blocking)
```

**Migration 003: Add Findings Table**

```sql
-- file: 003_create_findings_table.sql
-- status: Applied (2024-01-20)

CREATE TABLE findings (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  pull_request_id UUID NOT NULL REFERENCES pull_requests(id) ON DELETE CASCADE,
  type VARCHAR(50) NOT NULL,
  category VARCHAR(100) NOT NULL,
  severity VARCHAR(50) NOT NULL,
  message TEXT NOT NULL,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP
);

CREATE INDEX idx_findings_pr ON findings(pull_request_id);
CREATE INDEX idx_findings_type ON findings(type);

-- Status: ✓ Applied
-- Duration: 200ms
-- Downtime: None
```

### 11.3 Zero-Downtime Deployments

**Approach: Feature Flags**

```
1. Deploy with feature flag OFF
2. Add new column/table
3. Application: Handles both old and new code paths
4. Verify data in new column
5. Enable feature flag (switch to new code path)
6. Monitor
7. Later: Remove old code path
8. Clean up: Remove old column
```

**Example:**

```sql
-- Step 1: Add new column (backwards compatible)
ALTER TABLE users ADD COLUMN github_id INTEGER;

-- Step 2: Backfill existing data
UPDATE users SET github_id = 12345 WHERE email = 'john@example.com';

-- Step 3: Application code handles both:
github_id = user.github_id || user.legacy_github_id

-- Step 4: Enable feature flag
UPDATE feature_flags SET enabled = true WHERE name = 'use_github_id';

-- Step 5 (later): Remove legacy column
ALTER TABLE users DROP COLUMN legacy_github_id;
```

### 11.4 Rollback Strategy

**Reversible Migration:**

```sql
-- UP (apply change)
ALTER TABLE users ADD COLUMN nickname VARCHAR(100);

-- DOWN (undo change)
ALTER TABLE users DROP COLUMN nickname;
```

**Non-reversible (requires caution):**

```sql
-- Cannot easily undo deleting data
DELETE FROM users WHERE is_inactive = true;

-- Solution: Backup before, or keep in archive table
CREATE TABLE users_archived AS 
  SELECT * FROM users WHERE is_inactive = true;
DELETE FROM users WHERE is_inactive = true;
```

---

### Section 12: BACKUP & DISASTER RECOVERY

**Purpose:** 
Plan for data protection and recovery

**Length:** 
1-2 pages

```markdown
## Backup & Disaster Recovery

### 12.1 Backup Strategy

**Backup Types:**

```
Full Backup: Daily (00:00 UTC)
- Entire database
- Size: ~50GB (Year 1)
- Retention: 30 days

Incremental Backup: Hourly
- Only changed data
- Size: ~2GB per backup
- Retention: 7 days

Point-in-Time Recovery: WAL (Write-Ahead Logs)
- Transaction logs
- Enables recovery to any second
- Retention: 7 days
```

**AWS RDS Backup:**

```
- Automated backups: 30-day retention
- Manual snapshots: Indefinite retention
- Cross-region: Replicated to secondary region
- Geo-redundant: Survives region failure
```

### 12.2 Recovery Procedures

**RPO (Recovery Point Objective):** 15 minutes max
**RTO (Recovery Time Objective):** 1 hour max

**Scenario 1: Data Corruption**

```
1. Detect corruption (validation query)
2. Identify affected rows
3. Restore from backup (< 15 min old)
4. Reapply transactions after backup
5. Verify data integrity
6. Switch to recovered database
7. Monitor closely
8. Root cause analysis

Total RTO: ~30 minutes
```

**Scenario 2: Region Failure**

```
1. Detect primary region unavailable
2. Promote read replica in secondary region (2 min)
3. Update DNS (5 min propagation)
4. Verify replication completed
5. Monitor for anomalies
6. After 1 hour, declare successful failover

Total RTO: ~10 minutes
```

---

## 6. REAL-WORLD EXAMPLE QUERIES

**Purpose:** 
Show common queries using the schema

**Length:** 
1-2 pages

```markdown
## Real-World Query Examples

### Query 1: Get Recent PRs with Findings Count

```sql
SELECT 
  pr.id,
  pr.github_pr_number,
  pr.title,
  pr.author_name,
  COUNT(f.id) as finding_count,
  COALESCE(SUM(CASE WHEN f.severity = 'critical' THEN 1 ELSE 0 END), 0) as critical_count,
  COALESCE(SUM(CASE WHEN f.severity = 'warning' THEN 1 ELSE 0 END), 0) as warning_count
FROM pull_requests pr
LEFT JOIN findings f ON pr.id = f.pull_request_id
WHERE pr.repository_id = $1
  AND pr.created_at > NOW() - INTERVAL '7 days'
GROUP BY pr.id
ORDER BY pr.created_at DESC;

-- Uses indexes: idx_prs_repo, idx_prs_created_at
-- Performance: ~100ms for 1000 PRs
```

---

### Query 2: Find Active Users in Teams

```sql
SELECT DISTINCT
  u.id,
  u.email,
  u.first_name,
  u.last_name,
  COUNT(DISTINCT t.id) as team_count
FROM users u
INNER JOIN team_members tm ON u.id = tm.user_id
INNER JOIN teams t ON tm.team_id = t.id
WHERE u.is_active = true
  AND t.is_active = true
  AND tm.role = 'admin'
GROUP BY u.id
HAVING COUNT(DISTINCT t.id) > 0;

-- Uses indexes: idx_users_is_active, idx_team_members_user, idx_teams_owner
-- Performance: ~50ms
```

---

### Query 3: Find Critical Security Issues

```sql
SELECT 
  f.id,
  f.message,
  f.file_path,
  f.line_number,
  pr.github_pr_number,
  r.full_name as repository,
  t.name as team_name
FROM findings f
INNER JOIN pull_requests pr ON f.pull_request_id = pr.id
INNER JOIN repositories r ON pr.repository_id = r.id
INNER JOIN teams t ON r.team_id = t.id
WHERE f.type = 'security'
  AND f.severity = 'critical'
  AND f.dismissed = false
  AND pr.created_at > NOW() - INTERVAL '30 days'
ORDER BY f.created_at DESC;

-- Uses indexes: idx_findings_critical_security, idx_prs_created_at
-- Performance: ~50ms
```

---

### Query 4: Team Analytics

```sql
SELECT 
  t.id,
  t.name,
  COUNT(DISTINCT r.id) as repository_count,
  COUNT(DISTINCT pr.id) as pr_count,
  COUNT(DISTINCT f.id) as total_findings,
  ROUND(AVG(CASE WHEN f.severity = 'critical' THEN 1 ELSE 0 END), 2) as critical_avg,
  COUNT(DISTINCT tm.user_id) as member_count
FROM teams t
LEFT JOIN repositories r ON t.id = r.team_id
LEFT JOIN pull_requests pr ON r.id = pr.repository_id
LEFT JOIN findings f ON pr.id = f.pull_request_id
LEFT JOIN team_members tm ON t.id = tm.team_id
WHERE pr.created_at > NOW() - INTERVAL '30 days'
GROUP BY t.id
ORDER BY total_findings DESC;

-- Performance: ~500ms for all teams
```

---

## 7. DATA MANAGEMENT POLICIES

**Purpose:** 
Define rules for data retention and cleanup

**Length:** 
1 page

```markdown
## Data Management Policies

### Data Retention Policies

| Data Type | Retention | Action |
|-----------|-----------|--------|
| Active User | Forever | Never delete |
| Inactive User (>2 years) | 7 years | Archive to cold storage |
| Pull Requests | 7 years | Keep in database |
| Findings | 7 years | Keep in database |
| Audit Logs | 7 years | Keep immutable |
| Backups | 30 days rolling | Daily cleanup |
| Session Data | 30 days | Automatic cleanup |

### Purging Old Data

```sql
-- Archive inactive PRs to archive table
INSERT INTO pull_requests_archive
SELECT * FROM pull_requests
WHERE created_at < NOW() - INTERVAL '5 years'
  AND status IN ('merged', 'closed');

DELETE FROM pull_requests
WHERE created_at < NOW() - INTERVAL '5 years'
  AND status IN ('merged', 'closed');

-- Reclaim space
VACUUM ANALYZE pull_requests;
REINDEX TABLE pull_requests;
```

---

## BEST PRACTICES FOR BACKEND SCHEMA

✅ **DO:**
- Use UUID for primary keys (sharding-friendly)
- Always use TIMESTAMP WITH TIME ZONE
- Index foreign keys and frequently filtered columns
- Document rationale for each design decision
- Plan for scale from the beginning
- Use meaningful table and column names
- Create migrations for every change
- Test migrations on staging first
- Monitor query performance
- Keep schema documentation updated

❌ **DON'T:**
- Use SERIAL auto-increment (not sharding-friendly)
- Store timestamps without timezone info
- Over-index (hurts write performance)
- Store derived/calculated values (except strategic denorm)
- Use JSON for relational data
- Skip constraint validation
- Apply all migrations at once
- Deploy migrations without testing
- Ignore slow query logs
- Comment out constraints

---

## TEMPLATE CHECKLIST

```markdown
## Backend Schema Document Completion Checklist

### Section 1: Cover Page
- [ ] Document title and version
- [ ] Database owner and contact
- [ ] Stakeholder list
- [ ] Approval signatures
- [ ] Database technology specified

### Section 2: Executive Summary
- [ ] Data model overview
- [ ] Key entities listed
- [ ] Design principles stated
- [ ] Growth projections provided
- [ ] Technology choice rationale

### Section 3: ERD
- [ ] Entity Relationship Diagram visual
- [ ] All tables shown
- [ ] All relationships documented
- [ ] Cardinality indicated (1:1, 1:∞, ∞:∞)

### Section 4: Database Design
- [ ] Normalization level explained
- [ ] Denormalization rationale
- [ ] Data type decisions documented
- [ ] Constraint strategy defined

### Section 5: Table Definitions
- [ ] Every table documented
- [ ] All columns with types
- [ ] Primary keys defined
- [ ] Foreign keys specified
- [ ] Indexes planned
- [ ] Example rows provided

### Section 6: Relationships
- [ ] All foreign keys documented
- [ ] Delete behavior specified
- [ ] Referential integrity explained
- [ ] Cascade rules defined

### Section 7: Indexes
- [ ] Indexing strategy explained
- [ ] All indexes listed
- [ ] Index rationale provided
- [ ] Query optimization patterns shown

### Section 8: Data Types
- [ ] Data type choices explained
- [ ] Storage calculations
- [ ] Growth projections

### Section 9: Security
- [ ] Sensitive data identified
- [ ] Encryption approach
- [ ] Access control strategy
- [ ] Audit logging plan

### Section 10: Performance
- [ ] Query performance targets
- [ ] Scaling strategy
- [ ] Partitioning plan
- [ ] Connection pooling

### Section 11: Migrations
- [ ] Migration strategy
- [ ] Example migrations
- [ ] Zero-downtime approach
- [ ] Rollback procedures

### Section 12: Backup & Recovery
- [ ] Backup strategy (frequency, retention)
- [ ] RPO and RTO defined
- [ ] Recovery procedures
- [ ] Disaster recovery plan

### Section 13: Examples
- [ ] Common query examples
- [ ] Performance notes for queries
- [ ] Data management policies

### General
- [ ] Document well-organized
- [ ] Includes diagrams and visuals
- [ ] SQL examples provided
- [ ] All decisions explained
- [ ] Stakeholders reviewed
- [ ] Sign-off obtained
- [ ] Version controlled
```

---

## MAINTENANCE & UPDATES

**Document Maintenance Schedule:**

```
Weekly: Monitor slow queries, adjust indexes
Monthly: Review growth trends, validate projections
Quarterly: Schema review, identify improvements
Yearly: Major review, plan next year changes

Update Frequency:
- After schema change: Immediately update doc
- After migration: Document migration
- After performance issue: Update optimization section
- After security finding: Update security section
```

---

**Final Notes:**
- A good schema prevents 80% of performance issues
- Plan for scale from the beginning
- Document all decisions - your future self will thank you
- Test migrations on production-like data
- Monitor and optimize continuously
- This is a living document - keep it current
