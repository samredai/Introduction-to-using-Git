# Introduction to Git
 
* ## Table of Contents
[A Typical Day Using Git](#a-typical-day-using-git)  
[The GitHub concept](#section-1-the-github-concept)  
[GitHub vs. GitHub Enterprise](#section-2-github-vs-github-enterprise)  
[What is a Repo?](#section-3-what-is-a-repo)  
[Uploading your first code](#section-4-uploading-your-first-code)  
[Public vs. Private Repos](#section-5-public-vs-private-repos)  
[Markdown Language and the README.md file](#section-6-markdown-language-and-the-readmemd-file)  
[Commits](#section-7-commits)  
[Branches & Forks](#section-8-branches)  
[Merges](#section-9-merges)  
[Git vs. GitHub](#section-10-git-vs-github)  
[Git Command Line](#section-11-the-git-command-line-tool)  
[Pulling and Pushing](#section-12-pulling-and-pushing)  
[Pull Requests](#section-13-pull-requests)  
[Gists](#section-14-gists)  
[The Hidden .git Directory (and how dangerous it can be!)](#section-15-the-hidden-git-directory-and-how-dangerous-it-can-be)  
 
# A Typical Day Using Git

Before we dive into the details and concepts behind Git, I want to open with an overview of what a typical day using Git looks like. Later sections will dive into the more complex scenarios but for the most part, this is what your day to day as a developer versioning their code using Git will consist of:

You wake up, get ready for your day, and then head to your workspace.

You fire up your laptop and decide to work on your favorite project, let's call it Project A.

You navigate to the root directory of Project A (which should only contain all files and subfolders related to Project A)

```cd /path/to/project```

You start to wonder if any of your over-acheiving collaboraters were up until 4am last night commiting changes, so before you do anything you fetch information on any new changes.

```git fetch```

You notice there's one commit that happened since the last time you've fetched so you decide to merge that change into your local project folder.

```git merge origin/master```

_**note: as a shortcut to do both of these commands, you can just do ```git pull origin master``` and for an even shorter shortcut, if you're already in the master branch, you can just do ```git pull```.**_

Now you're all synced with the remote repository on GitHub and you want to start working on your project. You add some code and edit some files in your local directory as you normally would using your favorite tool (vim, UltraEdit, SAS EG etc.). After an hour of working and saving your work, you're in dire need of a fresh cup of coffee so you decide to commit your changes to your local git project.

```git add .```
```git commit -m "Added some cool optimizations"```

You come back with your fix and are ready to fix some code. You work straight though the day tirelessly, saving your work incessantly and occasionally doing commits like in the previous step when you finish a chunk of changes.

At the end of the day you're ready to call it quits and you want to push all of these commits you've been doing all day to GitHub so that now everyone will be able to see the changes you've been making all day.

```git push```

...and that's a typical day using git!

# Section 1: The GitHub concept
 
![Git Flow](https://github.com/samsetegne/Introduction-to-Git/blob/master/images/git_flow.jpeg)
 
GitHub is a web-based version-control and collaboration platform for software developers. Microsoft, the biggest single contributor to GitHub, initiated an acquisition of GitHub for $7.5 billion in June, 2018. GitHub, which is delivered through a software-as-a-service (SaaS) business model, was started in 2008 and was founded on Git, an open source code management system created by Linus Torvalds to make software builds faster.
Git is used to store the source code for a project and track the complete history of all changes to that code. It allows developers to collaborate on a project more effectively by providing tools for managing possibly conflicting changes from multiple developers. GitHub allows developers to change, adapt and improve software from its public repositories for free, but it charges for private repositories, offering various paid plans. Each public or private repository contains all of a project's files, as well as each file's revision history. Repositories can have multiple collaborators and can be either public or private.
GitHub facilitates social coding by providing a web interface to the Git code repository and management tools for collaboration. GitHub can be thought of as a serious social networking site for software developers. Members can follow each other, rate each other's work, receive updates for specific projects and communicate publicly or privately.
GitHub itself isn’t much more than a social network like Facebook or Flickr. You build a profile, upload projects to share and connect with other users by "following" their accounts. And while many users store programs and code projects, there’s nothing preventing you from keeping text documents or other file types in your project folders to show off.
 
# Section 2: GitHub vs. GitHub Enterprise
 
![Git vs Git Enterprise](https://github.com/samsetegne/Introduction-to-Git/blob/master/images/git_enterprise.jpg)
 
GitHub Enterprise is the on-premises version of GitHub.com. It makes collaborative coding possible and enjoyable for large-scale enterprise software development teams.
GitHub Enterprise includes the same great set of features as GitHub.com but packaged for running on your organization's local network. All repository data is stored on machines that you control, and access is integrated with your organization's authentication system (LDAP, SAML, or CAS).
 
# Section 3: What is a Repo?
 
![Git Data Locations Chart](https://github.com/samsetegne/Introduction-to-Git/blob/master/images/git_data_locations_chart.png)
 
A repository is a directory or storage space where your projects can live. Sometimes GitHub users shorten this to “repo.” It can be local to a folder on your computer, or it can be a storage space on GitHub or another online host. You can keep code files, text files, image files, you name it, inside a repository.
 
Here's the definition from the official GitHub documentation: *A repository is like a folder for your project. Your project's repository contains all of your project's files and stores each file's revision history.*
 
You can own a repo individually, and give other people collaborator access to your repository so that they can collaborate on your project. You can also share ownership of a repo with other people in an organization, and give organization members access permissions to collaborate on your repo.
 
Repos can be public or private. Public repos are visible to everyone. Only the owner and collaborators can view or contribute to a private repo.
 
Each person and organization can own unlimited public repos and invite an unlimited number of collaborators. You and your collaborators can work on your project using many your repo's tools including issues, pull requests, and project boards to name a few.
 
# Section 4: Uploading your first code
 
*First you have to setup an SSH Key (otherwise you'll get a permission denied error)*
1. Use putty to login to the server where you will be cloning repos
2. Run the command “ssh-keygen -t rsa”
3. It will ask you for a passphrase (You don’t have to set one, you can just hit enter twice)
4. It will tell you where it saved the key (Usually in a hidden folder in your user directory ```.ssh/id_rsa.pub```)
5. Change into that directory and print the key out using “cat id_rsa.pub”
6. Copy the key that’s printed, open up your browser and navigate to https://github.com/
7. Sign in and click your user logo in the top right, in the dropdown, click Settings
8. Go to the section “SSH and GPG keys”
9. Click “New SSH ley”
10. In the Key field, paste the key that you copied in step 6
11. Set a title (i.e. “Python Server 1” or "PU6")
12. Click Add SSH key
 
Now let's walkthrough creating a repository and uploading some code to it.
 
1. Create a new private repository on GitHub. To avoid errors, do not initialize the new repository with README, license, or gitignore files. You can add these files after your project has been pushed to GitHub.
 
2. Open up Putty and SSH into the server where your project's code is.
 
3. Change the current working directory to your local project.
 
4. Initialize the local directory as a Git repository.
 
  ```sh
  git init
  ```
  
5. Add the files in your new local repository. This stages them for the first commit.
 
  ```sh
  git add .
  ```
 
6. Commit the files that you've staged in your local repository.
 
  ```sh
  git commit -m "First commit"
  ```
 
7. At the top of your GitHub repository's Quick Setup page, click the little clipboard to copy the remote repository URL.
 
![New Repo](https://github.com/samsetegne/Introduction-to-Git/blob/master/images/new_repo.JPG)
 
8. In the Command prompt, add the URL for the remote repository where your local repository will be pushed. Optionally, you can verify the new URL using the -v argument.
 
  ```sh
  git remote add origin [remote repository URL goes here]
  git remote -v
  ```
*note: in the future you can change the remote origin using* ```git remote set-url origin [new url here]```
 
9. Push the changes in your local repo to GitHub.
 
  ```sh
  git push origin master
  ```
  
## What is "origin"?
 
"origin" is an alias on your system for a particular remote repository. It's not actually a property of that repository. By doing ```git push origin master``` you're telling git to push to the master branch in the origin repository. There's no requirement to name the remote repository origin: in fact the same repository could have a different alias for another developer. Remotes are simply an alias that store the URL of repositories. You can see what URL belongs to each remote by using ```git remote -v```.
 
When using the ```push``` command, you can use remotes or you can simply use a URL directly like this:
 
```git push git@github.com:git/git.git master```
 
## Where's the project's data moving in each of these steps?
 
Take a look at the image below that shows a simple overview of the different data locations and try to understand the flow of data during each of the steps above.
 
![Simple Data Locations](https://github.com/samsetegne/Introduction-to-Git/blob/master/images/simple_data_locations.png)
 
 
# Section 5: Public vs. Private Repos
 
Typically, your Github Enterprise instances are visible to developers within your organization. However, also within your organization, your might want to have a more-fine granular decision on who is allowed to see which repository.
 
Because of that, Github Enterprise has two visibility options for repositories - *Private* and *Public*.
 
Public repositories are a great choice for getting started! They're visible to any user on your GitHub Enterprise instance, so you can benefit from a collaborative community.
 
Private repositories require a little more setup. They're only available to you, the repository owner, as well as any collaborators you choose to share with.
 
# Section 6: Markdown Language and the README.md file
 
Markdown is a way to style text on the web. You control the display of the document; formatting words as bold or italic, adding images, and creating lists are just a few of the things we can do with Markdown. Mostly, Markdown is just regular text with a few non-alphabetic characters thrown in, like # or *. This guide you're reading right now is styled using Markdown!
 
You can use Markdown most places around GitHub:
 
-Gists
-Comments in Issues and Pull Requests
-Files with the .md or .markdown extension
 
Below are links to two great Markdown resources to bookmark:
 
The adam-p cheatsheet
https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
 
GitHub's official cheatsheet
https://enterprise.github.com/downloads/en/markdown-cheatsheet.pdf
 
# Section 7: Commits
 
Similar to saving a file, a commit is a change to one or more files in your branch. Git assigns each commit a unique ID, called a SHA or hash, that tracks:
 
  -The specific changes
  -When the changes were made
  -Who created the changes
 
When you make a commit, you must include a commit message that briefly describes the changes. You can also add a co-author on any commits you collaborate on.
 
 
![More Detailed Data Locations](https://github.com/samsetegne/Introduction-to-Git/blob/master/images/more_detailed_data_locations.png)
 
# Section 8: Branches
 
```sh
git branch mynewbranch
```
 
Branches are, simply put, pointers to a commit. To understand, we'll break it down a bit.
When you branch out, git is essentially making a new state of your current code, upon which you can work, without affecting the important main state of the code (which is in the master branch). When you're happy with your changes and want to merge your changes back into the main code, you run the following:
 
  ```sh
  git merge <branch name> master
  ```
This will tell git, to add in all of the changes from your feature branch into your master. Working with branches in git allows you to do stuff in parallel, with out affecting the main code that you use for production.
 
![Repo Network Graph](https://github.com/samsetegne/Introduction-to-Git/blob/master/images/repo_network_graph.png)
 
 
# Section 9: Merges
 
Git merge will combine multiple sequences of commits into one unified history. In the most frequent use cases, git merge is used to combine two branches. The git merge command lets you take the independent lines of development created by git branch and integrate them into a single branch.
 
![Merge Feature Into Dev](https://github.com/samsetegne/Introduction-to-Git/blob/master/images/merge_feature_into_dev.png)
 
It's important to note that git merge commands merge changes into your *current* branch. The current branch will be updated to reflect the merge, but the target branch will be completely unaffected.
 
![Merge vs Merge noff](https://github.com/samsetegne/Introduction-to-Git/blob/master/images/merge_vs_mergenoff.png)
 
# Section 10: Git vs. GitHub
 
> "While it’s possible to use GitHub without learning Git, there’s a big difference between using and understanding. Before I figured out Git I could use GitHub, but I didn’t really understand why." -Some Developer
 
Git is a revision control system, a tool to manage your source code history.
 
GitHub is a hosting service for Git repositories.
 
So they are not the same thing: Git is the tool, GitHub is the service for projects that use Git.
 
# Section 11: The Git Command Line Tool
 
## Below are the major git commands
 
## git init
Initializes a new Git repository. Until you run this command inside a repository or directory, it’s just a regular folder. Only after you input this does it accept further Git commands.
 
## git config
Short for “configure,” this is most useful when you’re setting up Git for the first time.
 
## git help
Forgot a command? Type this into the command line to bring up the 21 most common git commands. You can also be more specific and type “git help init” or another term to figure out how to use and configure a specific git command.
 
## git status
Check the status of your repository. See which files are inside it, which changes still need to be committed, and which branch of the repository you’re currently working on.
 
## git add
This does not add new files to your repository. Instead, it brings new files to Git’s attention. After you add files, they’re included in Git’s “snapshots” of the repository.
 
## git commit
Git’s most important command. After you make any sort of change, you input this in order to take a “snapshot” of the repository. Usually it goes git commit -m “Message here.” The -m indicates that the following section of the command should be read as a message.
 
## git branch
Working with multiple collaborators and want to make changes on your own? This command will let you build a new branch, or timeline of commits, of changes and file additions that are completely your own. Your title goes after the command. If you wanted a new branch called “cats,” you’d type git branch cats.
 
## git checkout
Literally allows you to “check out” a repository that you are not currently inside. This is a navigational command that lets you move to the repository you want to check. You can use this command as git checkout master to look at the master branch, or git checkout cats to look at another branch.
 
## git merge
When you’re done working on a branch, you can merge your changes back to the master branch, which is visible to all collaborators. git merge cats would take all the changes you made to the “cats” branch and add them to the master.
 
## git push
If you’re working on your local computer, and want your commits to be visible online on GitHub as well, you “push” the changes up to GitHub with this command.
 
## git pull
If you’re working on your local computer and want the most up-to-date version of your repository to work with, you “pull” the changes down from GitHub with this command.
 
# Section 12: Pulling and Pushing
 
When working in your cloned repository, your commits are all local. That means the real work in distributing your projects is in synchronizing the changes via git push and git pull.
 
> "If you’re new to Git, you may think that this is too much overhead and one that leads to a breakdown of control. Look at it this way: if your central server goes down, you’re usually hosed and prevented from working and collaborating with others. Since all of the work involved with actually creating revisions is done on your own machine, you can code whether the network is down without the permission of others or being subject to network issues." -Another Developer
 
**git pull**:
The git pull command is used to fetch and download content from a remote repository and immediately update the local repository to match that content. Merging remote upstream changes into your local repository is a common task in Git-based collaboration work flows. The git pull command is actually a combination of two other commands, git fetch followed by git merge. In the first stage of operation git pull will execute a git fetch scoped to the local branch that HEAD is pointed at. Once the content is downloaded, git pull will enter a merge workflow. A new merge commit will be-created and HEAD updated to point at the new commit.
 
**git push**:
The git push command is used to upload local repository content to a remote repository. Pushing is how you transfer commits from your local repository to a remote repo. It's the counterpart to git fetch, but whereas fetching imports commits to local branches, pushing exports commits to remote branches. Remote branches are configured using the git remote command. Pushing has the potential to overwrite changes, caution should be taken when pushing. These issues are discussed below.
 
# Section 13: Pull Requests
 
![Pull Request](https://github.com/samsetegne/Introduction-to-Git/blob/master/images/pull_request.png)
 
In their simplest form, pull requests are a mechanism for a developer to notify team members that they have completed a feature. Once their feature branch is ready, the developer files a pull request via GitHub. This lets everybody involved know that they need to review the code and merge it into the master branch.
 
But, the pull request is more than just a notification—it’s a dedicated forum for discussing the proposed feature. If there are any problems with the changes, teammates can post feedback in the pull request and even tweak the feature by pushing follow-up commits. All of this activity is tracked directly inside of the pull request.
 
# Section 14: Gists
 
With gists, you can share single files, parts of files, and full applications with other people.
Every gist is a Git repository, which means that it can be forked and cloned.
There are two types of gists: public gists and secret gists. For steps on creating gists, see "Creating gists."
 
Public gists
Public gists show up in Discover, where people can browse new gists as they're created. They're also searchable, so you can use them if you'd like other people to find and see your work. After creating a gist, you cannot convert it from public to secret.
 
Secret gists
Secret gists don't show up in Discover and are not searchable. Use them to jot down an idea that came to you in a dream, create a to-do list, or prepare some code or prose that's not ready to be shared with the world. After creating a gist, you cannot convert it from public to secret.
 
Secret gists aren't private. If you send the URL of a secret gist to a friend, they'll be able to see it. However, if someone you don't know discovers the URL, they'll also be able to see your gist. If you need to keep your code away from prying eyes, you may want to create a private repository instead.
 
# Section 15: The Hidden .git Directory (and how dangerous it can be!)
 
If you're using git for the first time, it's hard to wrap your head around how it's managing and keeping track of so many intricate details of so many copies of a project in so many different locations. One clue to it's inner workings lie in the hidden .git directory. Go into the root folder of one of your git projects and type ```cd .git``` then ```ls -l``` to change into this hidden directory and list it's contents. You'll see all kinds of folders and files containing familiar words (branches, index, fetch_head, etc.) and as you can guess, here is where many different versions of your code are stored as well as information that links your local repo to the main remote repo in GitHub.
 
One thing that happens extremely often is that developers (of all experience levels) upload this hidden folder along with their code. The reason why this is extremely dangerous is that it can contain older versions of your working directory that for a split second contained some sensitive material. While working in any of your current branches you'll probably never notice this unless you reverted back to a historical version of your code for some reason.
 
Here is an article that talks more about this: https://thenextweb.com/insider/2015/07/27/a-simple-developer-error-is-exposing-private-information-on-thousands-of-websites/
 
## Meta
 
Sam L. Setegne – ssetegne@email (Feel free to reach out if you run into any issues or have questions)
 
[https://github.com/samsetegne](https://github.com/samsetegne)
 
## Contributing
 
1. Fork it (</Introduction-to-Git/fork>)
2. Create your feature branch (`git checkout -b feature/fooBar`)
3. Commit your changes (`git commit -am 'Add some fooBar'`)
4. Push to the branch (`git push origin feature/fooBar`)
5. Create a new Pull Request
 
# Links to places that I relentlessly borrowed from
https://enterprise.github.com/faq  
https://help.github.com/articles/about-gists/  
https://www.atlassian.com/git/tutorials/syncing/git-push  
https://www.atlassian.com/git/tutorials/making-a-pull-request  
https://www.atlassian.com/git/tutorials/syncing/git-pull  
https://www.atlassian.com/git/tutorials/using-branches/git-merge  
https://stackoverflow.com/questions/13321556/difference-between-git-and-github  
http://gitready.com/beginner/2009/01/21/pushing-and-pulling.html  
https://git-scm.com/docs/git-merge  
https://www.quora.com/What-are-branches-in-GitHub  
https://github.com/Kunena/Kunena-Forum/wiki/Create-a-new-branch-with-git-and-manage-branches  
https://git-scm.com/book/en/v1/Git-Branching-What-a-Branch-Is  
https://help.github.com/desktop/guides/contributing-to-projects/committing-and-reviewing-changes-to-your-project/  
https://guides.github.com/introduction/flow/  
https://guides.github.com/features/mastering-markdown/  
https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet  
https://enterprise.github.com/downloads/en/markdown-cheatsheet.pdf  
https://help.github.com/articles/basic-writing-and-formatting-syntax/  
https://stackoverflow.com/questions/33130448/github-enterprise-public-vs-private-repo  
https://help.github.com/articles/about-repositories/  
https://readwrite.com/2013/09/30/understanding-github-a-journey-for-beginners-part-1/  
https://searchitoperations.techtarget.com/definition/GitHub  
https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line/  
