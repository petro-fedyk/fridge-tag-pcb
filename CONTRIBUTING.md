# Contributing to Fridge Tag PCB

Thank you for considering contributing to the Fridge Tag PCB project! This document provides guidelines for contributing.

## How to Contribute

### Reporting Issues

If you find a bug or have a suggestion:

1. Check if the issue already exists in the issue tracker
2. Create a new issue with a clear title and description
3. Include relevant details:
   - PCB version
   - Expected vs actual behavior
   - Steps to reproduce (if applicable)
   - Screenshots or diagrams (if helpful)

### Suggesting Enhancements

We welcome suggestions for improvements:

1. Open an issue describing the enhancement
2. Explain why this enhancement would be useful
3. Provide examples or mockups if possible

### Pull Requests

#### Before You Start

1. Fork the repository
2. Create a new branch for your feature or fix
   ```bash
   git checkout -b feature/your-feature-name
   ```

#### Making Changes

1. **PCB Design Changes**:
   - Use KiCad 6.0 or later
   - Follow existing design rules
   - Update relevant documentation
   - Run DRC (Design Rule Check) before committing

2. **Documentation Changes**:
   - Keep documentation clear and concise
   - Use proper markdown formatting
   - Update the README if needed

3. **File Organization**:
   - Place files in appropriate directories
   - Follow naming conventions
   - Don't commit temporary or generated files

#### Commit Guidelines

- Write clear, descriptive commit messages
- Use present tense ("Add feature" not "Added feature")
- Reference issues when applicable (#123)
- Keep commits focused and atomic

Example:
```
Add temperature calibration circuit

- Adds precision voltage reference
- Updates schematic and PCB layout
- Updates BOM with new components
- Fixes #42
```

#### Submitting Pull Requests

1. Ensure your code follows the project style
2. Update documentation to reflect changes
3. Test your changes thoroughly
4. Push to your fork
5. Create a pull request with:
   - Clear title and description
   - Reference to related issues
   - List of changes made
   - Any testing performed

### Design Guidelines

#### Schematic

- Use standard component symbols
- Label all nets clearly
- Add comments for complex circuits
- Follow electrical best practices

#### PCB Layout

- Follow the layout guidelines in `hardware/pcb/layout-guidelines.md`
- Run DRC and fix all errors
- Maintain consistent trace widths
- Keep RF considerations in mind

#### Documentation

- Use markdown for all documentation
- Include diagrams where helpful
- Keep language clear and accessible
- Update version numbers when applicable

## Code of Conduct

### Our Standards

- Be respectful and inclusive
- Welcome newcomers
- Accept constructive criticism gracefully
- Focus on what's best for the project

### Unacceptable Behavior

- Harassment or discrimination
- Trolling or insulting comments
- Publishing others' private information
- Other unprofessional conduct

## Questions?

If you have questions about contributing:
- Open a discussion in GitHub Discussions
- Ask in the issue tracker
- Check existing documentation

## Recognition

Contributors will be acknowledged in:
- Project README
- Release notes
- Git commit history

Thank you for contributing to making Fridge Tag better!
