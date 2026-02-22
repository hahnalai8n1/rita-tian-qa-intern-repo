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