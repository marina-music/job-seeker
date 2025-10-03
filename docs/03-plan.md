# Job Application Assistant - Execution Plan (DAG)

## Overview
This execution plan breaks down the project into phases and tasks, organized as a Directed Acyclic Graph (DAG) showing task dependencies and parallelization opportunities.

---

## Phase 0: Foundation & Research (Days 1-3)

### Tasks (Can run in parallel):

#### T0.1: Project Setup & Documentation
- [ ] **Status**: Not Started
- **Duration**: 1 day
- **Dependencies**: None
- **Outputs**:
  - vision.md
  - Repository structure
  - README.md
  - .gitignore
- **Tasks**:
  - Initialize Git repository
  - Create vision.md document
  - Set up basic project structure
  - Define directory layout (src/, tests/, docs/, data/)

#### T0.2: Research Job Boards & APIs
- [ ] **Status**: Not Started
- **Duration**: 2 days
- **Dependencies**: None
- **Outputs**:
  - docs/job-boards-research.md
  - List of accessible job boards with API details
- **Tasks**:
  - Research Canadian job boards (Indeed, LinkedIn, Glassdoor, Job Bank)
  - Research data science specific boards (Kaggle Jobs, AI Jobs)
  - Research healthcare/biotech boards (BioSpace, MedReps)
  - Document API availability, rate limits, authentication
  - Identify scraping requirements where APIs unavailable
  - Document data schemas from each source

#### T0.3: Research Application Success Factors
- [x] **Status**: Complete
- **Duration**: 1 day
- **Dependencies**: None
- **Outputs**:
  - docs/application-best-practices.md
- **Tasks**:
  - Research portfolio impact on interview rates
  - Document best practices for data science applications
  - Identify key success factors for technical roles
  - Research GitHub/online presence importance

#### T0.4: Design GitHub Issue Templates
- [ ] **Status**: Not Started
- **Duration**: 0.5 days
- **Dependencies**: T0.1 (vision.md)
- **Outputs**:
  - .github/ISSUE_TEMPLATE/vision.md
  - .github/ISSUE_TEMPLATE/feature.md
  - .github/ISSUE_TEMPLATE/epic.md
  - .github/ISSUE_TEMPLATE/user-story.md
- **Tasks**:
  - Design vision template
  - Design feature template
  - Design epic template
  - Design user story template
  - Set up GitHub repository with templates

---

## Phase 1: Infrastructure Setup (Days 4-6)

### Tasks:

#### T1.1: Database Setup
- **Duration**: 1 day
- **Dependencies**: T0.1 (project structure)
- **Outputs**:
  - PostgreSQL database configured
  - pgvector extension installed
  - Database schema design document
- **Tasks**:
  - Install PostgreSQL locally
  - Install and configure pgvector extension
  - Design database schema for jobs, profiles, applications
  - Create migration scripts
  - Set up connection configuration

#### T1.2: Python Environment Setup
- **Duration**: 0.5 days
- **Dependencies**: T0.1 (project structure)
- **Outputs**:
  - requirements.txt
  - Virtual environment
  - Development dependencies installed
- **Tasks**:
  - Create virtual environment
  - Define core dependencies (Streamlit, SQLAlchemy, psycopg2, etc.)
  - Define scraping dependencies (BeautifulSoup, Selenium, Scrapy)
  - Define ML dependencies (transformers, sentence-transformers, scikit-learn)
  - Create requirements.txt and requirements-dev.txt
  - Set up pre-commit hooks

#### T1.3: Project Architecture Design
- **Duration**: 1 day
- **Dependencies**: T0.1, T0.2, T1.1
- **Outputs**:
  - docs/architecture.md
  - Module structure defined
- **Tasks**:
  - Design module structure (scrapers/, models/, ui/, utils/)
  - Define data flow architecture
  - Design matching algorithm architecture
  - Plan RAG implementation with pgvector
  - Document API design patterns

#### T1.4: CI/CD Pipeline Setup
- **Duration**: 0.5 days
- **Dependencies**: T1.2
- **Outputs**:
  - .github/workflows/ci.yml
  - .github/workflows/tests.yml
