# Quality Engineering Knowledge Base
## Integrated Ontological Taxonomy with DDD and UX

**Date:** 2025-10-04
**Status:** Complete Synthesis
**Purpose:** Comprehensive QE taxonomy integrating ISTQB standards, DDD patterns, and UX architecture

---

## Executive Summary

This knowledge base synthesizes Quality Engineering best practices with Domain-Driven Design (DDD) and User Experience (UX) patterns to create a unified testing framework for the Job Seeker application. It provides:

1. **Ontological Taxonomy** - Hierarchical organization of all QE concepts
2. **DDD Integration** - How to test domain models (Value Objects, Aggregates, Bounded Contexts)
3. **UX Integration** - How to test user interfaces (Components, Pages, Workflows)
4. **Standards Alignment** - ISTQB, ISO 25010, IEEE compliance
5. **Practical Guidance** - When/how to apply each pattern with Job Seeker examples

---

## 1. Ontological Taxonomy

### Concept Type Classifications

```yaml
test_concepts:
  artifacts:
    - Test Strategy
    - Test Plan
    - Test Scenario
    - Test Case
    - Test Data
    - Test Result
    - Defect Report

  activities:
    - Test Planning
    - Test Design
    - Test Implementation
    - Test Execution
    - Test Evaluation
    - Test Reporting

  methods:
    test_levels:
      - Component/Unit Testing
      - Integration Testing
      - System Testing
      - Acceptance Testing

    test_types:
      functional:
        - Requirements-based Testing
        - Business Process Testing

      non_functional:
        - Performance Testing (Load, Stress, Endurance, Spike, Volume)
        - Security Testing
        - Usability Testing
        - Accessibility Testing (WCAG 2.2)
        - Reliability Testing
        - Maintainability Testing
        - Portability Testing
        - Compatibility Testing

    test_design_techniques:
      black_box:
        - Equivalence Partitioning
        - Boundary Value Analysis
        - Decision Table Testing
        - State Transition Testing
        - Use Case Testing

      white_box:
        - Statement Coverage
        - Branch Coverage
        - Path Coverage

      experience_based:
        - Error Guessing
        - Exploratory Testing
        - Checklist-based Testing

    test_approaches:
      - Shift-Left Testing
      - Shift-Right Testing
      - Continuous Testing
      - Risk-Based Testing
      - Exploratory Testing
      - Behavior-Driven Development (BDD)

  tools:
    - Test Management Tools
    - Test Automation Frameworks
    - CI/CD Integration Tools
    - Performance Testing Tools
    - Accessibility Testing Tools

  metrics:
    coverage_metrics:
      - Test Coverage
      - Code Coverage (Statement, Branch, Path)
      - Requirements Coverage

    quality_metrics:
      - Defect Density
      - Defect Detection Rate
      - Test Execution Progress
      - Pass/Fail Rate

    efficiency_metrics:
      - Test Automation Rate
      - Test Execution Time
      - Defect Resolution Time

  quality_characteristics:  # ISO 25010
    - Functional Suitability
    - Performance Efficiency
    - Compatibility
    - Usability
    - Reliability
    - Security
    - Maintainability
    - Portability
```

---

## 2. Test Level Hierarchy with DDD/UX Integration

### 2.1 Component/Unit Testing

**Purpose**: Test smallest testable units in isolation

**DDD Focus**:
- **Value Objects**: Validation, immutability, equality
- **Entities**: Identity, business logic, state transitions

**UX Focus**:
- **Atoms**: Buttons, inputs, labels (basic UI elements)
- **Molecules**: Form fields, search inputs (composed atoms)

**Job Seeker Examples**:

| DDD Unit | UX Unit | Test Focus |
|----------|---------|------------|
| `vo_email` | `comp_email_input` | Email format validation |
| `vo_skills` | `comp_skills_input` | Skills collection rules |
| `ent_candidate` | - | Candidate identity and business logic |

**Best Practices**:
- Fast execution (<1s per test)
- No external dependencies
- Test one thing per test
- Use AAA pattern (Arrange-Act-Assert)

---

### 2.2 Integration Testing

**Purpose**: Test interactions between components

