---
layout: post
title: DataCamp Introduction to Git
date: 2024-01-28 11:18 +0800
tags: [python]
toc:  true
---

<!-- Global site tag (gtag.js) - Google Analytics -->
  <script async src="https://www.googletagmanager.com/gtag/js?id=G-TG0XJZG53F"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());

    gtag('config', 'G-TG0XJZG53F');
  </script>

  <style TYPE="text/css">code.has-jax {font: inherit; font-size: 100%; background: inherit; border: inherit;}</style><script type="text/x-mathjax-config">
  MathJax.Hub.Config({
      tex2jax: {
          inlineMath: [['$','$'], ['\\(','\\)']],
          displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
          skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'] // removed 'code' entry
      }});
  MathJax.Hub.Queue(function() {
      var all = MathJax.Hub.getAllJax(), i;
      for(i = 0; i < all.length; i += 1) {
          all[i].SourceElement().parentNode.className += ' has-jax';
      }});
  </script><script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-AMS_HTML-full"></script>  

**Course Description**

This course introduces learners to version control using Git. You will discover the importance of version control when working on data science projects and explore how you can use Git to track files, compare differences, modify and save files, undo changes, and allow collaborative development through the use of branches. You will gain an introduction to the structure of a repository, how to create new repositories and clone existing ones, and show how Git stores data. By working through typical data science tasks, you will gain the skills to handle conflicting files.

## Introduction to Git
---
### Introduction toversion control withGit

**Useful shell commands**
```
$ pwd
/home/repl/Documents
```

```
$ ls
archive    finance.csv    finance_data_clean.csv    finance_data_modified.csv
```

**Changing directory**

```
$ cd archive
$ pwd
/home/repl/Documents/archive
```

**Editing a file**

```
nano finance.csv
```

Use nano to: delete, add, or change contents of a file

Save changes: Ctrl + O

Exit the text editor: Ctrl + X

**Editing a file**

echo—create or edit a file

Create a new file todo.txt

```
echo "Review for duplicate records" > todo.txt
```

Add content to existing file todo.txt
```
echo "Review for duplicate records" >> todo.txt
```

**Checking Git version**
```
$ git --version
git version 2.17.1
```
---
### Using the shell

Git commands are typically performed using the Shell.

Understanding some common shell commands allows you to perform more of your Git workflow in the shell without having to spend time navigating different programs.

In this exercise, you will need to perform shell commands to identify how many files and directories are in the data directory.

```
$ ls
data  report.md
```
---
### Checking the version of Git

Just like you need to know what version of a file you are working with, it's important to understand which version of Git is installed on your computer so you're aware of what functionality it offers.

**_Instructions:_**
* Using the terminal, enter the command to find out what version of Git is installed.

```
$ git --version
git version 2.17.1
```
---
### Where does Git store information?

Your home directory /home/repl contains a repo called mh_survey, which has a directory called data.

Where is information about the history of the files in /home/repl/mh_survey/data stored?

```
/home/repl/mh_survey/.git
```
---
### Saving files

**Accessing the .git directory**

```
$ ls
data    report.md
$ ls -a.     
.DS_Store    data
..    .git         report.md
```

**Modifying a file**

```
$ nano report.md
# Mental Health in Tech Survey
TODO: write executive summary.
TODO: include link to raw data.
```

Save using Ctrl + O and Ctrl + X

**Saving a file**

Adding a single file

```
git add report.md
```

Adding all modified files

```
git add .
```

. = all files and directories in current location

** Making a commit**
```
git commit -m "Updating TODO list in report.md"
```

Log message is useful for reference

Best practice = short and concise

**Check the status of files**

```
$ git status
on branch mainC
hanges to be committed:
(use "git restore --staged <file>..." to unstage)
modified: report.md
$ git commit -m "New TODO in report.md"
```

---
### Adding a file

For the remainder of the course, you will be working on a Git project analyzing the mental health of employees working at tech companies.

In this exercise, you will complete a version control workflow to modify the mental_health_survey.csv file.

You are located in mh_survey/data, which contains the csv file you need to edit.

