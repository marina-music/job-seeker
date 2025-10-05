# Quality Engineering Research Prompt

## Objective

Research and document best practices for Quality Engineering to create an ontological taxonomy that can be applied to describe test requirements for a system.

## Research Topics

Conduct comprehensive research on the following Quality Engineering topics organized by domain:

### I. Standards and Bodies of Knowledge

#### 1. Quality Engineering Standards
- **ISTQB (International Software Testing Qualifications Board)**
  - Foundation Level syllabus
  - Advanced Level certifications
  - AI Testing certification
  - Seven testing principles
  - Glossary and terminology
- **ISO/IEC Standards**
  - ISO 9001:2015 (Quality Management Systems)
  - ISO/IEC 25010 (Software Quality Model)
  - ISO 5055:2021 (Code Quality Standards)
- **ASQ Certified Quality Engineer (CQE) Body of Knowledge**
  - Seven pillars of quality engineering
  - Quality management principles
- **TMAP (Test Management Approach)**
  - DevOps and Agile testing
  - High Performance IT delivery models
- **IEEE Standards**
  - Software testing standards
  - Test documentation standards

### II. Testing Ontologies and Taxonomies

#### 2. Software Testing Ontologies
- **ROoST (Reference Ontology on Software Testing)**
  - Testing process and activities
  - Test artifacts taxonomy
  - Testing environment concepts
  - Testing techniques categorization
- **TestTDO (Test Top-Domain Ontology)**
  - Four-layered ontological architecture
  - Foundational, core, domain, and instance ontologies
  - 43 defined terms and 48 properties
- **STOWS (Software Testing Ontology)**
  - Elementary concepts (software/hardware)
  - Basic testing concepts (Tester, Artifact, Activity, Context, Method, Environment)
  - Compound testing concepts (Task, Capability)
- **Work Product Types (WPT) Pattern**
  - Document artifacts
  - Software items
  - Code artifacts
  - Information items

### III. Test Artifacts and Documentation

#### 3. Test Strategy
- Definition and purpose
- Organizational vs project test strategy
- When to create test strategies
- Components and structure
- Relationship to quality strategy
- Alignment with organizational goals
- Best practices and frameworks
- Continuous Testing Model (Dan Ashby)
- Holistic Testing Model (Janet Gregory)

#### 4. Test Plans
- Definition and components
- Differences from test strategies
- IEEE 829 test plan standard
- Test planning in Agile/DevOps
- Best practices for test plan creation
- Templates and standards
- Risk assessment in test planning
- Resource and schedule planning

#### 5. Test Scenarios
- Definition and characteristics
- How to write effective test scenarios
- Relationship to requirements and user stories
- Scenario-based testing approaches
- Best practices
- Traceability to requirements

#### 6. Test Cases
- Definition and structure
- Test case components (preconditions, steps, expected results)
- Differences from test scenarios
- Test case design best practices
- Test case management
- Reusability and maintainability

#### 7. Test Execution and Results
- Test execution process
- Test result documentation
- Pass/fail criteria
- Actual vs expected results
- Test execution logs

#### 8. Test Reports
- Test summary reports
- Defect reports
- Test metrics and KPIs
- Stakeholder communication

### IV. Test Levels

#### 9. Component/Unit Testing
- Definition and scope (ISTQB definition)
- Code-level testing
- Component isolation
- Best practices
- Code coverage strategies (statement, branch, path)
- Unit testing frameworks
- Test-Driven Development (TDD)

#### 10. Integration Testing
- Definition and scope (ISTQB definition)
- Interface and interaction testing
- Integration patterns:
  - Big Bang integration
  - Top-down integration
  - Bottom-up integration
  - Sandwich/hybrid integration
  - Continuous integration
- Component vs system integration
- API testing
- Challenges and solutions
- Best practices

#### 11. System Testing
- Definition and scope
- End-to-end system behavior
- Black-box testing approach
- System requirements verification
- Best practices

#### 12. Acceptance Testing
- Definition (ISTQB definition)
- User acceptance testing (UAT)
- Business acceptance testing
- Operational acceptance testing
- Contract acceptance testing
- Alpha and Beta testing
- Acceptance criteria
- Best practices

### V. Test Types and Characteristics

#### 13. Functional Testing
- Definition and scope
- Requirements-based testing
- Black-box testing techniques
- Functional test coverage

#### 14. Non-Functional Testing (ISO 25010 Quality Characteristics)
- **Performance Efficiency**
  - Load testing: techniques, tools, metrics
  - Stress testing: breaking points, recovery
  - Endurance/Soak testing: long-term stability
  - Spike testing: sudden load changes
  - Volume testing: large data sets
  - Scalability testing
  - Response time testing: benchmarks, optimization
