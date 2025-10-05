# Foundation: Standards and Ontologies

**Date:** 2025-10-04
**Status:** Phase 1 Complete
**Purpose:** Establish authoritative baseline definitions and understand existing ontological frameworks

---

## Executive Summary

This document provides the foundational knowledge for creating a comprehensive Quality Engineering ontological taxonomy. It synthesizes information from:
- International standards (ISTQB, ISO/IEC, IEEE)
- Existing software testing ontologies (ROoST, TestTDO, STOWS)
- Quality engineering bodies of knowledge (ASQ CQE, TMAP)

The research confirms that while several ontologies exist, there is an opportunity to create a more comprehensive, YAML-based taxonomy that integrates best practices from all sources and addresses modern testing needs (AI, accessibility, DevOps, microservices).

---

## 1. ISTQB (International Software Testing Qualifications Board)

### Overview
ISTQB is the leading global certification scheme in software testing with over 1.1 million certifications issued worldwide as of 2025.

### Foundation Level Syllabus v4.0

The ISTQB Foundation Level certification covers six main chapters:

#### Chapter 1: Fundamentals of Testing
- What is Testing
- Why Testing is Necessary
- **Seven Testing Principles** (core to all testing)
- Testing Activities, Testware & Test Roles
- Essential Skills & Good Practices

#### Chapter 2: Testing Throughout the Software Development Lifecycle
- Testing in SDLC Context
- **Test Levels**: Component, Integration, System, Acceptance
- **Test Types**: Functional, Non-functional, etc.
- Maintenance Testing

#### Chapter 3: Static Testing
- Static Testing Basics
- Feedback & Review Process

#### Chapter 4: Test Analysis & Design
- Test Techniques Overview
- **Black-Box Test Techniques**: Equivalence Partitioning, Boundary Value Analysis, Decision Table, State Transition
- **White-Box Test Techniques**: Statement, Branch, Path coverage
- **Experience-Based Test Techniques**: Error guessing, Exploratory testing
- Collaboration-Based Test Approaches

#### Chapter 5: Managing Test Activities
- Test Planning
- Risk Management
- Test Monitoring & Control
- Configuration Management
- **Defect Management**

#### Chapter 6: Test Tools
- Tool Support for Testing
- Benefits & Risks of Test Automation

### Key ISTQB Definitions

#### Test Case
**ISTQB Definition**: *A set of input values, execution preconditions, expected results and execution postconditions, developed for a particular objective or test condition, such as to exercise a particular program path or to verify compliance with a specific requirement.*

**Components**:
- Input values
- Execution preconditions
- Expected results
- Execution postconditions
- Test objective or condition

#### Test Plan
**ISTQB Definition**: *A document describing the scope, approach, resources and schedule of intended test activities. It identifies amongst others test items, the features to be tested, the testing tasks, who will do each task, degree of tester independence, the test environment, the test design techniques and entry and exit criteria.*

**Key Elements**:
- Scope
- Approach
- Resources
- Schedule
- Test items
- Features to be tested
- Testing tasks
- Responsibilities
- Test environment
- Test design techniques
- Entry and exit criteria

#### Test Strategy
**ISTQB Definition**: *A high-level description of the test levels to be performed and the testing within those levels for an organization or programme (one or more projects).*

**Scope**: Organizational or program level (broader than test plan)

### ISTQB Glossary
- **Location**: https://glossary.istqb.org/
- **Format**: Online searchable database
- **Coverage**: Comprehensive testing terminology
- **Usage**: Industry-standard reference for testing terms
- **Note**: Definitions should be prioritized as primary source

### ISTQB Certifications Relevant to This Research
- Foundation Level (CTFL v4.0) - Core testing concepts
- Advanced Level Test Manager (CTAL-TM) - Test strategy and management
- AI Testing - Testing AI-based systems (emerging, 2025)

---

## 2. ISO/IEC Standards

### ISO 9001:2015 - Quality Management Systems

**Purpose**: Globally recognized standard for quality management
**Relevance**: Establishes quality management principles applicable to testing
**Focus**: Process approach, customer satisfaction, continuous improvement

