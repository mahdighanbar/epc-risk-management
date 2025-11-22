# Contributing to EPC Project Manager

Thank you for your interest in contributing to the EPC Project Manager! This document provides guidelines for contributing to the project.

## Table of Contents
1. [Code of Conduct](#code-of-conduct)
2. [Getting Started](#getting-started)
3. [Development Setup](#development-setup)
4. [Making Changes](#making-changes)
5. [Submitting Changes](#submitting-changes)
6. [Coding Standards](#coding-standards)
7. [Testing Guidelines](#testing-guidelines)

## Code of Conduct

By participating in this project, you agree to maintain a respectful and inclusive environment for all contributors.

### Our Standards
- Use welcoming and inclusive language
- Be respectful of differing viewpoints
- Accept constructive criticism gracefully
- Focus on what's best for the community
- Show empathy towards other community members

## Getting Started

### Prerequisites
- Node.js 16 or higher
- npm or yarn
- Git
- MetaMask or another Web3 wallet
- Basic knowledge of React and Ethereum

### Finding Issues to Work On
- Check the [Issues](https://github.com/your-repo/issues) page
- Look for issues tagged with `good first issue` or `help wanted`
- Feel free to ask questions on any issue

## Development Setup

1. **Fork the repository**
   ```bash
   # Click "Fork" on GitHub, then clone your fork
   git clone https://github.com/your-username/epc-project-manager.git
   cd epc-project-manager
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment**
   ```bash
   cp .env.example .env
   # Edit .env with your configuration
   ```

4. **Start development server**
   ```bash
   npm start
   ```

5. **Create a branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

## Making Changes

### Branch Naming Convention
- Feature: `feature/description`
- Bug fix: `fix/description`
- Documentation: `docs/description`
- Performance: `perf/description`
- Refactor: `refactor/description`

### Commit Message Guidelines
Follow the [Conventional Commits](https://www.conventionalcommits.org/) specification:

```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `perf`: Performance improvements
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

**Examples:**
```bash
feat(payments): add batch payment approval
fix(dashboard): correct project count calculation
docs(readme): update installation instructions
```

## Submitting Changes

### Pull Request Process

1. **Update your branch**
   ```bash
   git fetch origin
   git rebase origin/main
   ```

2. **Run tests**
   ```bash
   npm test
   npm run lint
   ```

3. **Push your changes**
   ```bash
   git push origin feature/your-feature-name
   ```

4. **Create Pull Request**
   - Go to your fork on GitHub
   - Click "New Pull Request"
   - Provide a clear description of changes
   - Link related issues

### Pull Request Template

```markdown
## Description
[Describe your changes]

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Testing
[Describe how you tested your changes]

## Screenshots (if applicable)
[Add screenshots]

## Checklist
- [ ] Code follows project style guidelines
- [ ] Self-review completed
- [ ] Comments added for complex code
- [ ] Documentation updated
- [ ] No new warnings generated
- [ ] Tests added/updated
- [ ] All tests pass
```

## Coding Standards

### JavaScript/React
- Use functional components with hooks
- Follow ESLint configuration
- Use meaningful variable names
- Keep components small and focused
- Avoid deep nesting

### Example:
```javascript
// Good
const ProjectCard = ({ project }) => {
  const { name, budget, status } = project;
  
  return (
    <div className="project-card">
      <h3>{name}</h3>
      <p>Budget: {budget} ETH</p>
      <Badge status={status} />
    </div>
  );
};

// Avoid
const ProjectCard = (props) => {
  return (
    <div className="project-card">
      <h3>{props.project.name}</h3>
      <p>Budget: {props.project.budget} ETH</p>
      <Badge status={props.project.status} />
    </div>
  );
};
```

### CSS/Styling
- Use Tailwind utility classes
- Follow mobile-first approach
- Keep custom CSS minimal
- Use semantic color names

### Smart Contract Interactions
- Always handle errors
- Provide user feedback
- Validate input before transactions
- Use try-catch blocks

```javascript
// Good
const handleTransaction = async () => {
  try {
    setLoading(true);
    const tx = await contract.someFunction(params);
    toast.info('Transaction submitted...');
    await tx.wait();
    toast.success('Transaction confirmed!');
  } catch (error) {
    console.error('Transaction failed:', error);
    toast.error('Transaction failed');
  } finally {
    setLoading(false);
  }
};
```

## Testing Guidelines

### Unit Tests
- Test individual components
- Mock external dependencies
- Test edge cases

### Integration Tests
- Test component interactions
- Test Web3 functionality
- Test routing

### Example Test:
```javascript
import { render, screen } from '@testing-library/react';
import ProjectCard from './ProjectCard';

describe('ProjectCard', () => {
  it('renders project information', () => {
    const project = {
      name: 'Test Project',
      budget: '10',
      status: 'active'
    };
    
    render(<ProjectCard project={project} />);
    
    expect(screen.getByText('Test Project')).toBeInTheDocument();
    expect(screen.getByText('Budget: 10 ETH')).toBeInTheDocument();
  });
});
```

## Documentation

### Code Comments
- Explain "why", not "what"
- Document complex algorithms
- Add JSDoc for functions

```javascript
/**
 * Calculates the total project cost including fees
 * @param {number} baseCost - Base project cost in ETH
 * @param {number} feePercentage - Fee percentage (0-100)
 * @returns {number} Total cost including fees
 */
const calculateTotalCost = (baseCost, feePercentage) => {
  return baseCost * (1 + feePercentage / 100);
};
```

### README Updates
- Update README for new features
- Add examples for new functionality
- Update installation steps if needed

## Review Process

### What Reviewers Look For
1. Code quality and readability
2. Test coverage
3. Documentation completeness
4. Performance considerations
5. Security implications
6. Breaking changes

### Addressing Review Comments
- Respond to all comments
- Make requested changes
- Push updates to the same branch
- Request re-review when ready

## Release Process

### Versioning
We use [Semantic Versioning](https://semver.org/):
- MAJOR: Breaking changes
- MINOR: New features (backward compatible)
- PATCH: Bug fixes

### Release Notes
- Document all changes
- Credit contributors
- Highlight breaking changes
- Provide migration guides

## Getting Help

### Resources
- [README.md](README.md) - Project overview
- [USER_GUIDE.md](USER_GUIDE.md) - Usage instructions
- [DEPLOYMENT_GUIDE.md](DEPLOYMENT_GUIDE.md) - Deployment help
- [GitHub Discussions](https://github.com/your-repo/discussions) - Ask questions

### Communication Channels
- GitHub Issues - Bug reports and features
- GitHub Discussions - General questions
- Discord - Real-time chat (if available)
- Email - Maintainer contact

## Recognition

Contributors will be recognized in:
- README.md contributors section
- Release notes
- Project documentation

## License

By contributing, you agree that your contributions will be licensed under the same license as the project (MIT License).

---

Thank you for contributing to EPC Project Manager! Your efforts help make blockchain-based construction management better for everyone. 🚀
