# MCP Agent Skills Collection

A curated collection of **Agent Skills** for Claude Code - modular capabilities that extend Claude's functionality through organized folders containing instructions and resources.

## 🚀 What are Agent Skills?

Agent Skills are **model-invoked** capabilities that Claude autonomously uses based on your requests and the skill's description. Each skill consists of a `SKILL.md` file with YAML frontmatter and Markdown instructions that Claude reads when relevant.

**Key Features:**
- ✨ **Autonomous Activation** - Claude decides when to use skills based on context
- 📦 **Modular** - Each skill is self-contained with instructions and examples
- 🔄 **Reusable** - Reduce repetitive prompting with organized expertise
- 👥 **Shareable** - Distribute through git or plugins to your team

Learn more about [Agent Skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview).

## 📦 What's Included

This repository contains 5 ready-to-use Agent Skills:

### 1. **PDF Processor** 📄
Extract text, tables, fill forms, merge PDFs, and convert formats.

### 2. **Web Scraper** 🌐
Scrape web content with anti-detection features for static and dynamic websites.

### 3. **Database Manager** 🗄️
Universal database management across PostgreSQL, MySQL, SQLite, and MongoDB.

### 4. **API Tester** 🧪
Test REST, GraphQL, and gRPC APIs with automated test generation and load testing.

### 5. **Image Processor** 🖼️
Process and enhance images with AI - resize, compress, remove backgrounds, upscale.

## 🏗️ Repository Structure

```
mcp-skills/
├── .claude/skills/          # Project Skills (shared via git)
│   ├── pdf-processor/
│   │   └── SKILL.md
│   ├── web-scraper/
│   │   └── SKILL.md
│   ├── database-manager/
│   │   └── SKILL.md
│   ├── api-tester/
│   │   └── SKILL.md
│   └── image-processor/
│       └── SKILL.md
└── README.md                # This file
```

## 🛠️ How to Use These Skills

### Option 1: Use Project Skills (Recommended)

1. Clone this repository into your project:
```bash
git clone https://github.com/TianCai19/mcp-skills.git
```

2. Copy skills to your project:
```bash
cp -r mcp-skills/.claude/skills/ .claude/
```

3. Restart Claude Code - skills are automatically discovered!

### Option 2: Use Personal Skills

1. Create skills directory:
```bash
mkdir -p ~/.claude/skills
```

2. Copy skills:
```bash
cp -r mcp-skills/.claude/skills/* ~/.claude/skills/
```

3. Restart Claude Code

### Option 3: Create Your Own

1. Create a skill directory:
```bash
mkdir -p ~/.claude/skills/my-skill-name
```

2. Create `SKILL.md`:
```bash
touch ~/.claude/skills/my-skill-name/SKILL.md
```

3. Add YAML frontmatter and instructions (see template below)

## 📋 Skill Format

Each skill uses this structure:

### SKILL.md Format

```yaml
---
name: skill-name
description: Brief description of what this Skill does and when to use it
allowed-tools: Read, Grep, Glob  # Optional: restrict tool access
---

# Skill Name

## Instructions
Step-by-step guidance for Claude

## Examples
Concrete examples of using this skill
```

### Field Requirements

- **name**: Lowercase letters, numbers, and hyphens only (max 64 chars)
- **description**: What the skill does AND when to use it (max 1024 chars)
- **allowed-tools**: Optional - limit which tools Claude can use

## 🎯 When to Use Skills

Skills activate automatically when Claude determines they're relevant. Here's when each skill activates:

### PDF Processor
**Triggers:** "Extract text from PDF", "merge PDFs", "fill forms", "PDF files"
**Use for:** All PDF-related tasks

### Web Scraper
**Triggers:** "Scrape website", "extract web data", "HTML content"
**Use for:** Web scraping and data extraction

### Database Manager
**Triggers:** "SQL query", "database", "migration", "backup", "import data"
**Use for:** All database operations

### API Tester
**Triggers:** "Test API", "validate endpoint", "load test", "API health"
**Use for:** API testing and validation

### Image Processor
**Triggers:** "Resize image", "remove background", "compress photo", "image format"
**Use for:** Image processing and optimization

## 📝 Example Usage

### Basic Request
```
Can you extract text from this PDF document?
```
→ Claude automatically uses PDF Processor skill

### Specific Request
```
I need to scrape product data from this e-commerce site with pagination
```
→ Claude automatically uses Web Scraper skill

