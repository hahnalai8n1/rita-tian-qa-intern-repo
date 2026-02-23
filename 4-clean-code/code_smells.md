# Identifying & Fixing Code Smells

## Reflection

**What code smells did you find in your code?**
* **Magic Numbers:** I found hardcoded values like `if (status === 2)` instead of using a descriptive constant like `if (status === STATUS_ACTIVE)`.
* **Deeply Nested Conditionals:** Code that formed an "arrow shape" due to multiple `if/else` blocks inside each other.
* **Commented-Out Code:** Chunks of old, unused code that were left in "just in case," which clutters the file and causes confusion.



**How did refactoring improve readability and maintainability?**
Replacing magic numbers with named constants provides immediate, clear written context. Flattening nested conditionals using Guard Clauses makes the code read linearly from top to bottom, which aligns perfectly with how I process information methodically.

**How can avoiding code smells make future debugging easier?**
Clean, odor-free code isolates logic. When a QA test fails, a codebase without "God Objects" (classes that do everything) or duplicate code allows me to trace the bug directly to a single, easily digestible function.