# Quality Engineering Integration with DDD and UX

**Date:** 2025-10-04
**Status:** Integration Framework
**Purpose:** Define how QE taxonomy, test artifacts, and test scenarios integrate with DDD domain models and UX patterns

---

## Overview

Quality Engineering (QE) testing must align with both the domain model (DDD) and user experience (UX) to ensure comprehensive test coverage. This document establishes integration points, terminology alignment, and cross-reference requirements between QE, DDD, and UX research.

---

## Integration Principles

### 1. Three-Layer Testing Strategy

```yaml
testing_strategy:
  domain_layer:
    what: DDD constructs (Entities, Value Objects, Aggregates, Domain Services)
    test_types: Unit tests, Integration tests, Domain logic validation
    reference: DDD ontological taxonomy

  application_layer:
    what: Use cases, Application Services, Workflows
    test_types: Integration tests, Acceptance tests, End-to-end tests
    reference: DDD Application Services + UX Workflows

  presentation_layer:
    what: UX patterns (Pages, Components, Navigation, Interactions)
    test_types: UI tests, Usability tests, Accessibility tests, Visual regression
    reference: UX ontological taxonomy
```

### 2. Terminology Alignment

**DDD Terminology** → **QE Test Object**
- `Bounded Context` → Test scope boundary
- `Aggregate` → Unit of transactional testing
- `Value Object` → Validation testing target
- `Domain Event` → Event-driven test scenarios
- `Repository` → Integration testing interface
- `Application Service` → Use case testing target

**UX Terminology** → **QE Test Object**
- `Page` → Page Object Model
- `Component` → Component testing target
- `Workflow` → User journey test scenario
- `Navigation` → Navigation testing
- `Interaction` → Behavior-driven test scenarios
- `State Transition` → State machine testing

---

## Cross-Reference Framework

### QE → DDD References

Every test artifact SHOULD reference the DDD construct it tests:

```yaml
test_case:
  id: "tc_001_create_candidate_profile"
  name: "Create Candidate Profile with Valid Data"

  # DDD References
  bounded_context_ref: "bc_profile"
  aggregate_ref: "agg_candidate_profile"
  application_service_ref: "svc_app_create_profile"
  domain_events_expected:
    - "evt_profile_created"
    - "evt_skills_added"

  # Test metadata
  test_level: "integration"
  test_type: "functional"
```

### QE → UX References

Every UI test SHOULD reference the UX pattern it validates:

```yaml
test_case:
  id: "tc_ui_002_profile_form_validation"
  name: "Profile Form Displays Validation Errors"

  # UX References
  page_ref: "page_profile_edit"
  workflow_ref: "wf_update_profile"
  components_under_test:
    - "comp_skills_input"
    - "comp_email_input"
  interaction_pattern: "inline_validation_feedback"

  # Test metadata
  test_level: "ui"
  test_type: "usability"
```

### DDD + UX → QE Test Coverage Matrix

```yaml
coverage_matrix:
  bounded_context: "bc_profile"

  aggregates:
    - aggregate: "agg_candidate_profile"
      domain_tests:
        - unit: "Test Candidate entity validation"
        - integration: "Test Profile aggregate consistency"
      ui_tests:
        - page_ref: "page_profile_edit"
        - workflow_ref: "wf_update_profile"
        - usability: "Test profile form usability"
        - accessibility: "Test profile page WCAG 2.2 compliance"
```

---

## Test Taxonomy Integration

### Strategic Level: Testing Bounded Contexts

**DDD Bounded Context** = **QE Test Suite Scope**

```yaml
test_suite:
  id: "ts_bc_profile"
  name: "Profile Management Test Suite"
  bounded_context_ref: "bc_profile"

  categories:
    - domain_tests:  # Tests for DDD domain layer
        - entity_tests
        - value_object_tests
        - aggregate_tests
        - domain_service_tests

    - application_tests:  # Tests for DDD application layer
        - use_case_tests
        - application_service_tests
        - integration_tests

    - ui_tests:  # Tests for UX presentation layer
        - page_tests
        - component_tests
        - workflow_tests
        - accessibility_tests
```

**Example: Profile Management Bounded Context Testing**

