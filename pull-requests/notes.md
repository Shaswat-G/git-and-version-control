## Creating a Pull Request and dev cycle

### What is a Pull Request?
A pull request (PR) is a way to propose changes to a codebase. It allows developers to submit their changes for review and discussion before they are merged into the main codebase. A PR is typically created when a developer has completed a feature or bug fix and wants to share it with the rest of the team.

### Why do we use Pull Requests?
Pull requests are used to facilitate collaboration and communication between developers. They allow team members to review each other's code, provide feedback, and discuss changes before they are merged into the main codebase. This helps ensure that the code is of high quality, follows best practices, and is free of bugs.

### How do we create a Pull Request?
Creating a pull request is a simple process. First, we need to make sure we have the latest version of the main codebase. We can do this by pulling the latest changes from the main branch. Once we have the latest version, we can create a new branch for our changes. This is typically done using the `git checkout -b` command, followed by the name of the new branch.
1. Create a clear and concise title for the PR.
2. Write a TL;DR summary of the changes made.
3. Write a detailed description of the changes made, including any relevant links to issues or other PRs. Give context -> Why is this change needed? What problem does it solve? What are the benefits of this change? GIve instruction if things need to installed or setup or configured before someone can test the changes. YOu can also include screenshots or GIFs to help illustrate the changes made.
4. Assign team members to review the PR.
5. Add any relevant labels or tags to the PR.
6. Review your own PR you request anyone else to review yours. THen Submit the PR for review.
Once the PR is submitted, team members can review the changes, provide feedback, and discuss any issues that arise. This is typically done using the comments section of the PR. Once the review process is complete, the PR can be merged into the main codebase.

### What is the common dev workflow?
Usually, to work on a an independent feature, we create a new branch to keep the main code base clean. Its best practive to create a detailed issue first with descriptions, plans, inclusions, deliverarbles etc, complete with tags, parent issues, milestones and team member to be assigned. Once the issue is created we can make a new branch with a descriptive name, push it origin in the same name to be tracked remotely.

Then we follow the our coding cycle, which is idea -> code -> build -> test -> deploy -> iterate. ONce the code is ready, we can create a pull request with a detailed description of the changes made, tagging the issue it is solving, along with other issues that this PR is relateed to. We can assign team members to review the code, make comments or reques changes. Once we implement the changes, we can mark the PR as ready for reveiw once again. Once the PR is approved, we can merge it to the main branch which may or may not involve a merge conflict. We can choose to to do a fast forward merge (which creates a new merge commit) or a suash merge which squashes all the commits into a single commit. We can also choose to rebase the branch which will reapply the commits on top of the main branch to maintain a linear history. Once the PR is merged, we can delete the branch and close the issue.

## Philosophy
1. A PR should be laser focussed on doing one thing and one thing only - and it should do that well. Doing multiple things in a single PR is confusing, disorienting and makes it hard to review. It also makes it hard to revert a change if something goes wrong. Therefore, define a clear goal and stick to it.
2. A PR should be small enough to be reviewed in a short amount of time. If a PR is too large, it becomes overwhelming and hard to review. A good rule of thumb is to keep the PR under 200 lines of code. If a PR is larger than that, consider breaking it up into smaller PRs.
3. A PR should be self-contained. It should not depend on other PRs or changes that are not yet merged. This makes it easier to review and test the changes in isolation. If a PR depends on another PR, consider waiting for that PR to be merged before creating the new PR.
4. A PR should be well-documented. This includes a clear and concise title, a detailed description of the changes made, and any relevant links to issues or other PRs. This helps reviewers understand the context of the changes and makes it easier to review the code.
5. You should always review your own PR before requesting anyone else to review it. This helps catch any mistakes or issues before they are seen by others. It also shows that you care about the quality of your code and are willing to put in the effort to make it better. There are so many mistakes that you can catch by just reading your own code. ANd there aer many tools that can help you with this. For example, you can use linters to catch syntax errors, formatting issues, and other common mistakes. You can also use static analysis tools to catch more complex issues, such as potential bugs or performance problems. These tools can help you catch issues before they become a problem, and they can save you a lot of time and effort in the long run.
6. The goal while you make a PR is that your code will not require any cghanges or commits.


## How to review a PR
1. Read the title and description of the PR. This will give you an idea of what the PR is trying to accomplish and what changes have been made. Read the issue that the PR is trying to solve. This will give you context for the changes made in the PR and help you understand why they were made.
2. Check the code changes made in the PR. Look for any syntax errors, formatting issues, or other common mistakes. Pay attention to the logic of the code and make sure it makes sense. Look for any potential bugs or performance problems. (Files changed, Commits, Conversation)
3. See the sequence of commits to understand how did they develop this change. This will help you understand the thought process behind the changes and make it easier to review the code.
4. Checkout the branch locally and test the changes made in the PR. This will help you understand how the changes work in practice and make it easier to review the code. Look for any issues or bugs that may have been missed in the code review process.
5. Leave comments on the PR with any feedback or suggestions for improvement. Be specific and provide examples where possible. Avoid vague or general comments that are not helpful. Be respectful and constructive in your feedback. Remember that the goal is to help the author improve their code, not to criticize them personally. I personally appreciate the good things done and set a positive tone and ask curiosity driven questions being respectful and constructive.

Simply adding comments will flood the notificaions for all the poeple involved. Its better to start a review and then leave comments. This will only raise one notificaiton for the PR. You can also use the "resolve conversation" feature to mark comments as resolved once they have been addressed. This helps keep the conversation organized and makes it easier to track the progress of the PR.
6. Once you have completed your review, leave a summary comment with your overall thoughts on the PR. This can include any major issues or concerns, as well as any positive feedback or suggestions for improvement. You can also use the "approve" or "request changes" feature to indicate whether you think the PR is ready to be merged or if it needs further work.
7. If you approve the PR, make sure to leave a comment indicating that you have reviewed the changes and are happy with them.
8. You can choose to squash, ffm or rebase.