# Contributing to Claude Skills Repository

Thank you for considering contributing to this repository! This document provides guidelines and instructions for contributing new skills or improving existing ones.

## 🎯 What Makes a Good Skill?

A good skill should:
- **Solve a specific problem** - Clear use case and scope
- **Be well-documented** - Comprehensive instructions and examples
- **Follow best practices** - Industry standards and optimization techniques
- **Be tested** - Verified to work with Claude desktop app
- **Be maintained** - Keep dependencies and information up to date

## 📋 Contribution Process

### 1. Before You Start

- Check existing skills to avoid duplication
- Open an issue to discuss your idea (optional but recommended)
- Review the skill template in `docs/skill-template/`

### 2. Creating Your Skill

#### Step 1: Fork and Clone
```bash
# Fork the repository on GitHub, then:
git clone https://github.com/lavderenterprise/claude-skills.git
cd claude-skills
```

#### Step 2: Create a New Branch
```bash
git checkout -b add-skill-name
```

#### Step 3: Create Skill Directory
```bash
mkdir -p skills/your-skill-name
```

#### Step 4: Create Required Files

**SKILL.md** (required):
```markdown
---
name: your-skill-name
description: "Brief description (1-2 sentences) of what the skill does and when to trigger it"
license: MIT
---

# Your Skill Title

## Overview
Brief overview of the skill...

## Quick Reference
Essential commands/patterns...

[Rest of your documentation]
```

**LICENSE.txt** (required):
```
MIT License

Copyright (c) 2026 [Your Name]

[Standard MIT license text]
```

#### Step 5: Test Your Skill
```bash
# Copy to Claude's skills directory
cp -r skills/your-skill-name ~/.skills/

# Restart Claude desktop app
# Test the skill with relevant prompts
```

#### Step 6: Update Repository README
Add your skill to the "Available Skills" section in the main README.md

#### Step 7: Commit and Push
```bash
git add .
git commit -m "Add [skill-name] skill"
git push origin add-skill-name
```

#### Step 8: Create Pull Request
- Go to your fork on GitHub
- Click "Pull Request"
- Provide clear description of your skill
- Wait for review

## 📝 Skill Documentation Guidelines

### Frontmatter (Required)
```yaml
---
name: skill-name              # Lowercase, hyphens only
description: "Clear trigger description. Include: what it does, when to use it, key features"
license: MIT                  # Or other open-source license
---
```

### Description Best Practices
The `description` field is critical - Claude uses it to decide when to trigger the skill. Make it:
- **Specific** - Clear use cases and triggers
- **Comprehensive** - Include variations and keywords
- **Action-oriented** - Mention verbs (create, convert, optimize, etc.)

**Good Example:**
```yaml
description: "Use for WordPress development with Impreza theme and WPBakery. Triggers: converting designs (Figma, visual, described) to WordPress code, creating WPBakery shortcodes, building responsive layouts, WooCommerce integration."
```

**Bad Example:**
```yaml
description: "WordPress theme skill"
```

### Content Structure
Your SKILL.md should include:

1. **Overview** - What the skill does, current versions
2. **Quick Reference** - Table of common tasks
3. **Core Concepts** - Main functionality explained
4. **Examples** - Practical, copy-paste ready examples
5. **Best Practices** - Do's and don'ts
6. **Troubleshooting** - Common issues and solutions
7. **Resources** - Links to documentation

### Code Examples
- Use proper syntax highlighting
- Include comments explaining key parts
- Provide both simple and advanced examples
- Show expected output when relevant

### Formatting
- Use clear headings (H2 for sections, H3 for subsections)
- Use tables for reference material
- Use code blocks with language tags
- Include visual separators (`---`) between major sections

## 🔍 Review Criteria

Pull requests will be reviewed for:

### Content Quality
- [ ] Clear, comprehensive documentation
- [ ] Accurate and up-to-date information
- [ ] Practical, working examples
- [ ] Proper grammar and formatting

### Technical Correctness
- [ ] Code examples are tested and working
- [ ] Best practices are followed
- [ ] Security considerations addressed
- [ ] Performance implications noted

### Structure
- [ ] Follows template format
- [ ] Required files present (SKILL.md, LICENSE.txt)
- [ ] Proper frontmatter with description
- [ ] Logical organization

### Maintenance
- [ ] Version numbers included
- [ ] Dependencies documented
- [ ] Update date provided
- [ ] Contact/support info if applicable

## 🐛 Reporting Issues

Found a problem with an existing skill?

1. **Check existing issues** first
2. **Open a new issue** with:
   - Skill name
   - Problem description
   - Steps to reproduce
   - Expected vs actual behavior
   - Claude version and OS

## 💡 Suggesting Improvements

Have an idea for improving a skill?

1. Open an issue with tag `enhancement`
2. Describe the improvement
3. Explain the benefit
4. (Optional) Submit a PR implementing it

## 🚀 Skill Template

Located in `docs/skill-template/SKILL.md`, this template includes:
- Proper frontmatter structure
- Section placeholders
- Example formatting
- Comments with guidance

Copy this template as a starting point for new skills.

## 📊 Code of Conduct

- Be respectful and constructive
- Welcome newcomers
- Focus on the content, not the person
- Give credit where credit is due
- Follow the MIT License terms

## ❓ Questions?

- Open a [Discussion](https://github.com/lavderenterprise/claude-skills/discussions)
- Comment on existing issues
- Check existing documentation first

## 🙏 Thank You!

Every contribution makes this repository more valuable for the Claude community. Whether it's:
- A new skill
- Bug fix
- Documentation improvement
- Suggestion or idea

Your effort is appreciated! 🌟

---

**Last Updated:** February 19, 2026
