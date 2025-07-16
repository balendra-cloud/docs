# Git Workflow Guidelines
*Created by: @balendra-cloud*
*Last Updated: 2025-07-16 21:59:24 UTC*

## Table of Contents
- [Commit Message Structure](#commit-message-structure)
- [Branch Naming Conventions](#branch-naming-conventions)
- [Pull Request Guidelines](#pull-request-guidelines)
- [Commit Types](#commit-types)

## Branch Naming Conventions

### Pattern
```
<type>/<ticket-number>-<short-description>
```

### Branch Types
- `feature/` - New features
- `fix/` - Bug fixes
- `hotfix/` - Urgent fixes for production
- `release/` - Release branches
- `docs/` - Documentation updates
- `refactor/` - Code refactoring
- `test/` - Test additions or modifications

### Examples
```bash
feature/PROJ-123-add-user-authentication
fix/PROJ-456-fix-login-timeout
hotfix/PROJ-789-critical-security-patch
docs/PROJ-234-update-api-docs
```

## Pull Request Guidelines

### PR Title Format
```
[<type>] <ticket-number>: <brief-description>
```

### Example PR Titles
```
[Feature] PROJ-123: Implement OAuth2 authentication
[Fix] PROJ-456: Resolve session timeout issues
[Docs] PROJ-234: Update API documentation
```

### PR Description Template
```markdown
## Description
[Provide a brief description of the changes]

## Type of Change
- [ ] Feature (non-breaking change for new functionality)
- [ ] Fix (non-breaking change for fixing issues)
- [ ] Breaking Change (fix or feature causing existing functionality to break)
- [ ] Documentation Update

## Testing Done
- [ ] Unit Tests
- [ ] Integration Tests
- [ ] Manual Testing

## Checklist
- [ ] My code follows the project's style guidelines
- [ ] I have performed a self-review
- [ ] I have commented my code where needed
- [ ] I have updated the documentation
- [ ] I have added tests that prove my fix/feature works

## Screenshots (if applicable)
[Add screenshots here]

## Related Issues
Fixes #[issue_number]
```

## Commit Message Structure
```
<type>(<scope>): <subject>

[optional body]

[optional footer(s)]
```

## Commit Types

| Type | Description | Example |
|------|-------------|---------|
| `feat` | New features | `feat(auth): Add OAuth2 authentication` |
| `fix` | Bug fixes | `fix(api): Handle null response in users endpoint` |
| `docs` | Documentation | `docs(readme): Update installation steps` |
| `style` | Code style changes | `style(lint): Apply prettier formatting` |
| `refactor` | Code refactoring | `refactor(core): Optimize data processing` |
| `perf` | Performance improvements | `perf(query): Add index for faster lookups` |
| `test` | Testing changes | `test(api): Add integration tests for auth` |
| `chore` | Maintenance tasks | `chore(deps): Update dependencies` |

## Branch Workflow

### Feature Development
```bash
# Create new feature branch
git checkout -b feature/PROJ-123-new-feature develop

# Regular commits
git commit -m "feat(scope): Add new functionality"

# Push branch
git push origin feature/PROJ-123-new-feature
```

### Hotfix Process
```bash
# Create hotfix branch
git checkout -b hotfix/PROJ-789-critical-fix main

# Fix commit
git commit -m "fix(core): Resolve critical issue"

# Push hotfix
git push origin hotfix/PROJ-789-critical-fix
```

## Best Practices

### Commit Messages
- Limited to 50 characters in subject
- Use imperative mood
- Reference issues in footer

### Branches
- Keep branches focused and short-lived
- Delete branches after merging
- Regularly sync with base branch

### Pull Requests
- Keep changes atomic
- Include comprehensive tests
- Respond to reviews promptly
- Update branch when requested

## Git Commands Reference

### Branch Management
```bash
# Create new branch
git checkout -b <branch-name>

# List branches
git branch -a

# Delete branch
git branch -d <branch-name>

# Force delete branch
git branch -D <branch-name>
```

### Commit Management
```bash
# Create commit
git commit -m "type(scope): message"

# Amend commit
git commit --amend

# Interactive rebase
git rebase -i HEAD~<number-of-commits>
```

### Sync Operations
```bash
# Update branch
git pull origin <branch-name>

# Rebase on main
git rebase origin/main

# Push changes
git push origin <branch-name>
```

---

*For questions or suggestions about these guidelines, please contact @balendra-cloud*

```

Would you like me to:
1. Add more specific workflow patterns for your team?
2. Include CI/CD integration guidelines?
3. Add more detailed code review guidelines?
4. Include release management procedures?
5. Add any project-specific conventions?