# Claude Skills Repository

A collection of professional skills for Claude AI to enhance development workflows.

## 📦 Available Skills

### 🎨 impreza-wpbakery-dev
**WordPress development with Impreza theme and WPBakery Page Builder**

Transform designs (described, visual, or Figma) into production-ready WordPress code using the Impreza theme and WPBakery Page Builder.

**Features:**
- 63+ Impreza content elements documented
- Complete WPBakery shortcode reference
- Design-to-code workflows (Figma → WordPress)
- Responsive design patterns
- WooCommerce integration
- Performance optimization strategies
- SEO & Accessibility best practices

**Version:** 1.0.0  
**Last Updated:** February 19, 2026

[📖 Full Documentation](./skills/impreza-wpbakery-dev/SKILL.md)

---

## 🚀 Installation

### Option 1: Using npx skills (Recommended)

```bash
npx skills add https://github.com/lavderenterprise/claude-skills --skill 'impreza-wpbakery-dev' -g -y
```

### Option 2: Manual Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/lavderenterprise/claude-skills.git
   ```

2. **Copy skills to Claude's directory:**
   ```bash
   # For macOS/Linux
   cp -r claude-skills/skills/* ~/.skills/
   
   # For Windows
   xcopy /E /I claude-skills\skills\* %USERPROFILE%\.skills\
   ```

3. **Restart Claude desktop app**

### Option 3: Individual Skill Installation

```bash
# Create skills directory if it doesn't exist
mkdir -p ~/.skills

# Copy specific skill
cp -r skills/impreza-wpbakery-dev ~/.skills/
```

---

## 📁 Repository Structure

```
claude-skills/
├── README.md                          # This file
├── LICENSE                            # Repository license
├── .gitignore                         # Git ignore rules
├── skills/                            # Skills directory
│   ├── impreza-wpbakery-dev/         # Impreza + WPBakery skill
│   │   ├── SKILL.md                  # Skill documentation
│   │   └── LICENSE.txt               # Skill license
│   └── [future-skill]/               # Additional skills
│       ├── SKILL.md
│       └── LICENSE.txt
└── docs/                              # Additional documentation
    ├── CONTRIBUTING.md                # Contribution guidelines
    └── skill-template/                # Template for new skills
        └── SKILL.md
```

---

## 🛠️ Creating New Skills

1. **Copy the template:**
   ```bash
   cp -r docs/skill-template skills/your-skill-name
   ```

2. **Edit SKILL.md:**
   - Update the frontmatter (name, description)
   - Add your skill content
   - Follow the established format

3. **Test the skill:**
   ```bash
   cp -r skills/your-skill-name ~/.skills/
   # Restart Claude and test
   ```

4. **Submit a pull request**

---

## 📝 Skill Format

Each skill must have:

### Required Files
- `SKILL.md` - Main skill documentation with frontmatter
- `LICENSE.txt` - License for the skill (MIT recommended)

### Frontmatter Format
```yaml
---
name: skill-name
description: "Brief description of what the skill does and when to use it"
license: MIT
---
```

### Optional Files
- `scripts/` - Helper scripts (Python, JavaScript, etc.)
- `templates/` - Template files
- `examples/` - Example outputs

---

## 🤝 Contributing

Contributions are welcome! Please read [CONTRIBUTING.md](./docs/CONTRIBUTING.md) for guidelines.

### Ways to Contribute
- ⭐ Star this repository
- 🐛 Report bugs or issues
- 💡 Suggest new skills
- 📝 Improve documentation
- 🔧 Submit new skills via PR

---

## 📋 Skill Submission Checklist

Before submitting a new skill:

- [ ] Skill name is clear and descriptive
- [ ] SKILL.md includes proper frontmatter
- [ ] Description explains when to use the skill
- [ ] Documentation is comprehensive and well-organized
- [ ] Examples are provided where applicable
- [ ] LICENSE.txt is included
- [ ] Tested with Claude desktop app
- [ ] No sensitive information or API keys

---

## 🔒 License

This repository is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

Individual skills may have their own licenses - check each skill's LICENSE.txt file.

---

## 🌟 Featured Skills

### Planned Skills
- [ ] **figma-to-react** - Convert Figma designs to React components
- [ ] **api-integration** - RESTful API integration patterns
- [ ] **database-design** - SQL schema design and optimization
- [ ] **tailwind-components** - Tailwind CSS component library
- [ ] **seo-optimizer** - Advanced SEO optimization strategies

Want to contribute a skill? Open an issue or submit a PR!

---

## 📞 Support

- **Issues:** [GitHub Issues](https://github.com/lavderenterprise/claude-skills/issues)
- **Discussions:** [GitHub Discussions](https://github.com/lavderenterprise/claude-skills/discussions)

---

## 🙏 Acknowledgments

Built for the Claude AI community. Special thanks to:
- Anthropic for creating Claude
- All contributors and skill creators
- The open-source community

---

**Last Updated:** February 19, 2026  
**Repository Version:** 1.0.0
