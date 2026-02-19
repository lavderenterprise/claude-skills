# 🚀 Quick Start Guide - Claude Skills Repository

## 📦 What's Inside

This ZIP contains a complete GitHub-ready repository for Claude skills with:

```
claude-skills-repo/
├── README.md                 # Main documentation
├── LICENSE                   # MIT License
├── CHANGELOG.md             # Version history
├── .gitignore               # Git ignore rules
├── skills/                  # 👈 Your skills go here
│   ├── README.md
│   └── impreza-wpbakery-dev/    # Example skill
│       ├── SKILL.md
│       └── LICENSE.txt
└── docs/
    ├── CONTRIBUTING.md      # Contribution guidelines
    └── skill-template/      # Template for new skills
        └── SKILL.md
```

---

## 🎯 Getting Started (3 Steps)

### 1️⃣ Extract the ZIP
```bash
unzip claude-skills-repo.zip
cd claude-skills-repo
```

### 2️⃣ Push to GitHub
```bash
# Initialize git (if not already done)
git init

# Add all files
git add .

# Commit
git commit -m "Initial commit: Claude Skills Repository v1.0.0"

# Add your GitHub repo as remote
git remote add origin https://github.com/YOUR_USERNAME/claude-skills.git

# Push to GitHub
git push -u origin main
```

### 3️⃣ Test the Skill
```bash
# Copy to Claude's skills directory
cp -r skills/impreza-wpbakery-dev ~/.skills/

# Restart Claude desktop app
```

---

## ✏️ Adding Your Own Skills

### Method 1: Use the Template
```bash
# Copy template
cp -r docs/skill-template skills/my-new-skill

# Edit the SKILL.md file
# Add your content following the template structure
```

### Method 2: From Scratch
```bash
# Create directory
mkdir skills/my-new-skill

# Create SKILL.md with frontmatter:
cat > skills/my-new-skill/SKILL.md << 'EOF'
---
name: my-new-skill
description: "What the skill does and when to use it"
license: MIT
---

# My New Skill
[Your content here]
EOF

# Add license
cp skills/impreza-wpbakery-dev/LICENSE.txt skills/my-new-skill/
```

---

## 📋 Skill Structure

Every skill needs:

### Required Files
- ✅ `SKILL.md` - Main documentation with frontmatter
- ✅ `LICENSE.txt` - License file

### Optional Files
- `scripts/` - Helper scripts (Python, JS, etc.)
- `templates/` - Template files
- `examples/` - Example outputs
- `assets/` - Images, diagrams

---

## 🔧 Customization

### Update Repository Name
Edit in these files:
- `README.md` - Replace `YOUR_USERNAME`
- `docs/CONTRIBUTING.md` - Replace `YOUR_USERNAME`
- `docs/skill-template/SKILL.md` - Replace `YOUR_USERNAME`

### Update Author Info
- `LICENSE` - Add your name and year
- Individual skill `LICENSE.txt` files

---

## 📤 Publishing to GitHub

### First Time Setup
```bash
# Create new repo on GitHub (don't initialize with README)
# Then:
git remote add origin https://github.com/YOUR_USERNAME/claude-skills.git
git branch -M main
git push -u origin main
```

### Subsequent Updates
```bash
# Add new skill
git add skills/new-skill-name/
git commit -m "Add new-skill-name skill"
git push

# Update existing skill
git add skills/existing-skill/
git commit -m "Update existing-skill documentation"
git push
```

---

## 🎨 Skill Categories

Organize your skills by category:

- **Web Development** - HTML, CSS, JavaScript, frameworks
- **Backend** - APIs, databases, servers
- **DevOps** - CI/CD, Docker, Kubernetes
- **Design** - UI/UX, graphics, Figma
- **Data** - Analytics, ML, data science
- **Content** - Writing, SEO, documentation
- **Tools** - Development utilities

---

## 📝 Writing Good Skills

### Frontmatter (Critical!)
```yaml
---
name: skill-name
description: "Specific, clear description with triggers and use cases"
license: MIT
---
```

### Description Tips
- Include trigger words/phrases
- Mention specific tools/frameworks
- List key features
- Explain when NOT to use it

**Example:**
```yaml
description: "WordPress development with Impreza theme and WPBakery. Use when: converting Figma to WordPress, creating WPBakery shortcodes, building responsive layouts, WooCommerce integration. NOT for: Elementor, Gutenberg-only sites."
```

---

## 🌟 Example Workflow

Let's say you want to add a React skill:

```bash
# 1. Create from template
cp -r docs/skill-template skills/react-components

# 2. Edit SKILL.md
vim skills/react-components/SKILL.md
# Update frontmatter:
# name: react-components
# description: "React component development..."

# 3. Add your content
# (Write documentation, examples, etc.)

# 4. Test locally
cp -r skills/react-components ~/.skills/
# Restart Claude and test

# 5. Commit and push
git add skills/react-components/
git commit -m "Add React components skill"
git push
```

---

## 🔗 Using with npx skills

Once on GitHub, users can install with:

```bash
# Install all skills
npx skills add https://github.com/YOUR_USERNAME/claude-skills --all

# Install specific skill
npx skills add https://github.com/YOUR_USERNAME/claude-skills \
  --skill 'impreza-wpbakery-dev' -g -y
```

---

## 📊 Repository Maintenance

### Update README when adding skills
In `README.md`, add to "Available Skills" section:

```markdown
### your-skill-name
**Brief description**

Features:
- Feature 1
- Feature 2

**Version:** X.X.X  
**Last Updated:** YYYY-MM-DD

[📖 Documentation](./skills/your-skill-name/SKILL.md)
```

### Update CHANGELOG
In `CHANGELOG.md`:

```markdown
## [Unreleased]
### Added
- `your-skill-name` skill vX.X.X - Brief description
```

---

## 🐛 Troubleshooting

**Skills not showing up in Claude?**
- Ensure files are in `~/.skills/skill-name/`
- Restart Claude desktop app
- Check SKILL.md has valid frontmatter

**Git issues?**
- Run `git status` to see current state
- Check `.gitignore` isn't excluding your files
- Ensure you're on the right branch (`git branch`)

---

## 📞 Support

- Read `docs/CONTRIBUTING.md` for detailed guidelines
- Check existing skills for examples
- Open GitHub Issues for bugs
- Use GitHub Discussions for questions

---

## ✅ Checklist for Going Live

Before pushing to GitHub:

- [ ] Update `YOUR_USERNAME` in all files
- [ ] Customize LICENSE with your info
- [ ] Test all skills locally
- [ ] Write clear README descriptions
- [ ] Add at least one example skill
- [ ] Create GitHub repository
- [ ] Push and verify files on GitHub
- [ ] Test installation via `npx skills`

---

**Ready to share your skills with the world? Push to GitHub and start contributing!** 🚀

---

**File Structure Created:** February 19, 2026  
**Repository Version:** 1.0.0  
**Included Skills:** 1 (impreza-wpbakery-dev)
