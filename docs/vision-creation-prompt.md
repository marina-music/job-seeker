# Vision Document Creation Prompt

## Task
Create a comprehensive `wiki/vision.md` document for the Job Application Assistant product, then expand it to define all product features.

## Context Sources
Analyze the following documents in the `docs/` directory for product understanding:
- `01-egg.md` - Initial product concept and user context
- `02-prompt.md` - Detailed project prompt with objectives and requirements
- `03-plan.md` - Execution plan with phases and tasks

## Part 1: Create Vision Document

### Vision Document Structure
Create `wiki/vision.md` following this structure:

#### 1. Product Name & Tagline
- Clear, memorable product name
- One-line tagline capturing the essence

#### 2. Vision Statement
- **What**: What is this product?
- **Who**: Who is it for?
- **Why**: Why does it need to exist? What problem does it solve?
- **How**: How is it different from alternatives?

#### 3. Problem Statement
Based on `01-egg.md` and `02-prompt.md`, articulate:
- Current pain points in job searching for data scientists
- Challenges in matching skills to opportunities
- Difficulty identifying skill gaps and growth opportunities
- Manual, time-consuming job search process
- Low success rate in getting interviews

#### 4. Target User
From `01-egg.md`, define the primary user:
- **Background**: Junior data scientist with Masters in Computer Vision
- **Domain**: Bioinformatics, healthcare applications, CNNs, temporal convolutional networks
- **Skills**: Data science, AI/ML, data pipelines
- **Location**: Canadian resident seeking jobs in Canada
- **Career Stage**: Transitioning from research to industry
- **Goals**: Increase interview success rate, identify skill gaps, build relevant portfolio

#### 5. Core Value Propositions
From `02-prompt.md`, identify key value propositions:
1. **Automated Job Discovery**: Daily aggregation from multiple sources
2. **Intelligent Matching**: Semantic + keyword-based profile matching
3. **Market Intelligence**: Common requirements analysis in target jobs
4. **Skill Gap Identification**: Data-driven insights on missing skills
5. **Portfolio Guidance**: Project recommendations based on market demand
6. **Application Success Research**: Evidence-based strategies to increase interview rates

#### 6. Product Goals
- Reduce time spent searching for relevant jobs by 80%
- Increase interview rate by 2x through better targeting and portfolio projects
- Provide actionable insights for skill development
- Surface hidden opportunities that match user's unique profile
- Enable data-driven career development decisions

#### 7. Success Metrics
- Number of high-match jobs surfaced daily
- Accuracy of job matching (% of high-match jobs user finds relevant)
- Interview rate improvement over time
- Skills acquired from gap analysis recommendations
- Portfolio projects completed based on recommendations
- Time saved vs. manual job searching

#### 8. Principles & Constraints
**Technical Principles**:
- Profile-driven: All features center around user's `profile.md`
- Privacy-first: All data stored locally or in user-controlled database
- Automation-friendly: Daily scanning without manual intervention
- Extensible: Easy to add new job boards and scrapers

**Development Principles** (from `01-egg.md`):
- Agile methodology: Vision → Features → Epics → User Stories
- Documentation-first: Wiki-driven development
- Issue tracking: GitHub issues linked to wiki documents
- LLM-supervised development: Leverage AI for rapid iteration

**Technical Constraints**:
- Python-based implementation
- Streamlit for UI
- PostgreSQL + pgvector for RAG and semantic search
- GitHub CLI (`gh`) for git operations

#### 9. Out of Scope (Initial Version)
- Resume/cover letter generation (future enhancement)
- Direct application submission
- Interview scheduling automation
- Multi-user support
- Mobile application

#### 10. Strategic Context
**Why Build This?**
- Hypothesis: Submitting portfolio with working application increases interview rates
- This product itself serves as a portfolio piece demonstrating:
  - Data science skills (matching, analysis, ML)
  - Software engineering (architecture, database design, UI)
  - Domain knowledge (job market understanding)
  - AI/ML implementation (embeddings, semantic search)

## Part 2: Extract and Define Features

After creating the vision document, analyze it to extract and define all product features.

### Feature Extraction Process

1. **Review Core Value Propositions** in vision.md
2. **Identify Major Functional Areas** from `02-prompt.md` Core Features section
3. **Map to User Workflows** (what user needs to accomplish)
4. **Define Feature Hierarchy**

### Feature Definition Template

For each feature, create a file in `wiki/` with naming: `f{number}-feature-{name}.md`

