# Introduction
## What is Git?
- Git is an **open-source version control system** known for its:
  - **Speed**
  - **Stability**
  - **Distributed collaboration model**
- Originally created in **2006** by *Linus Torvalds* to manage the Linux kernel.
- Today, Git has:
  - A **comprehensive feature set**
  - **Active development team**
  - Several **free hosting communities** like GitHub, GitLab, Bitbucket, etc.

## Introduction to Version Control

- **Definition**: Version control is a system that tracks changes to files over time, enabling collaboration and version management.

- **Key Benefits**:
  - Maintains a **history of changes**, allowing you to view or revert to earlier versions.
  - Facilitates **collaboration** by letting multiple people work on the same project simultaneously.
  - Tracks **who made what changes** and when, providing accountability.
  - Reduces risk by serving as a **backup system** for your code or files.

- **Types of Version Control**:
  - **Local Version Control**: Stores changes on a single machine. Simple but limited for collaboration.
  - **Centralized Version Control**: Uses a central server to store files and version history (e.g., SVN, CVS).
  - **Distributed Version Control**: Each user has a complete copy of the repository (e.g., Git, Mercurial).

- **Common Use Cases**:
  - Software development (code management).
  - Document versioning and collaborative editing.
  - Managing configuration files and scripts.

- **Popular Tools**:
  - Git, Mercurial, Subversion (SVN), CVS.
  - Hosting services like GitHub, GitLab, and Bitbucket simplify sharing and collaboration.

- **Why It’s Essential**:
  - Helps avoid overwriting others' work.
  - Enables parallel development.
  - Provides a safety net against accidental data loss or errors.

## Centralized vs. Distributed Version Control

### Centralized Version Control Systems (CVCS)
- **How It Works**:
  - A single **central repository** stores all project files and version history.
  - Developers pull files from the central server, make changes, and push them back.
- **Examples**: Subversion (SVN), CVS.
- **Key Features**:
  - **Single Point of Truth**: The central server holds all the data.
  - **Network Dependency**: You need to be connected to the server for most operations.
  - **Simple to Understand**: The workflow is straightforward for small teams.
- **Challenges**:
  - If the central server goes down, work halts for everyone.
  - Limited offline capabilities.

### Distributed Version Control Systems (DVCS)
- **How It Works**:
  - Each developer has a **complete copy** of the repository, including full version history.
  - Changes can be made offline and shared with others by syncing repositories.
- **Examples**: Git, Mercurial.
- **Key Features**:
  - **Decentralized Model**: No single point of failure since every developer has a full backup.
  - **Offline Work**: You can commit changes, view history, and work locally without a network.
  - **Collaboration**: Developers can push/pull changes to/from each other's repositories.
- **Advantages**:
  - Fast and reliable, as most operations are local.
  - Great for large teams and open-source projects.

## Design Philosophy of Git
- Git was designed with a focus on **distributed software development**, avoiding the limitations of centralized systems like SVN (Subversion) or CVS (Concurrent Versions Systems).

## Key Benefits of Git's Distributed Model

1. **Faster Commands**:
   - Since Git stores the repository locally, almost all actions are performed on the **local machine**, eliminating the need to communicate with a central server.
   - This leads to **faster commands** and the ability to **work offline** without workflow disruption.

2. **Stability**:
   - Git's distributed nature means each collaborator has a **backup** of the entire project.
   - This lowers the risk of **data loss** from server crashes or repository corruption, a common issue in centralized systems reliant on a single point of access.

3. **Isolated Environments**:
   - Every Git repository, whether **local or remote**, retains the **full history** of a project.
   - Having a complete and isolated environment allows users to experiment with **new features** before integrating them into the main project.

4. **Efficient Merging**:
   - Since each developer has their own local history, their development branches may diverge.
   - Git excels in handling **divergent histories**, making it **highly efficient** at **merging branches** and resolving conflicts between different lines of development.


# Git Components

## Four Key Components of a Git Repository
1. **The Working Directory**
2. **The Staging Area**
3. **Committed History**
4. **Development Branches**

---

### 1. The Working Directory
- **What It Is:**
  - The **working directory** is where you interact with your files during development.
  - It is where you **edit files**, **compile code**, and perform other tasks related to your project.
  - You can treat the working directory as a **normal folder** where you directly modify the contents of the project.

- **Git's Role:**
  - The working directory gives you access to Git’s features, enabling you to **record changes**, **alter** files, and **transfer** them using Git commands.
  - Git keeps track of any changes you make in this directory before committing them to the project’s history.

---

### 2. The Staging Area
- **What It Is:**
  - The **staging area** acts as an intermediary between the **working directory** and the **project history**.
  - It allows you to prepare and organize changes before committing them to the history.

- **Functionality:**
  - Instead of committing all changes at once, Git allows you to **group related changes** into a **changeset**.
  - Changes staged in this area are not part of the project’s history until they are committed.
  - This gives you control over which changes to include in your commit.

---

### 3. Committed History
- **What It Is:**
  - Once changes are staged, you can **commit** them to the project history.
  - A **commit** records the state of the repository at a particular point in time.

- **Safety of Commits:**
  - Commits are considered "safe" in the sense that **Git does not alter them automatically**.
  - However, it is possible to **manually rewrite the project history** (e.g., with rebase or amend operations).

---

### 4. Development Branches
- **What They Are:**
  - Branches allow you to **fork the project history** and develop multiple features in **parallel**.
  - A branch creates a divergent path for your work, enabling you to develop **independently** without disrupting the main project history.

- **Git Branches vs. Centralized Systems:**
  - Git branches are **lightweight**, **cheap to create**, and **simple to merge**.
  - Unlike centralized version control systems, **Git branches** are **easy to share** and manage.

- **Branching in Git:**
  - Git branches are commonly used for:
    - **Long-running features** with multiple contributors.
    - **Quick fixes** (e.g., 5-minute patches).
  - Many developers prefer to work in **dedicated topic branches**, keeping the main history branch (e.g., `main` or `master`) clean and reserved for **public releases**.

# Getting Started

## Step 1: Install Git and SSH

### 1. **Install Git**
```bash
sudo apt update
sudo apt install git
```

### 2. **Install OpenSSH**
- If OpenSSH is not already installed, use the following command:
```bash
sudo apt install openssh-client
```

---

## **Step 2: Set Up SSH for GitHub**

### 1. **Generate an SSH Key Pair**
- Run the following command to create an SSH key:
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
- The above step will ask for a *location* to store SSH and a *passphrase* for protection. You can leave the *location* as default by not providing one. 
- This will generate a public and private SSH key in the `~/.ssh/` directory.

### 2. **Add the SSH Key to the SSH Agent**
- Start the SSH agent:
```bash
eval "$(ssh-agent -s)"
```
- Add your SSH private key:
```bash
ssh-add ~/.ssh/id_ed25519
```

### 3. **Add the SSH Key to GitHub**
- Copy the public SSH key:
```bash
cat ~/.ssh/id_ed25519.pub
```
- Log in to your GitHub account, navigate to **Settings > SSH and GPG Keys**, and add the copied key.

---

## **Step 3: Test Your SSH Connection**
- Verify the SSH connection to GitHub:
```bash
ssh -T git@github.com
```
- If successful, you should see:
```
Hi <username>! You've successfully authenticated, but GitHub does not provide shell access.
```

---

## **Step 4: Set SSH as Default for All Repositories**
- To always use SSH when cloning or interacting with repositories:
```bash
$ git config --global url."git@github.com:".insteadOf "https://github.com/"
```
- This modifies the `~/.gitconifg` file: 
```
[url "git@github.com:"]
          insteadOf = https://github.com/
```

## **Step 5: Configure Git**

### 1. **Set User Information**
- Set your name and email, which will be recorded with your commits:
```bash
$ git config --global user.name "John Smith"
$ git config --global user.email "john@example.com"
```
- Use the `--global` flag to apply these settings globally or omit it for repository-specific settings.

### 2. **Set Your Preferred Editor**
- Configure the default text editor for Git (e.g., VS Code):
```bash
$ git config --global core.editor "code --wait"
```
- Replace `code --wait` with your preferred editor, like `nano` or `vim`. The `--wait` flag ensures Git waits for the editor to close before proceeding.