- **Tasks**:
  - Set up GitHub Actions for testing
  - Configure linting (flake8, black, mypy)
  - Set up automated testing pipeline
  - Configure deployment workflow (optional)

---

## Phase 2: Core Data Layer (Days 7-10)

### Tasks:

#### T2.1: Database Models & ORM
- **Duration**: 2 days
- **Dependencies**: T1.1, T1.3
- **Outputs**:
  - src/models/job.py
  - src/models/profile.py
  - src/models/application.py
  - Migration scripts
- **Tasks**:
  - Implement Job model with all fields
  - Implement Profile model (from profile.md)
  - Implement Application tracking model
  - Implement JobRequirement extraction model
  - Create database migrations
  - Write unit tests for models

#### T2.2: Profile Parser
- **Duration**: 1 day
- **Dependencies**: T2.1
- **Outputs**:
  - src/parsers/profile_parser.py
  - Tests
- **Tasks**:
  - Build markdown parser for profile.md
  - Extract structured data (skills, education, location, etc.)
  - Handle profile updates
  - Create profile embeddings for semantic matching
  - Write unit tests

#### T2.3: Job Board Scraper Framework
- **Duration**: 2 days
- **Dependencies**: T0.2, T2.1
- **Outputs**:
  - src/scrapers/base_scraper.py
  - src/scrapers/scraper_factory.py
  - Error handling & retry logic
- **Tasks**:
  - Design base scraper interface
  - Implement scraper factory pattern
  - Build retry logic with exponential backoff
  - Implement rate limiting
  - Add proxy support (if needed)
  - Create logging infrastructure
  - Write unit tests

---

## Phase 3: Job Aggregation (Days 11-16)

### Tasks (Can be parallelized by job board):

#### T3.1: Indeed Scraper
- **Duration**: 1.5 days
- **Dependencies**: T2.3
- **Outputs**: src/scrapers/indeed_scraper.py
- **Tasks**:
  - Implement Indeed Canada scraper/API client
  - Parse job listings
  - Extract job details
  - Handle pagination
  - Write tests

#### T3.2: LinkedIn Scraper
- **Duration**: 1.5 days
- **Dependencies**: T2.3
- **Outputs**: src/scrapers/linkedin_scraper.py
- **Tasks**:
  - Implement LinkedIn Jobs scraper/API client
  - Handle authentication if required
  - Parse job listings
  - Extract job details
  - Write tests

#### T3.3: Glassdoor Scraper
- **Duration**: 1.5 days
- **Dependencies**: T2.3
- **Outputs**: src/scrapers/glassdoor_scraper.py
- **Tasks**:
  - Implement Glassdoor Canada scraper
  - Parse job listings
  - Extract salary data if available
  - Write tests

#### T3.4: Government Job Bank Scraper
- **Duration**: 1 day
- **Dependencies**: T2.3
- **Outputs**: src/scrapers/job_bank_scraper.py
- **Tasks**:
  - Implement Job Bank Canada scraper
  - Parse government job postings
  - Extract job details
  - Write tests

#### T3.5: Specialized Board Scrapers
- **Duration**: 2 days
- **Dependencies**: T2.3
- **Outputs**:
  - src/scrapers/kaggle_scraper.py
  - src/scrapers/biospace_scraper.py
  - Additional specialized scrapers
- **Tasks**:
  - Implement 2-3 specialized job board scrapers
  - Focus on data science / healthcare specific boards
  - Write tests

#### T3.6: Job Deduplication Logic
- **Duration**: 1 day
- **Dependencies**: T3.1, T3.2, T3.3, T3.4, T3.5
- **Outputs**: src/utils/deduplication.py
- **Tasks**:
  - Implement fuzzy matching for duplicate detection
  - Handle same job across multiple platforms
  - Create canonical job representations
  - Write tests

---

## Phase 4: Matching & Analysis Engine (Days 17-22)

### Tasks:

#### T4.1: Embedding & Vector Search Setup
- **Duration**: 2 days
- **Dependencies**: T1.1, T2.1
- **Outputs**:
  - src/embeddings/embedding_service.py
  - Embedding model selection doc