**_Instructions:_**
* Add a new row of data at the end of mental_health_survey.csv containing: "49,M,No,Yes,Never,Yes,Yes,No"
* Place the updated file in the staging area.
* Commit the modified file with the log message "Adding one new participant's data"

```
$ nano mental_health_survey.csv
$ git add mental_health_survey.csv
$ git commit -m "Adding one new participant's data"
[main 604a0bb] Adding one new participant's data
 1 file changed, 1 insertion(+)
```
---
### Adding multiple files

You've added one more task to the report.md and an extra row of participant data tomental_health_survey.csv files:

report.md:

TODO: Add data visualizations.

mental_health_survey.csv:

49,M,No,Yes,Never,Yes,Yes,No

You need to figure out which files are in the repo, and which are in the staging area, so you can update everything.

**_Instructions:_**
* Check which files are in the staging area but not yet committed.
* Add all files in your current directory and all subdirectories into the staging area.
* Commit all files in the staging area with the log message "Added 3 participants and a new section in report"

```
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   data/mental_health_survey.csv
        modified:   report.md

no changes added to commit (use "git add" and/or "git commit -a")
$ git add .
$ git commit -m "Added 3 participants and a new section in report"
[main 64f7816] Added 3 participants and a new section in report
 2 files changed, 2 insertions(+)
```
---
### Comparing files

**Comparing a single file**

```
nano report.md
```

**Updating the file**

```
git add .
git commit -m "Adding tasks for references and summary statistics in report.md"
```

**Updating the file again**

```
nano report.md
git diff report.md
```

**Comparing an unstaged file with the last commit**


```
git add report.md
git diff -r HEAD report.md
```

git diff -r won't work if it isn't followed by HEAD

```
cd data
nano mh_tech_survey.csv
git add mh_tech_survey.csv
```

```
git diff -r HEAD
```

**Recap**

Compare an unstaged file with the last committed version:
```
git diff filename
```

Compare a staged file with the last committed version:
```
git diff -r HEAD filename
```

Compare all staged files with the last committed versions:
```
git diff -r HEAD
```

---
### What has changed?

Checking how the current version of a file compares to the last saved version can help keep track of the last round of edits, particularly if we need to revert to a previous version.

You have been placed in the data directory of the mh_survey repo.

How many lines have been added to the current version of mental_health_survey.csv compared to the version in the latest commit?

```
$ git diff mental_health_survey.csvdiff --git a/data/mental_health_survey.csv b/data/mental_health_survey.csvindex e034015..82746b5 100644
--- a/data/mental_health_survey.csv
+++ b/data/mental_health_survey.csv
@@ -48,3 +48,4 @@ age,gender,family_history,treatment,work_interfere,benefits,mental_health_interv
 29,F,No,Yes,Rarely,Don't know,No,Don't know
 23,M,Yes,No,Sometimes,No,No,No
 25,M,Yes,Yes,Sometimes,Yes,No,Don't know
+41,M,Yes,Yes,Sometimes,No,No,No
```
```
The git diff output shows three lines changed at line 48 in the last commit,
and one additional line has been added in our current unstaged file.
```
---
### What's going to be committed?

Sometimes you could be on the verge of making a new commit and want to double-check if any other files need to be included.

You have been put in the mh_survey repo, where data/mental_health_survey.csv has been added to the staging area.

**_Instructions:_**
* Use a command to see how all files differ from the last saved revision.
* Use a Git command to add report.md to the staging area.
* Commit all files with the log message "New participant data and reminder for analysis"

```
$ git diff -r HEAD
diff --git a/data/mental_health_survey.csv b/data/mental_health_survey.csv
index e034015..82746b5 100644
--- a/data/mental_health_survey.csv
+++ b/data/mental_health_survey.csv
@@ -48,3 +48,4 @@ age,gender,family_history,treatment,work_interfere,benefits,mental_health_interv
 29,F,No,Yes,Rarely,Don't know,No,Don't know
 23,M,Yes,No,Sometimes,No,No,No
 25,M,Yes,Yes,Sometimes,Yes,No,Don't know
+41,M,Yes,Yes,Sometimes,No,No,No
diff --git a/report.md b/report.md
index 186398f..2d190de 100644
--- a/report.md
+++ b/report.md
@@ -2,3 +2,4 @@
 TODO: write executive summary.
 TODO: include link to raw data.
 TODO: remember to cite funding sources!
+TODO: Update analysis using new participant data
$ git add report.md
$ git commit -m "New participant data and reminder for analysis"
[main 932af1b] New participant data and reminder for analysis
 2 files changed, 2 insertions(+)
```
---
### What's in the staging area?