**DDD Focus**:
- **Aggregates**: Consistency boundaries, domain events
- **Repositories**: CRUD operations, queries
- **Application Services**: Use case orchestration

**UX Focus**:
- **Organisms**: Complex UI components (job cards, filter panels)
- **Pages**: Complete views with data loading

**Job Seeker Examples**:

| DDD Integration | UX Integration | Test Focus |
|-----------------|----------------|------------|
| `agg_candidate_profile` | `page_profile_edit` | Save profile workflow |
| `repo_job_posting` | `page_job_listings` | Load and display jobs |
| `svc_app_submit_application` | `wf_submit_application` | Submit application use case |

**Best Practices**:
- Use real database (in-memory or Docker)
- Test aggregate consistency enforcement
- Verify domain events published
- Test page data loading from backend

---

### 2.3 System Testing

**Purpose**: Test complete system capabilities

**DDD Focus**:
- **Bounded Contexts**: Complete business capabilities
- **Cross-Context Integration**: Event propagation between contexts

**UX Focus**:
- **Workflows**: Multi-step user processes
- **Cross-Page Flows**: Navigation across pages

**Job Seeker Examples**:

| System Component | Test Focus |
|------------------|------------|
| `bc_profile` context | Profile CRUD, completeness calculation |
| `bc_applications` context | Submit, track, update applications |
| Cross-context: Profile → Jobs → Application | Match score calculation, application creation |

**Best Practices**:
- Production-like environment
- Test complete user workflows
- Test cross-context event flows
- Test both functional and non-functional requirements

---

### 2.4 Acceptance Testing

**Purpose**: Validate business requirements and user needs

**DDD Focus**:
- **Use Cases**: Application services deliver business value
- **Business Rules**: Domain rules enforced correctly

**UX Focus**:
- **User Journeys**: Complete user goals accomplished
- **Usability**: System is easy and satisfying to use

**Job Seeker Examples**:

```gherkin
Feature: Submit Job Application
  As a job seeker,
  I want to submit an application,
  So that I can be considered for the position.

Scenario: Successful application
  Given candidate with complete profile
  And active job posting
  When candidate submits application
  Then application created with SUBMITTED status
  And confirmation email sent
  And application appears in my applications list
```

**Best Practices**:
- Write in business language (BDD/Gherkin)
- Involve stakeholders in defining criteria
- Test from user perspective
- Measure usability (SUS score, task completion)

---

## 3. Test Type Coverage (ISO 25010)

### 3.1 Functional Testing

**Definition**: Testing that the system does what it should do

**DDD Application**:
- Test business rules in Value Objects
- Test business logic in Entities/Aggregates
- Test use cases in Application Services

**UX Application**:
- Test form validation matches domain rules
- Test workflows complete successfully
- Test data displays correctly

---

### 3.2 Non-Functional Testing

#### Performance Efficiency

**Types**:
- **Load Testing**: System handles expected load
- **Stress Testing**: System behaves gracefully under extreme load
- **Endurance Testing**: System stable over long periods
- **Response Time Testing**: Operations complete within acceptable time

**DDD/UX Integration**:
- Repository query performance
- Page load time <3s
- Form submission response <1s

#### Security

**Focus Areas**:
- Authentication and authorization
- Input validation (prevent injection)
- Aggregate access control
- HTTPS enforcement

#### Usability

**ISO 25010 Sub-Characteristics**:
- Learnability
- Operability
- User error protection
- User engagement
- **Accessibility** (WCAG 2.2 Level AA)

**Testing**:
- Task completion rate >90%
- System Usability Scale (SUS) >75
- Keyboard navigation
- Screen reader compatibility

#### Accessibility Testing

**Standards**:
- WCAG 2.2 Level AA
- EN 301 549
- EU Accessibility Act (enforced June 28, 2025)

**Job Seeker Requirements**:
- All pages keyboard navigable
- All images have alt text
- Form inputs have labels
- Color contrast ratio ≥4.5:1
- Screen reader compatible

**Tools**:
- axe DevTools
- WAVE
- Lighthouse
- Manual testing with screen readers (NVDA, JAWS)

---

## 4. Test Design Techniques Applied

### 4.1 Equivalence Partitioning

**Definition**: Divide inputs into equivalence classes where system behaves similarly