### 3. **Create Command Aliases**
- Simplify commonly used Git commands with aliases:
```bash
# Syntax:
$ git config [--global] alias.<alias_name> "<command>"

# Examples:
$ git config --global alias.st status
$ git config --global alias.pu "push -u origin main"
```
- For instance, use `git st` instead of `git status`.
- Here is how `~/.gitconfig` file would like after executing above commands:
```
[user]
	name = John Smith
	email = john@example.com
[core]
	editor = code --wait
[alias]
	st = status
	pu = push -u origin main
```

### 4. **Explore More Options**
- Run `git help config` in the terminal to see all available configuration options.


# **Initializing Repositories**

## **Creating a New Repository:**
  
- To initialize a repository, run the following:
```bash
# Syntax
$ git init <path>

# Examples
$ git init 
$ git init ~/Documents/SampleProject
```
- The `<path>` argument can be left blank to initialize the repository in the current directory.
 -  Git is minimally invasive; it only adds a `.git` directory in the root of your project folder.

## **Cloning an Existing Repository:**
- Instead of initializing a new repository, you can **clone** an existing Git repository:
```bash
# Syntax
$ git clone ssh://<user>@<host>/path/to/repo[.git]
$ git clone https://github.com/user/repo[.git]

# Examples
$ git clone ssh://git@github.com/rnaveensrinivas/GitRepo
$ git clone https://github.com/rnaveensrinivas/GitRepo
```
- This command will create a full copy of the repository, including its history, working directory, staging area, and branch structure. Changes won’t be visible to others until you push them to a public repository.

## Optional: Swtiching to use SSH Instead of HTTPS for Cloned Repositories

### 1. **Check Your Current Remote URL**
- You must in a repository that is associated with Github execute the following command. If you don't have one simply create a GitHub repository and clone it in local. 
- Run the following command:
```bash
$ git remote -v
```
- If the URL starts with `https://`, you need to change it to SSH.

### 2. **Update the Remote URL**
- Replace `username/repository` with your GitHub username and repository name:
```bash
$ git remote set-url origin git@github.com:username/repository.git
```

### 3. **Verify the Change**
- Check the updated remote URL:
```bash
$ git remote -v
```
- The output should now display `git@github.com` instead of `https://`.

### 4. **Push Changes Using SSH**
- Push your changes without being prompted for a username and password:
```bash
$ git push
```

### 5. **Optional: Set SSH as Default for All Repositories**
- To always use SSH when cloning or interacting with repositories:
```bash
$ git config --global url."git@github.com:".insteadOf "https://github.com/"
```

## Summary of Commands
| Command  | Description |
|----------|-------------|
| `git config --global user.name "name"`| Sets the global Git username for all repositories.|
| `git config --global user.email "email"`| Sets the global Git email for all repositories.|
| `git config --global core.editor "editor --wait"`| Sets the default text editor for Git commands requiring user input, like commit messages.|
| `git config --global alias.alias_name "command"`| Creates a shortcut (alias) for a Git command.|
| `git help config`| Displays help information about Git configuration options.|
| `git init`| Initializes a new Git repository in the current directory.|
| `git init path`| Initializes a new Git repository at the specified path.|
| `git clone ssh://<user>@<host>/path/to/repo[.git]`| Clones a repository from a remote server using an SSH URL with user and host details.|
| `git clone https://github.com/user/repo[.git]`| Clones a repository from GitHub or another remote server using an HTTPS URL.|
| `git remote -v`| Displays the list of remote repositories and their URLs.|
| `git remote url remote_name new_url`| Updates the URL for a specified remote repository.|

# Recording Changes

## **Git Snapshots vs. CVCS Diffs**
### **Git’s Snapshot Model**:
  - Git records **snapshots** of the entire project instead of just diffs between files (as in SVN or CVS).
  - Each **commit** in Git represents a complete snapshot of all project files at a given point in time, making Git faster and more reliable.
  - Unlike systems that record incremental changes, Git stores the full version of each file in a commit.
  
#### **Advantages:**
  - Faster access to file versions.
  - Avoids the need to regenerate file states when requested.

## **The Staging Area**

### **What is the Staging Area?**
- The **staging area** (also known as the **index**) is an intermediary between the **working directory** and the **committed history**.
- It allows you - The **staging area** (also known as the **index**) is an intermediary between the **working directory** and the **committed history**.
- It allows you to **stage** (select) changes for the next commit, ensuring you can commit only the desired changes and not the entire working directory at once.to **stage** (select) changes for the next commit, ensuring you can commit only the desired changes and not the entire working directory at once.

### **Staging Changes:**
- **Add stuff to the staging area** using:
```bash
# Syntax
$ git add <path>

# Examples
$ git add .
$ git add afolder/
$ git add f1
```

### **Stage file deletion** (without removing the file from the working directory):
```bash
# Syntax
$ git rm --cached <file>

# Examples
$ git rm --cached f1
$ git rm -r --cached afolder/
```
#### **What happens if you simply do `git rm` or `rm`?**
```bash
# trying to use "git rm" on staged f1
$ git rm f1
error: the following file has changes staged in the index:
    f1
(use --cached to keep the file, or -f to force removal)

# trying to use "git rm" on a tracked file afolder/f4
$ git rm afolder/f4
rm 'afolder/f4'
# removes the file from working directory and stages the removal


# trying to use "rm" on staged f1
$ rm f1

$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
  new file:   f1

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
  deleted:    f1
```

### Inspecting the Stage

#### Check the Status of the Repository:
- To view the state of your repository and see which files are staged, modified, or untracked, use:
```bash
$ git status
```

##### Example Output:
- **Changes to be committed**: Files staged for commit.
- **Changes not staged for commit**: Modified files that are not yet staged.
- **Untracked files**: Files in the working directory that are not part of the repository.
```bash
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   f1

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   afolder/f3

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	f2
```


#### **Diffs:**
- To see **unstaged changes** (changes in the working directory):
```bash
# Syntax 
$ git diff

# Example
$ git diff
diff --git a/afolder/f3 b/afolder/f3
index e69de29..3b18e51 100644
--- a/afolder/f3
+++ b/afolder/f3
@@ -0,0 +1 @@
+hello world
```

- To see **staged changes** (changes in the staging area):
```bash
# Syntax
$ git diff --cached

# Example
$ git diff --cached
diff --git a/f1 b/f1
index e69de29..3b18e51 100644
--- a/f1
+++ b/f1
@@ -0,0 +1 @@
+hello world
```

## **Commits**

### **What is a Commit?**
- A **commit** is a snapshot of your project at a specific point in time, and it serves as an atomic unit in Git's version control.
- Each commit contains:
  - The **snapshot** of the entire project.
  - **Author information** (name and email).
  - The **commit message**.
  - A **unique SHA-1 checksum** that ensures the commit cannot be unintentionally altered.

### **Commit Process:**
- **Commit the staged snapshot** to the repository history:
```bash
$ git commit
```
- You'll be prompted to provide a **commit message** in a text editor.

### **Commit Message Format:**
- **First line (summary)**: A brief description (50 characters or less).
- **Second line**: Blank line.
- **Following lines**: A detailed description of changes, reasons, or relevant ticket numbers.

Example:
```plaintext
Fixed bug in user authentication

Detailed fix for user authentication issues, including validation errors
and user session management.
```
### **Commiting using options**
- Commiting without opening default text editor.
```bash
# Sytnax
$ git commit -m "commit message"

# Example
$ git commit -m "This is a commit message"
[master (root-commit) cbd9be4] This is a commit message
1 file changed, 0 insertions(+), 0 deletions(-)
create mode 100644 afile.txt
```

### **Inspecting Commits**

#### **View Commit History:**
- To see the list of commits in the current branch:
```bash
# Syntax
$ git log

# Example
$ git log
commit cbd9be4bb54c7573ff55d8826d8b1ea7582a2d0a (HEAD -> master)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 17:56:52 2024 +0530

    commit message
```

#### **Useful Options:**
- **Single-line log** (brief):
```bash
# Syntax
$ git log --oneline

# Example
$ git log --oneline
cbd9be4 (HEAD -> master) commit message
```

