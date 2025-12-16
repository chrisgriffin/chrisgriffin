# GitHub Copilot Instructions

This file defines the coding standards, processes, and guidelines for how GitHub Copilot should assist with development in this repository. Customize each section below to match your project's specific requirements.

---

## 1. Coding Standards

<!-- Define your code style, formatting rules, and linting requirements -->

### Style Guide
- **Language-specific guides**: Follow [style guide name] for [language] (e.g., PEP 8 for Python, Airbnb for JavaScript)
- **Indentation**: Use [tabs/spaces], [2/4] spaces per indent level
- **Line length**: Maximum [80/100/120] characters per line
- **Quotes**: Prefer [single/double] quotes for strings
- **Semicolons**: [Required/Optional/Never] for statement termination

### Formatting Rules
- **Auto-formatting**: Use [Prettier/Black/gofmt/etc.] with configuration file: `[config file path]`
- **Import ordering**: [Describe import organization, e.g., standard library, third-party, local]
- **Whitespace**: [Rules for blank lines, trailing whitespace, etc.]
- **Code organization**: [File structure preferences, e.g., exports at top/bottom]

### Linting Requirements
- **Linter**: Use [ESLint/Pylint/RuboCop/etc.] with configuration: `[config file path]`
- **Pre-commit hooks**: [Describe any pre-commit requirements]
- **Must fix**: All [error/warning] level violations before committing
- **Allowed exceptions**: [List any acceptable lint rule violations with justification]

**Example:**
```
// Use ESLint with Airbnb style guide
// Run: npm run lint
// Fix: npm run lint:fix
```

---

## 2. Naming Conventions

<!-- Define how to name files, variables, functions, classes, and other identifiers -->

### Files and Directories
- **Files**: Use [camelCase/kebab-case/snake_case/PascalCase]
- **Directories**: Use [camelCase/kebab-case/snake_case/PascalCase]
- **Test files**: Name pattern: `[name.test.js / name_test.py / test_name.rb]`
- **Component files**: [Describe component file naming, e.g., PascalCase for React components]

### Variables and Constants
- **Variables**: Use [camelCase/snake_case] (e.g., `userName`, `user_name`)
- **Constants**: Use [SCREAMING_SNAKE_CASE/UPPER_CASE] (e.g., `MAX_RETRIES`, `API_KEY`)
- **Private variables**: Prefix with [underscore/_/private keyword]
- **Boolean variables**: Prefix with `is`, `has`, `should`, `can` (e.g., `isActive`, `hasPermission`)

### Functions and Methods
- **Functions**: Use [camelCase/snake_case] (e.g., `getUserData`, `get_user_data`)
- **Private methods**: Prefix with [underscore/_]
- **Async functions**: [Optional prefix like `async` or `fetch`]
- **Event handlers**: Prefix with `handle` or `on` (e.g., `handleClick`, `onClick`)

### Classes and Types
- **Classes**: Use [PascalCase] (e.g., `UserService`, `DataProcessor`)
- **Interfaces**: Use [PascalCase], prefix with `I` [if applicable] (e.g., `IUserRepository`)
- **Types/Type aliases**: Use [PascalCase] (e.g., `UserProfile`, `ApiResponse`)
- **Enums**: Use [PascalCase] for enum name, [SCREAMING_SNAKE_CASE/PascalCase] for values

**Example:**
```javascript
// Good naming examples
const MAX_RETRY_COUNT = 3;
const isUserLoggedIn = true;

function handleUserLogin(userData) { ... }

class UserAuthenticationService { ... }
```

---

## 3. Architecture & Patterns

<!-- Define preferred design patterns, architectural decisions, and project structure -->

### Design Patterns
- **Preferred patterns**: [e.g., MVC, MVVM, Repository pattern, Factory pattern]
- **State management**: Use [Redux/MobX/Context API/Vuex/etc.]
- **Dependency injection**: [Describe DI approach if applicable]
- **Error handling**: Use [try-catch/error boundaries/result types/etc.]

### Project Structure
```
/project-root
  /src                  # [Description]
    /components         # [Description]
    /services           # [Description]
    /utils              # [Description]
    /models             # [Description]
  /tests                # [Description]
  /docs                 # [Description]
  /config               # [Description]
```

### Code Organization
- **Separation of concerns**: [Describe how to separate business logic, UI, data access]
- **Module boundaries**: [Define what constitutes a module and how they should interact]
- **File size limits**: Keep files under [X] lines; split if larger
- **Circular dependencies**: [Not allowed / How to handle]