Comparing all files with their latest committed version is useful, but what if you only need to look at a single file in the staging area?

The report.md file has been stored in the staging area.

From the mh_survey repo, what single command can you use to see the changes that have been made to the report.md file?

```
$ git diff -r HEAD report.md
```
---
## Making changes
---
### Storing data with Git

**Git log**

```
git log
```

Press space to show more recent commits

Press q to quit the log and return to the terminal

**Git hash**

Last commit: b22eb75a82a68b9c0f1c45b9f5a9b7abe281683a

Pseudo-random number generator—hash function

Hashes allow data sharing between repos. If two files are the same, then their hashes are the same

Git only needs to compare hashes

**Finding a particular commit**

```
git log
```

Only need the first 6-8 characters of the hash

```
git show c27fa856
```

---
### Viewing a repository's history

Recall that every commit has a unique identifier called a hash.

Git has a command you can use to display all commits made to a repo, along with the hash, author, and time of the commit.

Using the console, run a command to find the hash of the commit that added a summary report file.

```
$ git log
commit 7f71eadea60bf38f53c8696d23f8314d85342aaf (HEAD -> main, tag: append-mental-health-survey-data, tag: alter-report-title-master, tag: alter-report-title-branch, alter-report-title)
Author: Rep Loop <repl@datacamp.com>
Date:   Fri Aug 5 09:58:21 2022 +0000

    Adding fresh data for the survey.

commit 1182c28209a9b891cdc8f49f555ff9012b76451e (tag: add-results-directory, tag: add-data-file, tag: add-bin-directory)
Author: Rep Loop <repl@datacamp.com>
Date:   Fri Aug 5 09:58:21 2022 +0000

    Added CSV data file

commit 36b761e467df557b49c28e1abf2f2aa548217ff3 (tag: add-line-to-report)
Author: Rep Loop <repl@datacamp.com>
Date:   Fri Aug 5 09:58:21 2022 +0000

    Added reminder to cite funding sources.

commit e39ecc8975ce5602f615e1f29ba3495f949def3e (tag: add-report-as-markdown)
Author: Rep Loop <repl@datacamp.com>
Date:   Fri Aug 5 09:58:20 2022 +0000

    Added summary report file.
```
```
e39ecc89
```
---
### Viewing a specific commit

A common workflow with Git is to view all commits, then compare files between a specific commit and the current version of the file.

You are located in mh_survey.

In this exercise, you will look into the commit history for report.md.

**_Instructions:_**
* Use a command to display the repo's history.
* Use the hash from the second most recent commit to display the difference between report.md in that commit versus the latest version.

```
$ git log
commit 7f71eadea60bf38f53c8696d23f8314d85342aaf (HEAD -> main, tag: append-mental-health-survey-data, tag: alter-report-title-master, tag: alter-report-title-branch, alter-report-title)
Author: Rep Loop <repl@datacamp.com>
Date:   Fri Aug 5 09:58:21 2022 +0000

    Adding fresh data for the survey.

commit 1182c28209a9b891cdc8f49f555ff9012b76451e (tag: add-results-directory, tag: add-data-file, tag: add-bin-directory)
Author: Rep Loop <repl@datacamp.com>
Date:   Fri Aug 5 09:58:21 2022 +0000

    Added CSV data file

commit 36b761e467df557b49c28e1abf2f2aa548217ff3 (tag: add-line-to-report)
Author: Rep Loop <repl@datacamp.com>
Date:   Fri Aug 5 09:58:21 2022 +0000

    Added reminder to cite funding sources.

commit e39ecc8975ce5602f615e1f29ba3495f949def3e (tag: add-report-as-markdown)
Author: Rep Loop <repl@datacamp.com>
Date:   Fri Aug 5 09:58:20 2022 +0000

    Added summary report file.
$ git show 36b761
commit 36b761e467df557b49c28e1abf2f2aa548217ff3 (tag: add-line-to-report)
Author: Rep Loop <repl@datacamp.com>
Date:   Fri Aug 5 09:58:21 2022 +0000

    Added reminder to cite funding sources.

diff --git a/report.md b/report.md
index 35f4b4d..186398f 100644
--- a/report.md
+++ b/report.md
@@ -1,3 +1,4 @@
 # Mental Health in Tech Survey
 TODO: write executive summary.
 TODO: include link to raw data.
+TODO: remember to cite funding sources!
```
---
### Viewing changes