- **Log for a specific file**:
```bash
# Syntax
$ git log [--oneline] <file>

# Examples
$ git log afile.txt
commit cbd9be4bb54c7573ff55d8826d8b1ea7582a2d0a (HEAD -> master)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 17:56:52 2024 +0530

    commit message

# Example
$ git log --oneline afile.txt
cbd9be4 (HEAD -> master) commit message

```

- **Log for a specific range of commits**:
- `<since>` commit is excluded and `<until>` commit is included. 
```bash
# Syntax
$ git log <since>..<until>

# Examples
$ git log
commit 169223b27b5039d1d69b83889dd14e776891e9a1 (HEAD -> master)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:04:00 2024 +0530

    added some files in afolder

commit e09fdab287149a6c6a4c176b8c4a40df15284abd
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:03:24 2024 +0530

    changed file names

commit cbd9be4bb54c7573ff55d8826d8b1ea7582a2d0a
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 17:56:52 2024 +0530

    commit message

# cbd9be4 is excluded but 169223b is included.
$ git log cbd9be4..169223b
commit 169223b27b5039d1d69b83889dd14e776891e9a1 (HEAD -> master)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:04:00 2024 +0530

    added some files in afolder

commit e09fdab287149a6c6a4c176b8c4a40df15284abd
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:03:24 2024 +0530

    changed file names

# e09fdab is excluded but 169223b is included.
$ git log e09fdab..169223b
commit 169223b27b5039d1d69b83889dd14e776891e9a1 (HEAD -> master)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:04:00 2024 +0530

    added some files in afolder

```


- **Display a diffstat** (changes made in each commit):
```bash
# Syntax
$ git log --stat

# Example
$ git log --stat
commit 169223b27b5039d1d69b83889dd14e776891e9a1 (HEAD -> master)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:04:00 2024 +0530

    added some files in afolder

afolder/f3 | 0
afolder/f4 | 0
2 files changed, 0 insertions(+), 0 deletions(-)

commit e09fdab287149a6c6a4c176b8c4a40df15284abd
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:03:24 2024 +0530

    changed file names

a => afile.txt | 0
afolder/f1     | 0
afolder/f2     | 0
3 files changed, 0 insertions(+), 0 deletions(-)

commit cbd9be4bb54c7573ff55d8826d8b1ea7582a2d0a
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 17:56:52 2024 +0530

    commit message

a | 0
1 file changed, 0 insertions(+), 0 deletions(-)

```

#### **Visualizing History:**
- Use `gitk` to visualize the commit history graphically (available as a separate program).
```bash
$ gitk
```

## **Tagging Commits**

### **What are Tags?**
- Tags are **pointers** to specific commits, useful for marking important points in the project’s history, such as release versions.


### **Creating a Tag**  
* To create a lightweight tag on the commit you are sitting on:  
```bash
# Syntax
$ git tag <tag_name>

# Example
$ git tag v1.0

# notice the end of commit 169223b
$ git log
commit 169223b27b5039d1d69b83889dd14e776891e9a1 (HEAD -> master, tag: v1.0)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:04:00 2024 +0530

    added some files in afolder

commit e09fdab287149a6c6a4c176b8c4a40df15284abd
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:03:24 2024 +0530

    changed file names

commit cbd9be4bb54c7573ff55d8826d8b1ea7582a2d0a
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 17:56:52 2024 +0530

    commit message
```
* Adding a commit and printing the log, we can see tag stays behind.

```bash
$ git log
commit 8325a85452c5f8c2d2c6559e2cc055a1cce116ac (HEAD -> master)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:19:52 2024 +0530

    changed file name

commit 169223b27b5039d1d69b83889dd14e776891e9a1 (tag: v1.0)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:04:00 2024 +0530

    added some files in afolder

commit e09fdab287149a6c6a4c176b8c4a40df15284abd
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:03:24 2024 +0530

    changed file names

commit cbd9be4bb54c7573ff55d8826d8b1ea7582a2d0a
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 17:56:52 2024 +0530

    commit message
```

* To create an annotated tag with a message:  
```bash
# Syntax
$ git tag -a <tag_name> -m "Tag Message"

# Example
$ git tag -a v2.0 -m "Initial release"
$ git log
commit 8325a85452c5f8c2d2c6559e2cc055a1cce116ac (HEAD -> master, tag: v2.0)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:19:52 2024 +0530

    changed file name

commit 169223b27b5039d1d69b83889dd14e776891e9a1 (tag: v1.0)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:04:00 2024 +0530

    added some files in afolder

commit e09fdab287149a6c6a4c176b8c4a40df15284abd
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:03:24 2024 +0530

    changed file names

commit cbd9be4bb54c7573ff55d8826d8b1ea7582a2d0a
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 17:56:52 2024 +0530

    commit message
```

### **Listing Tags**  
* To see all tags in the repository:  
```bash
# Syntax
$ git tag

# Example
$ git tag
v1.0
v2.0
```

### **Pushing Tags to Remote**  
* By default, tags are not pushed to remote. Push a specific tag:  
```bash
# Syntax 
$ git push origin <tag_name>
```

To push all tags:  
```bash
# Syntax
$ git push --tags
```

### **Viewing a Tag**  
* To see details of a tag:  
```bash
# Syntax
$ git show <tag_name>
```
#### Examples

* Normal tag
```bash
$ git show v1.0
commit 169223b27b5039d1d69b83889dd14e776891e9a1 (tag: v1.0)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:04:00 2024 +0530

    added some files in afolder

diff --git a/afolder/f3 b/afolder/f3
new file mode 100644
index 0000000..e69de29
diff --git a/afolder/f4 b/afolder/f4
new file mode 100644
index 0000000..e69de29
```

* Annotated tag
```bash
$ git show v2.0
tag v2.0
Tagger: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:24:26 2024 +0530

Initial release

commit 8325a85452c5f8c2d2c6559e2cc055a1cce116ac (HEAD -> master, tag: v2.0)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:19:52 2024 +0530

    changed file name

diff --git a/afile.txt b/f1
similarity index 100%
rename from afile.txt
rename to f1
```

### **Using Tags for Checkout**  
* To checkout a specific tag (in a detached HEAD state):  
```bash
# Syntax
$ git checkout <tag_name>

# Example
$ git checkout v1.0 
Note: switching to 'v1.0'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 169223b added some files in afolder
```

## Summary of Commands:
| Command                               | Description                                                                                         |
|---------------------------------------|-----------------------------------------------------------------------------------------------------|
| `git add`                             | Stages all changes in the working directory for the next commit.                                   |
| `git add file/folder`                 | Stages specific files or folders for the next commit.                                              |
| `git rm`                              | Removes files from the working directory and stages the deletion for the next commit.             |
| `git rm --cached file`                | Removes a file from the staging area without deleting it from the working directory.              |
| `git rm -r --cached folder`           | Removes a folder from the staging area without deleting it from the working directory.            |
| `git status`                          | Shows the status of the working directory and staging area, listing changes to be committed.      |
| `git diff`                            | Displays unstaged changes in the working directory.                                               |
| `git diff --cached`                   | Displays changes staged for the next commit.                                                      |
| `git commit`                          | Commits staged changes to the repository.                                                         |
| `git commit -m "commit message"`      | Commits staged changes with a descriptive message in a single step.                               |
| `git log`                             | Displays the commit history of the repository.                                                    |
| `git log --oneline`                   | Shows a concise commit history with one commit per line.                                          |
| `git log --oneline file/folder`       | Shows a concise commit history for a specific file or folder.                                     |
| `git log <since>..<until>`            | Displays commits between two references (e.g., tags, branches), with `<since>` being exclusive.    |
| `git log --stat`                      | Shows commit history along with a summary of changes made in each commit.                         |
| `git tag tag_name`                    | Creates a lightweight tag for the current commit.                                                 |
| `git tag -a tag_name -m "tag message"` | Creates an annotated tag with a message for the current commit.                                   |
| `git tag`                             | Lists all tags in the repository.                                                                 |
| `git push origin tag_name`            | Pushes a specific tag to the remote repository.                                                   |
| `git push --tags`                     | Pushes all tags to the remote repository.                                                         |
| `git show tag_name`                   | Displays details of a specific tag, including the commit it references.                           |
| `git checkout tag_name`               | Checks out a specific tag, detaching the HEAD to a read-only state.                               |