### API Design
- **REST conventions**: Follow [REST best practices / specific API style guide]
- **GraphQL schema**: [Schema design principles if applicable]
- **Versioning**: Use [URL versioning / header versioning / etc.]
- **Response format**: Standard response structure: `{ data, error, metadata }`

**Example:**
```
// Use repository pattern for data access
class UserRepository {
  async findById(id) { ... }
  async save(user) { ... }
}
```

---

## 4. Testing Requirements

<!-- Define testing frameworks, coverage expectations, and test organization -->

### Testing Framework
- **Unit tests**: Use [Jest/pytest/RSpec/xUnit/etc.]
- **Integration tests**: Use [same as unit / different framework]
- **E2E tests**: Use [Cypress/Playwright/Selenium/etc.]
- **Test runner**: Execute with `[npm test / pytest / etc.]`

### Coverage Expectations
- **Minimum coverage**: [80/90/100]% overall
- **Critical paths**: [90/100]% coverage required
- **Coverage tool**: Use [Jest coverage / coverage.py / etc.]
- **Coverage reporting**: Run `[coverage command]`

### Test Organization
- **Test location**: [Co-located with source / separate test directory]
- **Test file naming**: `[component].test.[ext]` or `test_[module].[ext]`
- **Test structure**: Use [Arrange-Act-Assert / Given-When-Then]
- **Test descriptions**: Write clear, descriptive test names

### Test Naming Conventions
```
// Unit test naming pattern
describe('[Component/Module]', () => {
  it('should [expected behavior] when [condition]', () => {
    // Test implementation
  });
});
```

### Mocking and Fixtures
- **Mocking library**: Use [jest.mock / unittest.mock / etc.]
- **Test data**: Store fixtures in `[fixtures directory]`
- **External services**: Always mock [APIs/databases/file system]
- **Time-based tests**: Use [fake timers/freezegun/etc.]

**Example:**
```javascript
// Good test example
describe('UserService', () => {
  it('should return user data when valid ID is provided', async () => {
    const userId = '123';
    const result = await userService.getUserById(userId);
    expect(result).toBeDefined();
    expect(result.id).toBe(userId);
  });
});
```

---

## 5. Documentation Standards

<!-- Define expectations for code comments, README files, and API documentation -->

### Code Comments
- **When to comment**: Explain [why, not what] the code does
- **Complex logic**: Always document non-obvious algorithms or business rules
- **TODOs**: Format as `// TODO: [description]` with ticket reference
- **Deprecations**: Use `@deprecated` with migration guidance
- **Comment style**: Use [JSDoc/docstrings/XML comments/etc.]

### Function/Method Documentation
```javascript
/**
 * [Brief description of what the function does]
 * 
 * @param {type} paramName - [Parameter description]
 * @param {type} [optionalParam] - [Optional parameter description]
 * @returns {type} [Description of return value]
 * @throws {ErrorType} [When this error is thrown]
 * @example
 * // [Usage example]
 */
```

### README Requirements
- **Must include**:
  - Project description and purpose
  - Installation/setup instructions
  - Usage examples
  - Configuration options
  - Contributing guidelines
  - License information
- **Update when**: Adding features, changing setup process, modifying APIs

### API Documentation
- **Format**: Use [OpenAPI/Swagger / JSDoc / etc.]
- **Documentation location**: [docs/ directory / inline / separate API docs site]
- **Required sections**: Endpoint description, parameters, request/response examples, error codes
- **Auto-generation**: Use [tool name] to generate docs from code