**The HEAD shortcut**
```
git diff -r HEAD
```

Compares staged files to the version in the last commit

Use a tilde ~ to pick a specific commit to compare versions

HEAD~1 = the second most recent commit

HEAD~2 = the commit before that

Must not use spaces before or after the tilde ~

**Using HEAD with git show**
```
git show HEAD~3
```

**What changed between two commits?**

git show is useful for viewing changes made in a particular commit

git diff compares changes between two commits

To compare the the fourth and third most recent commits

```
git diff 35f4b4d 186398f
```

or

```
git diff HEAD~3 HEAD~2
```

**Changes per document by line**

```
git annotate report.md
```

**Summary**

Show what changed in the second most recent commit
```
git show HEAD~1
```

Show changes between two commits
```
git diff 35f4b4d 186398f
```

Show changes between two commits
```
git diff HEAD~1 HEAD~2
```

Show line-by-line changes and associated metadata
```
git annotate file
```

---
### Comparing to the second most recent commit

Being able to look at what happened in a specific commit is useful to check how files have changed over time.

Use an appropriate command to find out how current versions of files compare to the second most recent commit.

Choose the answer reflecting what changes occurred.

```
$ git diff HEAD~1
diff --git a/data/mental_health_survey.csv b/data/mental_health_survey.csv
index 8b9f09c..e034015 100644
--- a/data/mental_health_survey.csv
+++ b/data/mental_health_survey.csv
@@ -45,3 +45,6 @@ age,gender,family_history,treatment,work_interfere,benefits,mental_health_interv
 18,M,No,Yes,Sometimes,Don't know,No,Don't know
 19,M,No,Yes,Sometimes,Don't know,No,Don't know
 28,M,No,Yes,Rarely,Yes,No,Yes
+29,F,No,Yes,Rarely,Don't know,No,Don't know
+23,M,Yes,No,Sometimes,No,No,No
+25,M,Yes,Yes,Sometimes,Yes,No,Don't know
```
---
### Comparing commits

Not only can Git be used to check what changed in a specific commit, it also allows you to compare changes between commits!

Which files were modified between the fourth most recent and second most recent commits?

```
$ git diff HEAD~3 HEAD~1
```
---
### Who changed what?

Sometimes you need to see more detail than the commands you've used previously can provide.

Your task is to use an appropriate command to show changes such as author, change made, time of change, and commit hash, for report.md.

Display line-by-line changes and associated metadata for report.md.

```
$ cd mh_survey
$ git annotate report.md
e39ecc89        (  Rep Loop     2022-08-05 09:58:20 +0000       1)# Mental Health in Tech Survey
e39ecc89        (  Rep Loop     2022-08-05 09:58:20 +0000       2)TODO: write executive summary.
e39ecc89        (  Rep Loop     2022-08-05 09:58:20 +0000       3)TODO: include link to raw data.
36b761e4        (  Rep Loop     2022-08-05 09:58:21 +0000       4)TODO: remember to cite funding sources!
```
---
### Undoing changes before committing

**Unstaging a single file in Git**

To unstage a single file:
```
git reset HEAD summary_statistics.csv
nano summary_statistics.csv
git add summary_statistics.csv
git commit -m "Adding age summary statistics"
```

**Unstaging all files**

To unstage all files:
```
git reset HEAD
```

**Undo changes to an unstaged file**

Suppose we need to undo changes to a file in the repository
```
git checkout -- summary_statistics.csv
```

checkout means switching to a different version. Defaults to the last commit

This means losing all changes made to the unstaged file forever

**Undo changes to all unstaged files**

```
git checkout .
```

. refers to the current directory when used in a shell command

