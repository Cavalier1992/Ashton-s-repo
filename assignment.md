# Using Git Rebase

### Why Rebase Instead of Merge?

While working collaboratively, maintaining a clear and concise version history is essential. Git branches allow contributors to work independently, but eventually, all changes will need to be integrated into the main branch. This is where rebasing becomes a valuable technique.

### Rebase vs. Merge

While merging preserves the branching structure and shows how changes from different branches came together, rebasing reapplies your changes on top of the updated main branch, resulting in a linear history.

### Clean, Linear Commit History

One of the most compelling reasons to use rebase is to maintain a clean and linear commit history. In documentation projects, where updates are frequent and involve multiple contributors, a series of merge commits can more quickly clutter the history.

With rebasing, your commits are "replayed" onto the latest version of the main branch, making it look as though your changes were made after the most recent updates. This eliminates unnecessary merge commits and makes the history easier to read.

**Example**:

Instead of seeing the following history:

```text
*   Merge branch 'fix-typos'  
|\
| * Fixed typo in chapter 2  
| * Fixed typo in chapter 1  
* Updated introduction  
```

After rebasing, the same history becomes:

```text
* Fixed typo in chapter 2  
* Fixed typo in chapter 1  
* Updated introduction  
```

This streamlined history is especially helpful when reviewing project changes or tracking down issues.

### Easy-to-Track Changes

In documentation work, it’s common to make small but frequent updates. Rebasing allows you to squash related commits into a single, meaningful one. For example, if you made three minor edits to a tutorial in separate commits, you can squash them into one meaningful commit during an interactive rebase. This helps to keep the commit log concise and avoids overwhelming reviewers with numerous minor changes.


### Minimal Conflict During Collaboration

When you rebase your branch before merging it into the main branch, you’re integrating the latest changes proactively. This means you've already resolved any conflicts on your branch, rather than dealing with them during a merge. This helps reduce the chance of introducing new conflicts into the main branch during integration.

## How to Rebase

Regular rebasing is useful when you want to integrate only the latest changes from the main branch into your working branch. This essentially applies commits on the tip of the base branch.

(1) Check out your feature branch:

```text
git checkout my-branch
```

(2) Update your main branch:

```text
git fetch origin
```

(3) Rebase your branch onto the main branch:

```text
git rebase origin/main
```

(4) Resolve any conflicts:

Git will pause and highlight any conflicts. Fix the conflicting files and mark them as resolved:

```text
git add <file>
git rebase --continue
```

(5) Push your changes:

If you've already pushed the original version of the branch, you'll need to force-push:

```text
git push --force
```

### When to Avoid Rebase

While rebasing is a very useful technique for maintaining a clean and concise commit history, you should avoid rebasing public or shared branches. Rebasing alters commit history, which can confuse collaborators or disrupt shared work if others have already based work on those commits.
