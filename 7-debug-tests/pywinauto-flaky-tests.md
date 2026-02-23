# Handling Flaky Tests & Improving Stability

## Reflection

**What are the most common causes of flaky tests in Pywinauto?**
Flaky tests (tests that pass and fail randomly) are usually caused by timing issues, race conditions, or dynamic UI elements that render slower than the script executes. 

**How do implicit waits help prevent timing-related test failures?**
Implicit waits set a global, default maximum time that Pywinauto will wait for any element to appear before throwing an error. This acts as a safety net for minor application lags, ensuring the script doesn't fail just because the app took 0.5 seconds longer to load.

**When should explicit waits be used instead of implicit waits?**
Explicit waits (like `wait('visible')` or `wait('enabled')`) should be used for specific, known bottlenecks. For example, waiting for a "Save Complete" notification after submitting a form. Explicit waits are clear, direct instructions that tell the script exactly what state to look for, making the code much more reliable and easier to read.


**How does retry logic help with test stability, and when should it be avoided?**
Retry logic (e.g., trying to click a button up to 3 times if it throws an exception) helps handle brief network hiccups or animations that obscure elements. However, it should be avoided as a "band-aid" for poorly written tests. Overusing retries masks real performance bugs and drastically slows down the test suite.

**What strategies can prevent flaky tests in large test suites?**
1. Always prefer explicit waits over static `time.sleep()`.
2. Isolate test data so tests do not interfere with each other.
3. Run tests in a controlled, isolated CI environment rather than a busy local machine.