Undo changes to all unstaged files in the current directory and subdirectories

This command must be run in the main directory i.e., mh_survey

**nstaging and undoing**

```
git reset HEAD
git checkout .
git add .
git commit -m "Restore repo to previous commit"
```

---
### How to unstage a file

You've been working on the Mental Health in Tech project and have added mental_health_survey.csv to the staging area.

However, you've just received data from one more participant.

**_Instructions:_**
* Unstage mental_health_survey.csv.
* Add 41,M,Yes,No,No,No,Often,Yes to the end of mental_health_survey.csv.
* Restage this file.
* Make a commit with the log message "Extra participant".

```
$ git reset HEAD mental_health_survey.csv
Unstaged changes after reset:
M       data/mental_health_survey.csv
$ nano mental_health_survey.csv
$ git add mental_health_survey.csv
$ git commit -m "Extra participant"
[main 4f45e9b] Extra participant
 2 files changed, 5 insertions(+)
 create mode 100644 summary_statistics.csv
```
---
### Undoing changes to unstaged files

git reset is useful for unstaging files, but what if you need to undo changes made to a file that is not in the staging area?

You've been working on the report.md file, starting a discussion about the results of the project. You've not yet saved the file, and have just realized that the summary statistics changed with the addition of the last participant's data. As a result, your discussion is no longer accurate and you'd prefer to start over.

Your task is to use a Git command that will discard the changes made to report.md and allow you to start over on the discussion section.

**_Instructions:_**
* Undo the changes made to report.md.

```
$ git checkout -- report.md
```
---
### Undoing all changes

You've been practicing your shell command skills to edit files when you realize you've accidentally been adding content to the wrong files—the report.md file now has participant data in, and you've added some summary statistics into the mental_health_survey.csv file!

You have already added these files to the staging area.

You will need to perform a couple of commands to undo these changes.

**_Instructions:_**
* Remove all files from the staging area.
* Undo changes to all unstaged files since the last commit.

```
$ git reset HEAD
Unstaged changes after reset:
M       data/mental_health_survey.csv
M       report.md
$ git checkout .
```
---
## Restoring and reverting

**Project scale**

git log is useful to find the commit we want to revert to

Larger project = more commits = larger output

**Customizing the log output**

We can restrict the number of commits displayed using -:
```
git log -3
```

To only look at the commit history of one file:
```
git log -3 report.md
```

**Customizing the log output**

Restrict git log by date:
```
git log --since='Month Day Year'
```

Commits since 2nd April 2022:
```
git log --since='Apr 2 2022'
```

Commits between 2nd and 11th April:
```
git log --since='Apr 2 2022' --until='Apr 11 2022'
```

**Restoring an old version of a file**
```
git log --since='Jul 6 2022'
```

**Restoring an old version of a file**
```
git checkout -- filename
```

To revert to a version from a specific commit:

```
git checkout dc9d8fac mental_health_survey.csv
```

This was the second to last commit, so another approach is:
```
git checkout HEAD~1 mental_health_survey.csv
```

**Restoring a repo to a previous state**
```
git checkout dc9d8fac
```

Alternatively:
```
git checkout HEAD~1
```

**Cleaning a repository**

See what files are not being tracked:
```
git clean -n
```

Delete those files (cannot be undone!):
```
git clean -f
```

---
### Restoring an old version of a repo

Restoring versions of files can be extremely powerful and useful, particularly if you've made a mistake and can pinpoint when it occurred.

You've been working on the mental health in tech project for a couple of days when you spot an error in the participant data held in mental_health_survey.csv. Since then, you've modified report.md, summary_statistics.csv, and created a references document.

Therefore, you need to restore versions of all of these files to the second to last commit, which is where the error occurred.

**_Instructions:_**
* Use a command to restore all files to their version located in the commit with a hash starting 7f71eade.

```
$ git checkout 7f71eade
Note: checking out '7f71eade'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

HEAD is now at 7f71ead Adding fresh data for the survey.
```
---
### Restoring an old version of a file

You previously saw how to use git checkout to undo the changes that you made since the last commit. This command can also be used to go back even further into a file's history and restore versions of that file from a commit. In this way, you can think of committing as saving your work and checking out as loading that saved version.

