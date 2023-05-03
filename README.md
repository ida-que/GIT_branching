## GIT - homework 2 - GIT_branching
This is a part of GIT homework 1. To see all the GIT homeworks, click [here](https://github.com/ida-que/GIT-homeworks).</br>
_Note: To work with GIT repos, I used some of these necessary tools:_
- _a GitHub account_
- _GitBash (for Windows) to write commands_
- _Git installed to operate Git repos_
- _folders for keeping local repos (I used `mkdir` Bash command to create those in terminal)_

After that, I had to set some preconditions to go to the first step of the scenario:
- creating a remote repo called _Git_branching_ in GitHub
- copying HTML link to the remote repo
- cloning this repo to the local directory with `git clone <HTML link to remote repo here>`

## STEPS
#### 1. In your local repository, make branches for:
- Postman
- Jmeter
- Checklists
- Bug Reports
- SQL
- Charles
- Mobile Testing


This step requires only one command `git branch`, using it 7 times to make 7 branches (example with _Postman_ branch below):
```
$ git branch Postman
```
_Note: it is not possible to create multiple branches with different names in one-line command. However, we can use pipes `|` or double ampersands `&&` this way:_
```
$ git branch Postman && git branch Jmeter && git branch Checklists && git branch Bug_Reports && git branch SQL && git branch Charles && git branch Mobile_Testing
```
_Note: branch names must not have space characters._
#### 2. Push all the branches to the remote repository.
If I had only 1 branch to push, I would do this (example with _Postman_ branch):
```
$ git push -u origin Postman
```
Here, _origin_ refers to the remote branches, `-u` is an option for tracking reference for the remote branch. In fact, we associate local _Postman_ with a remote one, and it allows us not to specify branch names during pushing and pulling in the future.</br>
This command automatically pushed all my new branches.
#### 3. In _Bug_Reports_ branch, create a text document with the structure of the bug report.
First, I need to check out/switch to the _Bug_Reports_ branch:
```
$ git checkout Bug_Reports
```
Then I create e.g. a txt file in GUI or terminal and put desired content into it (example with terminal below):
```
 $ vim BR_attributes.txt              # press Insert, type all what you need, then press Esc and :wq to save and quit
```
#### 4. Push the bug report structure to the remote repository.
Now we need to execute add, commit and push:
```
$ git add .

$ git commit -m "BR_attributes.txt added to Bug_Reports"
[Bug_Reports 3a8f47d] BR_structure.txt added to Bug_Reports
 1 file changed, 13 insertions(+)
 create mode 100644 BR_attributes.txt
```
#### 5. Merge _Bug Reports_ branch into _main_.
First, we need to go to the branch `main`:
```
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
```
Then, we have to make our new file _BR_attributes.txt_ to appear in this branch:
```
$ git merge Bug_Reports
Updating 97441d2..3a8f47d
Fast-forward
 BR_attributes.txt | 13 +++++++++++++
 1 file changed, 13 insertions(+)
 create mode 100644 BR_attributes.txt
```
#### 6. Push _main_ to the remote repository.
Now we have the file added to the local `main`. Quick checkup the current status to see the difference with the remote `main`:
```
$ git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.              # this line shows the difference
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```
We just need to sync the repos:
```
$ git push
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/ida-que/GIT_branching.git
   97441d2..3a8f47d  main -> main
```
#### 7. In the _Checklists_ branch, create a document with checklist structure.
This step is almost as same as Step 3, so we use `git checkout <branchname>` command, then use `vim <filename>.txt`, type necessary info, save and quit.
#### 8. Push this checklist structure to the remote repository.
This step is similar to Step 4. Let's try to do it in one-line command:
```
$ git add . && git commit -m "Checklist_attributes.txt added" && git push
[Checklists 3cd07e0] Checklist_attributes.txt added
 1 file changed, 12 insertions(+)
 create mode 100644 Checklist_attributes.txt
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 514 bytes | 257.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/ida-que/GIT_branching.git
   97441d2..3cd07e0  Checklists -> Checklists
```
#### 9. In the remote repository, do a pull request of _Checklists_ branch into _main_.
Let's go to GitHub website and follow the steps:
- go to the _GIT_branching_ remote repository
- in the branches, choose `Checklists` instead of `main`
- click on `Compare & pull request` to open a pull request
- in the first input field, write your commit message (I will leave it as proposed: _"Checklist_attributes.txt added"_)
- add a comment (optional - I didn't leave any)
- click on `Create pull request`
- after going to the next page of merging, click on `Merge pull request` and `Confirm merge`

Now we can check up the main branch and see both _BR_attributes.txt_ and _Checklist_attributes.txt_ there.
#### 10. Synchronize remote and local main branches.
We need to update the local main branch to the state of our remote main branch. Go to terminal for `git pull` command execution:
```
$ git checkout main                             # checking out at the main branch first
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
```
Here, as we upload the files from the previously set upstream branch (i.e. have a straight connection between local and remote main branches), we don't need to specify the merge parameters.</br>
_Note: `git pull` = `git fetch` + `git merge`_.
```
$ git pull
Updating 22a9a40..be7a617
Fast-forward
 Checklist_attributes.txt | 12 ++++++++++++
 1 file changed, 12 insertions(+)
 create mode 100644 Checklist_attributes.txt
```