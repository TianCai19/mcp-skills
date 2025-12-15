# MCP Skills Collection

A comprehensive collection of Model Context Protocol (MCP) skills for enhancing your AI assistant capabilities.

## 🚀 What's This?

This repository contains a curated collection of MCP skill configurations that can be used with Claude Code and other MCP-compatible AI assistants. Each skill is a JSON configuration file that defines a specific tool or capability.

## 📦 What's Included

### Ready-to-Use Skills

1. **PDF Processor** - Extract text, tables, create and manipulate PDF documents
2. **Web Scraper** - Advanced web scraping with anti-detection features
3. **Database Manager** - Universal database management across multiple DB types
4. **API Tester** - Comprehensive API testing with automated test generation
5. **Image Processor** - AI-powered image processing and enhancement

### Templates & Examples

- Skill configuration template for creating your own skills
- Basic skill examples for beginners
- Advanced configuration examples

## 🏗️ Repository Structure

```
mcp-skills/
├── skills/              # Ready-to-use skill configurations
│   ├── pdf-processor.json
│   ├── web-scraper.json
│   ├── database-manager.json
│   ├── api-tester.json
│   └── image-processor.json
├── templates/           # Skill configuration templates
│   └── skill-template.json
├── examples/           # Example configurations and usage
│   ├── README.md
│   └── basic-skill.json
└── README.md           # This file
```

## 🛠️ How to Use These Skills

### Option 1: Use Individual Skills

1. Browse the `skills/` directory
2. Find a skill that meets your needs
3. Copy the JSON configuration
4. Import it into your MCP-compatible AI assistant

### Option 2: Create Your Own

1. Use the template in `templates/skill-template.json`
2. Fill in your skill details
3. Test your configuration
4. Share it with the community!

### Example Usage

```bash
# Install a skill
npm install -g pdf-processor-cli

# Use the skill
extract_text document.pdf --output text.txt
```

## 📋 Skill Configuration Schema

Each skill uses the following schema:

```json
{
  "name": "skill-name",
  "description": "What the skill does",
  "category": "category-name",
  "tags": ["tag1", "tag2"],
  "version": "1.0.0",
  "author": "Your Name",
  "configuration": {
    "required_env": ["ENV_VAR"],
    "optional_env": ["OPTIONAL_VAR"],
    "parameters": { /* skill parameters */ }
  },
  "capabilities": ["List of features"],
  "usage_examples": [{ /* examples */ }],
  "installation": { /* install commands */ },
  "documentation_url": "https://..."
}
```

## 🎯 Categories

Skills are organized into the following categories:

- **Document Processing** - PDF, DOCX, and other document tools
- **Web Automation** - Scraping, testing, and automation
- **Database** - Management, migration, and backup tools
- **Testing** - API testing, unit tests, and QA tools
- **Image Processing** - Image manipulation and AI enhancement
- **Examples** - Sample skills for learning

## 🔧 Installation Requirements

Each skill may have different requirements. Check the individual skill's `installation` field for specific commands.

Common requirements:
- Node.js (for NPM packages)
- Python (for pip packages)
- Specific CLI tools
- API keys or environment variables

## 🤝 Contributing

We welcome contributions! Here's how:

1. Fork this repository
2. Create a new skill configuration
3. Test your skill thoroughly
4. Submit a pull request
5. Add it to the collection!

### Contribution Guidelines

- Use the provided template
- Include clear documentation
- Add usage examples
- Tag appropriately
- Test your configuration
- Follow semantic versioning

## 📝 Adding Your Skills

Want to share your skill? Here's what to include:

1. **Complete JSON configuration** following the schema
2. **Installation instructions** for users
3. **Usage examples** showing common use cases
4. **Documentation links** for more details

## 🔍 Finding Skills

Search by:
- **Category**: Filter by type (document, web, database, etc.)
- **Tags**: Find skills by technology or feature
- **Name**: Use keywords in skill names

## 📚 Documentation

For more information:
- [MCP Documentation](https://modelcontextprotocol.io/)
- [Skill Template Guide](templates/skill-template.json)
- [Example Configurations](examples/)

## 🐛 Troubleshooting

Common issues:

1. **Invalid JSON**: Ensure your configuration is valid JSON
2. **Missing dependencies**: Check the `installation` field
3. **Environment variables**: Verify required env vars are set
4. **Permissions**: Ensure you have necessary file/DB permissions

## 📄 License

This project is open source. Feel free to use, modify, and distribute these configurations.

## ⭐ Show Your Support

If you find these skills useful, please:
- ⭐ Star this repository
- 🔄 Share it with others
- 🤝 Contribute your own skills
- 📢 Spread the word!

## 📞 Support

Need help? Have questions?

- Open an issue on GitHub
- Check existing documentation
- Review the examples folder

## 🎉 Acknowledgments

Thanks to all contributors who help make this collection better!

---

**Happy Skill Building!** 🚀

Built with ❤️ by Claude Code
