# Static Analysis Checks in CI/CD

## Reflection

**What is the purpose of CI/CD?**
Continuous Integration and Continuous Deployment (CI/CD) automates the process of testing, linting, and deploying code every time a change is pushed to the repository.




**How does automating style checks improve project quality?**
Automated bots run Husky hooks and GitHub Actions to enforce rules (like Markdown linting and spell checks) *before* human review. This is incredibly efficient. It means when I review a PR, I am not distracted by typos or formatting errors; I can focus entirely on the logic. It removes the need for interpersonal friction over code style.

**What are some challenges with enforcing checks in CI/CD?**
Strict rules can sometimes block a PR for minor, trivial issues (like a single trailing space), which can be frustrating if the developer is trying to push an urgent hotfix.

**How do CI/CD pipelines differ between small projects and large teams?**
In small projects, CI might just run a quick linter. In large teams, CI/CD is the ultimate gatekeeper. It runs hundreds of automated end-to-end (E2E) tests, security scans, and formatting checks to ensure nobody accidentally breaks the `main` branch asynchronously.