| DDD Construct | Test Level | Test Type | UX Integration |
|---------------|------------|-----------|----------------|
| `vo_skills` Value Object | Unit | Validation | `comp_skills_input` validation rules |
| `vo_email` Value Object | Unit | Validation | `comp_email_input` format checking |
| `ent_candidate` Entity | Unit | Business logic | - |
| `agg_candidate_profile` Aggregate | Integration | Consistency boundary | `page_profile_edit` form submission |
| `svc_app_update_profile` App Service | Integration | Use case | `wf_update_profile` workflow |
| `evt_profile_updated` Domain Event | Integration | Event handling | Toast notification behavior |
| `page_profile_edit` Page | UI | Usability, Accessibility | Full page testing |
| `wf_update_profile` Workflow | E2E | User journey | Multi-step workflow testing |

---

### Tactical Level: Testing Patterns

#### 1. Testing DDD Tactical Patterns

**Entity Testing:**
```yaml
test_pattern:
  name: "Entity Identity and Equality Testing"
  applies_to: DDD Entities

  test_cases:
    - "Entity with same ID equals another entity with same ID"
    - "Entity identity persists across state changes"
    - "Entity validation rules enforce invariants"

  example:
    entity: "ent_candidate"
    test: "Two Candidate entities with same CandidateId are equal"
```

**Value Object Testing:**
```yaml
test_pattern:
  name: "Value Object Immutability and Validation Testing"
  applies_to: DDD Value Objects

  test_cases:
    - "Value object is immutable (no setters)"
    - "Value object validation rules reject invalid inputs"
    - "Value object equality based on attributes, not identity"
    - "Value object formatting displays correctly"

  example:
    value_object: "vo_email"
    test: "Email('invalid') throws ValidationException"
    ui_integration: "comp_email_input displays inline error"
```

**Aggregate Testing:**
```yaml
test_pattern:
  name: "Aggregate Consistency Boundary Testing"
  applies_to: DDD Aggregates

  test_cases:
    - "Aggregate enforces consistency rules within boundary"
    - "Aggregate root is the only entry point"
    - "Aggregate publishes domain events on state changes"
    - "One aggregate per transaction rule enforced"

  example:
    aggregate: "agg_candidate_profile"
    test: "Updating skills publishes evt_skills_changed"
    ui_integration: "Form saves entire aggregate, not individual fields"
```

**Domain Event Testing:**
```yaml
test_pattern:
  name: "Domain Event Publishing and Handling Testing"
  applies_to: DDD Domain Events

  test_cases:
    - "Event is published when aggregate state changes"
    - "Event contains all necessary data"
    - "Event handlers process events correctly"
    - "Event ordering is maintained"

  example:
    event: "evt_application_submitted"
    test: "ApplicationSubmitted event triggers notification"
    ui_integration: "Toast notification appears when event fires"
```

**Repository Testing:**
```yaml
test_pattern:
  name: "Repository Interface Testing"
  applies_to: DDD Repositories

  test_cases:
    - "Repository retrieves aggregate by ID"
    - "Repository saves aggregate completely"
    - "Repository queries respect aggregate boundaries"
    - "Repository handles concurrency conflicts"

  example:
    repository: "repo_candidate_profile"
    test: "get_by_id returns complete aggregate with all value objects"
```

---

#### 2. Testing UX Patterns

**Page Architecture Testing:**
```yaml
test_pattern:
  name: "Page Type Testing"
  applies_to: UX Page Architecture

  test_cases_by_page_type:
    list_page:
      - "Displays collection of items from repository"
      - "Pagination works correctly"
      - "Filters/search updates results"
      - "Empty state displays when no items"

    detail_page:
      - "Displays single aggregate details"
      - "Related aggregates load correctly"
      - "Actions available match aggregate state"

    form_page:
      - "Form fields map to aggregate attributes"
      - "Validation matches value object rules"
      - "Submit invokes correct application service"
      - "Success publishes expected domain event"

    dashboard_page:
      - "Aggregates data from multiple bounded contexts"
      - "Widgets query correct repositories"
      - "Cross-context navigation works"

  example:
    page: "page_profile_edit"
    aggregate_ref: "agg_candidate_profile"
    tests:
      - "Skills input validates against vo_skills rules"
      - "Save button calls svc_app_update_profile"
      - "Success shows 'Profile updated' (evt_profile_updated)"
```

