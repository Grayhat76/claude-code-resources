# Contributing to Claude Code Resources

Thank you for your interest in contributing! This project aims to be the definitive resource for Claude Code users.

## How to Contribute

### Reporting Bugs

1. Check if the bug has already been reported in [Issues](../../issues)
2. If not, create a new issue with:
   - Clear title
   - Detailed description
   - Steps to reproduce
   - Expected vs actual behavior
   - Your environment (OS, bash version, etc.)

### Suggesting Enhancements

1. Check [Discussions](../../discussions) for similar suggestions
2. Create a new discussion with:
   - Clear description of the enhancement
   - Use case / problem it solves
   - Example of how it would work

### Pull Requests

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Test thoroughly
5. Commit with clear messages
6. Push to your fork
7. Open a Pull Request

#### PR Guidelines

- **Documentation changes**: Ensure clarity and accuracy
- **Script changes**: Test on Mac, Linux, and WSL
- **Agent changes**: Ensure YAML frontmatter is valid
- **Examples**: Include working, tested examples

### Code Style

**Bash Scripts:**
- Use 4-space indentation
- Include comments for complex logic
- Use shellcheck for linting
- Test on multiple platforms

**Markdown:**
- Use clear headings
- Include examples
- Keep line length reasonable
- Use code blocks appropriately

**Agents:**
- Valid YAML frontmatter
- Clear instructions
- Specific tool permissions
- Example outputs

## Development Setup

```bash
# Clone your fork
git clone https://github.com/YOUR-USERNAME/claude-code-resources.git
cd claude-code-resources

# Test the jumpstart script
./claude-code-jumpstart.sh

# Validate bash syntax
bash -n claude-code-jumpstart.sh

# Run shellcheck (if available)
shellcheck claude-code-jumpstart.sh
```

## Testing

Before submitting:

1. Test jumpstart script in clean directory
2. Verify all documentation links work
3. Check agent YAML frontmatter
4. Test on multiple platforms if possible

## Commit Messages

Use clear, descriptive commit messages:

```
feat: add Python data science command
fix: correct .gitignore creation logic
docs: update README with Windows instructions
refactor: simplify agent selection logic
```

## Questions?

- **General questions**: [Discussions](../../discussions)
- **Bug reports**: [Issues](../../issues)
- **Security issues**: Email john@greatfallsventures.com directly

## Code of Conduct

- Be respectful and constructive
- Focus on the code, not the person
- Accept feedback gracefully
- Help others learn

## Recognition

Contributors will be recognized in:
- README.md acknowledgments section
- Release notes
- Project documentation

Thank you for helping make this resource better! 🎉