**DDD Example**: `vo_experience_years`
```yaml
equivalence_classes:
  - valid: [0, 1, 2, ..., 70]
  - invalid_negative: [-10, -5, -1]
  - invalid_too_high: [71, 100, 200]

test_cases:
  - test_valid: input=5 → ExperienceYears(5)
  - test_invalid_negative: input=-1 → ValidationException
  - test_invalid_high: input=71 → ValidationException
```

**UX Example**: `comp_experience_input`
- Test one value from each class
- Verify UI validation matches domain rules

---

### 4.2 Boundary Value Analysis

**Definition**: Test at boundaries of equivalence classes

**DDD Example**: `vo_experience_years` (valid: 0-70)
```yaml
boundary_tests:
  - just_below_min: -1 → ValidationException
  - min: 0 → Valid
  - just_above_min: 1 → Valid
  - just_below_max: 69 → Valid
  - max: 70 → Valid
  - just_above_max: 71 → ValidationException
```

**UX Example**: `comp_experience_input`
- Test UI handles boundary values
- Error messages display correctly at boundaries

---

### 4.3 State Transition Testing

**Definition**: Test state changes and transitions

**DDD Example**: `agg_application` States
```yaml
states: [DRAFT, SUBMITTED, IN_REVIEW, ACCEPTED, REJECTED, WITHDRAWN]

valid_transitions:
  - DRAFT → SUBMITTED
  - SUBMITTED → IN_REVIEW
  - IN_REVIEW → ACCEPTED
  - IN_REVIEW → REJECTED
  - SUBMITTED → WITHDRAWN

invalid_transitions:
  - ACCEPTED → REJECTED
  - WITHDRAWN → SUBMITTED
```

**UX Example**: Application status badge
- Badge color/text changes with state
- Transitions animate smoothly
- Invalid transitions prevented

---

## 5. Test Automation Strategy

### 5.1 Test Automation Pyramid

```
                      E2E Tests (10%)
                    [User Journeys]
                   /                \
              Integration Tests (30%)
            [Aggregates, Pages]
           /                        \
      Unit Tests (60%)
  [Value Objects, Components]
```

**Rationale**:
- **60% Unit**: Fast, stable, easy to maintain
- **30% Integration**: Test component interactions
- **10% E2E**: Test critical user journeys only

---

### 5.2 Page Object Model (POM)

**Pattern**: Encapsulate page structure in page objects

**Job Seeker Example**: `ProfileEditPageObject`
```typescript
class ProfileEditPage {
  // Locators
  private skillsInput = '[data-testid="skills-input"]';
  private saveButton = '[data-testid="save-profile-btn"]';
  private successToast = '[data-testid="success-toast"]';

  // Actions
  async addSkill(skill: string) {
    await this.page.fill(this.skillsInput, skill);
    await this.page.press(this.skillsInput, 'Enter');
  }

  async saveProfile() {
    await this.page.click(this.saveButton);
  }

  // Assertions
  async assertSkillAdded(skill: string) {
    await expect(this.page.locator(`[data-skill="${skill}"]`)).toBeVisible();
  }

  async assertSaveSuccessful() {
    await expect(this.page.locator(this.successToast)).toContainText('Profile updated');
  }
}
```

**Benefits**:
- Centralize page structure knowledge
- Reduce test maintenance when UI changes
- Reusable across tests

---

### 5.3 BDD Automation

**Framework**: Cucumber, SpecFlow, Behave

**Example**: Automate acceptance criteria
```gherkin
Feature: Update Candidate Profile

Scenario: Add new skill to profile
  Given I am logged in as a candidate
  And I am on the profile edit page
  When I add the skill "React"
  And I save the profile
  Then the skill "React" should appear in my profile
  And I should see a success message "Profile updated successfully"
```

**Step Definitions**:
```typescript
Given('I am on the profile edit page', async () => {
  await profileEditPage.navigate();
});

When('I add the skill {string}', async (skill: string) => {
  await profileEditPage.addSkill(skill);
});

When('I save the profile', async () => {
  await profileEditPage.saveProfile();
});

Then('the skill {string} should appear in my profile', async (skill: string) => {
  await profileEditPage.assertSkillAdded(skill);
});
```