**Component Testing:**
```yaml
test_pattern:
  name: "Component Testing by Atomic Level"
  applies_to: UX Component Architecture

  test_cases_by_level:
    atom:
      - "Renders correctly with all props"
      - "Handles user interactions (click, focus, hover)"
      - "Applies styling correctly"

    molecule:
      - "Composed atoms work together"
      - "Internal state management works"
      - "Validation feedback displays"

    organism:
      - "Complex interactions work correctly"
      - "Data flows through component tree"
      - "Event handlers trigger correctly"

    domain_component:
      - "Displays domain aggregate/value object correctly"
      - "Respects domain rules and constraints"
      - "Updates when domain events fire"

  example:
    component: "comp_skills_input" (molecule)
    value_object_ref: "vo_skills"
    tests:
      - "Displays current skills from vo_skills"
      - "Validates new skill against vo_skills rules"
      - "Shows error when invalid skill added"
```

**Workflow Testing:**
```yaml
test_pattern:
  name: "Workflow Pattern Testing"
  applies_to: UX Workflow Patterns

  test_cases_by_workflow_type:
    linear_wizard:
      - "Steps progress in correct order"
      - "Cannot skip required steps"
      - "Progress indicator shows current step"
      - "Can navigate back to previous steps"
      - "Final submit calls application service"

    flexible_workflow:
      - "User can complete tasks in any order"
      - "Dashboard shows task completion status"
      - "Tasks can be saved independently"

    long_running_workflow:
      - "Background job starts correctly"
      - "Progress updates in real-time"
      - "User can navigate away and return"
      - "Completion notification appears"

  example:
    workflow: "wf_submit_application"
    application_service_ref: "svc_app_submit_application"
    tests:
      - "Step 1: Select job (loads agg_job_posting)"
      - "Step 2: Review profile (displays agg_candidate_profile)"
      - "Step 3: Submit (calls svc_app_submit_application)"
      - "Final: Confirmation (listens for evt_application_submitted)"
```

**Navigation Testing:**
```yaml
test_pattern:
  name: "Navigation Pattern Testing"
  applies_to: UX Navigation Patterns

  test_cases:
    global_navigation:
      - "All primary bounded contexts accessible"
      - "Active section highlighted"
      - "Navigation persists across pages"

    local_navigation:
      - "Context-specific navigation shows"
      - "Sub-navigation matches current context"
      - "Breadcrumbs show context hierarchy"

    cross_context_navigation:
      - "Transitions between contexts are clear"
      - "Context changes update navigation"
      - "Back navigation returns to previous context"

  example:
    navigation: "global_nav"
    tests:
      - "'Profile' navigates to bc_profile"
      - "'Jobs' navigates to bc_job_catalog"
      - "'Applications' navigates to bc_applications"
```

**Behavioral Testing:**
```yaml
test_pattern:
  name: "Interaction and Feedback Testing"
  applies_to: UX Behavioral Specifications

  test_cases:
    state_transitions:
      - "Component state matches aggregate state"
      - "State changes render correctly"
      - "State transitions animate smoothly"

    feedback_mechanisms:
      - "Immediate feedback on user actions"
      - "Success feedback after domain events"
      - "Error feedback on validation failures"

    domain_event_triggered_behavior:
      - "UI updates when domain event fires"
      - "Notifications display for relevant events"
      - "Real-time updates work across components"

  example:
    behavior: "application_status_badge"
    aggregate_ref: "agg_application"
    tests:
      - "Badge shows 'Draft' when status = DRAFT"
      - "Badge updates to 'Submitted' when evt_application_submitted fires"
      - "Status transition animates"
```

---

## Test Data Integration

### Test Data References DDD Constructs

```yaml
test_data:
  id: "td_valid_candidate_profile"
  name: "Valid Candidate Profile Test Data"

  # DDD References
  bounded_context: "bc_profile"
  aggregate: "agg_candidate_profile"

  # Test data values
  data:
    candidate:
      id: "cand_12345"
      email: "test@example.com"  # vo_email compliant
      skills:  # vo_skills compliant
        - "Python"
        - "JavaScript"
        - "React"
      experience_years: 5  # vo_experience_years compliant

  # Validation
  satisfies_invariants: true
  valid_for_contexts: ["bc_profile", "bc_matching"]
```

### Test Data for UX Scenarios

```yaml
test_scenario:
  id: "ts_ui_profile_form_happy_path"
  name: "User Successfully Updates Profile"

  # UX References
  workflow_ref: "wf_update_profile"
  pages: ["page_profile_edit"]

  # Test data
  given:
    user_authenticated: true
    current_profile: "td_existing_profile"

  when:
    user_enters: "td_updated_skills"
    user_clicks: "btn_save_profile"

  then:
    application_service_called: "svc_app_update_profile"
    domain_event_published: "evt_profile_updated"
    ui_feedback: "Toast: 'Profile updated successfully'"
    page_state: "Saved state, form unlocked"
```