- **Security Testing**
  - Confidentiality testing
  - Integrity testing
  - Authentication and authorization
  - Non-repudiation
  - Accountability
  - Vulnerability scanning
  - Penetration testing
  - Security compliance (OWASP, etc.)
- **Usability Testing**
  - User interface testing
  - User experience testing
  - Learnability and operability
  - Accessibility testing (WCAG 2.2, EN 301 549)
  - European Accessibility Act compliance
- **Reliability Testing**
  - Fault tolerance
  - Recoverability
  - Availability testing
  - Mean Time Between Failures (MTBF)
- **Maintainability Testing**
  - Modularity assessment
  - Reusability evaluation
  - Analyzability
  - Modifiability
  - Testability
  - Code quality metrics
- **Portability Testing**
  - Adaptability
  - Installability
  - Replaceability
- **Compatibility Testing**
  - Co-existence
  - Interoperability
  - Browser compatibility
  - Platform compatibility

#### 15. Regression Testing
- Definition and purpose
- Regression test selection
- Test suite maintenance
- Automated regression testing
- Best practices

#### 16. Smoke and Sanity Testing
- Definitions and differences
- When to use each
- Build verification testing
- Best practices

### VI. Test Design Techniques

#### 17. Black-Box Testing Techniques
- **Equivalence Partitioning**
  - Definition and theory
  - Valid and invalid partitions
  - Partition coverage
  - Best practices
- **Boundary Value Analysis (BVA)**
  - Definition and rationale
  - Two-point vs three-point BVA
  - Robustness testing
  - Edge case identification
  - Best practices
- **Decision Table Testing**
  - Definition and structure
  - Condition and action combinations
  - Full vs limited entry tables
  - Decision table reduction
  - Best practices
- **State Transition Testing**
  - State diagrams and tables
  - Valid and invalid transitions
  - State coverage criteria
  - Event-driven systems
  - Best practices
- **Use Case Testing**
  - Scenario-based testing
  - Basic and alternative flows
  - Exception handling

#### 18. White-Box Testing Techniques
- Statement coverage
- Branch/decision coverage
- Path coverage
- Condition coverage
- Multiple condition coverage
- Code complexity metrics (cyclomatic complexity)

#### 19. Experience-Based Techniques
- Error guessing
- Exploratory testing
- Checklist-based testing
- Attack-based testing

### VII. Test Approaches and Methodologies

#### 20. Shift-Left Testing
- Definition and principles
- Four types of shift-left testing:
  - Traditional shift-left
  - Incremental shift-left
  - Agile/DevOps shift-left
  - Model-based shift-left
- Benefits: early defect detection, cost reduction
- Implementation strategies
- Integration with development process

#### 21. Shift-Right Testing
- Testing in production
- Monitoring and observability
- Canary releases
- A/B testing
- Feature flags
- Chaos engineering

#### 22. Continuous Testing
- Definition and scope
- Integration with CI/CD pipelines
- Automated test execution
- Immediate feedback loops
- DevOps alignment
- Test automation strategy

#### 23. Risk-Based Testing (RBT)
- Definition and principles
- Risk identification and analysis
- Risk assessment (likelihood × impact)
- Risk prioritization (High, Medium, Low)
- Test prioritization based on risk
- 70% resource allocation to high-risk areas
- 40% reduction in low-risk testing
- 95% defect coverage achievement
- 35% faster critical defect detection
- Traceability: risks → tests → results → defects
- Best practices

#### 24. Exploratory Testing
- Charter-based testing
- Session-based test management
- Heuristics and oracles
- Relationship to scripted testing

#### 25. Model-Based Testing
- Test model creation
- Model-driven test generation
- Specification-based models
- State models and flow graphs

### VIII. Test Automation

#### 26. Test Automation Strategy
- When to automate vs manual testing
- Test automation ROI
- Tool selection criteria
- Automation framework design
- Test automation pyramid
- Test automation anti-patterns
- Maintenance and sustainability

#### 27. Test Automation Frameworks
- Linear scripting
- Structured/modular frameworks
- Data-driven frameworks
- Keyword-driven frameworks
- Hybrid frameworks
- Behavior-Driven Development (BDD)
- Page Object Model (POM)
- Best practices for framework design

#### 28. Test Orchestration
- Definition: coordinating automated test execution
- Sequential and parallel test execution
- Test workflow optimization
- CI/CD integration (100% availability requirement)
- Environment management (VMs, containers, cloud)
- Test scheduling and prioritization
- Resource allocation and optimization
- Reduced manual effort and faster feedback
- Test orchestration tools and platforms

#### 29. Continuous Integration/Continuous Delivery (CI/CD) Testing
- Pipeline integration points
- Build verification
- Automated test gates
- Deployment testing
- Feedback mechanisms