- **Tasks**:
  - Research and select embedding model (sentence-transformers)
  - Implement embedding generation for job descriptions
  - Implement embedding generation for user profile
  - Set up pgvector indexes
  - Implement vector similarity search
  - Write tests

#### T4.2: Job Matching Algorithm
- **Duration**: 3 days
- **Dependencies**: T2.2, T4.1
- **Outputs**:
  - src/matching/matcher.py
  - src/matching/scoring.py
- **Tasks**:
  - Implement multi-criteria matching algorithm:
    - Education level matching
    - Experience level matching
    - Location matching
    - Skills matching (keyword + semantic)
    - Domain/industry matching
  - Implement configurable weighting system
  - Calculate composite match scores
  - Classify jobs into tiers (High/Medium/Low)
  - Write comprehensive tests

#### T4.3: Requirements Extraction
- **Duration**: 2 days
- **Dependencies**: T4.1
- **Outputs**:
  - src/analysis/requirements_extractor.py
- **Tasks**:
  - Implement NLP-based requirement extraction
  - Extract technical skills from job descriptions
  - Extract soft skills
  - Extract education requirements
  - Extract experience requirements
  - Categorize and normalize requirements
  - Write tests

#### T4.4: Requirements Analysis & Aggregation
- **Duration**: 2 days
- **Dependencies**: T4.3
- **Outputs**:
  - src/analysis/requirements_analyzer.py
- **Tasks**:
  - Aggregate requirements across high-match jobs
  - Identify most common requirements
  - Calculate frequency statistics
  - Generate skill gap analysis
  - Create LLM-friendly summaries
  - Write tests

---

## Phase 5: Scheduling & Automation (Days 23-25)

### Tasks:

#### T5.1: Job Scanning Scheduler
- **Duration**: 1.5 days
- **Dependencies**: T3.6, T4.2
- **Outputs**:
  - src/scheduler/job_scanner.py
  - Cron configuration or Airflow DAG
- **Tasks**:
  - Implement daily job scanning orchestrator
  - Schedule scraping jobs across all boards
  - Implement incremental updates (only new jobs)
  - Handle scraper failures gracefully
  - Store results in database
  - Write tests

#### T5.2: Daily Digest Generator
- **Duration**: 1.5 days
- **Dependencies**: T4.2, T5.1
- **Outputs**:
  - src/digest/digest_generator.py
  - Email/notification templates
- **Tasks**:
  - Generate daily summary of new jobs
  - Sort by match score (high to low)
  - Format with job links and key details
  - Implement email delivery (optional)
  - Create markdown/HTML digest format
  - Write tests

---

## Phase 6: Streamlit UI (Days 26-32)

### Tasks:

#### T6.1: UI Architecture & Layout
- **Duration**: 1 day
- **Dependencies**: T1.2
- **Outputs**:
  - src/ui/app.py
  - src/ui/pages/
  - UI wireframes
- **Tasks**:
  - Design Streamlit app structure
  - Create multi-page layout
  - Design navigation
  - Set up state management
  - Create common components

#### T6.2: Profile Manager Page
- **Duration**: 1.5 days
- **Dependencies**: T2.2, T6.1
- **Outputs**: src/ui/pages/profile_manager.py
- **Tasks**:
  - Display current profile from profile.md
  - Implement profile editing UI
  - Save profile updates to profile.md
  - Validate profile data
  - Show profile completeness indicator

#### T6.3: Dashboard Page
- **Duration**: 2 days
- **Dependencies**: T4.2, T6.1
- **Outputs**: src/ui/pages/dashboard.py
- **Tasks**:
  - Show job market overview
  - Display match score distribution
  - Show trending skills in target jobs
  - Display profile fit analysis
  - Create visualizations (charts, graphs)

#### T6.4: Job Browser Page
- **Duration**: 2 days
- **Dependencies**: T4.2, T6.1
- **Outputs**: src/ui/pages/job_browser.py
- **Tasks**:
  - Display searchable job list
  - Implement filters (location, match tier, date, etc.)
  - Show match scores and reasoning
  - Display job details in expandable cards
  - Add "Apply" and "Save" actions
  - Implement pagination