---

## Test Scenario Examples

### Example 1: Testing Value Object with UI Integration

**DDD Construct:** `vo_email` Value Object

**QE Test Cases:**

```yaml
# Unit Test (Domain Layer)
test_case:
  id: "tc_unit_vo_email_validation"
  name: "Email Value Object Validates Email Format"
  test_level: "unit"
  test_type: "functional"

  ddd_ref:
    value_object: "vo_email"
    bounded_context: "bc_profile"

  scenarios:
    - given: "Email string 'test@example.com'"
      when: "Email.create('test@example.com')"
      then: "Returns Email value object"

    - given: "Invalid email 'not-an-email'"
      when: "Email.create('not-an-email')"
      then: "Throws ValidationException with message 'Invalid email format'"

# UI Test (Presentation Layer)
test_case:
  id: "tc_ui_email_input_validation"
  name: "Email Input Component Displays Validation Error"
  test_level: "ui"
  test_type: "functional"

  ux_ref:
    component: "comp_email_input"
    page: "page_profile_edit"

  ddd_ref:
    value_object: "vo_email"  # Validation rules from here

  scenarios:
    - given: "User on profile edit page"
      when: "User enters 'not-an-email' in email input"
      and: "User tabs out of field (blur event)"
      then: "Inline error displays: 'Invalid email format'"
      and: "Input border turns red"
      and: "Save button remains disabled"
```

---

### Example 2: Testing Aggregate with Workflow Integration

**DDD Construct:** `agg_application` Aggregate + `svc_app_submit_application` Application Service

**UX Construct:** `wf_submit_application` Workflow (Linear Wizard)

**QE Test Cases:**

```yaml
# Integration Test (Application Layer)
test_case:
  id: "tc_int_submit_application"
  name: "Submit Application Service Creates Application Aggregate"
  test_level: "integration"
  test_type: "functional"

  ddd_ref:
    application_service: "svc_app_submit_application"
    aggregate: "agg_application"
    bounded_context: "bc_applications"

  scenarios:
    - given: "Valid candidate profile exists"
      and: "Job posting is active"
      when: "svc_app_submit_application(candidate_id, job_id)"
      then: "Application aggregate created with status SUBMITTED"
      and: "evt_application_submitted published"
      and: "Application saved to repository"

# End-to-End Test (Full Workflow)
test_case:
  id: "tc_e2e_submit_application_workflow"
  name: "User Submits Application via Workflow"
  test_level: "end_to_end"
  test_type: "functional"

  ux_ref:
    workflow: "wf_submit_application"
    pages: ["page_job_detail", "page_application_review", "page_application_confirmation"]

  ddd_ref:
    application_service: "svc_app_submit_application"
    aggregates: ["agg_job_posting", "agg_candidate_profile", "agg_application"]

  scenarios:
    - given: "User logged in as candidate"
      and: "User viewing job detail page"

      when: "User clicks 'Apply for Job' button"
      then: "Application wizard step 1 displays"
      and: "Job details shown (agg_job_posting)"

      when: "User clicks 'Next'"
      then: "Step 2 displays profile review"
      and: "Profile details shown (agg_candidate_profile)"
      and: "Skills gap widget shows (bc_skills_analysis)"

      when: "User clicks 'Submit Application'"
      then: "Application service called: svc_app_submit_application"
      and: "Loading spinner displays"

      when: "Application created successfully"
      then: "evt_application_submitted event fires"
      and: "Step 3 displays confirmation"
      and: "Toast notification: 'Application submitted successfully!'"
      and: "Email sent to candidate (evt_application_submitted handler)"

      when: "User clicks 'View My Applications'"
      then: "Navigates to applications list (bc_applications)"
      and: "New application appears with status 'Submitted'"
```

---

### Example 3: Testing Domain Event with UI Behavior

**DDD Construct:** `evt_application_status_changed` Domain Event

**UX Construct:** Real-time notification behavior

**QE Test Cases:**