**Key Principles**:
- Customer focus
- Leadership
- Engagement of people
- Process approach
- Improvement
- Evidence-based decision making
- Relationship management

### ISO/IEC 25010:2023 - Software Quality Model

**Purpose**: Defines software product quality characteristics
**Framework**: Part of SQuaRE (Systems and software Quality Requirements and Evaluation)

#### Eight Quality Characteristics

1. **Functional Suitability** (3 sub-characteristics)
   - Functional completeness
   - Functional correctness
   - Functional appropriateness

2. **Performance Efficiency** (3 sub-characteristics)
   - Time behaviour
   - Resource utilization
   - Capacity

3. **Compatibility** (2 sub-characteristics)
   - Co-existence
   - Interoperability

4. **Usability/Interaction Capability** (8 sub-characteristics)
   - Appropriateness recognizability
   - Learnability
   - Operability
   - User error protection
   - User engagement
   - Inclusivity
   - User assistance
   - Self-descriptiveness

5. **Reliability** (4 sub-characteristics)
   - Maturity
   - Availability
   - Fault tolerance
   - Recoverability

6. **Security** (5 sub-characteristics)
   - Confidentiality
   - Integrity
   - Non-repudiation
   - Accountability
   - Authenticity

7. **Maintainability** (5 sub-characteristics)
   - Modularity
   - Reusability
   - Analyzability
   - Modifiability
   - Testability

8. **Portability** (3 sub-characteristics)
   - Adaptability
   - Installability
   - Replaceability

**Total**: 8 characteristics, 31+ sub-characteristics

**Significance**:
- Added Security and Compatibility to ISO 9126's original six characteristics
- Provides comprehensive framework for non-functional testing
- Cornerstone of product quality evaluation systems

### ISO 5055:2021 - Code Quality Standards

**Purpose**: Measuring internal structure of software products
**Focus**: Four business-critical factors
- Security
- Reliability
- Performance Efficiency
- Maintainability

**Application**: Automated static code analysis and quality metrics

### IEEE Standards

**IEEE 829** - Test Documentation Standard
- Defines structure and content of test documentation
- Test plan templates
- Test case specifications
- Test procedure specifications
- Test reports

**Note**: Other relevant IEEE standards for testing exist but require IEEE Xplore access for detailed review

---

## 3. Software Testing Ontologies

### 3.1 ROoST (Reference Ontology on Software Testing)

**Source**: NEMO (Networked Ontology Specification), University of Espírito Santo, Brazil
**URL**: https://dev.nemo.inf.ufes.br/seon/ROoST.html
**Integration**: Part of SEON (Software Engineering Ontology Network)

#### Structure: Five Sub-Ontologies

1. **Testing Artifacts**
2. **Testing Stakeholders**
3. **Testing Techniques**
4. **Testing Process**
5. **Testing Environment**

#### Taxonomies

ROoST includes taxonomies for:
- **Tester** (roles and responsibilities)
- **Context** (testing contexts)
- **Testing Activities** (what testers do)
- **Testing Methods** (techniques and approaches)
- **Testing Artifacts** (documents and work products)

#### Key Concepts and Definitions

**Stakeholders**:
- **Test Manager**: Stakeholder responsible for planning and managing the testing activities
- **Test Case Designer**: Stakeholder responsible for designing test cases and analyzing test results
- **Tester**: Stakeholder responsible for coding and executing test cases

**Testing Levels**:
- **Unit Testing**: Focuses on individual components
- **Integration Testing**: Focuses on larger component interactions
- **System Testing**: Focuses on entire system behavior

**Testing Techniques**:
- **Black-box Testing**: Ignores internal mechanisms, focuses on inputs/outputs
- **White-box Testing**: Derives tests from code structure
- **Model-based Testing**: Derives test cases from system models
- **Mutation Testing**: Evaluates test cases by creating program mutations

**Test Artifacts**:
- **Test Plan**: Roadmap for testing activities
- **Test Case**: Document with input data, expected results, and testing conditions
- **Test Suite**: Collection of test cases
- **Test Result**: Document with actual test execution results
- **Test Analysis Report**: Analysis of test results