### Changelog
- **Maintain**: Keep `CHANGELOG.md` updated following [Keep a Changelog](https://keepachangelog.com/)
- **Format**: Organize by version with Added, Changed, Deprecated, Removed, Fixed, Security sections
- **Update when**: Every release and significant change

**Example:**
```javascript
/**
 * Authenticates a user with provided credentials
 * 
 * @param {string} email - User's email address
 * @param {string} password - User's password
 * @returns {Promise<AuthToken>} Authentication token and user data
 * @throws {AuthenticationError} When credentials are invalid
 * @example
 * const token = await authenticateUser('user@example.com', 'password123');
 */
async function authenticateUser(email, password) { ... }
```

---

## 6. Build & Development

<!-- Define how to build, run, and test the code locally -->

### Prerequisites
- **Required tools**:
  - [Node.js] version [X.X.X] or higher
  - [Python] version [X.X.X] or higher
  - [Database] (e.g., PostgreSQL 14+, MongoDB 5+)
  - [Other tools/dependencies]

### Local Development Setup
```bash
# Clone the repository
git clone [repository-url]

# Install dependencies
[npm install / pip install -r requirements.txt / bundle install]

# Set up environment variables
cp .env.example .env
# Edit .env with your local configuration

# Set up database
[database setup commands]

# Run migrations
[migration commands]
```

### Development Workflow
```bash
# Start development server
[npm run dev / python manage.py runserver / etc.]

# Run in watch mode
[npm run watch / etc.]

# Access the application
# Web: http://localhost:[PORT]
# API: http://localhost:[PORT]/api
```

### Build Process
```bash
# Production build
[npm run build / python setup.py build / etc.]

# Build output location
[dist/ / build/ / etc.]

# Build verification
[npm run build && npm run test:build]
```

### Running Tests
```bash
# Run all tests
[npm test / pytest / etc.]

# Run specific test file
[npm test -- path/to/test.js]

# Run tests in watch mode
[npm test -- --watch]

# Run tests with coverage
[npm run test:coverage]
```

### Linting and Formatting
```bash
# Run linter
[npm run lint]

# Auto-fix linting issues
[npm run lint:fix]

# Format code
[npm run format]

# Type checking
[npm run type-check]
```

### Debugging
- **Debugger**: Use [VS Code debugger / pdb / etc.]
- **Configuration**: Launch configuration in `.vscode/launch.json`
- **Logging**: Set log level with `[LOG_LEVEL=debug]`
- **Debug tools**: [Describe any debug utilities or tools]

**Example:**
```bash
# Complete local setup
npm install
cp .env.example .env
npm run db:migrate
npm run dev
```

---

## 7. Dependencies

<!-- Define how to manage packages, versions, and third-party libraries -->

### Package Management
- **Package manager**: Use [npm/yarn/pnpm/pip/bundler/etc.]
- **Lock files**: Always commit [package-lock.json/yarn.lock/Pipfile.lock/etc.]
- **Installation**: Use `[npm ci / pip install / etc.]` in CI/CD
- **Registry**: Use [default registry / private registry URL]

### Adding Dependencies
- **Before adding**: Check if functionality exists in current dependencies
- **Evaluation criteria**:
  - Active maintenance and community support
  - Security track record
  - License compatibility ([MIT/Apache/BSD/etc.] preferred)
  - Bundle size impact (for frontend)
  - Performance implications
- **Documentation**: Note why dependency was added in PR description

### Version Constraints
- **Pinning strategy**: 
  - Production: Use [exact versions / caret (^) / tilde (~)]
  - Development: Use [caret (^) / tilde (~)]
- **Version format**: Follow [semver](https://semver.org/)
- **Major version updates**: Require review and testing
- **Security updates**: Apply promptly, even for major versions

### Dependency Updates
- **Update frequency**: Review dependencies [weekly/monthly/quarterly]
- **Update process**:
  ```bash
  # Check for outdated packages
  [npm outdated / pip list --outdated]
  
  # Update dependencies
  [npm update / pip install --upgrade]
  
  # Test after updates
  [npm test]
  ```
- **Breaking changes**: Document in PR and update migration guide

### Prohibited Dependencies
- **Not allowed**: [List any banned packages or categories]
- **Alternatives**: [Suggest alternatives to common problematic packages]
- **Exceptions**: Require approval from [team lead/architect]

**Example:**
```json
// package.json - Use exact versions for critical dependencies
{
  "dependencies": {
    "express": "^4.18.2",
    "lodash": "4.17.21"
  }
}
```

---

## 8. Git Workflow

<!-- Define commit message format, branch naming, and pull request requirements -->

### Branch Naming
- **Feature branches**: `feature/[ticket-id]-[brief-description]` or `feat/[description]`
- **Bug fixes**: `fix/[ticket-id]-[brief-description]` or `bugfix/[description]`
- **Hotfixes**: `hotfix/[description]`
- **Releases**: `release/[version]`
- **Experiments**: `experiment/[description]`

### Commit Message Format
Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, semicolons, etc.)
- `refactor`: Code refactoring without feature changes
- `perf`: Performance improvements
- `test`: Adding or updating tests
- `chore`: Maintenance tasks, dependency updates
- `ci`: CI/CD configuration changes

**Example:**
```
feat(auth): add OAuth2 authentication support

Implement OAuth2 authentication flow with Google and GitHub providers.
Includes token refresh logic and secure session management.

Closes #123
```

### Commit Best Practices
- **Atomic commits**: Each commit should represent one logical change
- **Commit frequency**: Commit often, push when feature/fix is complete
- **Message length**: Subject line ≤ 50 chars, body ≤ 72 chars per line
- **Imperative mood**: "Add feature" not "Added feature" or "Adds feature"

### Pull Request Requirements
- **PR title**: Follow commit message format: `type(scope): description`
- **PR description must include**:
  - What changed and why
  - Testing performed
  - Screenshots (for UI changes)
  - Breaking changes (if any)
  - Related issue/ticket number
- **Size limits**: Keep PRs under [300/500] lines when possible
- **Draft PRs**: Use for work-in-progress that needs early feedback

### PR Checklist
Before submitting a PR, ensure:
- [ ] Code follows style guide and passes linting
- [ ] All tests pass locally
- [ ] Added/updated tests for changes
- [ ] Updated documentation (README, comments, API docs)
- [ ] No console.log or debug statements
- [ ] Reviewed own code diff
- [ ] Branch is up to date with main/master

### Merge Strategy
- **Merge method**: Use [squash and merge / merge commit / rebase and merge]
- **Merge requirements**:
  - [X] number of approvals required
  - All CI checks must pass
  - No unresolved conversations
  - Branch must be up to date
- **Delete branches**: Automatically delete branches after merge

**Example branch and commit:**
```bash
# Create feature branch
git checkout -b feature/AUTH-123-add-oauth-login

# Make changes and commit
git add .
git commit -m "feat(auth): add OAuth2 login with Google provider"

# Push and create PR
git push origin feature/AUTH-123-add-oauth-login
```

---

## 9. Code Review Guidelines

<!-- Define what reviewers should check and how to conduct effective reviews -->

### Review Responsibilities
- **Author**: Ensure code is ready for review (passes tests, linting, self-reviewed)
- **Reviewer**: Provide constructive feedback within [24/48] hours
- **Approvals needed**: [1/2/3] approvals required depending on change scope

### What to Review
- [ ] **Correctness**: Does the code do what it's supposed to do?
- [ ] **Tests**: Are there adequate tests? Do they pass?
- [ ] **Design**: Is the code well-structured and maintainable?
- [ ] **Naming**: Are names clear and follow conventions?
- [ ] **Complexity**: Is the code as simple as possible?
- [ ] **Documentation**: Are complex parts documented?
- [ ] **Security**: Are there any security vulnerabilities?
- [ ] **Performance**: Are there obvious performance issues?
- [ ] **Error handling**: Are errors handled appropriately?
- [ ] **Edge cases**: Are edge cases considered?

### Review Best Practices
- **Be respectful**: Focus on code, not the person
- **Be specific**: Point to exact lines and explain why
- **Suggest alternatives**: Don't just critique, offer solutions
- **Distinguish**:
  - **Must fix**: Blocking issues (bugs, security, violations)
  - **Should fix**: Important but not blocking (style, performance)
  - **Nice to have**: Suggestions for improvement
- **Ask questions**: Use questions to understand intent
- **Praise good code**: Recognize well-written code

### Review Comments Format
```
[MUST FIX] This creates a SQL injection vulnerability
→ Use parameterized queries instead: db.query('SELECT * FROM users WHERE id = ?', [id])

[SHOULD FIX] This function is doing too many things
→ Consider splitting into getUserData() and validateUser()

[NICE TO HAVE] Could use array.map() here for better readability

[QUESTION] Why are we using setTimeout here instead of a Promise?

[PRAISE] Excellent test coverage and clear naming!
```

### Response to Feedback
- **Author should**: 
  - Address all "must fix" comments
  - Respond to all comments (even if just acknowledging)
  - Mark conversations as resolved when addressed
  - Request re-review if significant changes made
- **Resolve disagreements**: Discuss in comments, escalate to [team lead] if needed

### Self-Review Checklist
Before requesting review:
- [ ] Read through every line of the diff
- [ ] Check for debug code, commented code, TODOs
- [ ] Verify tests cover new/changed functionality
- [ ] Run linter and fix all issues
- [ ] Test manually if applicable
- [ ] Update PR description with testing steps

**Example review comment:**
```
[MUST FIX] Line 45: This will throw an error if `user` is null

const email = user.email; // ❌

Suggestion:
const email = user?.email || 'default@example.com'; // ✅
```

---

## 10. Security & Best Practices

<!-- Define security considerations, performance guidelines, and quality standards -->

### Security Considerations
- **Authentication/Authorization**:
  - Always validate user permissions before operations
  - Use [JWT/session-based] authentication
  - Implement rate limiting on auth endpoints
  - Never store passwords in plain text (use [bcrypt/argon2])

- **Input Validation**:
  - Validate and sanitize all user input
  - Use [validation library name] for input validation
  - Implement allowlists over denylists
  - Escape output to prevent XSS

- **Data Protection**:
  - Encrypt sensitive data at rest
  - Use HTTPS/TLS for data in transit
  - Store secrets in environment variables, never in code
  - Use [secret management service] for production secrets

- **SQL/NoSQL Injection**:
  - Always use parameterized queries or ORMs
  - Never concatenate user input into queries
  - Use least-privilege database accounts

- **Dependencies**:
  - Regularly update dependencies for security patches
  - Run `[npm audit / safety check]` before releases
  - Review security advisories for critical dependencies

### Common Vulnerabilities to Avoid
- [ ] SQL Injection
- [ ] Cross-Site Scripting (XSS)
- [ ] Cross-Site Request Forgery (CSRF)
- [ ] Insecure Direct Object References
- [ ] Security Misconfiguration
- [ ] Sensitive Data Exposure
- [ ] Broken Authentication
- [ ] Insufficient Logging/Monitoring

### Performance Guidelines
- **Database**:
  - Use indexes for frequently queried fields
  - Avoid N+1 queries (use eager loading)
  - Implement query pagination for large datasets
  - Cache expensive queries

- **API**:
  - Implement response caching where appropriate
  - Use compression (gzip/brotli)
  - Implement request throttling/rate limiting
  - Return only necessary data (avoid over-fetching)

- **Frontend**:
  - Lazy load components and routes
  - Optimize images (compression, proper formats)
  - Minimize bundle size (code splitting, tree shaking)
  - Use CDN for static assets

- **General**:
  - Profile before optimizing (measure, don't guess)
  - Optimize for [readability/performance] first
  - Document any performance-critical sections

### Code Quality Standards
- **DRY Principle**: Don't Repeat Yourself - extract common logic
- **SOLID Principles**: Follow [specific principles relevant to your stack]
- **YAGNI**: You Aren't Gonna Need It - don't add unused features
- **Keep it Simple**: Prefer simple solutions over clever ones
- **Boy Scout Rule**: Leave code better than you found it

### Error Handling
- **Graceful degradation**: Handle errors without crashing
- **User-friendly messages**: Don't expose stack traces to users
- **Logging**: Log errors with context for debugging
- **Error types**: Use custom error classes for different scenarios
- **Recovery**: Implement retry logic for transient failures

### Logging and Monitoring
- **Log levels**: Use appropriate levels (ERROR, WARN, INFO, DEBUG)
- **Structured logging**: Use JSON format for machine parsing
- **PII protection**: Never log sensitive user data
- **Monitoring**: Set up alerts for [error rates / performance metrics]
- **Log retention**: Follow [retention policy]

**Example security implementation:**
```javascript
// ❌ BAD: SQL injection vulnerability
const query = `SELECT * FROM users WHERE email = '${userEmail}'`;

// ✅ GOOD: Parameterized query
const query = 'SELECT * FROM users WHERE email = ?';
db.execute(query, [userEmail]);

// ❌ BAD: XSS vulnerability
element.innerHTML = userInput;

// ✅ GOOD: Escaped output
element.textContent = userInput;
// or use a sanitization library

// ❌ BAD: Exposed secret
const apiKey = 'sk_live_abc123...';

// ✅ GOOD: Environment variable
const apiKey = process.env.API_KEY;
```

---

## Customization Instructions

To customize this template for your project:

1. **Replace placeholders**: Search for `[...]` and replace with your specific values
2. **Remove irrelevant sections**: Delete sections that don't apply to your project
3. **Add project-specific rules**: Include any unique requirements for your codebase
4. **Update examples**: Replace generic examples with real examples from your project
5. **Share with team**: Ensure all contributors review and agree to these guidelines
6. **Keep updated**: Revisit and update as your project evolves

---

## Additional Resources

- **Project documentation**: [Link to docs]
- **Team wiki**: [Link to wiki]
- **Style guide**: [Link to style guide]
- **Architecture decision records**: [Link to ADRs]
- **Onboarding guide**: [Link to onboarding]

---

*Last updated: [Date]*
*Maintained by: [Team/Person]*
