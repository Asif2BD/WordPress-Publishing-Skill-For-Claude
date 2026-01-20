# WordPress Publisher Skill for Claude

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Claude Skill](https://img.shields.io/badge/Claude-Skill-blueviolet)](https://claude.ai)
[![SkillsMP](https://img.shields.io/badge/SkillsMP-Listed-blue)](https://skillsmp.com)
[![WordPress](https://img.shields.io/badge/WordPress-REST%20API-21759B)](https://developer.wordpress.org/rest-api/)
[![Version](https://img.shields.io/badge/version-1.0.0-green)](https://github.com/Asif2BD/WordPress-Publishing-Skill-For-Claude/releases)

A Claude skill that enables direct publishing to WordPress sites via the REST API with full Gutenberg block support, automatic category selection, SEO tag generation, and preview capabilities.

## 🚀 Installation

### Via Claude Code Marketplace (Recommended)

```bash
# Add the marketplace
/plugin marketplace add Asif2BD/WordPress-Publishing-Skill-For-Claude

# Install the skill
/plugin install wordpress-publisher@wordpress-publisher-marketplace
```

### Via SkillsMP

Search for "wordpress-publisher" on [SkillsMP](https://skillsmp.com) and follow the installation instructions.

### Manual Installation

<details>
<summary><strong>For Claude Code</strong></summary>

```bash
# Clone to your skills directory
git clone https://github.com/Asif2BD/WordPress-Publishing-Skill-For-Claude.git ~/.claude/skills/wordpress-publisher
```
</details>

<details>
<summary><strong>For Claude.ai (Web)</strong></summary>

1. Download this repository as ZIP
2. Extract and upload the skill folder via **Claude.ai → Settings → Skills → Upload custom skill**
</details>

<details>
<summary><strong>For Codex CLI</strong></summary>

```bash
# Clone to Codex skills directory
git clone https://github.com/Asif2BD/WordPress-Publishing-Skill-For-Claude.git ~/.codex/skills/wordpress-publisher
```
</details>

## ✨ Features

| Feature | Description |
|---------|-------------|
| **Direct Publishing** | Create, update, and manage posts via WordPress REST API |
| **Gutenberg Blocks** | Full conversion of Markdown/HTML to WordPress Gutenberg blocks |
| **Smart Categories** | Auto-load categories and intelligently match content |
| **SEO Tags** | Automatically generate relevant tags for discoverability |
| **Preview Workflow** | Create drafts, preview, then publish with confidence |
| **Media Upload** | Upload and attach featured images |
| **Scheduling** | Schedule posts for future publication |
| **CLI Support** | Command line interface for automation |

## 📋 Requirements

- **WordPress**: Version 5.0+ (Gutenberg editor)
- **REST API**: Enabled (default in WordPress)
- **User Role**: Editor or Administrator
- **Authentication**: Application Password (not regular password)

## ⚡ Quick Start

### 1. Create Application Password in WordPress

1. Go to **Users → Profile** in WordPress admin
2. Scroll to **Application Passwords**
3. Enter name: `Claude Publisher`
4. Click **Add New** and copy the password

### 2. Use with Claude

Simply ask Claude:

> "Publish this article to my WordPress site at https://mysite.com"

Claude will:
1. Ask for your credentials (if not provided)
2. Convert your content to Gutenberg blocks
3. Suggest appropriate categories
4. Generate SEO tags
5. Create a draft for preview
6. Publish when you approve

### 3. Example Code Usage

```python
from scripts.wp_publisher import WordPressPublisher
from scripts.content_to_gutenberg import convert_to_gutenberg

# Connect
wp = WordPressPublisher(
    site_url="https://yoursite.com",
    username="admin",
    password="xxxx xxxx xxxx xxxx"  # Application password
)

# Convert and publish
content = convert_to_gutenberg("# Hello World\n\nThis is my post.")
result = wp.publish_content(
    title="Hello World",
    content=content,
    category_names=["Blog"],
    auto_generate_tags=True,
    status="draft"
)

print(f"Preview: {result['preview_url']}")
```

## 📖 Documentation

| Document | Description |
|----------|-------------|
| [SKILL.md](SKILL.md) | Complete skill instructions for Claude |
| [Gutenberg Reference](references/gutenberg-blocks.md) | Block format documentation |
| [CHANGELOG.md](CHANGELOG.md) | Version history |
| [CONTRIBUTING.md](CONTRIBUTING.md) | Contribution guidelines |

## 🔧 Supported Conversions

| Markdown | Gutenberg Block |
|----------|-----------------|
| `# Heading` | `wp:heading` |
| `**bold**` | `<strong>` |
| `*italic*` | `<em>` |
| `[link](url)` | `<a href>` |
| `- list` | `wp:list` |
| `1. ordered` | `wp:list {"ordered":true}` |
| `` `code` `` | `wp:code` |
| `> quote` | `wp:quote` |
| `![img](url)` | `wp:image` |
| `\| table \|` | `wp:table` |

## 🛠️ CLI Usage

```bash
# Test connection
python scripts/wp_publisher.py --url https://site.com --user admin --password "xxxx" --test

# List categories
python scripts/wp_publisher.py --url https://site.com --user admin --password "xxxx" --list-categories

# Publish article
python scripts/wp_publisher.py --url https://site.com --user admin --password "xxxx" \
    --publish article.html --title "My Post" --category "Blog" --auto-tags
```

## 🐛 Error Codes

| Code | Meaning | Solution |
|------|---------|----------|
| 401 | Auth failed | Check application password |
| 403 | Permission denied | Need Editor/Admin role |
| 404 | Not found | Check REST API is enabled |
| 500 | Server error | Check WordPress logs |

## 🤝 Contributing

Contributions welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) first.

```bash
# Setup development environment
git clone https://github.com/Asif2BD/WordPress-Publishing-Skill-For-Claude.git
cd WordPress-Publishing-Skill-For-Claude
pip install -r requirements-dev.txt

# Run tests
pytest tests/
```

## 📄 License

This project is licensed under the GPL v3 License - see the [LICENSE](LICENSE) file for details.

## 👤 Author

**M Asif Rahman**

- Website: [MAsifRahman.com](https://MAsifRahman.com)
- GitHub: [@Asif2BD](https://github.com/Asif2BD)

## 🔗 Links

- **GitHub**: [Asif2BD/WordPress-Publishing-Skill-For-Claude](https://github.com/Asif2BD/WordPress-Publishing-Skill-For-Claude)
- **Issues**: [Report a bug](https://github.com/Asif2BD/WordPress-Publishing-Skill-For-Claude/issues)
- **SkillsMP**: [Skills Marketplace](https://skillsmp.com)

## 🙏 Acknowledgments

- WordPress REST API Team
- Gutenberg Block Editor Team
- Claude AI by Anthropic

---

<p align="center">
  Made with ❤️ by <a href="https://MAsifRahman.com">M Asif Rahman</a>
</p>
