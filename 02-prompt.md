# Job Application Assistant - Project Prompt

## Objective
Build a Python application with Streamlit UI to help job seekers successfully apply for positions by:
- Aggregating job postings from multiple sources
- Matching jobs to user profile (stored in `profile.md`)
- Analyzing common requirements in high-match jobs
- Providing actionable insights for skill development
- Recommending portfolio projects based on market demands

## User Profile
User profile is maintained separately in `profile.md` and includes:
- Target position(s) and seniority level
- Education and experience
- Technical and soft skills
- Location and work authorization
- Domain expertise and interests
- Career goals and preferences

The application reads this profile to personalize job matching and recommendations.

## Core Features

### 1. Job Aggregation & Monitoring
- Research and integrate with job posting websites relevant to the user's target role and location
- Support for major job boards:
  - General: Indeed, LinkedIn Jobs, Glassdoor
  - Location-specific: Government job banks, regional job boards
  - Industry-specific: Based on user's domain (e.g., BioSpace, Nature Jobs for research/biotech)
  - Company career pages
  - Professional associations and communities
- Daily automated scanning for new postings
- Store job data in PostgreSQL with pgvector for semantic search/matching
- Configurable search parameters based on user profile

### 2. Profile Matching & Classification
- Implement intelligent job matching algorithm that scores how closely each posting matches user profile based on:
  - Required education level vs. user's education
  - Domain/industry alignment with user's expertise and interests
  - Experience level requirements vs. user's experience
  - Location requirements vs. user's location/preferences
  - Required technical skills vs. user's skillset
  - Soft skills alignment
  - Work authorization requirements
- Use semantic similarity (pgvector embeddings) for nuanced matching beyond keyword search
- Classify jobs into tiers (High Match, Medium Match, Low Match)
- Daily summary of new jobs sorted by match score with links
- Configurable weighting of matching criteria based on user priorities

### 3. Requirements Analysis
- For high-match jobs, extract and analyze common requirements:
  - Technical skills (programming languages, tools, frameworks)
  - Soft skills
  - Domain knowledge
  - Educational requirements
  - Experience expectations
- Generate summarized common requirements suitable for feeding to LLM for project ideation

### 4. Application Success Research
- Research and test hypothesis: "Submitting a code repo with working application and live demo increases interview chances"
- Compile best practices for successful job applications in user's target industry/role
- Provide actionable recommendations tailored to user's profile and target positions

### 5. Project Recommendation Engine
- Use analyzed common requirements to suggest concrete portfolio projects
- Projects should align with frequently requested skills in high-match jobs
- Provide project ideas that can be supervised LLM development tasks

## Technical Stack
- **Language**: Python
- **UI**: Streamlit
- **Database**: PostgreSQL with pgvector extension for RAG/semantic search
- **Version Control**: Git with GitHub
- **CLI Tools**: `gh` (GitHub CLI) for integration
- **Job Board APIs**: Research and integrate available APIs or web scraping solutions

## Development Approach

### Project Structure
Following a structured development paradigm:

1. **Vision** (vision.md) - High-level what and why
2. **Features** - Major functional areas
3. **Epics** - Groups of related user stories
4. **User Stories** - Specific implementable requirements

### Documentation & Issue Management
- Store development artifacts in Git wiki
- Design GitHub issue templates for:
  - Vision documents
  - Features
  - Epics
  - User stories
- Use `gh` CLI to create and manage issues from refined wiki content
- Maintain traceability from vision → features → epics → user stories → issues

## Deliverables

### Application Features
1. **Profile Manager**: View and edit user profile (`profile.md`)
2. **Dashboard**: Overview of job market trends and profile fit analysis
3. **Job Browser**: Searchable, filterable list of aggregated jobs with match scores
4. **Daily Digest**: Automated daily summary of new jobs (high to low match)
5. **Requirements Analyzer**: Visual representation of common requirements in high-match jobs
6. **Skills Gap Analysis**: Identify missing skills based on target job requirements
7. **Project Recommender**: Suggested portfolio projects based on market analysis
8. **Application Tracker**: Track applications submitted, responses, interviews

### Documentation
1. Vision document
2. GitHub issue templates
3. User documentation for the application
4. Technical documentation for maintenance/extension

## Research Tasks

### 1. Job Board Identification
Research and document:
- Which websites have job postings for the user's target role and location
- General job boards (Indeed, LinkedIn, Glassdoor, etc.)
- Industry/domain-specific job boards based on user profile
- Whether they offer APIs or require web scraping
- Rate limits and usage policies
- Data structure of job postings
- Authentication and access requirements

### 2. Application Success Factors
Research and validate:
- Does submitting a portfolio/demo increase interview rates?
- What makes a successful job application for the user's target role?
- How important is GitHub activity and online presence?
- Industry-specific best practices based on user profile
- Role-specific application strategies (technical vs. non-technical roles)

### 3. RAG Implementation Strategy
- How to use pgvector for job matching and semantic search
- Embedding model selection for job descriptions and user profile
- Similarity scoring approach for multi-dimensional profile matching
- Handling different types of data (skills, experience, education, preferences)
- Balancing keyword matching with semantic similarity

## Success Metrics
- Application successfully aggregates jobs from at least 5 sources
- Match scoring accurately identifies relevant positions (>80% of high-match jobs are actually relevant)
- Daily digest delivered automatically
- Requirements analysis identifies actionable skill gaps
- Application helps secure at least 2x more interviews

## Next Steps
1. Create vision.md document
2. Break down into features
3. Design GitHub issue templates
4. Set up project infrastructure (PostgreSQL, Streamlit, repo structure)
5. Begin implementation with highest-value features first
