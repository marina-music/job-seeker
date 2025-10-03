# Git Workflow

## Pre-Work Branch Check

Before starting work on a new user story, always verify the current branch status:

```bash
# Check if current branch has been merged to main
git branch --merged main
```

### If Current Branch Is Merged
1. Switch to main and pull latest changes:
```bash
git checkout main
git pull origin main
```

2. Create a new feature branch:
```bash
git checkout -b f{feature-no}-e{epic-no}-s{story-no}-{short-description}
```

### If Current Branch Is NOT Merged
Create a new feature branch from the existing unmerged branch:
```bash
git checkout -b f{feature-no}-e{epic-no}-s{story-no}-{short-description}
```

## Branch Naming Convention

Follow this pattern for feature branches:
```
f{feature-no}-e{epic-no}-s{story-no}-{short-description}
```

Examples:
- `f1-e1-s1-profile-input-form`
- `f2-e1-s3-api-integration`
- `f5-e2-s5-visualization-component`

## Pre-Commit Workflow

Before committing, always execute the following verification steps:

### 1. Run Git Hooks
```bash
# Ensure pre-commit hooks are installed
git config core.hooksPath .githooks

# Manually run pre-commit checks (if applicable)
npm run lint
npm run format
```

### 2. Full Local Verification
Execute all verification steps to ensure code quality:

```bash
# Run linter
npm run lint

# Run formatter check
npm run format:check

# Run all tests
npm test

# Run build to check for compilation errors
npm run build

# Type checking (if TypeScript)
npm run type-check
```

### 3. Fix Any Issues
If any of the above steps fail:
- Fix all linting errors
- Fix all formatting issues
- Fix all failing tests
- Fix all build errors
- Fix all type errors

Do not proceed to commit until all checks pass.

## Commit Process

### 1. Stage Changes
```bash
git add .
```

### 2. Create Commit Message
Follow this format (WITHOUT AI attribution):

```
<type>: <short description>

<detailed description if needed>

Relates to #<issue-number>
```

**Important**: Remove all AI contribution footers. Do NOT include:
- ❌ `🤖 Generated with [Claude Code](https://claude.com/claude-code)`
- ❌ `Co-Authored-By: Claude <noreply@anthropic.com>`

### Commit Types
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, missing semicolons, etc.)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks (dependencies, configuration, etc.)
- `perf`: Performance improvements

### 3. Commit
```bash
git commit -m "feat: implement user profile input form

Add form components for capturing user information including
name, location, and target position preferences.

Relates to #<issue-number>"
```

## Push and Pull Request

### 1. Push to Remote
```bash
git push -u origin <branch-name>
```

### 2. Create Pull Request
```bash
gh pr create --title "F{feature-no}-E{epic-no}-S{story-no}: <Story Name>" --body "$(cat <<'EOF'
## Summary
- <Brief description of changes>
- <What was implemented>
- <What problem it solves>

## Related Issues
Closes #<issue-number>

## Test Plan
- [ ] All unit tests pass
- [ ] All integration tests pass
- [ ] Manual testing completed
- [ ] Browser compatibility verified
- [ ] Responsive design verified

## Verification Steps
1. Step-by-step instructions to verify the changes
2. Expected behavior
3. Screenshots/recordings if UI changes

## Checklist
- [ ] Code follows project style guidelines
- [ ] All tests pass locally
- [ ] Documentation updated
- [ ] No console errors or warnings
- [ ] Accessibility requirements met
EOF
)"
```

## Post-Merge Cleanup

After a pull request is merged:

### 1. Switch to Main
```bash
git checkout main
```

### 2. Pull Latest Changes
```bash
git pull origin main
```

### 3. Delete Local Feature Branch
```bash
git branch -d <branch-name>
```

### 4. Delete Remote Feature Branch (if not auto-deleted)
```bash
git push origin --delete <branch-name>
```

## Quick Reference

### Starting New Work
```bash
# Check merge status
git branch --merged main

# If merged: pull main and create new branch
git checkout main && git pull origin main
git checkout -b f1-e1-s1-description

# If not merged: create branch from current
git checkout -b f1-e1-s2-description
```

### Pre-Commit Checklist
```bash
npm run lint
npm run format:check
npm test
npm run build
npm run type-check  # if TypeScript
```

### Commit (without AI attribution)
```bash
git add .
git commit -m "feat: description

Detailed explanation

Relates to #issue-number"
```

### Push and PR
```bash
git push -u origin <branch-name>
gh pr create
```

## Best Practices

1. **Commit Often**: Make small, focused commits that represent logical units of work
2. **Clear Messages**: Write descriptive commit messages that explain the "why" not just the "what"
3. **Always Verify**: Never skip the pre-commit verification steps
4. **Keep Branches Updated**: Regularly sync feature branches with main to avoid conflicts
5. **Clean History**: Consider squashing commits before merging (if team policy)
6. **No AI Attribution**: Always remove AI contribution messages from commits
7. **Link Issues**: Always reference the related issue number in commits and PRs
8. **Test Locally**: Ensure everything works locally before pushing