**Testing Environment**:
- Collection of Test Hardware and Software Resources
- **Test Management Tools**: Support test planning and tracking
- **Incident Management Tools**: Support defect tracking and management

#### Strengths
- Comprehensive coverage of testing domain
- Well-structured modular design
- Integration with broader software engineering ontology (SEON)
- Focuses on dynamic testing activities
- Reuses ontology patterns from Software Process Ontology Pattern Language (SP-OPL)

#### Limitations
- Primarily focused on traditional/dynamic testing
- May not fully cover modern practices (DevOps, continuous testing)

---

### 3.2 TestTDO (Test Top-Domain Ontology)

**Authors**: Tebes, Olsina, et al.
**Latest Version**: v1.3 (as of search date)
**Architecture**: Four-layered ontological architecture (FCD-OntoArch)

#### Four-Layer Architecture

1. **Foundational Level**: Basic ontological concepts (upper ontology)
2. **Core Level**: Cross-domain concepts applicable to multiple domains
3. **Domain Level**: Software testing-specific concepts
4. **Instance Level**: Specific instantiations and examples

**Framework**: FCD-OntoArch (Foundational, Core, and Domain Ontological Architecture for Sciences)

#### Technical Composition

- **43 defined terms**
- **48 defined properties**
- **36 defined non-taxonomic relationships**
- **14 axioms specified in first-order logic**

#### Development Methodology

TestTDO was developed by:
- Analyzing Systematic Literature Review (SLR) results on software testing ontologies
- Reviewing state-of-the-art test-related standards
- Extending concepts from:
  - **SituationCO** (Situation Core Ontology)
  - **ProcessCO** (Process Core Ontology)

#### Strengths
- Rigorous formal foundation (first-order logic axioms)
- Clear layered architecture enables reuse and extension
- Built on proven core ontologies
- Systematic development process based on literature review
- Explicit property and relationship definitions

#### Characteristics
- Defines terms, properties, relationships, and axioms explicitly and unambiguously
- Addresses complexity of software testing concepts
- Provides robust conceptual base
- Designed for evolution (multiple versions: v1.1, v1.2, v1.3, mentions of v2.0)

---

### 3.3 STOWS (Software Testing Ontology for Web Services)

**Authors**: Zhu and Huo
**Target Domain**: Web-based applications and web services
**Representation**: UML (high-level) and XML (computer processing)

#### Three-Tier Concept Classification

1. **Elementary Concepts**
   - General concepts about computer software and hardware
   - Foundation layer

2. **Basic Testing Concepts**
   - **Tester**: Testing roles
   - **Artifact**: Testing work products
   - **Activity**: Testing actions
   - **Context**: Testing environment and circumstances
   - **Method**: Testing techniques and approaches
   - **Environment**: Infrastructure for testing

3. **Compound Testing Concepts**
   - **Task**: Combinations of activities, artifacts, methods
   - **Capability**: Combinations defining what can be tested and how

#### Taxonomies

STOWS provides taxonomies for:
- Activity
- Test Type
- Target Under Test
- Test Environment
- Test Schedule
- Test Capability (composed of Test Type, Test Activity, Test Environment, Target)

#### Application Domain

Specifically designed for:
- Web services testing
- Service-oriented architecture (SOA)
- Registration, discovery, and invocation of test services
- Multi-agent testing systems

#### Implementation

- **Representation**: UML for human validation
- **Codification**: XML for computer processing and agent communication
- **Flexibility**: Designed for extensibility
- **Integration**: Support for integrating new testing tools as agents

#### Strengths
- Clear three-tier conceptual hierarchy
- Practical application in multi-agent systems
- Machine-readable (XML) and human-readable (UML)
- Domain-specific (web services)

#### Limitations
- **Not published**: Limited accessibility for research community
- Narrower scope (web services) may limit general applicability
- May not cover modern microservices patterns fully

---

## 4. Other Standards and Bodies of Knowledge

### 4.1 ASQ Certified Quality Engineer (CQE) Body of Knowledge

**Organization**: American Society for Quality (ASQ)
**URL**: https://asq.org

#### Seven Pillars of Quality Engineering