# Undoing Changes

## **Importance of Undoing:**
- Undoing changes allows you to correct mistakes or experiments without fear of breaking the code.
- Git provides tools to undo changes at different stages: working directory, staging area, and commits.

## **Undoing can mean:**
  - Undo changes in the **working directory**.
  - Undo changes in the **staging area**.
  - Undo an **entire commit**.

## **Undoing in the Working Directory**

### **Reset to the Last Commit:**
- To discard all uncommitted changes (both in working directory and staging area), use:
```bash
# Syntax
$ git reset --hard HEAD

# Example
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	deleted:    afolder/f4
	modified:   f1

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   afolder/f3

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	commands
	f2

# Reseting working directory and staging area to most recent commit
$ git reset --hard HEAD
HEAD is now at 8325a85 changed file name

$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	commands
	f2

nothing added to commit but untracked files present (use "git add" to track)
```
- `git reset --hard HEAD` resets the working directory and staging area to the state of the **most recent commit** (HEAD).
* Since Git doesn't store untracked files, it does nothing to them. 
* To remove untracked files, use: 
```bash
# Syntax
$ git clean -f

# Example
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	commands
	f2

nothing added to commit but untracked files present (use "git add" to track)

# Clearning untracked files
$ git clean -f
Removing commands
Removing f2

$ git status
On branch master
nothing to commit, working tree clean
```
- `git clean -f` removes **untracked files** (files that Git is not tracking).
- The **-f** flag is required to force deletion of untracked files.

### **Undo Changes to a Specific File:**
- To revert a single file (file could be in **working directory** or **staging area**) to the version from the last commit:
```bash
# Syntax
$ git checkout HEAD <file>

# Example
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   afolder/f2
	modified:   f1

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	f

no changes added to commit (use "git add" and/or "git commit -a")

# Reverting f1 to previous commit state
$ git checkout HEAD f1
Updated 1 path from dd3c5af

$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   afolder/f2

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	f

no changes added to commit (use "git add" and/or "git commit -a")
```

- This will replace the file in your working directory with the version from **HEAD**, without altering the project history.

## **Undoing in the Staging Area**

### **Unstage Changes:**
- If you accidentally stage a file, you can unstage it with:
```bash
$ git reset HEAD <file>
```

- This command removes the file from the staging area but leaves your working directory unchanged, resulting in an unstaged modification.

## **Undoing Commits**

### **Two Ways to Undo Commits:**
1. **Reset**: Removes a commit entirely from the history.
2. **Revert**: Creates a new commit that undoes the changes of a previous commit.

### **1. Resetting Commits:**
- **git reset** is used to move the `HEAD` reference and remove a commit from the history:
#### Reseting the most recent commit
```bash
# Syntax
$ git reset HEAD~<NUM> 

# Example
$ git log
commit bdab6c6e81cb82dd603db485c5e41c564a210dde (HEAD -> master)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sun Dec 29 05:37:31 2024 +0530

    bad commit

commit 8325a85452c5f8c2d2c6559e2cc055a1cce116ac (tag: v2.0)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:19:52 2024 +0530

    changed file name

commit 169223b27b5039d1d69b83889dd14e776891e9a1 (tag: v1.0)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:04:00 2024 +0530

    added some files in afolder

... 

# Undoing the previous commit
$ git reset HEAD~1
Unstaged changes after reset:
M	afolder/f2

$ git log
commit 8325a85452c5f8c2d2c6559e2cc055a1cce116ac (HEAD -> master, tag: v2.0)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:19:52 2024 +0530

    changed file name

commit 169223b27b5039d1d69b83889dd14e776891e9a1 (tag: v1.0)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:04:00 2024 +0530

    added some files in afolder
```

- `HEAD~1` refers to the commit before the most recent commit (`HEAD`). This command moves `HEAD` backward, removing the most recent commit.
- We can move many commits back by using `HEAD~<NUM>` eg `HEAD~3`, to move three commits backward. 

---

#### Resetting to a Previous Commit in Git

To reset your repository to a specific commit in the past, follow these steps. Consider the current commit history:

```bash
$ git log
commit 173d36dddfc4c474ac38135f95dd00bb377ed9e8 (HEAD -> master)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sun Dec 29 05:58:47 2024 +0530

    updated f1
    
    fixed a typo in f1

commit 442f724d702b6ac5199bfe80de8e08009b737019
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sun Dec 29 05:47:13 2024 +0530

    Revert "bad commit"
    
    This reverts commit e4a9e9928f1648638e3292f5d0a36934ff18ecd6.
    
    Changed the file by mistake

commit e4a9e9928f1648638e3292f5d0a36934ff18ecd6
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sun Dec 29 05:42:51 2024 +0530

    bad commit

commit 8325a85452c5f8c2d2c6559e2cc055a1cce116ac (tag: v2.0)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:19:52 2024 +0530

    changed file name

commit 169223b27b5039d1d69b83889dd14e776891e9a1 (tag: v1.0)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:04:00 2024 +0530

    added some files in afolder
```

We want to **reset the repository to `tag: v2.0`**, removing all commits after it. There are two ways to accomplish this:

---

##### Option 1: `git reset --soft`
```bash
$ git reset --soft 8325a854   # Or git reset --soft v2.0
```

- **What it does**:
  - Resets the repository to the specified commit (`tag: v2.0` in this case).
  - Deletes all commits made after `tag: v2.0`.
  - **Preserves changes** introduced by deleted commits and stages them for the next commit.

- **Example**:
  ```bash
  $ git reset --soft 8325a854

  $ git log
  commit 8325a85452c5f8c2d2c6559e2cc055a1cce116ac (HEAD -> master, tag: v2.0)
  Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
  Date:   Sat Dec 28 18:19:52 2024 +0530

      changed file name

  commit 169223b27b5039d1d69b83889dd14e776891e9a1 (tag: v1.0)
  Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
  Date:   Sat Dec 28 18:04:00 2024 +0530

      added some files in afolder

  # Files from deleted commits are now staged
  $ git status
  On branch master
  Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
    modified:   f1
  ```

---

##### Option 2: `git reset --hard`
```bash
$ git reset --hard 8325a854   # Or git reset --hard v2.0
```

- **What it does**:
  - Resets the repository to the specified commit (`tag: v2.0` in this case).
  - Deletes all commits made after `tag: v2.0`.
  - **Discards all changes** introduced by deleted commits without saving them.

- **Example**:
  ```bash
  $ git reset --hard 8325a854
  HEAD is now at 8325a85 changed file name
  ```

---

### ⚠️ Important Notes

1. **Resetting rewrites history**:
   - This can lead to issues in **collaborative projects**, especially if the commits have been shared with others.

2. **Safe Use Cases**:
   - It’s safe to reset **private commits** (commits only in your local repository).
   - Avoid resetting commits that others rely on to prevent conflicts.

--- 

### **2. Reverting Commits:**
- **git revert** is a safer alternative to `git reset`, especially in public repositories:
```bash
# Syntax
$ git revert <commit-id>

# Example
$ git log
commit e4a9e9928f1648638e3292f5d0a36934ff18ecd6 (HEAD -> master)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sun Dec 29 05:42:51 2024 +0530

    bad commit

commit 8325a85452c5f8c2d2c6559e2cc055a1cce116ac (tag: v2.0)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:19:52 2024 +0530

    changed file name

commit 169223b27b5039d1d69b83889dd14e776891e9a1 (tag: v1.0)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:04:00 2024 +0530

... 

# Reverting
$ git revert HEAD
hint: Waiting for your editor to close the file... 
```