---

## 6. Defect Management

### 6.1 Defect Lifecycle

```
NEW → OPEN → IN_PROGRESS → RESOLVED → VERIFIED → CLOSED
              ↓
          REJECTED
```

### 6.2 Defect Classification

**By Severity**:
- **Critical**: System crash, data loss, security breach
- **High**: Major functionality broken
- **Medium**: Functionality impaired but workarounds exist
- **Low**: Minor cosmetic issues

**By Priority**:
- **P1**: Fix immediately
- **P2**: Fix in current sprint
- **P3**: Fix in next sprint
- **P4**: Fix when time permits

### 6.3 Defect Tracking by Bounded Context

**Job Seeker Example**:
```yaml
defect:
  id: "BUG-123"
  title: "Cannot save profile with special characters in skills"
  severity: High
  priority: P2

  ddd_references:
    bounded_context: bc_profile
    aggregate: agg_candidate_profile
    value_object: vo_skills

  ux_references:
    page: page_profile_edit
    component: comp_skills_input

  reproduction_steps:
    - Navigate to profile edit
    - Enter skill "C++"
    - Click save

  expected: "Skill 'C++' saved successfully"
  actual: "Validation error: 'Invalid characters'"

  root_cause: "vo_skills validation regex too restrictive"
  fix: "Update regex to allow '+' character"
```

---

## 7. Quality Metrics

### 7.1 Coverage Metrics

**Test Coverage**:
- Requirements covered by tests: >95%
- User stories with acceptance tests: 100%

**Code Coverage**:
- Domain layer: >90%
- Application layer: >85%
- UI components: >80%

### 7.2 Quality Metrics

**Defect Metrics**:
- Defect density: <0.5 defects per KLOC
- Defect detection rate: >90% found in testing
- Defect escape rate: <10% found in production

**Test Effectiveness**:
- Pass rate: >95%
- Automation rate: >70%
- Test execution time: <30 min (full suite)

### 7.3 Usability Metrics

**System Usability Scale (SUS)**:
- Target: >75 (Good)
- Excellent: >85

**Task Completion**:
- Success rate: >90%
- Time on task: <5 min for common tasks

---

## 8. Testing by Bounded Context

### bc_profile (Profile Management)

**Test Priorities**:
1. Profile creation/update workflows
2. Skills validation (vo_skills)
3. Email validation (vo_email)
4. Profile completeness calculation

**Key Test Scenarios**:
- Create profile with valid data
- Update existing profile
- Validate required fields
- Calculate completeness percentage

---

### bc_job_catalog (Job Listings)

**Test Priorities**:
1. Job search and filtering
2. Job detail display
3. Match score accuracy
4. Skills gap analysis

**Key Test Scenarios**:
- Browse active jobs
- Filter by location, skills, experience
- View job details with match score
- See skills gap for job

---

### bc_applications (Application Tracking)

**Test Priorities**:
1. Submit application workflow
2. Application status tracking
3. Status change notifications
4. Application history

**Key Test Scenarios**:
- Submit application for job
- Track application status
- Receive notification on status change
- View all applications

---

### bc_matching (Match Scoring)

**Test Priorities**:
1. Match score calculation accuracy
2. Skills overlap calculation
3. Experience matching
4. Location matching

**Key Test Scenarios**:
- Calculate match between candidate and job
- Verify score considers skills, experience, location
- Update score when profile changes

---

## 9. Integration with Development Workflow

### 9.1 Shift-Left Testing

**Principles**:
- Test early and often
- Developers write tests alongside code
- TDD/BDD practices
- Continuous testing in CI/CD

**Job Seeker Implementation**:
- Developers write unit tests for Value Objects first
- Application services have integration tests
- UI components tested in Storybook
- All tests run on every commit

---

### 9.2 CI/CD Pipeline Integration

```yaml
pipeline:
  commit:
    - Lint code
    - Run unit tests (60% of suite, <2 min)
    - Build application

  pull_request:
    - Run unit + integration tests (90% of suite, <10 min)
    - Code coverage check (>80%)
    - Accessibility tests (axe)

  merge_to_main:
    - Run full test suite (100%, <30 min)
    - E2E tests (critical paths)
    - Performance tests
    - Security scans

  deploy_to_staging:
    - Smoke tests
    - UAT environment ready

  deploy_to_production:
    - Smoke tests
    - Monitor for errors
```