```yaml
# Event Test (Domain Layer)
test_case:
  id: "tc_event_application_status_changed"
  name: "Application Status Change Publishes Domain Event"
  test_level: "integration"
  test_type: "functional"

  ddd_ref:
    aggregate: "agg_application"
    domain_event: "evt_application_status_changed"

  scenarios:
    - given: "Application with status SUBMITTED"
      when: "Employer changes status to IN_REVIEW"
      then: "evt_application_status_changed published"
      and: "Event contains: application_id, old_status=SUBMITTED, new_status=IN_REVIEW, changed_by"

# UI Behavior Test (Event Handler)
test_case:
  id: "tc_ui_application_status_notification"
  name: "UI Displays Notification When Application Status Changes"
  test_level: "ui"
  test_type: "functional"

  ux_ref:
    behavior: "domain_event_triggered_notification"
    component: "comp_toast_notification"

  ddd_ref:
    domain_event: "evt_application_status_changed"

  scenarios:
    - given: "Candidate viewing applications list page"
      and: "WebSocket connection established"

      when: "evt_application_status_changed event received"
      and: "Event: {application_id: '123', new_status: 'IN_REVIEW'}"

      then: "Toast notification displays"
      and: "Message: 'Your application for [Job Title] is now In Review'"
      and: "Application status badge updates to 'In Review'"
      and: "Notification auto-dismisses after 5 seconds"
```

---

## Test Coverage Requirements

### Comprehensive Coverage Across All Layers

For each **Bounded Context**, ensure coverage of:

1. **Domain Layer Tests**
   - All Value Objects validated
   - All Entities tested for business logic
   - All Aggregates tested for consistency
   - All Domain Services tested
   - All Domain Events published and handled

2. **Application Layer Tests**
   - All Application Services tested (use cases)
   - All Repository interfaces tested
   - Integration between domain and infrastructure tested

3. **Presentation Layer Tests**
   - All Pages tested (rendering, data display, navigation)
   - All Components tested (atoms, molecules, organisms, domain components)
   - All Workflows tested (user journeys)
   - All Interactions tested (clicks, hovers, state transitions)

4. **Cross-Cutting Tests**
   - Accessibility (WCAG 2.2 compliance for all pages/components)
   - Performance (load times, responsiveness)
   - Security (authentication, authorization, input sanitization)
   - Usability (user can complete tasks efficiently)

---

## Test Type Mapping

### Functional Testing

| Test Level | DDD Target | UX Target | Example |
|------------|------------|-----------|---------|
| Unit | Value Object, Entity | Atom, Molecule | `vo_email` validation, `comp_button` rendering |
| Integration | Aggregate, Domain Service, Repository | Organism, Page | `agg_candidate_profile` consistency, `page_profile_edit` |
| System | Application Service | Workflow | `svc_app_submit_application`, `wf_submit_application` |
| Acceptance | Use Case | User Journey | End-to-end application submission |

### Non-Functional Testing (ISO 25010)

| Quality Characteristic | DDD Testing | UX Testing |
|------------------------|-------------|------------|
| **Functional Suitability** | Domain rules correctness | Feature completeness |
| **Performance Efficiency** | Repository query performance | Page load time, animation smoothness |
| **Security** | Aggregate access control | Authentication UI, HTTPS |
| **Usability** | Ubiquitous language in errors | Navigation clarity, form usability |
| **Reliability** | Domain invariants enforced | Error handling, graceful degradation |
| **Maintainability** | Code modularity | Component reusability |
| **Portability** | Database abstraction | Responsive design |
| **Compatibility** | API compatibility | Browser compatibility |

---

## Anti-Pattern Testing

### DDD Anti-Patterns to Test Against

```yaml
anti_pattern_tests:
  anemic_domain_model:
    test: "Entities should have behavior, not just getters/setters"
    check: "Entity has business methods, not just properties"

  god_object:
    test: "No single object does everything"
    check: "Aggregates have focused responsibility"

  primitive_obsession:
    test: "Domain concepts use Value Objects, not primitives"
    check: "Email is vo_email, not string"

  leaky_abstraction:
    test: "Domain doesn't know about persistence"
    check: "Domain objects don't reference ORM annotations"
```

### UX Anti-Patterns to Test Against

```yaml
anti_pattern_tests:
  god_component:
    test: "Components should be focused, not do too much"
    check: "Component has single responsibility"

  mystery_meat_navigation:
    test: "Navigation should be clear, not cryptic"
    check: "Icons have labels or aria-labels"

  unclear_progress:
    test: "User knows where they are in workflow"
    check: "Progress indicator displays current step"

  losing_user_data:
    test: "Data persists in long workflows"
    check: "Draft state auto-saves"
```

