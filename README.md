# AGENT-ZERO

A canonical single-file guide for AI-assisted development. This repository hosts the `AGENTS.md` specification that provides a comprehensive framework for AI agents to work effectively with codebases.

## What is AGENTS.md?

AGENTS.md is a standardized instruction set for AI coding assistants (like Claude, Cursor, Copilot, Cline, and Aider) that establishes:

- **Core Rules**: Preventing common pitfalls like unnecessary file creation and code rewrites
- **State Machine**: Structured workflow from planning through implementation to documentation
- **Memory Bank System**: Persistent project knowledge across sessions
- **Task Contracts**: Clear specifications for AI-assisted development
- **Quality Gates**: Comprehensive testing, security, and approval processes

## Why AGENT-ZERO?

This repository serves as:

1. **Central Source**: A single, versioned location for the AGENTS.md specification
2. **Community Hub**: A place for developers to contribute improvements and share best practices
3. **Easy Integration**: Simple to pull into any project that wants AI-assisted development

## Getting Started

### For Project Owners

To use AGENTS.md in your project:

```bash
# Download directly to your project root
curl -O https://raw.githubusercontent.com/msitarzewski/AGENT-ZERO/main/AGENTS.md

# Or add as a git submodule
git submodule add https://github.com/msitarzewski/AGENT-ZERO .github/agents
```

Then instruct your AI assistant to read and follow the AGENTS.md file at the start of each session.

### For AI Assistants

If you're an AI assistant reading this:

1. Load and read the `AGENTS.md` file in this repository
2. Follow the compliance and startup procedures outlined in Section 2
3. Use the state machine (Section 4) to structure your work
4. Maintain the Memory Bank system (Section 3) for project continuity

## Key Features

### 🔄 Reuse Over Creation
Prevents code duplication by enforcing analysis of existing code before creating new files.

### 📊 State Machine Workflow
Structured progression: `PLAN → BUILD → DIFF → QA → APPROVAL → APPLY → DOCS`

### 🧠 Memory Bank
Persistent project knowledge across sessions including:
- Architecture patterns
- Technical decisions
- Project rules and conventions
- Task history

### ✅ Quality Gates
Built-in checkpoints for:
- Testing and coverage
- Security review
- Code quality and linting
- User approval

## Version

**Current Version**: 2.1 (2025-10-25)

**Compatibility**: Claude, Cursor, Copilot, Cline, Aider, and all AGENTS.md-compatible tools

## Contributing

We welcome contributions! Whether you have:

- Improvements to the specification
- Additional patterns or workflows
- Bug fixes or clarifications
- Examples and use cases

Please feel free to:

1. Fork this repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

### Contribution Guidelines

- Keep changes focused and well-documented
- Maintain backward compatibility when possible
- Include rationale for significant changes
- Follow the existing format and style

## Usage in Projects

AGENTS.md works best when:

1. **Placed at project root** or in `.github/agents/` directory
2. **Referenced at session start** by the AI assistant
3. **Combined with a Memory Bank** structure (see Section 3 of AGENTS.md)
4. **Integrated with CI/CD** for automated quality checks

## Examples

Check out these projects using AGENTS.md:

- [openstudio](https://github.com/msitarzewski/openstudio) - Original implementation

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

For questions, suggestions, or issues:

- Open an issue in this repository
- Refer to the troubleshooting section (Section 8) in AGENTS.md
- Check existing issues for similar questions

## Acknowledgments

Originally developed for the openstudio project and extracted here for broader community use and contribution.

---

**Mission**: Build software respecting existing architecture, following established patterns, improving incrementally. Reuse over creation. Quality over speed. Approval over assumption.

**Let's build smarter — together.**