1. Quality Concepts
2. Quality Systems
3. Product and Process Design
4. Product and Process Control
5. Measurement and Analysis
6. Continuous Improvement
7. Quality Audit

**Relevance**: Broader quality engineering context beyond software testing
**Certification**: Professional certification with examination based on BoK
**Application**: General quality engineering principles applicable to software QE

### 4.2 TMAP (Test Management Approach)

**URL**: https://www.tmap.net
**Focus**: Body of knowledge for quality engineering and testing in IT delivery

#### Coverage Areas

- **DevOps Testing**: Testing in continuous delivery pipelines
- **Scrum/Agile Testing**: Testing in iterative development
- **High Performance IT Delivery Models**: Modern delivery approaches
- **Test Types**:
  - Performance testing
  - Security testing
  - Maintainability testing
  - Usability testing

#### Characteristics
- Practical, industry-focused approach
- Aligned with modern development methodologies
- Comprehensive testing lifecycle coverage
- Tool and framework agnostic

---

## 5. Terminology Cross-Reference

### Core Testing Artifacts

| Concept | ISTQB | ROoST | TestTDO | STOWS | ISO/IEEE |
|---------|-------|-------|---------|-------|----------|
| **Test Strategy** | High-level test levels description | Implicit in Planning | Domain concept | Method | IEEE 829 |
| **Test Plan** | Scope, approach, resources, schedule | Roadmap for testing | Domain artifact | Artifact | IEEE 829 |
| **Test Scenario** | Not explicitly defined | Part of Test Design | Domain concept | Context | - |
| **Test Case** | Input, preconditions, expected results, postconditions | Document with input/expected results | Domain artifact | Artifact | IEEE 829 |
| **Test Suite** | Not in glossary excerpt | Collection of test cases | Domain concept | Artifact | IEEE 829 |
| **Test Result** | Not in glossary excerpt | Actual execution results | Domain artifact | Artifact | IEEE 829 |
| **Defect/Incident** | Managed in Ch. 5 | Tracked via Incident Mgmt Tools | Domain concept | - | IEEE 829 |

### Test Levels

| Level | ISTQB | ROoST | Applicability |
|-------|-------|-------|---------------|
| **Component/Unit Testing** | Foundation Ch. 2 | Individual components | Universal |
| **Integration Testing** | Foundation Ch. 2 | Component interactions | Universal |
| **System Testing** | Foundation Ch. 2 | Entire system behavior | Universal |
| **Acceptance Testing** | Foundation Ch. 2 | User/business validation | Universal |

### Test Types

| Type | ISTQB | ISO 25010 | ROoST |
|------|-------|-----------|-------|
| **Functional Testing** | Foundation Ch. 2 | Functional Suitability | Requirements-based |
| **Performance Testing** | Foundation Ch. 2 | Performance Efficiency | - |
| **Security Testing** | Foundation Ch. 2 | Security | - |
| **Usability Testing** | Foundation Ch. 2 | Usability | - |
| **Reliability Testing** | Foundation Ch. 2 | Reliability | - |
| **Maintainability Testing** | Foundation Ch. 2 | Maintainability | - |
| **Portability Testing** | Foundation Ch. 2 | Portability | - |
| **Compatibility Testing** | Foundation Ch. 2 | Compatibility | - |

### Test Design Techniques

| Technique | ISTQB | ROoST | Type |
|-----------|-------|-------|------|
| **Equivalence Partitioning** | Foundation Ch. 4 | - | Black-box |
| **Boundary Value Analysis** | Foundation Ch. 4 | - | Black-box |
| **Decision Table Testing** | Foundation Ch. 4 | - | Black-box |
| **State Transition Testing** | Foundation Ch. 4 | - | Black-box |
| **Statement Coverage** | Foundation Ch. 4 | - | White-box |
| **Branch Coverage** | Foundation Ch. 4 | - | White-box |
| **Path Coverage** | Foundation Ch. 4 | - | White-box |
| **Black-box Testing** | General category | Inputs/outputs focus | - |
| **White-box Testing** | General category | Code structure-based | - |
| **Model-based Testing** | - | Test cases from models | - |
| **Mutation Testing** | - | Evaluate test quality | - |
| **Error Guessing** | Foundation Ch. 4 | - | Experience-based |
| **Exploratory Testing** | Foundation Ch. 4 | - | Experience-based |

