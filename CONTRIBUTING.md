# Contributing to Hugo Garden Module

Thanks for your interest in contributing! 🌱

## Development Setup

1. Clone the repository:
```bash
git clone https://github.com/mbbroberg/hugo-garden-module.git
cd hugo-garden-module
```

2. Test with the example site:
```bash
cd exampleSite
hugo server
```

The example site is already configured with a `go.mod` that has a `replace` directive pointing to the parent module directory, so it will use your local changes automatically.

3. Make your changes in the module files (not in exampleSite)

## Guidelines

### Code Style
- Use semantic HTML
- Follow existing CSS patterns and variable naming
- Keep JavaScript minimal and dependency-free
- Comment complex template logic

### Commit Messages
- Use clear, descriptive commit messages
- Start with a verb (Add, Fix, Update, Remove)
- Reference issues when applicable

### Pull Requests
- Create a branch for your feature/fix
- Update documentation if needed
- Test with the example site
- Describe your changes clearly in the PR

## Testing

Before submitting:

1. Test the example site runs without errors
2. Check responsive design (mobile, tablet, desktop)
3. Verify all configuration options work
4. Test with different growth stages
5. Check both light and dark mode if applicable

## Questions?

Open an issue for discussion before making major changes.

Happy gardening! 🌿