**Feature Document Structure**:

```markdown
# Feature F{number}: {Feature Name}

**Feature ID**: F{number}
**Vision Alignment**: {Which vision goal this supports}
**Priority**: Critical | High | Medium | Low
**Status**: Not Started | In Progress | Complete

## Description
{2-3 sentence description of the feature}

## Business Value
{Why this feature matters to the user and product success}

## User Benefit
As a {user type}, this feature allows me to {benefit}, so that {outcome}.

## Acceptance Criteria
- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Criterion 3

## Related Epics
{To be defined - will break this feature into epics}

## Dependencies
{Any technical or feature dependencies}

## Success Metrics
{How we measure success of this feature}

## Technical Considerations
{High-level technical approach, constraints, or challenges}

## Out of Scope
{What this feature explicitly does NOT include}

## Definition of Done
- [ ] All epics completed
- [ ] Feature tested end-to-end
- [ ] Documentation updated
- [ ] User can successfully use the feature
- [ ] Success metrics being tracked
```

### Expected Features to Extract

Based on `02-prompt.md` analysis, expect these features (adjust as needed):

1. **F1: Profile Management**
   - Maintain user profile in `profile.md`
   - View and edit profile
   - Profile completeness tracking

2. **F2: Job Aggregation & Monitoring**
   - Multi-source job board scraping
   - Daily automated scanning
   - Incremental updates (only new jobs)
   - Deduplication across sources

3. **F3: Intelligent Job Matching**
   - Semantic + keyword profile matching
   - Multi-criteria scoring (education, skills, location, domain)
   - Match tier classification (High/Medium/Low)
   - Match reasoning/explanation

4. **F4: Requirements Analysis**
   - Extract requirements from job descriptions
   - Aggregate requirements across high-match jobs
   - Identify common patterns
   - Generate LLM-friendly summaries

5. **F5: Skills Gap Analysis**
   - Compare user skills to market demands
   - Identify missing skills
   - Rank by importance/frequency
   - Track skill acquisition progress

6. **F6: Project Recommendations**
   - Suggest portfolio projects based on skill gaps
   - Align with market demands
   - Provide implementation guidance
   - Link to resources

7. **F7: Daily Job Digest**
   - Automated daily summary
   - Sorted by match score
   - New jobs only
   - Email/notification delivery

8. **F8: Job Browser & Search**
   - Searchable job interface
   - Advanced filtering
   - Job details view
   - Save and track jobs

9. **F9: Application Tracking**
   - Track applications submitted
   - Status management
   - Timeline view
   - Notes and reminders

10. **F10: Market Intelligence Dashboard**
    - Job market trends
    - Skill demand trends
    - Salary insights (if available)
    - Competition analysis

## Workflow

1. **Read and analyze** `docs/01-egg.md`, `docs/02-prompt.md`, `docs/03-plan.md`

2. **Create `wiki/vision.md`** following the structure above

3. **Extract features** from the vision document

4. **Create feature files**:
   - `wiki/f1-feature-profile-management.md`
   - `wiki/f2-feature-job-aggregation.md`
   - `wiki/f3-feature-intelligent-matching.md`
   - ... (continue for all features)

5. **Update `wiki/vision.md`** to add a "Features" section linking to all feature files:
   ```markdown
   ## Features
   - [F1: Profile Management](f1-feature-profile-management.md)
   - [F2: Job Aggregation & Monitoring](f2-feature-job-aggregation.md)
   - [F3: Intelligent Job Matching](f3-feature-intelligent-matching.md)
   ...
   ```

6. **Create `wiki/Home.md`** navigation:
   - Link to vision.md
   - Link to all features
   - Overview of agile document structure

## Deliverables

1. `wiki/vision.md` - Comprehensive product vision
2. `wiki/f{1-10}-feature-{name}.md` - Individual feature documents
3. Updated `wiki/Home.md` - Navigation and overview

## Next Steps After Completion

Once vision and features are defined:
1. Break each feature into epics (`f{n}-e{n}-epic-{name}.md`)
2. Break each epic into user stories (`f{n}-e{n}-s{n}-story-{name}.md`)
3. Create GitHub issues from user stories
4. Begin implementation following `03-plan.md` execution plan

## Notes

- Use insights from `03-plan.md` to inform feature priorities and technical considerations
- Keep features user-centric, not implementation-centric
- Ensure each feature aligns with vision and provides clear user value
- Features should be independently deliverable where possible
- Consider MVP scope when prioritizing features