```bash
Revert "bad commit"

This reverts commit e4a9e9928f1648638e3292f5d0a36934ff18ecd6.

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# On branch master
# Changes to be committed:
#	new file:   afolder/f2
#
Changeg the file by mistake
```
* type the comment and close the file.
* As soon as you do that, the  `hint:` goes away.
```bash
$ git revert HEAD
[master 442f724] Revert "bad commit"
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 afolder/f2

$ git log
commit 442f724d702b6ac5199bfe80de8e08009b737019 (HEAD -> master)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sun Dec 29 05:47:13 2024 +0530

    Revert "bad commit"
    
    This reverts commit e4a9e9928f1648638e3292f5d0a36934ff18ecd6.
    
    Changeg the file by mistake

commit e4a9e9928f1648638e3292f5d0a36934ff18ecd6
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sun Dec 29 05:42:51 2024 +0530

    bad commit

commit 8325a85452c5f8c2d2c6559e2cc055a1cce116ac (tag: v2.0)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:19:52 2024 +0530

    changed file name

commit 169223b27b5039d1d69b83889dd14e776891e9a1 (tag: v1.0)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:04:00 2024 +0530

    added some files in afolder
```

- **Ideal for public repositories**, as it doesn't rewrite history but introduces a new commit that "cancels out" previous changes.


## **Amending Commits**

### **Amend the Most Recent Commit:**
- If you want to modify the most recent commit (e.g., to add forgotten changes or fix the commit message), use:
```bash
# Syntax
$ git commit --amend

# Example
$ ls
afolder  f1

$ echo "hello wordl" > f1

$ git add . ; git commit -m "updated f1"
[master 53932d1] updated f1
 1 file changed, 1 insertion(+)

$ git log
commit 53932d1315f14a3a0bff75f24918848fc71b598c (HEAD -> master)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sun Dec 29 05:58:47 2024 +0530

    updated f1

commit 442f724d702b6ac5199bfe80de8e08009b737019
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sun Dec 29 05:47:13 2024 +0530

    Revert "bad commit"
    
    This reverts commit e4a9e9928f1648638e3292f5d0a36934ff18ecd6.
    
    Changeg the file by mistake

commit e4a9e9928f1648638e3292f5d0a36934ff18ecd6
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sun Dec 29 05:42:51 2024 +0530

    bad commit

commit 8325a85452c5f8c2d2c6559e2cc055a1cce116ac (tag: v2.0)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:19:52 2024 +0530

    changed file name

$ echo "hello world" > f1
$ git add . ; git commit --amend
hint: Waiting for your editor to close the file... 
```
* opens COMMIT_EDITOR file
```bash
updated f1

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# Date:      Sun Dec 29 05:58:47 2024 +0530
#
# On branch master
# Changes to be committed:
#	modified:   f1
#
fixed a typo in f1
```
* As soon as you close the file, 
```bash
$ git add . ; git commit --amend
[master 173d36d] updated f1
 Date: Sun Dec 29 05:58:47 2024 +0530
 1 file changed, 1 insertion(+)

$ git log
commit 173d36dddfc4c474ac38135f95dd00bb377ed9e8 (HEAD -> master)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sun Dec 29 05:58:47 2024 +0530

    updated f1
    
    fixed a typo in f1

commit 442f724d702b6ac5199bfe80de8e08009b737019
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sun Dec 29 05:47:13 2024 +0530

    Revert "bad commit"
    
    This reverts commit e4a9e9928f1648638e3292f5d0a36934ff18ecd6.
    
    Changeg the file by mistake

commit e4a9e9928f1648638e3292f5d0a36934ff18ecd6
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sun Dec 29 05:42:51 2024 +0530

    bad commit

commit 8325a85452c5f8c2d2c6559e2cc055a1cce116ac (tag: v2.0)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:19:52 2024 +0530

    changed file name
...
```

- This replaces the previous commit with a new one, which is useful if you need to tweak the latest commit without creating a new one.

- **Caution**: This also rewrites history, so avoid amending commits that have already been shared with others.

## Summary of commands

| **Command**| **Description**|
|------------|----------------|
| `git reset --hard HEAD`| Resets the working directory to the state of the last commit.|
| `git clean -f`| Deletes untracked files from the working directory.|
| `git checkout HEAD <file>`| Reverts a specific file to its state in the last commit.|
| `git reset HEAD <file>`| Removes a file from the staging area, leaving its changes in the working directory. |
| `git reset HEAD~1`| Removes the last commit from history and keeps its changes in the working directory. |
| `git reset --hard <commit-id>`| Resets to a specific commit, discarding all changes after it.|
| `git reset --soft <commit-id>`| Resets to a specific commit, keeping changes staged but removing subsequent commits. |
| `git revert <commit-id>`| Creates a new commit that reverses the changes made by a specific commit.|
| `git commit --amend`| Edits the most recent commit message or adds changes to it.|


# Branches

Branches in Git allow you to create multiple development paths, enabling parallel work on different versions of a project. When you create a new branch, you essentially get a new environment for working, including an isolated working directory, staging area, and project history.

## Manipulating Branches

### Listing Branches  
You can view all your branches with the `git branch` command, which shows the current branch with an asterisk next to it:
```bash
# Syntax
$ git branch

# Example
$ git branch
* master
```

### Creating Branches
Create a new branch using the command:
```bash
# Syntax
$ git branch <name>

# Example
$ git branch sample_branch
$ git branch
* master
  sample_branch
```
This creates a new branch that points to the current commit, but it **does not automatically switch to it**.

### Deleting Branches
To delete a branch, use:
```bash
# Syntax
$ git branch -d <name>

# Example
$ git branch -d sample_branch 
Deleted branch sample_branch (was 8325a85).
```

If the branch has unmerged commits, Git will prevent the deletion to avoid data loss. You can force deletion with:
```bash
$ git branch -D <name>
```

### Checking Out Branches
To switch between branches, use the `git checkout` or `git switch` command:
```bash
# Syntax
$ git checkout <branch>
$ git switch <branch>

# Example
$ git checkout sample_branch 
Switched to branch 'sample_branch'

$ git switch sample_branch 
Switched to branch 'sample_branch'
```

### Creating and Checking out Simulataneously

#### 1. `git checkout -b <new-branch-name>`

- **Function:** 
  - Creates a new branch with the specified name.
  - Automatically switches the working directory to this new branch.

- **Usage Example:**
  ```bash
  $ git checkout -b feature/login
  ```
  This command:
  - Creates a new branch called `feature/login`.
  - Switches to the `feature/login` branch.

- **Behind the scenes:**
  - Equivalent to running:
    ```bash
    $ git branch <new-branch-name>
    $ git checkout <new-branch-name>
    ```
  - This two-step process (create and switch) is combined into one with the `-b` option.

#### 2. `git switch -c <new-branch-name>`

- **Function:** 
  - A newer and more intuitive command introduced in Git 2.23 (released in August 2019).
  - Similar to `git checkout -b`, it creates and switches to a new branch in a single step.

- **Usage Example:**
  ```bash
  $ git switch -c feature/login
  ```
  This command does the same as `git checkout -b feature/login`.

- **Why `git switch`?**
  - `git switch` was introduced to separate branch-related operations from file-related ones.
  - Makes it clear that you’re working with branches and not modifying files in the working directory.

#### When to Use Which?

- **If you prefer older commands or are using an older version of Git (< 2.23):**
  Use `git checkout -b`.

- **If you're using Git 2.23 or later and prefer clarity:**
  Use `git switch -c`.

#### Key Notes:

1. **Naming the branch:**
   Ensure your branch name is descriptive and relevant to the work you’ll be doing on it, e.g., `bugfix/payment`, `feature/signup`, etc.

2. **Branch creation context:**
   - The new branch is created from the **current branch’s HEAD**. If you want to create it from a different branch, you must first switch to that branch or use `git switch`/`checkout` with additional options.

3. **Default branch movement:**
   By default, branches are based on the `HEAD` of your current branch unless you specify a different base.


### Detached HEADs
A detached HEAD occurs when you check out a specific commit or tag rather than a branch. In this state, any new commits won’t belong to a branch and may be lost when switching branches. 
```bash
# Background
$ git log
commit 8325a85452c5f8c2d2c6559e2cc055a1cce116ac (HEAD -> sample_branch, tag: v2.0, master)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:19:52 2024 +0530

    changed file name

commit 169223b27b5039d1d69b83889dd14e776891e9a1 (tag: v1.0)
Author: rnaveensrinivas <rnaveensrinivas@gmail.com>
Date:   Sat Dec 28 18:04:00 2024 +0530

    added some files in afolder

...

# Checking out tag v1.0, we are warned!
$ git checkout v1.0
Note: switching to 'v1.0'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 169223b added some files in afolder
```

