# Git Understanding: Merge Conflicts

## Merge Conflicts & Conflict Resolution

**What caused the conflict?**
A merge conflict happens when Git is unable to automatically merge branches. In my test, it occurred because two different branches (`main` and my new test branch) had different edits on the exact same line of the same file. Git could not decide which version of the text was the "correct" one, so it paused the merge and flagged the conflict for manual review.

**How did you resolve it?**
1. I opened my Git desktop client (and VS Code) to view the conflicting file.
2. Git highlighted the conflict, showing the `<<<<<<< HEAD` (current changes on main) and the `>>>>>>> branch-name` (incoming changes).
3. I reviewed both sets of changes to understand the context.
4. I chose to manually edit the file to keep the correct information, removed the Git conflict markers (`<<<`, `===`, `>>>`), and saved the file.
5. Finally, I staged the resolved file and committed the merge.

**What did you learn?**
I learned that merge conflicts are completely normal and not "errors" to panic over. They are simply Git's way of asking for a human decision. Because I value clear, detailed written instructions, I see now how important it is for teams to communicate asynchronously about which files they are modifying. Pulling from `main` frequently before starting new QA tasks will help me minimize these conflicts in the future.

## Git Concepts: Staging vs. Committing

**What is the difference between staging and committing?**
* **Staging (`git add`):** This is the drafting phase. It’s like putting items into a shipping box. You are telling Git, "I want to include these specific changes in the next update," but you haven't finalized it yet.
* **Committing (`git commit`):** This is the finalization phase. It’s like sealing the box and attaching a descriptive shipping label. The changes are now permanently recorded in the repository's history.

**Why does Git separate these two steps?**
Git separates them to provide flexibility and precision. It allows me to make multiple scattered changes across my workspace, but selectively group only the related changes together into a single, highly focused commit.

**When would you want to stage changes without committing?**
When I am QA testing and adjusting multiple files (e.g., fixing a UI test script and an API test script simultaneously). I would want to stage and commit the UI changes first with a clear message, and then stage and commit the API changes separately. The staging area gives me the time and space to organize my work logically before making it permanent.

## Branching & Team Collaboration

**Why is pushing directly to main problematic?**
The `main` branch represents the stable, production-ready version of the software. Pushing directly to `main` bypasses all QA checks and code reviews. If a bug is introduced, it immediately breaks the primary codebase for everyone.

**How do branches help with reviewing code?**
Branches create an isolated, quiet sandbox for each new feature or test. Once the work is done, it is submitted via a Pull Request (PR). This setup heavily supports asynchronous work—it provides a clear, documented space for the team to leave detailed written feedback and allows the author time to process and address those comments before the code ever touches `main`.

**What happens if two people edit the same file on different branches?**
When those branches are eventually merged, Git will attempt to combine them. If the edits overlap on the exact same lines, a "merge conflict" occurs, requiring a human to manually review the written changes and decide which version to keep (as I practiced in the conflict resolution exercise).