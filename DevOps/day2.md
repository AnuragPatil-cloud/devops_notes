## GIT 
- what is git ?
- Git is a distributed version control system that allows multiple developers to work on a project simultaneously without interfering with each other's changes.

1) What is GIT?:
✽ Git is Distributed Version Control System Tool.
✽ Git is not acronym and hence no expansion.But most of the people abbreviated as
✽ "Global Information Tracker".
✽ GIT is developed by Linus Torvalds(Finnish software engineer), who also developed
Linux Kenel.
✽ Most of the companies like Microsoft,Facebook,Yahoo,LinkedIn,Intel using Git as
Version Control System Tool.


### Basic Git Commands
```
git add --> To add files from working directory to staging area.
git commit -->To commit changes from staging area to local repository.
git push --> To move files from local repository to remote repository.
git clone -->To create a new local repository from the remote repository.
git pull --> To get updated files from remote repository to local repository.
git status ---> It shows the current status of all files in each area, like which files are untracked, which
               are modified, which are staged etc.
git log --> It shows history of all commits.
           It provides commit id, author name,mail id , timestamp and commit message.
git config ---> We can use this command to configure git like user name, mail id etc
```
```
git config --global user.email "youremail@email.com"
git config --global user.name "username"
```
## Life Cycle of File in GIT
<img width="1077" height="266" alt="Screenshot 2026-01-22 at 11 30 36 AM" src="https://github.com/user-attachments/assets/6b956178-d718-4bdd-b7f6-5d847fc3141f" />

1) Untracked:
 The files which are newly created in working directory and git does not aware of these
files are said to be in untracked state.


2) Staged:
✽ The files which are added to staging area are said to be in staged state.
✽ These files are ready for commit.
<img width="634" height="84" alt="Screenshot 2026-01-22 at 11 25 56 AM" src="https://github.com/user-attachments/assets/cf0aaf20-7cd9-4338-9ba6-ca8e5a121c59" />


3) In Repository/ Committed:
Any file which is committed is said to be In Repository/Committed State.



4) Modified:
Any file which is already tracked by git, but it is modified in working directory is said to
be in Modified State.
<img width="802" height="105" alt="Screenshot 2026-01-22 at 11 25 51 AM" src="https://github.com/user-attachments/assets/07237b70-5789-4393-b6cf-33a088fdbbca" />