---

## YAML Schema Integration

### Test Artifact Schema References DDD and UX

```yaml
# QE Test Case Schema (Enhanced with DDD/UX references)
test_case:
  id: string  # tc_[type]_[number]_[name]
  name: string
  description: string

  # Test classification
  test_level: enum [unit, integration, system, acceptance, ui, e2e]
  test_type: enum [functional, performance, security, usability, accessibility, ...]

  # DDD References (optional, when applicable)
  ddd_references:
    bounded_context: string  # bc_[name]
    aggregate: string  # agg_[name]
    entity: string  # ent_[name]
    value_object: string  # vo_[name]
    domain_service: string  # svc_dom_[name]
    application_service: string  # svc_app_[name]
    repository: string  # repo_[name]
    domain_event: string  # evt_[name]

  # UX References (optional, when applicable)
  ux_references:
    page: string  # page_[name]
    workflow: string  # wf_[name]
    component: string  # comp_[name]
    navigation_pattern: string
    interaction_pattern: string
    behavior: string

  # Test definition
  preconditions: [string]
  test_steps: [step]
  expected_results: [string]
  postconditions: [string]

  # Test data
  test_data_refs: [string]  # td_[name]

  # Metadata
  priority: enum [critical, high, medium, low]
  tags: [string]
  author: string
  created_date: date
```

---

## Benefits of Integration

### 1. Comprehensive Test Coverage
- Domain logic tested (DDD)
- User experience tested (UX)
- End-to-end scenarios tested (DDD + UX)

### 2. Traceability
- Test cases trace to domain concepts
- Test cases trace to UI elements
- Requirements → Domain Model → UI → Tests (full traceability)

### 3. Consistency
- Ubiquitous language used in test names and descriptions
- UI terminology matches domain terminology
- Test data uses domain constructs

### 4. Maintainability
- When domain changes, affected tests identified via references
- When UI changes, affected tests identified via references
- Refactoring domain or UI updates test references automatically

### 5. Communication
- QA, Developers, Designers all use same terminology
- Test reports understandable by business stakeholders
- Test coverage maps to business capabilities

---

## Implementation Checklist

### Phase 1: Setup
- [ ] Review DDD ontological taxonomy
- [ ] Review UX ontological taxonomy
- [ ] Establish QE-DDD-UX cross-reference system
- [ ] Create integrated glossary
- [ ] Define YAML schema with DDD/UX references

### Phase 2: Test Planning
- [ ] For each Bounded Context, create test suite
- [ ] Map DDD constructs to test targets
- [ ] Map UX patterns to test scenarios
- [ ] Define coverage requirements

### Phase 3: Test Design
- [ ] Design tests for each test level
- [ ] Reference DDD constructs in test cases
- [ ] Reference UX patterns in UI tests
- [ ] Create test data aligned with domain model

### Phase 4: Test Implementation
- [ ] Implement domain layer tests
- [ ] Implement application layer tests
- [ ] Implement presentation layer tests
- [ ] Implement end-to-end tests

### Phase 5: Validation
- [ ] Verify coverage across all layers
- [ ] Validate test references are correct
- [ ] Check anti-patterns are tested against
- [ ] Ensure traceability end-to-end

---

## References

### QE Research
- `research/qe/qe-prompt.md` - QE research topics
- `research/qe/qe-research-plan.md` - QE research plan
- `research/qe/deliverables/01-foundation-standards.md` - QE foundation

### DDD Research
- `wiki/research/ddd/working-docs/06-ontological-taxonomy.md` - DDD patterns hierarchy
- `wiki/research/ddd/working-docs/03-tactical-patterns.md` - DDD tactical patterns
- `wiki/research/ddd/working-docs/02-strategic-patterns.md` - DDD strategic patterns

### UX Research
- `wiki/research/ux/working-docs/08-ux-ontological-taxonomy.md` - UX patterns hierarchy
- `wiki/research/ux/UX-DDD-INTEGRATION.md` - UX-DDD integration
- `wiki/research/ux/working-docs/04-page-architecture.md` - UX page types
- `wiki/research/ux/working-docs/05-component-architecture.md` - UX components

---

*Integration framework established: 2025-10-04*
*QE testing aligned with DDD domain model and UX patterns*