### IX. Test Data and Environment Management

#### 30. Test Data Management
- Test data strategies and approaches
- Test data creation techniques:
  - Manual creation
  - Data generation tools
  - Production data masking
  - Synthetic data generation
- Data maintenance and versioning
- Test data security and privacy
- GDPR and compliance considerations
- Test data independence
- Data refresh strategies
- Best practices

#### 31. Test Environment Management
- Environment configuration
- Environment provisioning
- Virtual machines and containers
- Cloud-based test environments
- Environment consistency
- Environment monitoring
- Best practices

### X. Test Doubles and Mocking

#### 32. Test Doubles Taxonomy
- **Dummy Objects**
  - Definition: passed but never used
  - Use cases
- **Stubs**
  - Definition: provide canned responses
  - When to use stubs
  - Implementation strategies
- **Fakes**
  - Definition: working implementations with shortcuts
  - Examples: in-memory databases
  - When to use fakes
- **Mocks**
  - Definition: objects with expectations for verification
  - Behavior verification
  - When to use mocks vs stubs
  - Mock frameworks
- **Spies**
  - Definition: record information about calls
  - Partial mocking
- When to use each type
- Best practices and common pitfalls
- Over-mocking anti-pattern

### XI. Testing in Different Contexts

#### 33. Agile Testing
- Testing in Scrum
- Sprint testing activities
- Definition of Done
- Acceptance criteria
- Test automation in Agile
- Whole team approach
- Continuous feedback

#### 34. DevOps Testing
- Testing in DevOps pipeline
- Infrastructure as Code testing
- Containerization testing
- Microservices testing
- Testing in production
- ChatOps and collaboration

#### 35. Mobile Testing
- Platform-specific testing (iOS, Android)
- Device fragmentation
- Mobile-specific test types
- Emulators vs real devices
- Mobile test automation

#### 36. API Testing
- RESTful API testing
- SOAP/GraphQL testing
- API contract testing
- API security testing
- API performance testing

#### 37. Microservices Testing
- Service isolation testing
- Contract testing
- Service virtualization
- End-to-end testing challenges
- Distributed tracing

### XII. Quality Management and Metrics

#### 38. Defect Management
- Defect lifecycle
- Defect classification (severity, priority)
- Defect tracking and reporting
- Root cause analysis
- Defect metrics:
  - Defect density
  - Defect removal efficiency
  - Defect aging
  - Defect leakage
- Defect prevention strategies
- Historical defect data analysis for risk assessment

#### 39. Test Metrics and Measurement
- Coverage metrics
- Test execution metrics
- Defect metrics
- Quality metrics
- Productivity metrics
- Test effectiveness metrics
- KPIs for testing
- Metrics-driven improvements

#### 40. Test Process Improvement
- Test maturity models (TMMi)
- Process assessment
- Continuous improvement
- Retrospectives and lessons learned
- Best practices adoption

### XIII. Emerging Topics and Trends

#### 41. AI and Machine Learning in Testing
- AI-augmented testing
- ML-based test generation
- Intelligent test automation
- Predictive analytics for testing
- AI system testing (ISTQB AI Testing)

#### 42. Accessibility and Inclusive Testing
- WCAG 2.2 standards
- EN 301 549 compliance
- European Accessibility Act (enforced June 28, 2025)
- Automated accessibility tools
- Manual accessibility testing
- Screen reader testing
- Keyboard navigation testing

#### 43. IoT and Blockchain Testing
- IoT device testing
- IoT security testing
- Blockchain testing approaches
- Smart contract testing

## Research Requirements

For each topic, provide:

### Content Requirements
1. **Clear, authoritative definitions**
   - Use ISTQB glossary definitions where applicable
   - Reference ISO/IEC standards
   - Include multiple perspectives if definitions vary
2. **Detailed descriptions**
   - Explain the purpose and context
   - Describe key concepts and principles
   - Provide real-world applicability
3. **Best practices and strategies**
   - Industry-standard approaches
   - Proven methodologies
   - Common patterns and frameworks
4. **When and how to apply each technique**
   - Appropriate contexts and scenarios
   - Prerequisites and dependencies
   - Step-by-step guidance
5. **Common pitfalls and anti-patterns**
   - What to avoid
   - Mistakes and misconceptions
   - Lessons learned from industry
6. **Relationships to other testing concepts**
   - Hierarchical relationships (parent/child)
   - Dependencies and prerequisites
   - Complementary concepts
   - Conflicts or trade-offs
7. **Industry standards and frameworks**
   - ISO standards (ISO 9001, ISO 25010, ISO 5055)
   - IEEE standards
   - ISTQB certifications and syllabi
   - ASQ CQE Body of Knowledge
   - TMAP framework
   - Other relevant frameworks