#### T6.5: Requirements Analyzer Page
- **Duration**: 1.5 days
- **Dependencies**: T4.4, T6.1
- **Outputs**: src/ui/pages/requirements_analyzer.py
- **Tasks**:
  - Visualize common requirements in high-match jobs
  - Show skill frequency charts
  - Display skill gap analysis
  - Show comparison with user profile
  - Provide actionable insights

#### T6.6: Skills Gap Analysis Page
- **Duration**: 1.5 days
- **Dependencies**: T4.4, T6.1
- **Outputs**: src/ui/pages/skills_gap.py
- **Tasks**:
  - Identify missing skills from user profile
  - Rank skills by importance/frequency
  - Show learning resources for each skill
  - Track skill acquisition progress

#### T6.7: Project Recommender Page
- **Duration**: 1.5 days
- **Dependencies**: T4.4, T6.1
- **Outputs**: src/ui/pages/project_recommender.py
- **Tasks**:
  - Generate project recommendations based on skill gaps
  - Display project ideas with descriptions
  - Show skills each project would demonstrate
  - Provide implementation guidance
  - Link to relevant tutorials/resources

#### T6.8: Application Tracker Page
- **Duration**: 1.5 days
- **Dependencies**: T2.1, T6.1
- **Outputs**: src/ui/pages/application_tracker.py
- **Tasks**:
  - Display applications submitted
  - Track application status (applied, interview, rejected, offer)
  - Show application timeline
  - Add notes and follow-up reminders
  - Generate application statistics

---

## Phase 7: Testing & Documentation (Days 33-36)

### Tasks (Can run in parallel):

#### T7.1: Integration Testing
- **Duration**: 2 days
- **Dependencies**: All Phase 6 tasks
- **Outputs**:
  - tests/integration/
  - Test coverage report
- **Tasks**:
  - Write end-to-end tests for job aggregation flow
  - Test matching algorithm with real data
  - Test UI workflows
  - Test database operations
  - Achieve >80% code coverage

#### T7.2: User Documentation
- **Duration**: 2 days
- **Dependencies**: T6.8
- **Outputs**:
  - docs/user-guide.md
  - docs/setup-guide.md
  - docs/faq.md
- **Tasks**:
  - Write setup instructions
  - Document how to use each feature
  - Create FAQ
  - Add screenshots/screencasts
  - Document profile.md format

#### T7.3: Technical Documentation
- **Duration**: 2 days
- **Dependencies**: All Phase 2-6 tasks
- **Outputs**:
  - docs/technical-guide.md
  - docs/api-reference.md
  - Code documentation (docstrings)
- **Tasks**:
  - Document architecture
  - Document database schema
  - Document API endpoints (if any)
  - Ensure all code has docstrings
  - Generate API documentation

#### T7.4: Performance Testing & Optimization
- **Duration**: 1.5 days
- **Dependencies**: T7.1
- **Outputs**:
  - Performance benchmarks
  - Optimization recommendations
- **Tasks**:
  - Test scraping performance
  - Test matching algorithm performance
  - Test database query performance
  - Optimize slow operations
  - Implement caching where beneficial

---

## Phase 8: Deployment & Productionization (Days 37-40)

### Tasks:

#### T8.1: Production Database Setup
- **Duration**: 1 day
- **Dependencies**: T1.1, T7.1
- **Outputs**:
  - Production PostgreSQL instance
  - Backup strategy
- **Tasks**:
  - Set up production PostgreSQL (local or cloud)
  - Configure pgvector in production
  - Set up automated backups
  - Implement database security
  - Migrate schema to production

#### T8.2: Deployment Configuration
- **Duration**: 1.5 days
- **Dependencies**: T7.1
- **Outputs**:
  - Deployment scripts
  - Environment configuration
- **Tasks**:
  - Create production configuration files
  - Set up environment variables
  - Configure logging for production
  - Set up monitoring (optional)
  - Create deployment scripts

#### T8.3: Scheduler Deployment
- **Duration**: 1 day
- **Dependencies**: T5.1, T8.1
- **Outputs**:
  - Production scheduler running
  - Monitoring alerts
- **Tasks**:
  - Deploy job scanning scheduler
  - Set up cron jobs or Airflow
  - Configure daily digest delivery
  - Set up error notifications
  - Test scheduled runs