---

## 10. Anti-Patterns to Avoid

### Testing Anti-Patterns

**1. Ice Cream Cone** (inverted pyramid):
- Too many E2E tests, too few unit tests
- Fix: Follow test pyramid (60-30-10)

**2. Testing Implementation Details**:
- Tests break on refactoring even though behavior unchanged
- Fix: Test public API, not internals

**3. Flaky Tests**:
- Tests fail intermittently
- Fix: Remove timing dependencies, improve test isolation

**4. No Test Data Management**:
- Tests interfere with each other
- Fix: Reset database between tests, use test fixtures

---

### DDD Testing Anti-Patterns

**1. Testing Getters/Setters**:
- No business value
- Fix: Test business logic, not data access

**2. Mocking Aggregates**:
- Defeats purpose of aggregate testing
- Fix: Use real aggregates in tests

**3. Testing Multiple Aggregates in Transaction**:
- Violates DDD one-aggregate rule
- Fix: Test one aggregate per transaction

---

### UX Testing Anti-Patterns

**1. Snapshot Tests Without Understanding**:
- Blindly approving snapshot changes
- Fix: Understand what snapshot represents

**2. Ignoring Accessibility**:
- No screen reader testing
- Fix: Run axe, test with keyboard, use screen reader

**3. Not Testing Error States**:
- Only testing happy path
- Fix: Test loading, error, empty states

---

## 11. Tools and Frameworks Summary

### Backend/Domain Testing
- **Unit**: Jest, pytest, JUnit, xUnit
- **Mocking**: Mockito, unittest.mock, Jest
- **Assertions**: Chai, Should, AssertJ

### Frontend/UI Testing
- **Unit**: Jest, Vitest, React Testing Library
- **Integration**: Testing Library, Playwright Component Testing
- **E2E**: Playwright, Cypress
- **Visual**: Storybook, Chromatic
- **Accessibility**: axe-core, jest-axe, Lighthouse

### BDD
- **Frameworks**: Cucumber, SpecFlow, Behave
- **Language**: Gherkin (Given-When-Then)

### Performance
- **Load**: JMeter, Gatling, k6
- **Profiling**: Chrome DevTools, Lighthouse

### CI/CD
- **Runners**: GitHub Actions, GitLab CI, Jenkins
- **Containers**: Docker, TestContainers

---

## 12. Key Takeaways

### Integrated Testing Approach
1. **Test at All Levels**: Unit → Integration → System → Acceptance
2. **Align with DDD**: Test Value Objects → Entities → Aggregates → Bounded Contexts
3. **Align with UX**: Test Atoms → Molecules → Organisms → Pages → Workflows
4. **Use Standards**: Follow ISTQB, ISO 25010, WCAG 2.2

### Success Criteria
- ✓ Comprehensive test coverage across all layers
- ✓ Automated tests in CI/CD pipeline
- ✓ Accessibility compliance (WCAG 2.2 AA)
- ✓ High code quality (>80% coverage)
- ✓ Fast feedback (<30 min full suite)
- ✓ Business value validated (acceptance tests)

---

## References

### Standards
- ISTQB Foundation Level Syllabus v4.0
- ISO/IEC 25010:2023 Software Quality Model
- WCAG 2.2 Level AA
- EU Accessibility Act (2025)

### DDD
- Evans, "Domain-Driven Design" (2003)
- Vernon, "Implementing Domain-Driven Design" (2013)
- Job Seeker DDD Research: `wiki/research/ddd/working-docs/`

### UX
- Frost, "Atomic Design"
- Rosenfeld, "Information Architecture"
- Job Seeker UX Research: `wiki/research/ux/working-docs/`

### Integration
- QE-DDD-UX Integration: `research/qe/QE-DDD-UX-INTEGRATION.md`
- Foundation Research: `research/qe/deliverables/01-foundation-standards.md`

---

**Document Status:** Complete Synthesis
**Version:** 1.0
**Date:** 2025-10-04
**Next Steps:** Create YAML schema, executive summary
