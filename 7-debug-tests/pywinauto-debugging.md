# Debugging & Handling Common Test Failures

## Reflection

**What are the most common reasons for E2E test failures?**
Beyond timing issues, failures often happen due to unexpected modal dialogs (like update prompts stealing focus) or elements changing their `AutomationId` dynamically between builds.

**How do you determine if a test is flaky?**
If I run the exact same test script against the exact same application version three times, and it passes twice but fails once, it is a flaky test.

**What strategies can you use to improve test reliability?**
Using a hybrid approach for WebViews is critical: using Pywinauto to handle the native Windows context and attaching Selenium to the DevTools port to handle the DOM explicitly. This provides precise control over each specific environment.

**How can logging and screenshots help with debugging test failures?**
They are the ultimate form of asynchronous feedback. By configuring Pytest to automatically capture a screenshot and print a stack trace upon failure, I instantly get all the detailed, written, and visual context I need to diagnose the problem independently. I do not need to reproduce the bug live on a video call.