### Ontological Requirements
For building the taxonomy, identify for each concept:
- **Concept type**: Artifact, Activity, Role, Method, Tool, Metric, Quality Characteristic
- **Parent concepts**: What this concept belongs to or extends
- **Child concepts**: What concepts are contained within or derived from this
- **Related concepts**: Associated concepts in different branches
- **Attributes**: Key properties and characteristics
- **Constraints**: Rules, preconditions, postconditions
- **Lifecycle**: When in the development/testing lifecycle this applies

## Deliverables

### Stage 1: Working Documents
Create individual working documents for each topic domain (I-XIII) with detailed research findings:
- One document per major domain section
- Comprehensive coverage of all subtopics within each domain
- Cross-references to related concepts in other domains
- Source citations and references

### Stage 2: Synthesis
Create a comprehensive summary document with two components:

#### Component 1: Quality Engineering Knowledge Base
An integrated document containing:
- **Ontological Taxonomy**: Hierarchical organization of all QE concepts
  - Organized by concept type (Artifacts, Activities, Roles, Methods, Tools, Metrics, Quality Characteristics)
  - Parent-child relationships clearly mapped
  - Cross-references and dependencies documented
- **Definitions and Standards**: Elaborate definitions of all terms
  - ISTQB glossary alignments
  - ISO/IEC standard references
  - Multiple perspectives where applicable
- **Best Practices Compendium**: Detailed strategies for implementation
  - When to apply each concept
  - How to implement effectively
  - Common pitfalls to avoid
- **Relationship Maps**: Visual and textual representations of concept relationships
  - Hierarchies
  - Dependencies
  - Trade-offs and conflicts

#### Component 2: Formal YAML Language for Test Requirements
Create a formal YAML schema/language inspired by ROoST, TestTDO, and STOWS ontologies that describes the structure of test requirements in a hierarchical way:

**Structure Requirements:**
- **Test Artifact Types**
  - TestStrategy
  - TestPlan
  - TestScenario
  - TestCase
  - TestData
  - TestEnvironment
  - TestResult
  - DefectReport
- **Test Activity Types**
  - Planning
  - Design
  - Implementation
  - Execution
  - Evaluation
  - Reporting
- **Test Method Types**
  - Test levels (Unit, Integration, System, Acceptance)
  - Test types (Functional, Non-functional)
  - Test design techniques (BVA, EP, Decision Table, State Transition)
  - Test approaches (Shift-Left, Risk-Based, Exploratory)
- **Quality Characteristics** (ISO 25010)
  - Functional Suitability
  - Performance Efficiency
  - Security
  - Usability
  - Reliability
  - Maintainability
  - Portability
  - Compatibility
- **Relationships and Constraints**
  - Traceability links (requirement → test scenario → test case → defect)
  - Dependencies between artifacts
  - Coverage mappings
  - Execution ordering constraints
- **Metadata and Properties**
  - Required and optional fields for each artifact type
  - Validation rules
  - Status lifecycles
  - Version control
- **Extensibility Mechanisms**
  - Custom artifact types
  - Custom attributes
  - Domain-specific extensions
  - Tool integration points

**YAML Schema Features:**
- Clear naming conventions aligned with ISTQB terminology
- Reusable component definitions
- Support for inheritance and composition
- Validation constraints
- Documentation annotations
- Examples for each artifact type

## Expected Outcome

An ontological taxonomy that provides:

### Knowledge Management
- A clear, standardized vocabulary for quality engineering aligned with ISTQB, ISO, and industry standards
- Comprehensive definitions with authoritative sources
- Best practices derived from industry bodies of knowledge (TMAP, ASQ CQE, ISTQB)

### Structural Framework
- Hierarchical structure showing relationships between testing concepts (inspired by ROoST, TestTDO, STOWS)
- Clear concept type classifications (Artifact, Activity, Role, Method, Tool, Metric, Quality Characteristic)
- Parent-child relationships and dependency maps
- Cross-domain concept relationships

### Practical Application
- A formal specification language (YAML) for describing test requirements
- Practical guidance on applying each concept in real-world scenarios
- Reusable templates and patterns
- Traceability mechanisms for requirements-to-tests-to-defects

### Flexibility and Scale
- A framework that can be used across different systems and projects
- Extensibility for domain-specific needs
- Support for various development methodologies (Waterfall, Agile, DevOps)
- Integration points for test management tools and CI/CD pipelines

### Industry Alignment
- Compliance with recognized standards (ISO 25010, ISTQB, IEEE)
- Addresses modern needs (Accessibility Act 2025, AI Testing, Shift-Left/Right)
- Supports emerging technologies (IoT, Blockchain, Microservices)
