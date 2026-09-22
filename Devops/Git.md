# Git & GitHub Notes

# What is SCM?
SCM stands for Source Code Management.
It used to track and manage the changes in software code.
It helps Developer to Collaborate, maintain code versions and ensure consistency across a project.

# Example
In production house there was dev1 and dev2 so both dev1 and dev2 used to communicate each other using a central server i.e., SVN
if dev1 has additional(program) functionalities and dev2 has subtraction(program) functionality but when it comes to share with each other it can only share from centralized system (SVN)
all things are depend on central server (SVN)

To solve it distributed version control system take place
in distributed version control system there is also dev1 and dev2 it also has same functionality as previous.
when it comes to communicate with each other they either do through distributed version control system and dev2 can pick it, or dev1 can create multiple copies of distributed version control system and called it DVCS2 similarly dev2 also creates multiple copies of it's picked DVCS.
so what DVCS advantages is in some cases if CVS goes down for some time the communication between dev1 and dev2 no longer existing. communication relying only on CVS
but in DVCS u can create multiple copies of main program.
and when it comes to changes in that program u can't do changes in main program instead u changes copied program. and saying dev2 to pick changes from copied ones.
and the terminology called as fork
what is fork? u create copies of whole program
(example.com (main program) example.fork (copied program))


If we lost our main program u still have it's copy to access it.
means we have multiple versions of our program and don't need to depend on single place.
and that advantage is provides DVCS.

# Difference Centralized Vesrion Control System (CVCS) vs Distributed Version Control System (DVCS).

### Introduction to Git?
Git is a **version control system** that enables efficient tracking of changes, branching, and collaboration among developerss. 

It is like a "save history" for your code — every time you save (commit), Git remembers exactly what changed, who changed it, and when. If something breaks, you can go back in time to an older, working version.

# Git Lifecycle 

1. Working Directory

This is where you actually create or modify files.
For example: vim app.py
After modifying the file: git status
This shows which files are modified, untracked, or ready to be committed.

2. Staging Area

Before committing, we select the changes that we want to include in the next commit.
git add app.py Or git add .

3. Local Repository

Now permanently save the staged changes in your local Git repository:
git commit -m "Added login functionality"
A commit creates a unique commit ID (hash) that represents that version of the code.
git add = select changes
git commit = save changes

4. Remote Repository

After committing locally, send your commits to a remote repository such as GitHub:
git push origin main

5. Pull Latest Changes

Before starting work or when you need the latest code:
git pull origin main
It basically gets changes from the remote repository and integrates them into your local branch.
Example: git clone https://github.com/user/project.git

cd project

Make changes
vim Dockerfile

Check changes
git status

Stage changes
git add Dockerfile

Save changes locally
git commit -m "Updated Dockerfile"

Send changes to GitHub
git push origin main

If another developer has pushed changes:
git pull origin main

Git Lifecycle is the process of managing code using Git. First, we make changes in the working directory. Then we use git add to move the required changes to the staging area. After that, git commit saves those changes in the local repository with a commit ID. Finally, git push sends the commits to a remote repository like GitHub. To get the latest changes from the remote repository, we use git pull. 
So the basic flow is Working Directory → Staging Area → Local Repository → Remote Repository.


### 2. What is GitHub?
Git and GitHub are **not the same thing**.
- **Git** = the tool that tracks changes in your code (works on your computer, no internet needed).
- **GitHub** = a website that hosts your Git projects online, so you can share code, collaborate with others, and back it up in the cloud.

Simple: Git is the engine, GitHub is the garage where you park and show off your car.

### 3. What is a repository (repo)?
A repository is just a **folder that Git is tracking**. It contains your files plus a hidden `.git` folder that stores the entire history of changes.

### 4. What's the difference between `git init` and `git clone`?
- `git init` — turns an existing folder on your computer into a Git repo (starts tracking from scratch).
- `git clone` — downloads a copy of a repo that already exists somewhere else (like GitHub) onto your computer.

### 5. What is the difference between `git add` and `git commit`?
- `git add` — puts your changed files into a "staging area" (like putting items in a shopping cart before checkout).
- `git commit` — actually saves those staged changes into Git's history (like completing the checkout).

### 6. What is `git status` used for?
It tells you what's currently happening in your repo — which files were changed, which are staged, and which are untracked. It's like checking your surroundings before you move.

### 7. What is `git push` and `git pull`?
- `git push` — sends your local commits up to GitHub (uploading).
- `git pull` — brings the latest changes from GitHub down to your computer (downloading + merging).