You can create a new branch from this state with:
```bash
$ git checkout -b <new-branch-name>
# or
$ git switch -c <new-branch-name>
```

---

## Merging Branches

Merging is used to combine changes from one branch into another. The general process involves two steps:

```bash
$ git checkout <branch_you_want_other_branch_to_merge_into>
$ git merge <other_branch_name>
```

This tells Git to merge the changes from `<other_branch_name>` into the branch you currently have checked out.

Internally git manages merging in two ways: 
1. **Fast-forward Merge**
2. **3-way Merge**
---

### 1. Fast-forward Merge

A fast-forward merge happens when there have been no new commits on the target branch since the branch was created. Git simply moves the branch pointer forward to include the commits from the other branch.

#### Example:

1. Assume the following branch structure:
   ```
   * Commit C (feature)
   |
   * Commit B
   |
   * Commit A (main)
   ```
   - `main` is the target branch.
   - `feature` is the branch to merge.

2. Commands:
   ```bash
   $ git checkout main
   $ git merge feature
   ```

3. Resulting branch structure:
   ```
   * Commit C (main, feature)
   |
   * Commit B
   |
   * Commit A
   ```
   The `main` branch now includes all commits from `feature`, and the `feature` branch pointer fast-forwards to the same commit as `main`.

---

### 2. Three-way Merge

A 3-way merge is required when the two branches have diverged, meaning both branches have new commits. Git uses the **common ancestor** of both branches and the changes on each branch to create a new **merge commit**.

#### Example:

1. Assume the following branch structure:
   ```
   (feature) D *          * Commit C (main)
                \        /
                 * Commit B
                 |
                 * Commit A
   ```
   - Both `main` and `feature` have unique commits (`C` and `D`, respectively).

2. Commands:
   ```bash
   $ git checkout main
   $ git merge feature
   ```

3. Resulting branch structure:
   ```
                  * Merge Commit (main)
                /        \
   (feature) D *          * Commit C
                \        /
                 * Commit B
                 |
                 * Commit A
   ```
   A **merge commit** is created to combine the changes from both branches.

---

### How to Resolve Merge Conflicts

If there are conflicting changes in the files between the two branches, Git will pause the merge and mark the conflicting files. You’ll need to manually resolve it by editing the file.

1. Identify conflicts:
   ```bash
   $ git status
   ```
   Conflicting files will be listed with the status **both modified**.

2. Open the conflicting files and resolve conflicts:
   - Git marks conflicts in the file like this:
     ```diff
     <<<<<<< HEAD
     Changes from the current branch
     =======
     Changes from the branch being merged
     >>>>>>> <other_branch_name>
     ```
   - Edit the file to combine or choose the appropriate changes.

3. After fixing the conflict, stage the file with
   ```bash
   $ git add <conflicted_file>
   ```

4. Complete the merge:
   ```bash
   $ git commit
   ```

---

### Summary of Merge Strategies

| **Merge Type**| **When It Happens**| **Result**|
|---------------|--------------------|-----------|
| **Fast-forward Merge**  | When the target branch has no new commits since branching.| Moves the branch pointer forward, no new commit is created.|
| **3-way Merge**| When both branches have diverged with new commits.| Creates a new merge commit to combine changes.|
| **Merge Conflicts**| When changes in the branches conflict and cannot be automatically merged. | Requires manual resolution before completing the merge.|

## Rebasing

### What is Rebasing?
- Rebasing is the process of moving a branch to a new base.
- It helps in manually organizing branches, creating a cleaner and more linear history.

### Basic Rebasing Workflow
1. Check out the branch you want to rebase:
```bash
$ git checkout some-feature
```
2. Rebase onto another branch:
```bash
$ git rebase master
```
- This moves the `some-feature` branch onto the tip of `master`, creating a linear history.

### Comparison: Rebase vs. Merge
#### Rebase
- Creates a linear history by moving the branch onto the new base.
- No additional merge commits are created.
- Example:
```
* Commit D (some-feature)
* Commit C (master)
* Commit B
* Commit A
```
#### Merge
- Combines branches using a merge commit.
- May result in a cluttered history if done repeatedly.
- Example:
```
  * Merge Commit
  |\
  | * Commit D (some-feature)
  |/
  * Commit C (master)
  * Commit B
  * Commit A
```
### Advantages of Rebasing
- Creates a clean and linear history.
- Eliminates superfluous merge commits.
- Enhances readability and navigability of the project history.

### Disadvantages of Rebasing
- **History Rewriting**:
  - Rebasing creates new commits with different IDs, effectively destroying the original commits.
  - This can lead to issues in collaborative workflows if others are working on the same branch.

### Interactive Rebasing  

Imagine your Git repository has the following commit history:  

```
* 6ac8a9f Second commit for a new feature
* 58dec2a First commit for a new feature
* a1f76d0 Latest commit on master
* b3c19e1 Older commit on master
```

You want to **clean up your feature branch** so that the two commits are combined into one with a meaningful message.  

---

#### Step-by-Step Workflow  

##### 1. Start Interactive Rebase
Run the following command:  
```bash
$ git rebase -i master
```  
This means:  
- "Rebase my feature branch commits (`6ac8a9f` and `58dec2a`) onto the `master` branch (`a1f76d0`)."

---

##### 2. Interactive Rebase Prompt
Git opens an editor with the list of commits from the feature branch:  
```plaintext
pick 58dec2a First commit for new feature
pick 6ac8a9f Second commit for new feature
```  
Each line represents a commit and begins with a command (`pick` by default).  

---

##### 3. Modify the Rebase Instructions
You decide to combine the two commits into one. Change the second `pick` to `squash`:  
```plaintext
pick 58dec2a First commit for new feature
squash 6ac8a9f Second commit for new feature
```  
Explanation:  
- `pick`: Keep the first commit as is.  
- `squash`: Combine the changes from the second commit into the first.  

---

##### 4. Edit the Commit Message
Git will prompt you to write a new commit message for the combined commit. For example:  
```plaintext
# This is a combination of 2 commits.
# The first commit's message is:
First commit for new feature

# The following commit message will be discarded:
Second commit for new feature

# Please write a new message for the commit:
Added a new feature with necessary updates
```  

---

##### 5. Resulting Commit History
After completing the rebase, the history looks cleaner:  
```plaintext
* d9e72f3 Added a new feature with necessary updates
* a1f76d0 Latest commit on master
* b3c19e1 Older commit on master
```  
- The two commits are now a single commit with a meaningful message.  

---

#### Visualizing Common Commands  

| **Command** | **Effect**| **Example Use Case**|
|-------------|-----------|---------------------|
| **pick**    | Keep the commit as is.| Retain a commit without changes.|
| **reword**  | Modify the commit message only.| Correct a typo or clarify the commit message.|
| **edit**    | Pause the rebase to make changes to the commit (e.g., modify files or amend the commit).| Update code in an old commit.|
| **squash**  | Combine the commit with the previous one and merge their messages.| Clean up commits to reduce clutter in the history.|
| **fixup**   | Combine the commit with the previous one but discard its commit message.| Merge minor fixes (e.g., typo corrections) into a larger commit.|
| **drop**    | Remove the commit entirely from history.| Delete commits that added experimental code that is no longer needed.|

---

#### Best Practices  

1. **Use Interactive Rebase for Local Cleanup:**  
   - Before sharing your branch, squash redundant commits and reword unclear messages to maintain a clean history.  

2. **Avoid Rebasing Public Branches:**  
   - Never rewrite history for branches others are working on to prevent conflicts.  

3. **Rebase vs. Merge:**  
   - Use rebase to clean up commits in private branches.  
   - Use merge for public branches to preserve history and avoid disruption.  

## Summary of Branches

