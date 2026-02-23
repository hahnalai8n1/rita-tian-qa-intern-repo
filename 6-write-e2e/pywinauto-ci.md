# Integrating Pywinauto Tests into CI/CD

## Reflection

**How does running tests in CI/CD help maintain application stability?**
It acts as an automated, asynchronous gatekeeper. Every time a developer opens a Pull Request, the CI/CD pipeline runs the Pywinauto test suite. This guarantees that basic flows (like starting a focus session) are never broken in the `main` branch, giving me the peace of mind to focus on complex edge cases.

**What are the challenges of running GUI-based tests (Pywinauto) in CI/CD pipelines?**
Unlike purely headless web tests, Windows GUI automation often requires an *active desktop session* to render native windows. Standard Linux CI runners won't work. We need a dedicated Windows runner configured to auto-logon with an unlocked screen, as Pywinauto cannot send real mouse clicks to a locked Windows machine.



**How can flaky tests be handled in a CI/CD environment?**
1. **Never use static sleeps.** Always use explicit waits.
2. **Auto-Retries:** Configure the CI framework (like Pytest) to automatically retry a failed UI step once before failing the entire build.
3. **Artifacts:** Configure the pipeline to take an automatic screenshot if a test fails and save it as a CI artifact. This provides me with clear, direct visual evidence of the bug to analyze asynchronously.

**What would be the next steps to fully integrate Focus Bear’s automated tests into its deployment pipeline?**
1. Set up a self-hosted Windows runner on GitHub Actions with an active display.
2. Write a `.github/workflows/e2e-tests.yml` script that installs Python, Pywinauto, and dependencies.
3. Ensure the test outputs a detailed, written JUnit XML report that the team can review asynchronously in the GitHub PR interface.