# git revert and git restore
git revert <commit-hash> = undoes the commited change by creating a new commit.

git restore <file-name> = restore files

### 8. What is a branch in Git?
A branch is like a **parallel version of your project**. The main branch (usually `main` or `master`) holds the stable code. When you want to try something new or build a feature without breaking the main code, you create a separate branch to work in.

### 9. What is `git merge`?
Merging takes the changes from one branch and combines them into another branch. For example, once your feature branch is done and tested, you merge it back into `main`.

### 10. What is a commit message and why does it matter?
It's a short note explaining what changes you made in that commit. Good commit messages (like "Fix login button bug" instead of "stuff") make it much easier for you and your team to understand project history later.

### 11. What is `.gitignore`?
A file where you list things you **don't** want Git to track — like log files, `node_modules`, passwords, or system files. Anything listed here gets ignored by Git.

### 12. What is a pull request (PR) on GitHub?
A pull request is a way of saying: "Hey, I made some changes in my branch — can someone review them before we merge them into the main project?" It's the standard way teams collaborate and review code on GitHub.

### 13. What is a fork?
Forking creates your **own personal copy** of someone else's repository on GitHub. You can make changes freely in your fork without affecting the original project, and later suggest your changes back via a pull request.

---

## INTERMEDIATE

### 14. What's the difference between `git merge` and `git rebase`?
Both combine changes from one branch into another, but differently:
- **Merge** keeps full history and creates a new "merge commit" showing where branches joined. History looks like a tree with branches.
- **Rebase** takes your commits and replays them on top of another branch, making history look like one straight line — cleaner, but it rewrites commit history.

Simple: Merge is like joining two roads with a roundabout (you can see both paths came together). Rebase is like moving your road so it looks like it was built straight from the other road all along.

### 15. What is a merge conflict, and how do you resolve it?
A conflict happens when Git can't automatically decide how to combine changes — usually because two people edited the **same line** of the same file differently. 

To fix it:

1. Git marks the conflicting section in the file with `<<<<<<<`, `=======`, `>>>>>>>`.

2. You manually edit the file to decide what the final version should look like.

3. You `git add` the fixed file and commit.

### 16. What is `git stash`?
It temporarily "shelves" your uncommitted changes so you can switch branches or pull updates without committing half-done work. Later, you run `git stash pop` to bring those changes back.

### 17. What's the difference between `git reset` and `git revert`?
- `git reset` — moves your branch pointer backward, effectively "undoing" commits. It can rewrite history (dangerous if already pushed/shared).
- `git revert` — creates a **new commit** that undoes the changes of a previous commit, without erasing history. Safer for shared/public branches.

### 18. What is `HEAD` in Git?
`HEAD` is just a pointer to whatever commit or branch you're currently "standing on." Most of the time it points to the latest commit of your current branch.

### 19. What is the difference between `git fetch` and `git pull`?
- `git fetch` — downloads new commits from GitHub but does **not** merge them into your current work. It just updates your knowledge of what's out there.
- `git pull` — does a fetch **and** automatically merges those changes into your current branch. (`git pull` = `git fetch` + `git merge`)

### 20. What is a remote in Git?
A remote is simply a saved link/address to a repo hosted elsewhere (usually GitHub). The default name for the main remote is usually `origin`.

### 21. What is `git cherry-pick`?
It lets you grab **one specific commit** from another branch and apply it to your current branch — without merging the whole branch. Useful when you only need one bug fix from somewhere else.

### 22. What are tags in Git, and why use them?
Tags are like bookmarks on specific commits, usually used to mark release versions (e.g., `v1.0.0`). Unlike branches, tags don't move once created.

### 23. What is the difference between a local and a remote branch?
- **Local branch** — exists only on your computer.
- **Remote branch** — exists on GitHub (or another server) and is usually referenced as `origin/branch-name`.

### 24. How do you undo the last commit but keep the changes?
```
git reset --soft HEAD~1
```
This removes the last commit but keeps your changes staged, ready to be re-committed.

### 25. What's the difference between `git diff` and `git log`?
- `git diff` — shows the actual line-by-line changes between files/commits.
- `git log` — shows the history of commits (who, when, what message) but not the line-by-line content changes.

---

## ADVANCED Notes

### 26. What are Git's internal objects (blob, tree, commit)?
Git stores data as objects, identified by a unique SHA-1 hash:
- **Blob** — the actual content of a file.
- **Tree** — represents a directory; it points to blobs and other trees.
- **Commit** — a snapshot pointing to a tree, plus metadata (author, message, parent commit).