#### T8.4: Streamlit App Deployment
- **Duration**: 1.5 days
- **Dependencies**: T6.8, T8.1
- **Outputs**:
  - Running Streamlit application
  - Access URL
- **Tasks**:
  - Deploy Streamlit app (Streamlit Cloud / local / Docker)
  - Configure production settings
  - Set up SSL/security (if needed)
  - Test production deployment
  - Create deployment documentation

---

## Phase 9: Enhancement & Iteration (Days 41+)

### Optional Enhancement Tasks:

#### T9.1: Advanced Features
- Email notifications for new high-match jobs
- Resume/cover letter generator based on job requirements
- Interview preparation guidance
- Salary insights and negotiation tips
- Company research integration
- Networking recommendations

#### T9.2: ML Model Improvements
- Train custom embedding model on job descriptions
- Fine-tune matching algorithm based on user feedback
- Implement learning from successful applications
- Add A/B testing for matching strategies

#### T9.3: Additional Integrations
- Google Calendar for interview scheduling
- CRM integration for application tracking
- LinkedIn profile sync
- GitHub profile analysis
- Portfolio website generator

---

## Dependency Graph Summary

```
Phase 0 (Foundation & Research)
├── T0.1 (Project Setup) ─────────┐
├── T0.2 (Job Board Research) ────┤
├── T0.3 (Success Research) ──────┤
└── T0.4 (GitHub Templates) ──────┤
                                  ↓
Phase 1 (Infrastructure)
├── T1.1 (Database) ──────────────┤
├── T1.2 (Python Env) ────────────┤
├── T1.3 (Architecture) ──────────┤
└── T1.4 (CI/CD) ─────────────────┤
                                  ↓
Phase 2 (Core Data Layer)
├── T2.1 (DB Models) ─────────────┤
├── T2.2 (Profile Parser) ────────┤
└── T2.3 (Scraper Framework) ─────┤
                                  ↓
Phase 3 (Job Aggregation)
├── T3.1 (Indeed) ────────────────┤
├── T3.2 (LinkedIn) ──────────────┤
├── T3.3 (Glassdoor) ─────────────┤
├── T3.4 (Job Bank) ──────────────┤
├── T3.5 (Specialized) ───────────┤
└── T3.6 (Deduplication) ─────────┤
                                  ↓
Phase 4 (Matching & Analysis)
├── T4.1 (Embeddings) ────────────┤
├── T4.2 (Matching Algo) ─────────┤
├── T4.3 (Req Extraction) ────────┤
└── T4.4 (Req Analysis) ──────────┤
                                  ↓
Phase 5 (Automation)
├── T5.1 (Scheduler) ─────────────┤
└── T5.2 (Digest) ────────────────┤
                                  ↓
Phase 6 (Streamlit UI)
├── T6.1 (UI Architecture) ───────┤
├── T6.2 (Profile Manager) ───────┤
├── T6.3 (Dashboard) ─────────────┤
├── T6.4 (Job Browser) ───────────┤
├── T6.5 (Req Analyzer) ──────────┤
├── T6.6 (Skills Gap) ────────────┤
├── T6.7 (Project Recomm) ────────┤
└── T6.8 (App Tracker) ───────────┤
                                  ↓
Phase 7 (Testing & Docs)
├── T7.1 (Integration Tests) ─────┤
├── T7.2 (User Docs) ─────────────┤
├── T7.3 (Technical Docs) ────────┤
└── T7.4 (Performance) ───────────┤
                                  ↓
Phase 8 (Deployment)
├── T8.1 (Prod Database) ─────────┤
├── T8.2 (Deploy Config) ─────────┤
├── T8.3 (Scheduler Deploy) ──────┤
└── T8.4 (Streamlit Deploy) ──────┤
                                  ↓
Phase 9 (Enhancement)
└── Optional improvements
```

---

## Critical Path

The critical path (longest dependency chain) is approximately **40 days**:

1. T0.1 → T1.1 → T2.1 → T3.6 → T4.1 → T4.2 → T5.1 → T6.4 → T7.1 → T8.4