---

## 6. Ontological Analysis

### Concept Type Classifications (Synthesis from All Sources)

#### Artifacts (Work Products)
- Test Strategy
- Test Plan
- Test Scenario
- Test Case
- Test Suite
- Test Data
- Test Script
- Test Result
- Test Report
- Test Analysis Report
- Defect/Incident Report
- Test Environment Configuration

#### Activities (Actions)
- Test Planning
- Test Analysis
- Test Design
- Test Implementation
- Test Execution
- Test Evaluation
- Test Reporting
- Test Monitoring and Control
- Defect Management
- Test Environment Setup

#### Roles (Stakeholders)
- Test Manager
- Test Analyst
- Test Case Designer
- Tester (Test Execution)
- Test Automation Engineer
- Quality Assurance Engineer
- Developer (in testing context)

#### Methods (Techniques and Approaches)
- **Test Levels**: Unit, Integration, System, Acceptance
- **Test Types**: Functional, Non-functional (8 ISO characteristics)
- **Test Design Techniques**: Black-box, White-box, Experience-based
- **Test Approaches**: Risk-based, Model-based, etc.

#### Tools
- Test Management Tools
- Test Automation Tools
- Defect Management Tools
- Test Data Management Tools
- Performance Testing Tools
- Static Analysis Tools

#### Metrics
- Test Coverage
- Defect Density
- Test Execution Progress
- Defect Detection Rate
- Code Coverage (statement, branch, path)

#### Quality Characteristics (ISO 25010)
- Functional Suitability
- Performance Efficiency
- Compatibility
- Usability
- Reliability
- Security
- Maintainability
- Portability

---

## 7. Identified Gaps in Existing Ontologies

### Modern Testing Practices

#### Not Well Covered in Existing Ontologies:
1. **Shift-Left Testing** - Early testing in development lifecycle
2. **Shift-Right Testing** - Testing in production
3. **Continuous Testing** - Testing in CI/CD pipelines
4. **Test Orchestration** - Coordinating automated test execution
5. **DevOps Testing** - Testing in DevOps culture
6. **Microservices Testing** - Service isolation, contract testing
7. **API Testing** - RESTful, GraphQL, SOAP testing
8. **Chaos Engineering** - Resilience testing
9. **AI/ML Testing** - Testing AI systems and AI-augmented testing
10. **Accessibility Testing** - WCAG 2.2, EN 301 549 compliance

### Test Automation
- Test automation strategy and frameworks
- Page Object Model
- Behavior-Driven Development (BDD)
- Data-driven testing
- Keyword-driven testing

### Modern Quality Characteristics
- Accessibility (now part of ISO 25010 Usability)
- Inclusivity
- Sustainability/Green Testing
- Observability

---

## 8. Terminology Alignment Strategy

### Primary Source Hierarchy

For the ontological taxonomy, terminology will be aligned in this priority order:

1. **ISTQB Glossary** - Primary source for testing terminology
2. **ISO/IEC Standards** - Primary for quality characteristics and models
3. **ROoST Ontology** - Reference for structural organization
4. **TestTDO** - Reference for formal rigor and axioms
5. **IEEE Standards** - Reference for documentation structures
6. **Industry Practice** - For emerging concepts not yet standardized

### Handling Conflicts

When definitions conflict:
1. Document all perspectives
2. Note the context in which each applies
3. Prefer ISTQB for testing-specific terms
4. Prefer ISO for quality characteristics
5. Clearly mark emerging/evolving terms

---

## 9. Architectural Approach for QE Taxonomy

Based on analysis of existing ontologies, the QE taxonomy will adopt:

### Four-Layer Architecture (inspired by TestTDO)

1. **Foundational Layer**
   - Basic concepts: Entity, Activity, Artifact, Role, etc.
   - Applicable across all domains

2. **Core Layer**
   - Software engineering concepts
   - Process concepts (from ProcessCO model)
   - Situation concepts (from SituationCO model)