Understanding this helps explain why Git is so fast and reliable — it's essentially a content-addressed filesystem, not a simple "diff tracker."

### 27. What is `git rebase -i` (interactive rebase) used for?
It lets you **rewrite commit history** before merging — you can combine (squash) multiple messy commits into one clean commit, reorder them, edit messages, or drop commits entirely. Commonly used to "clean up" a feature branch before opening a pull request.

### 28. What is `git reflog`?
It's like a **safety net** — a log of everywhere `HEAD` has pointed, even for commits that were deleted or reset away. If you accidentally lose a commit, `git reflog` can often help you recover it.

### 29. What is `git bisect`?
A debugging tool that uses **binary search** to find which commit introduced a bug. You mark a "good" commit and a "bad" commit, and Git automatically checks out commits in between, asking you "good or bad?" until it pinpoints the exact commit that broke things.

### 30. What are Git hooks?
Scripts that automatically run at certain points in the Git workflow — like right before a commit (`pre-commit`) or right after a push (`post-push`). Teams use them to enforce things like code linting, running tests, or checking commit message formats before allowing a commit/push.

### 31. What is a submodule in Git?
A way to include one Git repository **inside** another as a subfolder, while keeping its own separate history. Useful when your project depends on another repo (like a shared library) that's maintained separately.

### 32. What is the difference between Gitflow and trunk-based development?
- **Gitflow** — uses multiple long-living branches (`main`, `develop`, `feature/*`, `release/*`, `hotfix/*`). More structured, good for scheduled releases.
- **Trunk-based development** — everyone works off a single main branch with short-lived feature branches, merging frequently. Favored by teams doing continuous integration/deployment.

### 33. What happens internally when you run `git commit`?
Git takes everything in the staging area, creates a new **tree object** representing that snapshot, wraps it in a **commit object** with metadata (author, timestamp, message, and a pointer to the parent commit), and moves the branch pointer (and `HEAD`) to this new commit.

### 34. What's the difference between a fast-forward merge and a three-way merge?
- **Fast-forward** — happens when the target branch hasn't changed since you branched off; Git just moves the pointer forward, no new commit needed.
- **Three-way merge** — happens when both branches have diverged (new commits on both sides); Git looks at the common ancestor plus both branch tips to create a new merge commit.

### 35. How do you resolve a detached HEAD state?
A detached HEAD happens when you check out a specific commit instead of a branch — any new commits you make there aren't attached to a branch and can get lost. To fix it, either create a new branch from that point (`git checkout -b new-branch-name`) to save your work, or just check out an existing branch to go back to normal.

### 36. What are GitHub Actions?
GitHub's built-in **automation/CI-CD tool**. You write workflow files (YAML) that automatically run tasks — like testing code, building projects, or deploying — whenever something happens in the repo (e.g., on every push or pull request).

### 37. What is the difference between squash merge, merge commit, and rebase merge on GitHub pull requests?
- **Merge commit** — keeps all individual commits plus adds one merge commit. Full history preserved.
- **Squash and merge** — combines all commits from the PR into a single commit on the main branch. Cleaner history, but individual commit detail is lost.
- **Rebase and merge** — replays each commit from the PR onto the main branch individually, without a merge commit. Keeps a linear history.

### 38. How would you recover a deleted branch?
If you know the last commit hash of the deleted branch (findable via `git reflog`), you can recreate the branch with:
```
git checkout -b recovered-branch <commit-hash>
```

### 39. What is the difference between `git pull --rebase` and a normal `git pull`?
- Normal `git pull` merges incoming changes, potentially creating an extra merge commit.
- `git pull --rebase` replays your local commits on top of the newly fetched commits instead, keeping history linear and avoiding unnecessary merge commits.

### 40. How does Git know a file has changed (efficiently, without comparing every byte)?
Git doesn't compare full file contents every time. Instead, it uses **SHA-1 hashes** of file content and checks file metadata (like modification time) first as a quick filter. If a file's hash matches what's already stored, Git knows nothing changed — making status checks very fast even in huge repos.

---

## 💡 Quick Tips for the Interview
- If asked to explain something, use an **analogy first**, then the technical term — interviewers love clarity.
- Be ready to explain **why** you'd pick merge vs rebase, or reset vs revert — knowing the trade-offs matters more than memorizing commands.
- If you don't know something, it's fine to say: "I haven't used that in practice, but based on what I know, it should work like this..." — shows honesty and reasoning ability.