| **Command**                            | **Description**                                                                 |
|----------------------------------------|---------------------------------------------------------------------------------|
| `git branch`                           | Lists all local branches in the repository.                                    |
| `git branch branch_name`               | Creates a new branch with the specified name.                                  |
| `git branch -d branch_name`            | Deletes the specified branch (only if it has been fully merged).               |
| `git branch -D branch_name`            | Force deletes the specified branch, even if it has not been merged.            |
| `git checkout branch_name`             | Switches to the specified branch.                                              |
| `git switch branch_name`               | Another command to switch to the specified branch (preferred over `checkout`). |
| `git checkout -b branch_name`          | Creates a new branch and switches to it.                                       |
| `git switch -c branch_name`            | Creates a new branch and switches to it (preferred over `checkout`).           |
| `git checkout <commit-id>/<tags>`      | Checks out a specific commit or tag in a detached HEAD state.                  |
| **Merging**                            |                                                                                 |
| `git checkout develop`                 | Switches to the `develop` branch.                                              |
| `git merge feature`                    | Merges the `feature` branch into the current branch (`develop`).               |
| **Rebasing (Opposite of Merging)**     |                                                                                 |
| `git checkout feature`                 | Switches to the `feature` branch.                                              |
| `git rebase develop`                   | Reapplies the commits from `feature` onto `develop` for a linear history.      |
| **Interactive Rebasing**               |                                                                                 |
| `git checkout feature`                 | Switches to the `feature` branch.                                              |
| `git rebase -i develop`                | Opens an interactive rebase session for `feature` on top of `develop`.         |


# Branching Workflows in Git

Git’s lightweight and easy-to-merge branches make it a powerful tool for software development. 

## Key Commands for Branching Workflows
- `git branch`: Create, list, or delete branches.
- `git checkout`: Switch to another branch or restore files.
- `git merge`: Merge changes from one branch into another.

---

## Types of Branches

Branches can be categorized into two main types:

### 1. Permanent Branches
- **Purpose**: These branches contain the main history of a project and serve as integration points for stable, finalized changes.
- **Characteristics**:
  - Typically long-lived and persist throughout the project lifecycle.
  - Often include branches like `master` (or `main`) and `develop`.
- **Common Workflows**:
  - Use `master` exclusively for stable, production-ready code.
  - Use an intermediate integration branch like `develop` for combining and testing features before merging them into `master`.
- **Example Workflow**:
  - Developers work on feature branches.
  - Feature branches are merged into `develop` for integration and testing.
  - Once stable, `develop` is merged into `master` for public release.
- **Benefits**:
  - Clear distinction between stable code and code under development.
  - Allows for orderly releases and minimizes risks to the production branch.

#### Example:
```plaintext
master ← develop ← [feature-1, feature-2, ...]
```
### 2. Topic Branches

Topic branches are temporary and created for specific tasks or changes. They help keep the project organized and protect permanent branches from untested code.

#### **Feature Branches**
- **Purpose**: Encapsulate a new feature or refactor.
- **Characteristics**:
  - Typically stem from `develop` or another integration branch.
  - Not merged directly into `master`.
  - Short-lived and deleted after the feature is completed and integrated.
- **Benefits**:
  - Isolates new features from the main codebase until they are complete and tested.
  - Encourages parallel development by multiple contributors.

#### Example Workflow:
```plaintext
master ← develop ← feature/new-feature
```
1. Create a feature branch:
   ```bash
   # create a new branch based on develop
   git checkout -b feature/new-feature develop
   ```
2. Work on the feature and commit changes.
3. Merge the feature branch into `develop` when ready:
   ```bash
   git checkout develop
   git merge feature/new-feature
   ```
4. Delete the feature branch:
   ```bash
   git branch -d feature/new-feature
   ```

#### **Hotfix Branches**
- **Purpose**: Quickly patch bugs or issues in the production code.
- **Characteristics**:
  - Stem directly from `master` (or the public release branch).
  - Focus on critical bug fixes or updates that cannot wait for the next release cycle.
  - Merged back into both `master` and `develop` to keep branches synchronized.
- **Example Workflow**:
  - Developers work on feature branches.
  - Feature branches are merged into `develop` for integration and testing.
  - Once stable, `develop` is merged into `master` for public release.
- **Benefits**:
  - Ensures production issues are resolved quickly.
  - Maintains consistency across all branches.

#### Example Workflow:
```plaintext
master ← hotfix/fix-critical-bug
```
1. Create a hotfix branch:
   ```bash
   # create a hotfix branch based on master
   git checkout -b hotfix/fix-critical-bug master
   ```
2. Apply the patch and commit changes.
3. Merge the hotfix into `master`:
   ```bash
   git checkout master
   git merge hotfix/fix-critical-bug
   ```
4. Merge the hotfix into `develop` to synchronize:
   ```bash
   git checkout develop
   git merge hotfix/fix-critical-bug
   ```
5. Delete the hotfix branch:
   ```bash
   git branch -d hotfix/fix-critical-bug
   ```
## Branching Workflow Flexibility

- Git treats all branches equally—the roles and purposes of branches are purely conventional.
- Adapt these workflows to suit your project’s needs.
- Understanding the mechanics of branches enables you to design custom workflows that align with your team’s requirements and preferences.

## Summary of Key Points

- **Permanent Branches**:
  - `master` (stable, production-ready code).
  - `develop` (integration branch for combining features).
- **Topic Branches**:
  - Feature branches (encapsulate new features).
  - Hotfix branches (critical fixes for production).
- **Best Practices**:
  - Always branch off from the appropriate branch (`develop` for features, `master` for hotfixes).
  - Test and review changes before merging.
  - Delete topic branches after merging to keep the repository clean.

# Remote Repositories

## What is a Remote Repository?

- A **remote repository** is a version of your project hosted outside your local machine. It could be:
  - On a **central server** like GitHub, GitLab, or Bitbucket.
  - On another developer’s personal computer.
  - Located elsewhere on your network or file system.

- **Purpose of Remote Repositories:**
  - Enable collaboration among developers by sharing code and changes.
  - Allow distributed development workflows.

- **Best Practices for Branches and Repositories:**
  - Assign **entire repositories** to developers for their work.
  - Use **branches** for feature development within a repository (not to manage individual developer workflows).

## Manipulating Remote Repositories

The `git remote` command is used to manage connections to remote repositories.

### Listing Remotes
- To list all configured remotes:
```bash
git remote
origin
```
- This example shows a single remote named `origin`, which is automatically added when cloning a repository.

- To view remote URLs:
```bash
git remote -v
origin  https://github.com/user/repo.git (fetch)
origin  https://github.com/user/repo.git (push)
```
---

### Creating a Remote
- To add a remote:
```bash
git remote add <name> <url>
```
- Example:
```bash
git remote add origin https://github.com/user/repo.git
```
- `origin`: A common name for the primary remote repository.
- `https://github.com/user/repo.git`: The URL of the remote repository.

---

### Deleting a Remote
- To remove a remote:
```bash
git remote rm <name>
```
- Example:
```bash
git remote rm origin
```
- This removes the reference to the remote repository but does not affect the repository itself.


## Working with Remote Branches

### What are Remote Branches?
- Remote branches are pointers to the state of branches in a remote repository.
- Example:
  - `origin/master` is the `master` branch in the `origin` remote repository.

### Fetching Remote Branches
- Fetching downloads changes from the remote repository without merging them:
```bash
git fetch <remote> <branch>
```
- Example:
```bash
git fetch origin master
```
- Downloads the latest `master` branch from the `origin` remote.

- Fetch all branches:
```bash
git fetch origin
```

- List all remote branches:
```bash
git branch -r
origin/master
origin/feature/some-feature
```
---

### Inspecting Remote Branches
- Remote branches are read-only:
  - To check out a remote branch:
    ```bash
    git checkout origin/feature/some-feature
    ```
    - You enter a **detached HEAD state**, meaning you're not on a local branch.
  - Compare commits between your local branch and a remote branch:
    ```bash
    git log master..origin/master
    ```
    - Lists commits in `origin/master` that are not in your local `master`.

---

## Integrating Changes from Remote Branches

### Merging Changes
- Use `git merge` to integrate changes from a remote branch:
```bash
git fetch origin
git merge origin/master
```

### Rebasing Changes
- Use `git rebase` to apply changes on top of your branch:
```bash
git fetch origin
git rebase origin/master
```
- Keeps history linear and avoids merge commits.

