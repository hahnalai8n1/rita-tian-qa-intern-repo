# Introduction to Automated E2E Testing

## Reflection

**What is the difference between E2E, unit, and integration testing?**
* **Unit Testing:** Tests individual, isolated functions or components (e.g., testing if a single math function returns the correct sum).
* **Integration Testing:** Tests how multiple units work together (e.g., testing if the database correctly saves the data sent by the API).
* **E2E (End-to-End) Testing:** Simulates a real user clicking through the application from start to finish. It tests the entire system as a whole, ensuring the UI, database, and backend all interact correctly.


**What are the key benefits of E2E tests in a real-world application?**
E2E tests catch real-world, user-facing bugs that unit tests might miss. For my workflow, automated E2E tests act as an asynchronous assistant—once written, they run quietly in the background, executing repetitive manual test steps precisely and freeing up my time to focus on complex, exploratory QA testing.

**How does automated testing help Focus Bear reduce regression bugs?**
Focus Bear has complex core features, like strictly blocking distracting apps. When developers push new code, automated E2E tests can quickly verify that the app-blocking feature wasn't accidentally broken (a regression) without needing me to manually test every single app on my computer again.

**What are some challenges of writing and maintaining E2E tests?**
E2E tests can be "flaky" (failing randomly due to slow loading times or network issues). They are also slower to run and require high maintenance if the UI changes frequently, meaning clear written documentation on UI changes is essential.