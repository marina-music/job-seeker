# Wiki Workflow Setup and Management Prompt

## Initial Setup

Create a git submodule linking to the wiki repository:

```bash
git submodule add git@github.com:marina-music/job-seeker.wiki.git wiki
git submodule update --init --recursive
```

This `wiki` directory will store agile documentation including:
- Vision documents
- Features
- Epics
- User stories

## Naming Convention

All agile documents follow this slug-based naming pattern:

```
f{feature-no}-e{epic-no}-s{story-no}-{type}-{name}.md
```

Examples:
- `f1-feature-authentication.md` (feature level)
- `f1-e1-epic-user-login.md` (epic level)
- `f1-e1-s1-story-email-password-login.md` (story level)

## Workflow Commands

### "push wiki"
When the user says "push wiki", execute:
```bash
cd wiki
git add .
git commit -m "Update agile documentation"
git push origin master
cd ..
```

### "pull wiki"
When the user says "pull wiki", execute:
```bash
cd wiki
git pull origin master
cd ..
```

**Important**: Always ensure you're in the wiki directory when performing git operations on wiki content.

## Git Issue Templates

### Feature Template
```markdown
## Feature: [Feature Name]

**Feature ID**: F{number}

### Description
[Clear description of the feature]

### Business Value
[Why this feature matters]

### Acceptance Criteria
- [ ] Criterion 1
- [ ] Criterion 2

### Related Epics
- E{number}: [Epic name]

### Dependencies
[Any dependencies or blockers]

### Definition of Done
- [ ] All epics completed
- [ ] Documentation updated
- [ ] Stakeholder approval
```

### Epic Template
```markdown
## Epic: [Epic Name]

**Epic ID**: F{feature-no}-E{number}
**Feature**: F{feature-no} - [Feature name]

### Description
[Clear description of the epic]

### Goals
[What this epic aims to achieve]

### User Stories
- S{number}: [Story name]

### Acceptance Criteria
- [ ] Criterion 1
- [ ] Criterion 2

### Dependencies
[Any dependencies or blockers]

### Definition of Done
- [ ] All user stories completed
- [ ] Code reviewed and merged
- [ ] Tests passing
- [ ] Documentation updated
```

### User Story Template
```markdown
## User Story: [Story Name]

**Story ID**: F{feature-no}-E{epic-no}-S{number}
**Epic**: F{feature-no}-E{epic-no} - [Epic name]

### Story
As a [user type]
I want to [action]
So that [benefit]

### Acceptance Criteria
- [ ] Given [context], when [action], then [outcome]
- [ ] Given [context], when [action], then [outcome]

### Technical Notes
[Implementation details, APIs, components involved]

### Tasks
- [ ] Task 1
- [ ] Task 2

### Dependencies
[Any dependencies or blockers]

### Definition of Done
- [ ] Code complete and reviewed
- [ ] Unit tests written and passing
- [ ] Integration tests passing
- [ ] Documentation updated
- [ ] Acceptance criteria met
```

## Best Practices

1. **Use gh CLI when possible**: Prefer `gh` commands over raw `git` commands for GitHub operations
2. **Commit frequently**: Push wiki updates after completing each document
3. **Link issues**: Cross-reference GitHub issues in wiki documents using `#issue-number`
4. **Keep hierarchy clear**: Maintain the feature → epic → story hierarchy in file names and content
5. **Update incrementally**: Don't wait to document; write as you plan
6. **Sync regularly**: Pull wiki updates before making changes to avoid conflicts