### Complex Task
```
Test my REST API endpoints and generate a test report
```
→ Claude automatically uses API Tester skill

## 🔧 Installation & Setup

### Install Required Dependencies

Each skill may require Python packages:

```bash
# PDF Processor
pip install pypdf pdfplumber PyPDF2

# Web Scraper
pip install requests beautifulsoup4 lxml selenium playwright

# Database Manager
pip install sqlalchemy psycopg2-binary alembic pymongo

# API Tester
pip install requests httpx jsonschema pytest locust

# Image Processor
pip install Pillow opencv-python rembg waifu2x-ncnn-vulkan
```

### Set Environment Variables

```bash
# Database Manager
export DATABASE_URL="postgresql://user:pass@localhost/dbname"

# API Tester
export API_BASE_URL="https://api.example.com"
export API_TOKEN="your-token"
```

## 🤝 Creating Your Own Skills

### Step 1: Create Skill Directory
```bash
mkdir -p .claude/skills/your-skill-name
```

### Step 2: Create SKILL.md
Use this template:

```yaml
---
name: your-skill-name
description: Brief description of what this Skill does and when to use it. Include specific triggers like "when user mentions X" or "use for Y tasks".
---

# Your Skill Name

## Instructions
Provide clear, step-by-step guidance:

1. First step
2. Second step
3. Use tools as needed

## Requirements
List any dependencies:
```bash
pip install package-name
```

## Examples
Show when to use:
- Example 1: "User asks about X"
- Example 2: "When working with Y"

## Tips
Additional guidance or best practices
```

### Step 3: Test Your Skill
Ask Claude a question that matches your description:
```
Can you help me with [your skill's use case]?
```

Claude will automatically use your skill if the description matches!

## 🔍 Best Practices

### Writing Effective Descriptions

**Good (Specific):**
```
description: Analyze Excel spreadsheets, create pivot tables, and generate charts. Use when working with Excel files, spreadsheets, or analyzing tabular data in .xlsx format.
```

**Bad (Vague):**
```
description: Helps with data
```

### Keep Skills Focused

**Good:**
- "PDF form filling"
- "Excel data analysis"
- "Git commit messages"

**Too Broad:**
- "Document processing" → split into separate skills
- "Data tools" → split by data type

### Tool Permissions

Use `allowed-tools` to restrict access:

```yaml
---
name: safe-file-reader
description: Read files without making changes. Use when you need read-only file access.
allowed-tools: Read, Grep, Glob
---
```

## 📚 Additional Resources

- [Agent Skills Overview](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview)
- [Authoring Best Practices](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/best-practices)
- [Quick Start Guide](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/quickstart)
- [Agent SDK Documentation](https://docs.claude.com/en/docs/agent-sdk/skills)

## 🎓 Learning Examples

Each skill includes:
- ✅ Clear instructions
- ✅ Code examples
- ✅ Usage scenarios
- ✅ Requirements
- ✅ Tips and best practices

Study these examples to learn how to write your own skills!

## 🐛 Troubleshooting

### Claude doesn't use my skill

**Check 1: Is the description specific enough?**
- Include both what it does AND when to use it
- Add trigger keywords users would mention

**Check 2: Is YAML valid?**
```bash
# Check frontmatter
head -n 15 SKILL.md

# Ensure:
# - Opening --- on line 1
# - Closing --- before content
# - Valid YAML (no tabs)
```

**Check 3: Is the file in the right location?**
```bash
# Personal skills
ls ~/.claude/skills/*/SKILL.md

# Project skills
ls .claude/skills/*/SKILL.md
```

### View Skill Loading Errors

Run Claude Code in debug mode:
```bash
claude --debug
```

## 📄 License

Open source - feel free to use, modify, and distribute.

## ⭐ Contributing

Want to add your skills? Here's how:

1. Fork this repository
2. Create a new skill in `.claude/skills/`
3. Follow the format and best practices
4. Test your skill thoroughly
5. Submit a pull request

### Contribution Checklist

- [ ] Created `.claude/skills/your-skill/SKILL.md`
- [ ] Used valid YAML frontmatter
- [ ] Included specific description with triggers
- [ ] Added clear instructions
- [ ] Provided code examples
- [ ] Listed requirements
- [ ] Tested the skill works

## 🎉 Acknowledgments

Thanks to all contributors who help make this collection better!

---

**Happy Skill Building!** 🚀

Built with ❤️ by Claude Code
