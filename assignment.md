### Using Git Rebase

### Why Rebase instead of merge?

While working collaboratively, it's essential to maintain a clear and concise version history. Branches keep work independent. Writers work on branches independently. Eventually, you will integrate changes to the main branch. This is where rebasing becomes a valuable technique.

While merging preserves the branching structure and shows how changes from different branches came together, rebasing takes a different approach. Instead of combining branches with a merge commit, rebasing reapplies your changes on top of the updated main branch, resulting in a linear history.

### linear commit history

Most compelling reasons to use rebase is to maintain a clean and linear commit history. In documentation projects, where updates can happen frequently and involve multiple contributors, a series of merge commits can more quick clutter the project history.

With rebasing, your commits are "rebased" onto the latest version of the main branch, making it look as if your changes were made after the most recent updates. This eliminates unnecessary merge commits and makes the history more easy to read.

**Example**:

Instead of seeing:

```text
*   Merge branch 'fix-typos'  
|\
| * Fixed typo in chapter 2  
| * Fixed typo in chapter 1  
* Updated introduction  
```

After rebasing, you get a straightforward history:

```text
* Fixed typo in chapter 2  
* Fixed typo in chapter 1  
* Updated introduction  
```

This simplicity is especially helpful when looking back at project changes or performing reviews.

### Easy-to-Track Changes

In documentation work, it’s common to make small but frequent updates. Rebasing allows you to squash minor, related changes into a single commit, making the final history more concise and understandable.

For example, if you made three minor edits to a tutorial in separate commits, you can squash them into one meaningful commit during an interactive rebase. This way, your commit log doesn’t overwhelm reviewers with minor changes.

### Minimal Conflict During Collaboration

When you rebase your branch before integrating it into the main documentation, you’re updating your branch with the latest changes before finalizing your work. This means you have handled any conflicts proactively on your branch, rather than dealing with them during a merge. This helps reduce the chance of introducing new conflicts into the main branch.

## How to Rebase

Regular rebasing is useful when you just want to integrate the latest changes from the main branch into your working branch. This essentially applies commits on the tip of the base branch.

(1) Check out your feature branch:

```text
git checkout my-branch
```

(2) Update your main branch:

(3) Rebase your branch onto the main branch:

(4) Resolve any conflicts:

Git will pause and prompt you to resolve conflicts if any arise. Edit the conflicting files and mark them as resolved:

```text
git add <file>
git rebase --continue
```

(5) Push your changes:

```text
git push --force
```

### When to Avoid Rebase

While rebasing is useful for maintaining a clean history, it’s essential to avoid rebasing public or shared branches. Rebasing changes the commit history, which can cause confusion or disrupt collaborative work if others have already pulled your changes.