#### Setting Rebase as Default for `git pull`

To always use `rebase` instead of `merge` for `git pull`:
1. **Globally for all repositories:**
   ```bash
   git config --global pull.rebase true
   ```
2. **For a specific repository:**
   ```bash
   git config pull.rebase true
   ```

   - To check the current setting:
    ```bash
    git config pull.rebase
    ```

### Pulling Changes
- `git pull` combines fetch and merge [rebase] in one step:
  ```bash
  git pull [--rebase] origin master
  ```

## Pushing Changes to Remote Repositories

### Pushing a Branch
- To push your local branch to a remote:
```bash
git push <remote> <branch>
```
- Example:
```bash
git push origin my-feature
```
- This uploads `my-feature` to the `origin` remote.

### `git push -u origin main`

The command `git push -u origin main` serves two purposes:

---

#### 1. Push the Local `main` Branch to the Remote `origin` Repository

- `git push`: Pushes the changes from your local repository to the remote repository.  
- `origin`: Refers to the name of the remote repository (default name when you clone a repository).  
- `main`: The branch you want to push.  

When executed, this command uploads your local `main` branch to the remote repository named `origin`.

---

#### 2. Set the `main` Branch as the Upstream for Future Push/Pull

- `-u` (or `--set-upstream`):  
  - Links your local `main` branch to the remote `origin/main` branch.  
  - After this, you can simply use `git push` or `git pull` without specifying the remote and branch name again.  

This simplifies workflows by establishing a tracking relationship between your local branch and the remote branch.

---

#### Detailed Workflow

##### Scenario  
You have a local repository with a `main` branch. The remote repository exists but doesn't yet have a `main` branch.

1. **Before the command:**
```plaintext
Local: main branch exists.
Remote: No main branch yet.
```

1. **Run the command:**
```bash
git push -u origin main
```

1. **Result after the command:**
- The `main` branch is created in the remote repository and populated with the contents of your local branch.
- Your local branch now tracks `origin/main`.

```plaintext
Local: main (tracking origin/main)
Remote: main branch now exists.
```

---

#### Why Use `-u`?

- To save time. Once the tracking relationship is established, you can:
  - Push updates using `git push` instead of `git push origin main`.
  - Pull changes using `git pull` instead of `git pull origin main`.

---

#### Example Usage

##### Initial Push
```bash
$ git push -u origin main
```

##### Subsequent Pushes
```bash
$ git push
```

##### Pull Changes
```bash
$ git pull
```

Using `git push -u origin main` is a common practice when you push a branch to a remote repository for the first time. It simplifies future commands by linking the local branch to its remote counterpart.

---

### Push to Colleague
- Pushing to a colleague’s repository:
```bash
git push mary my-feature
```
- Sends your `my-feature` branch to Mary’s remote repository.

### Caution with Pushing
- Avoid creating unnecessary branches on the remote repository:
  - Pushing creates remote branches visible to all collaborators.
  - Coordinate with your team to avoid cluttering the repository.

---

## Summary of Remote Repositories

# Git Remote Commands Overview

| **Command**| **Description**|
|------------|----------------|
| `git remote`| Lists all remote repositories configured in the local repository.|
| `git remote -v`| Displays the full URLs of the configured remote repositories.|
| `git remote add remote_name url`| Adds a new remote repository with a friendly name (`remote_name`) and its URL. |
| `git remote rm remote_name`| Removes the specified remote repository connection.|
| `git fetch remote_name branch_name`| Fetches updates from the specified branch of the remote repository.|
| `git fetch remote_name`| Fetches updates from all branches of the specified remote repository.|
| `git branch -r`| Lists all remote branches available.|
| **Fetching and Merging**||
| `git fetch remote_name`| Fetches changes from the remote repository without merging them.|
| `git merge remote_name/master`| Merges changes from the remote `master` branch into the current branch.|
| **Shortcut for Fetch + Merge**||
| `git pull remote_name master`| Fetches and merges changes from the remote `master` branch into the current branch. |
| **Fetching and Rebasing**||
| `git fetch remote_name`| Fetches changes from the remote repository without merging them.|
| `git rebase remote_name/master`| Rebases the current branch on top of the remote `master` branch.|
| **Shortcut for Fetch + Rebase**||
| `git pull --rebase remote_name master`| Fetches and rebases changes from the remote `master` branch into the current branch. |
| **Pushing Changes**||
| `git push remote_name branch_name`| Pushes the specified local branch to the remote repository.|
| `git push -u remote_name branch_name` | Pushes the branch and sets the upstream branch for future pushes/pulls.|

# Remote Workflows

- **Remote workflows** refer to the processes in which multiple developers collaborate on a project by sharing code through remote repositories.
- There are two common collaboration models:
  1. **Centralized Workflow**
  2. **Integrator Workflow**
- Git treats all repositories as equals, unlike SVN or CVS which have a "master" repository. The central repository is merely a project convention.

## Public (Bare) Repositories
- **Public repositories** serve as points of entry for multiple developers.
- **Bare repositories** are used for collaboration, and they lack a working directory to prevent overwriting work from multiple developers.
  - Create a bare repository with the command:
    ```bash
    git init --bare <path>
    ```
  - Example of a bare repository:
    ```bash
    git init --bare some-repo.git
    ```

## The Centralized Workflow
- The **centralized workflow** is ideal for small teams where each developer has write access to the central repository.
- Developers work in their own local repositories and push their changes to the central repository.
- Common workflow:
  1. Developers complete their work locally.
  2. They merge the feature into their local master branch.
  3. Changes are pushed to the central repository.
  4. Other developers fetch the changes and integrate them into their local projects.

### Issues in the Centralized Workflow
- Conflicts can arise when multiple developers attempt to push changes simultaneously.
  - Example: If John pushes changes before Mary, Mary will encounter a **non-fast-forward error**:
    ```
    ! [rejected] master -> master (non-fast-forward)
    error: failed to push some refs to 'some-repo.git'
    ```
  - To resolve this, Mary must:
    1. Fetch the latest changes from the central repository:
       ```bash
       git fetch origin master
       ```
    2. Rebase her changes onto the latest version:
       ```bash
       git rebase origin/master
       ```
    3. Push her changes:
       ```bash
       git push origin master
       ```
### Advantages of the Centralized Workflow
- Simple setup with only one server needed.
- Ideal for small teams or projects with a trusted group of developers.

## The Integrator Workflow
- The **integrator workflow** addresses scalability and security issues inherent in the centralized model.
- Developers maintain a **private repository** and a **public repository**. The public repository is used for pushing contributions, while the integrator (maintainer) fetches, reviews, and merges them into the central project repository.
  
### Workflow in the Integrator Model
1. A contributor makes a fix or feature in their own public repository.
2. The integrator (project maintainer) fetches the changes using HTTP (read-only protocol) to ensure no unintended changes are introduced.
3. After review, the integrator merges the changes into their local branch and pushes them to the official repository.
4. Contributors only need push access to their own repositories, not the central repository.

### Security and Scalability in the Integrator Workflow
- **Security**: Contributors can only push to their own repositories, not to the central repository, avoiding potential malicious or unapproved changes.
- **Scalability**: This model allows for greater scalability by avoiding a central choke point and allowing many developers to contribute independently.

### Key Characteristics of the Integrator Workflow
- Developers must agree on a single **official repository** for the project to avoid disorder and keep everyone in sync.
- Integrators need to manage multiple remotes, but this provides the flexibility and security of managing contributions from multiple developers.
- The integrator workflow is ideal for **open-source projects** where large numbers of contributors are involved.

## Comparison of Centralized and Integrator Workflows
- **Centralized Workflow**: Suitable for small teams with direct access to the central repository.
  - Simple, easy to set up, but can lead to conflicts when multiple developers push at the same time.
- **Integrator Workflow**: Suitable for larger teams or open-source projects, providing security and scalability.
  - Contributors push to their own repositories, and integrators review and merge changes into the central repository.

### Conclusion
- Git’s distributed nature makes the **integrator workflow** highly scalable, making it ideal for large open-source projects.
- The **centralized workflow** is easier for small teams but can run into issues when multiple developers try to update the central repository simultaneously.