**Key Milestones:**
- **Day 3**: Research complete, foundation ready
- **Day 6**: Infrastructure setup complete
- **Day 10**: Core data layer operational
- **Day 16**: Job aggregation functional
- **Day 22**: Matching engine complete
- **Day 25**: Automation implemented
- **Day 32**: UI complete
- **Day 36**: Testing & documentation complete
- **Day 40**: Production deployment complete

---

## Parallelization Opportunities

### High Parallelization:
- **Phase 0**: All tasks can run in parallel (except T0.4 depends on T0.1)
- **Phase 3**: All scraper implementations (T3.1-T3.5) can run in parallel
- **Phase 6**: Most UI pages (T6.2-T6.8) can be developed in parallel
- **Phase 7**: All documentation and testing tasks can run in parallel

### Moderate Parallelization:
- **Phase 1**: T1.1 and T1.2 can run in parallel
- **Phase 2**: T2.2 can start once T2.1 is partially complete
- **Phase 4**: T4.3 can run in parallel with T4.2

---

## Resource Requirements

### Development Team Composition (Optimal):
- **1 Backend Developer**: Data layer, scrapers, matching algorithm
- **1 ML Engineer**: Embeddings, matching algorithm, NLP
- **1 Frontend Developer**: Streamlit UI
- **1 DevOps Engineer** (part-time): Infrastructure, deployment

### Solo Developer Timeline:
- Estimated **50-60 days** accounting for task switching overhead
- Focus on MVP first, then iterate

---

## MVP Scope (Reduced Timeline: ~25 days)

For a faster MVP, prioritize:

### Phase 0: T0.1, T0.2 (2 days)
### Phase 1: T1.1, T1.2, T1.3 (3 days)
### Phase 2: T2.1, T2.2, T2.3 (5 days)
### Phase 3: T3.1, T3.2, T3.6 (4 days) - Only Indeed + LinkedIn
### Phase 4: T4.1, T4.2 (5 days) - Basic matching only
### Phase 6: T6.1, T6.4 (3 days) - Only Job Browser
### Phase 8: T8.1, T8.4 (3 days) - Basic deployment

**MVP Features:**
- Job aggregation from 2 sources
- Basic profile matching
- Simple job browser UI
- Manual daily checks (no automation)

**Defer to v2.0:**
- Additional job boards
- Advanced analytics
- Automation/scheduling
- Project recommendations
- Application tracking

---

## Risk Management

### High-Risk Tasks:
1. **T0.2 (Job Board Research)**: API availability may be limited
   - **Mitigation**: Prepare web scraping fallbacks

2. **T3.1-T3.5 (Scrapers)**: Sites may block scrapers
   - **Mitigation**: Implement rate limiting, proxy rotation, API-first approach

3. **T4.2 (Matching Algorithm)**: Algorithm may not be accurate
   - **Mitigation**: Iterative development with test dataset, user feedback loop

4. **T8.3 (Scheduler Deployment)**: Scheduled jobs may fail silently
   - **Mitigation**: Comprehensive logging, alerting, health checks

### Medium-Risk Tasks:
1. **T1.1 (pgvector setup)**: May have compatibility issues
   - **Mitigation**: Test early, have fallback (e.g., FAISS)

2. **T4.1 (Embeddings)**: Model selection may impact performance
   - **Mitigation**: Benchmark multiple models early

---

## Success Criteria

### Technical Success:
- [ ] Application runs without errors
- [ ] Jobs aggregated from 5+ sources
- [ ] Match accuracy >80%
- [ ] Daily digest delivered automatically
- [ ] All tests passing with >80% coverage
- [ ] Deployment stable and accessible

### Business Success:
- [ ] User completes profile successfully
- [ ] User finds relevant jobs daily
- [ ] Skill gap analysis provides actionable insights
- [ ] Project recommendations are helpful
- [ ] Interview rate increases (measured over time)

---

## Next Immediate Steps

1. **Review and approve this plan**
2. **Set up Git repository** (T0.1)
3. **Create vision.md** (T0.1)
4. **Start job board research** (T0.2)
5. **Design GitHub issue templates** (T0.4)
6. **Break down Phase 1 tasks into GitHub issues**
