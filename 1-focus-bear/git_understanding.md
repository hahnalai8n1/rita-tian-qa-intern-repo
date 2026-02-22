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

## Advanced Git Commands & When to Use Them

**What does each command do?**
* `git checkout main -- <file>`: Restores a single file to its state in the `main` branch, throwing away local uncommitted changes for just that file.
* `git cherry-pick <commit>`: Grabs one specific commit from another branch and applies it to your current branch without merging the entire history.
* `git log`: Displays the chronological history of commits.
* `git blame <file>`: Annotates each line of a file, showing the exact commit and author who last modified it.

**When would you use it in a real project?**
As a QA, if I accidentally break a complex test script, I can use `checkout` to instantly reset just that script to the clean `main` version. If a developer fixes a blocker bug on a separate feature branch, I can `cherry-pick` just that fix into my testing branch to continue my work. `git blame` and `git log` are vital for async communication: instead of asking "who wrote this?" in a noisy channel, I can silently find the author and read their exact commit message for context.

**What surprised you while testing these commands?**
I was surprised by `git blame`. Despite its aggressive-sounding name, it is actually just a highly detailed, line-by-line historical map. It provides the clear, direct written context I need to understand why a specific line of code exists.

## Debugging with `git bisect`

**What does `git bisect` do?**
It performs a binary search through your commit history to find the exact commit that introduced a bug. You tell Git a "bad" commit (where the bug exists) and a "good" commit (where it didn't), and Git automatically checks out commits in the middle for you to test until the culprit is isolated.

[Image of a git bisect binary search process]

**When would you use it in a real-world debugging situation?**
If a feature was working flawlessly last Friday but is completely broken today, and there have been 50 commits merged over the weekend. Instead of guessing, I can use `git bisect` to mathematically pinpoint the exact code change that caused the failure.

**How does it compare to manually reviewing commits?**
Manual review is linear and exhausting (checking every single commit). `git bisect` reduces the time complexity to $O(\log N)$ compared to the $O(N)$ of linear review. It removes the guesswork and provides a clear, structured set of instructions (test this -> good/bad -> test next), which perfectly matches my preferred working style.