Your task is to restore a file to a previous version and update the repo so it contains this as the current version of the file.

**_Instructions:_**
* Display the last two commits for the report file.
* Use the commit hash to restore the version of report.md from the second most recent commit.
* Put the restored version of report.md into the staging area.
* Commit the restored file with a log message of "Restoring version from commit e39ecc8".

```
$ git log -2 report.md
commit 36b761e467df557b49c28e1abf2f2aa548217ff3 (tag: add-line-to-report)
Author: Rep Loop <repl@datacamp.com>
Date:   Fri Aug 5 09:58:21 2022 +0000

    Added reminder to cite funding sources.

commit e39ecc8975ce5602f615e1f29ba3495f949def3e (tag: add-report-as-markdown)
Author: Rep Loop <repl@datacamp.com>
Date:   Fri Aug 5 09:58:20 2022 +0000

    Added summary report file.
$ git checkout e39ecc8 report.md
Note: checking out 'e39ecc'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

HEAD is now at e39ecc8 Added summary report file.
$ git add report.md
$ git commit -m "Restoring version from commit e39ecc8"
HEAD detached at e39ecc8
nothing to commit, working tree clean
```
---
## Git workflows
---
### Configuring Git

**Levels of settings**

git config --list

Git has three levels of settings:

1. --local: settings for one specific project

2. --global: settings for all of our projects

3. --system: settings for every users on this computer

**What can we configure?**

```
$git config --list
user.email=repl@datacamp.com
user.name=Rep Loop
core.editor=nano
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
```

user.email and user.name are needed by some commands, so setting these saves time!

user.email and user.name are global settings

**Changing our settings**

```
git config --global setting value
```

Change email address to johnsmith@datacamp.com:
```
git config --global user.email johnsmith@datacamp.com
```

Change username to John Smith:
```
git config --global user.name 'John Smith'
```

If we don't use '' and our user.name has a space: Git would save user.name as John

**Using an alias**

Set up an alias through global settings

Typically used to shorten a command

To create an alias for committing files by executing ci:

```
git config --global alias.ci 'commit -m'
```

Again, we use '' so Git processes characters after the space

We can now commit files by executing:

```
git ci
```

**Creating a custom alias**

We can create an alias for any command

If we often unstage files:

```
git config --global alias.unstage 'reset HEAD'
```

Be careful not to overwrite existing commands!

**Tracking aliases***

```
.gitconfig filegit config --global --list
```
Output format: alias.aliasname=command

```
alias.ci=commit -m
alias.unstage=reset HEAD
```

**Ignoring specific files**

```
nano .gitignore
```

```
*.log
```

* = Wildcard

Commonly ignored files: APIs, credentials, system files, software dependencies

---
### Modifying your email address in Git

Updating your configuration settings with Git can save you time, particularly where some commands require your credentials to verify access to repositories.

In this exercise, you'll configure your email settings.


**_Instructions:_**
* Display all settings.
* Change the email address to I_love_Git@datacamp.com.
* Check the global settings to see if the update has been made.

```
$ git config --listuser.email=repl@datacamp.com
user.name=Rep Loopcore.editor=nano
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
$ git config --global user.email I_love_Git@datacamp.com
$ git config --global --list
user.email=I_love_Git@datacamp.com
user.name=Rep Loop
core.editor=nano
```
---
### Creating an alias

As you work with Git more regularly, you will likely notice that you are performing certain tasks repetitively.

In this case, you have noticed that you are often checking which files have been modified and where you are in the workflow.

Therefore, you will change the command used to check the state of files to an alias, allowing you to save time.

**_Instructions:_**
* Create an alias for the global command used to check the state of files, calling it st.
* Run the new alias command to confirm it works.

```
$ git config --global alias.st 'status'
$ git st
On branch main
nothing to commit, working tree clean
```
---
## Branches

**Identifying branches**

```
$ git branch  
  alter-report-title  
  main
* summary-statistics
```

* = current branch

**Creating a new branch**

```
$ git checkout -b report
Switched to a new branch 'report'
$ git branch
  alter-report-title
  main
  summary-statistics
* report
```

The difference between branches

```
git diff main summary-statistics
```
