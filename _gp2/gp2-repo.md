---
title: Guided Project 2 WolfScheduler - Activity and Event
tags: [software engineering, software lifecycle, CS2, CSC216, GP2]
description: Guided Task - Guided Project 2 GitHub Repository
navigation: on
pagegroup: gp2
---

# Guided Task: Guided Project 2 GitHub Repository
{% include iconHeader.html type="task" %}

You will be assigned a separate [GitHub](https://github.ncsu.edu) repository for each Guided Project and each major Project.  This is to ensure that your work on each is distinct and that any work on a new project doesn't get recorded as late work on an old project.  However, you will continue with the same WolfScheduler project for GP2.  You need to share the project to your GP2 repository.

{% capture callout_content %}
  * Disconnect a project from a GitHub repository
  * Share a project with a new GitHub repository
  * Push changes to a new remote GitHub repository
{% endcapture %}
{% include callout.html content=callout_content icon="objective" type="learningOutcomes" title="Learning Outcomes" %}
  
{% capture callout_content %}
A project may belong to only a single local repository.  That is because a Git repository is represented as a folder on a file system with a special `.git/` folder that stores Git metadata.  The *same* project cannot be in two locations on the file system at once.  The process outlined below will let you share an existing Eclipse project with a new repository and then retain a copy of your Guided Project 1 submission in a local copy of your Guided Project 1 repository.
{% endcapture %}
{% include callout.html content=callout_content icon="vcTool" type="bestPractices" title="Best Practice: Version Control" %}

{% capture callout_content %}
[Git](https://git-scm.com/) is a distributed version control system.  Git supports the [creation of repositories](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-repo), [copying of repositories (cloning)](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-clone), [committing changes](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-commit), [working with remote repositories](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-remote), and [merging changes](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-merge).  In Git, all repositories are considered equal and each maintains its own history.  You can move information between connected repositories through pulling and pushing any changes.
{% endcapture %}
{% include callout.html content=callout_content type="tools" icon="vcTool" title="Tools: Git and GitHub" %}


## Disconnect `WolfScheduler` from GP1 Repository
Disconnecting a project from a Git repository removes any associated metadata about the project from the repository.  To disconnect, do the following:

  * Right click on the `WolfScheduler` project
  * Select **Team > Disconnect**.
  * The repository name to the right of the `WolfScheduler` project will no longer be available.


{% capture reminder-content %}

**Cloning a Repository**
  * [Cloning in Git Bash](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-clone#cloning-in-git-bash)
  * [Cloning in EGit](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-clone#cloning-in-egit)
  
**Adding (Staging a Project)**
  * [Add Files to the Staging Area in Git Bash](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-staging#adding-files-to-your-staging-area-using-git-bash)
  * [Add Files to the Staging Area in EGit](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-staging#adding-files-to-your-staging-area-using-egit)
  
**Committing Staged Changes**
  * [Commit Using Git Bash](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-commit.html#commit-using-git-bash)
  * [Commit Using EGit](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-commit.html#commit-using-egit)
  
**Pushing Committed Changes**
  * [Push Using Git Bash](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-push.html#push-using-git-bash)
  * [Push Using EGit](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-push.html#push-using-egit)
{% endcapture %}
{% include mention.html content=reminder-content icon="vcTool" type="reminder" title="Reminder: Working with GitHub" %}
## Push `WolfScheduler` to your GP2 Repository
Complete the following steps to push `WolfScheduler` to your GP2 repository.

  * Clone your GP2 repository provided by the teaching staff.  The pattern will be `csc216-GP2-XXX-YYY`, where XXX is your section number and YYY is your repository number.
  * Stage your `WolfScheduler` to your GP2 repository by right clicking on the project and selecting **Team > Share Project**.
  * In the **Configure Git Repository** pop-up, uncheck the option **Use or create repository in parent folder of project**. Then select your new repository from the drop down and check your project. 

  {% include image.html file="images/ShareRepo.PNG" caption="Figure: Sharing Project with Repository" %}

  * Now that your project is staged for the GP2 repository, add the files to the index by right clicking on the `WolfScheduler` project and selecting **Team > Add to index**. Then **Commit and Push** the project to start GP2!  Use a commit message like "[Skeleton] Starting GP2 with GP1 WolfScheduler".
  * You may need to refresh the **Git Staging** view for the files to show as staged.  It's also ok if you don't have some of the `.gitignore` files that are in the screenshot.

  {% include image.html file="images/StageRepo.PNG" caption="Figure: Staging Files" %}

## Reset your GP1 `WolfScheduler`
When you shared the `WolfScheduler` project with your new GP2 repo, that removed the `WolfScheduler` directory from your *local* GP1 repo directory.  If you want to keep a copy of your GP1 `WolfScheduler`, you should reset your local GP1 repository to the last commit in the remote.  Then your local GP1 repository will have a copy of your final GP1 `WolfScheduler` submission.  You can use that as a backup as you're working on GP2!

Choose to do the reset in either Eclipse or Git Bash!

In Eclipse, do the following:

  * Right click on your GP1 repository in the **Git Repositories** view and select **Reset**.
  * Make sure the last commit is selected and select the option for a **Reset type** of **Hard (HEAD, index, and working tree updated)**.  Click **Reset**.
  
  {% include image.html file="images/Reset1.PNG" caption="Figure: Resetting Files" %}
  
  * You will receive a warning about overwriting your local changes.  This is what we want since we want to bring a copy of the project back into our local GP1 repository and erase all of your uncommitted local changes (which in this case is all the deleted `WolfScheduler` files).  Click **Reset**.
  
  {% include image.html file="images/Reset2.PNG" caption="Figure: Reset Warning" %}
  
  * Check that `WolfScheduler` is now in the `Working Tree/` directory of your GP1 repository.
  
  {% include image.html file="images/Reset3.PNG" caption="Figure: WolfScheduler is now in GP1 repo" %}
  
In Git Bash, do the following:

  * Change directory to your repository location.
  * Enter the command `git reset --hard HEAD`.  This will reset the local repository to the same information as the remote and erase all of your uncommitted local changes (which in this case is all the deleted `WolfScheduler` files).
  


{% capture callout_content %}
 In this case, resetting the repo is useful, but the reset command can lead to major problems.  Use the power of the reset command carefully!
{% endcapture %}
{% include callout.html content=callout_content icon="stop" type="reminder" title="Caution: Resetting a Repo" %}
           

## Check Your Submission
You should ALWAYS verify that your pushed changes are on the remote repository.  You can do this by going to your repository on the GitHub website and making sure that your `WolfScheduler` project has been pushed to your GP2 repository.

  * Log into [NCSU's GitHub](https://github.ncsu.edu)
  * Select the appropriate organization and repository.
  * Verify that your latest commit message is listed and that all pushed files are in the repository.
     
Verify that your Guided Project 2 [Jenkins job]({{site.data.grades.jenkins-server}}) is pulling your `WolfScheduler` from your GP2 repository (this job will start with `GP2-`.  If [Jenkins]({{site.data.grades.jenkins-server}}) does not recognize your project, please notify the teaching staff via Piazza or the sup list as early as possible to ensure that your project is set up correctly for auto grading.

{% capture callout_content %}
At this point, your Jenkins build will be a **red ball**.  That is expected because there are several things that we have to do in Guided Project 2 before our code will even compile.  The important thing is that the job runs and gives you a red ball!
{% endcapture %}
{% include callout.html content=callout_content icon="stop" type="reminder" title="Caution: Red Ball on Jenkins is OK (at this point)" %}

{% capture reminder-content %} 
GitHub Resources:

  * [Staging Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-staging)
  * [Committing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-commit)
  * [Pushing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-push)
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Reference: Staging and Pushing to GitHub"%} 
## Check Your Progress
{% include iconHeader.html type="glance" %}

  - [ ] Make sure that all fields, methods, and constructors are commented.
  - [ ] Resolve all static analysis notifications.
  - [ ] Fix test failures.
  - [ ] Commit and push your code changes with a meaningful commit message.  Label your commit with "[Skeleton]" for future you!