3. **Domain Layer** (Quality Engineering)
   - Testing concepts (inspired by ROoST structure)
   - Quality characteristics (ISO 25010)
   - Test artifacts, activities, roles, methods
   - Modern testing practices

4. **Instance Layer**
   - Specific test scenarios
   - Example implementations
   - Project-specific extensions

### Modular Structure (inspired by ROoST)

Primary modules:
- **Test Artifacts** (documents, data, results)
- **Test Activities** (planning, design, execution, evaluation)
- **Test Stakeholders** (roles and responsibilities)
- **Test Methods** (levels, types, techniques, approaches)
- **Test Environment** (infrastructure, tools, configuration)
- **Quality Characteristics** (ISO 25010 + extensions)
- **Test Metrics** (coverage, defects, effectiveness)

### Concept Classification (inspired by STOWS)

- **Elementary Concepts**: Basic software/system concepts
- **Basic QE Concepts**: Artifacts, Activities, Roles, Methods, Tools, Metrics, Quality Characteristics
- **Compound Concepts**: Test scenarios, test capabilities, test strategies

---

## 10. Key Takeaways

### Standards Authority
- **ISTQB**: Industry-standard terminology for software testing
- **ISO 25010**: Authoritative model for software quality characteristics
- **IEEE 829**: Standard for test documentation

### Ontological Frameworks
- **ROoST**: Comprehensive, modular, well-structured
- **TestTDO**: Rigorous, formal, layered architecture
- **STOWS**: Three-tier classification, practical application

### Coverage Analysis
- **Well Covered**: Traditional testing (levels, techniques, artifacts, roles)
- **Partially Covered**: Quality characteristics, test automation
- **Gaps**: Modern practices (DevOps, microservices, AI, accessibility)

### Alignment Strategy
- Prioritize ISTQB for testing terms
- Integrate ISO 25010 for quality model
- Adopt architectural patterns from existing ontologies
- Extend to cover modern testing practices
- Provide YAML-based machine-readable specification

---

## 11. Next Steps

### Immediate Actions
1. Proceed with domain-by-domain research (Phase 2)
2. Extract detailed ISTQB definitions for all key terms
3. Map ISO 25010 sub-characteristics to testing practices
4. Research modern testing topics (AI, accessibility, DevOps)

### Ongoing Activities
- Maintain bibliography of sources
- Create concept inventory with classifications
- Build relationship maps between concepts
- Document emerging practices

### Validation Checkpoints
- Cross-check against ISTQB glossary
- Verify ISO 25010 coverage
- Compare structure with ROoST, TestTDO, STOWS
- Ensure modern practices are included

---

## 12. References

### Primary Standards
- ISTQB. (2023). *Certified Tester Foundation Level Syllabus v4.0*. Retrieved from https://istqb.org/
- ISTQB. (2025). *ISTQB Glossary*. Retrieved from https://glossary.istqb.org/
- ISO/IEC. (2023). *ISO/IEC 25010:2023 - Systems and software Quality Requirements and Evaluation (SQuaRE)*. Retrieved from https://iso25000.com/
- ISO. (2015). *ISO 9001:2015 - Quality Management Systems*. Retrieved from https://www.iso.org/

### Ontologies
- Falbo, R. A., et al. (2017). *ROoST: Reference Ontology on Software Testing*. Applied Ontology, 12(1). Retrieved from https://dev.nemo.inf.ufes.br/seon/ROoST.html
- Tebes, G., Olsina, L., et al. (2020). *TestTDO: A Top-Domain Software Testing Ontology*. Retrieved from arXiv:2104.09232
- Zhu, H., & Huo, Q. *Software Testing Ontology for Web Services (STOWS)*. [Referenced in systematic literature reviews]

### Bodies of Knowledge
- ASQ. *Certified Quality Engineer (CQE) Body of Knowledge*. Retrieved from https://asq.org/
- TMAP. *Test Management Approach*. Retrieved from https://www.tmap.net/

### Supporting Literature
- IEEE. *IEEE 829 - Standard for Software and System Test Documentation*.

---

**Document Status**: Phase 1 Complete
**Next Document**: 02-domain-I-standards.md (Detailed standards analysis)
**Research Phase**: Foundation established, ready for domain research
