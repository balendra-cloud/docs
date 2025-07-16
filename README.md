# Development Guidelines
*Maintained by [@balendra-cloud](https://github.com/balendra-cloud)*  
*Last Updated: 2025-07-16 22:07:57 UTC*

> A comprehensive collection of development best practices, guidelines, and templates.

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Enabled-green?style=flat-square)](https://balendra-cloud.github.io/development-guidelines)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)

## 📚 Quick Links

- [Git Guidelines](docs/README.md)
- [Code Review Process](docs/CODE_REVIEW_GUIDELINES.md.md)


## 🎯 Purpose

This repository serves as a centralized resource for development best practices, coding standards, and workflow guidelines. It aims to:

- Standardize development practices
- Improve code quality
- Streamline review processes
- Provide reusable templates
- Share best practices

## 📖 Documentation

Visit our [GitHub Pages](https://balendra-cloud.github.io/development-guidelines) for the full documentation.

## 🗂️ Repository Structure

```
development-guidelines/
├── docs/                     # Main documentation
│   ├── git/                 # Git guidelines
│   ├── code-review/        # Review process
│   └── templates/          # Reusable templates
├── examples/                # Real-world examples
└── .github/                 # GitHub configurations
```

## 🚀 Getting Started

1. Browse the documentation on [GitHub Pages](https://balendra-cloud.github.io/development-guidelines)
2. Check out specific guidelines in the [docs](docs/) directory
3. Find practical examples in the [examples](examples/) directory
4. Use templates from the [templates](docs/templates/) directory

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guidelines](CONTRIBUTING.md).

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔄 Updates

- Regular updates: Weekly
- Last major update: 2025-07-16
- Maintainer: [@balendra-cloud](https://github.com/balendra-cloud)

## 📞 Contact

- GitHub: [@balendra-cloud](https://github.com/balendra-cloud)
- Issues: [Issue Tracker](https://github.com/balendra-cloud/development-guidelines/issues)
```

````markdown name=CONTRIBUTING.md
# Contributing Guidelines
*Last Updated: 2025-07-16 22:07:57 UTC*

Thank you for considering contributing to our Development Guidelines! This document outlines the process and standards for contributions.

## Table of Contents
- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
- [Submission Guidelines](#submission-guidelines)
- [Style Guidelines](#style-guidelines)

## Code of Conduct

This project adheres to a Code of Conduct. By participating, you are expected to uphold this code.

## How Can I Contribute?

### Reporting Issues
- Use the issue templates
- Provide clear descriptions
- Include relevant examples
- Follow up on questions

### Submitting Changes
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

### Documentation Improvements
- Fix typos and grammar
- Clarify confusing sections
- Add examples
- Update outdated content

## Submission Guidelines

### Pull Request Process
1. Use the PR template
2. Link related issues
3. Update documentation
4. Add examples if applicable
5. Request review

### Commit Messages
Follow our [Git Guidelines](docs/git/commit-guidelines.md)

## Style Guidelines

### Markdown
- Use ATX-style headers (`#` for headers)
- Wrap lines at 80 characters
- Use code blocks for examples
- Include alt text for images

### Content
- Be clear and concise
- Use active voice
- Provide examples
- Link to references

## Need Help?
- Check existing issues
- Read documentation
- Ask for clarification
```

````yaml name=.github/ISSUE_TEMPLATE/documentation.yml
name: Documentation Update
description: Suggest improvements or report issues with documentation
title: "[Docs]: "
labels: ["documentation"]
body:
  - type: markdown
    attributes:
      value: |
        Thanks for taking the time to improve our documentation!
  - type: input
    id: page
    attributes:
      label: Documentation Page
      description: Which page needs updating?
      placeholder: "e.g., git/commit-guidelines.md"
    validations:
      required: true
  - type: textarea
    id: description
    attributes:
      label: Description
      description: What needs to be changed or improved?
      placeholder: "Clear description of the changes needed..."
    validations:
      required: true
  - type: textarea
    id: suggestion
    attributes:
      label: Suggested Changes
      description: What would you like to see instead?
      placeholder: "Your suggested improvements..."
  - type: checkboxes
    id: terms
    attributes:
      label: Code of Conduct
      description: By submitting this issue, you agree to follow our Code of Conduct
      options:
        - label: I agree to follow this project's Code of Conduct
          required: true
```

````yaml name=.github/ISSUE_TEMPLATE/guideline.yml
name: New Guideline
description: Propose a new development guideline
title: "[Guideline]: "
labels: ["guideline"]
body:
  - type: dropdown
    id: category
    attributes:
      label: Category
      description: What type of guideline is this?
      options:
        - Git
        - Code Review
        - Development
        - Security
        - Testing
        - Other
    validations:
      required: true
  - type: textarea
    id: description
    attributes:
      label: Description
      description: What is this guideline about?
      placeholder: "Describe the guideline..."
    validations:
      required: true
  - type: textarea
    id: rationale
    attributes:
      label: Rationale
      description: Why is this guideline needed?
      placeholder: "Explain why..."
    validations:
      required: true
  - type: textarea
    id: examples
    attributes:
      label: Examples
      description: Provide examples of this guideline in practice
      placeholder: "Share examples..."
```

````yaml name=.github/workflows/markdown.yml
name: Markdown Lint

on:
  push:
    paths:
      - '**/*.md'
  pull_request:
    paths:
      - '**/*.md'

jobs:
  markdown-lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: markdownlint-cli
        uses: nosborn/github-action-markdown-cli@v3.0.1
        with:
          files: .
          config_file: .markdownlint.json
```

````yaml name=.github/workflows/pages.yml
name: GitHub Pages

on:
  push:
    branches:
      - main
  workflow_dispatch:

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      
      - name: Setup Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '16'

      - name: Install dependencies
        run: |
          npm install -g docsify-cli

      - name: Build
        run: |
          docsify init ./docs
          cp README.md docs/

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./docs
```

````json name=.markdownlint.json
{
  "default": true,
  "MD013": false,
  "MD033": false,
  "MD041": false,
  "MD002": false,
  "MD026": false
}
```
