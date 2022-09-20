---
title: Guided Project 1 - Software Development Practices and Tools
tags: [software engineering, software lifecycle, CS2, CSC216, GP1]
description: Guided Task - Push WolfScheduler to GitHub
navigation: on
pagegroup: gp1
---

# Guided Task: Push WolfScheduler to GitHub
{% include iconHeader.html type="task" %}
Submission of all major course deliverables for Guided Projects, Labs, and Part 2s of Projects is through the [Git](../git-tutorial/) version control system and [NCSU's Enterprise GitHub](https://github.ncsu.edu).  You should go through the [Git and GitHub Tutorial](../git-tutorial/) to familiarize yourself with the technologies before completing this Guided Task.

{% capture callout_content %}
  * Clone a GitHub repository
  * Share a project with a GitHub repository
  * Push changes to a remote GitHub repository
{% endcapture %}
{% include callout.html content=callout_content icon="objective" type="learningOutcomes" title="Learning Outcomes" %}
  
{% capture callout_content %}
A *version control system* stores the history of development on a given project in a central location.  Additionally, a version control system provides mechanisms for teams to collaborate on the same code base.  In a version control system, there is typically a remote repository that contains the main copy of the code and all of the development history or contributions of the developers.  Developers have a local copy of the remote's code where they can make changes to fix bugs or add new functionality.  Those changes are then copied or pushed to the remote's repository and are integrated into the main code base.  Other team members can checkout or pull the changes from the remote to their local copies of the code and continue working on their development tasks.  If there are major issues with a system, a development team can roll back to an earlier version of the code base.
{% endcapture %}
{% include callout.html content=callout_content icon="vcTool" type="bestPractices" title="Best Practice: Version Control" %}

{% capture callout_content %}
[Git](https://git-scm.com/) is a distributed version control system.  Git supports the [creation of repositories](../git-tutorial/git-repo), [copying of repositories (cloning)](../git-tutorial/git-clone), [committing changes](../git-tutorial/git-commit), [working with remote repositories](../git-tutorial/git-remote), and [merging changes](../git-tutorial/git-merge).  In Git, all repositories are considered equal and each maintain their own history.  You can move information between connected repositories through pulling and pushing any changes.  

When using Git, you will have a remote Git repository that exists on NCSU's Enterprise GitHub server.  That remote repository is where all of your files must end up for grading.  You will have a local repository that is cloned from the provided remote repository.  You will develop in your local repository and push your changes to the remote repository.  If you're working with a partner, your partner can pull your changes into their local repository and continue development.  The [workflow](../git-tutorial/git-workflow) is similar if you're using Git Bash or Eclipse EGit.

You will be using [NCSU's Enterprise GitHub](https://github.ncsu.edu/), which is a web interface for working with Git repositories.  The web interface provides a mechanism for viewing your remote Git repository (where all your work is submitted).  Additionally, GitHub provides functionality for providing feedback on code and tracking issues.

To be assigned a repository, you must log into NCSU's GitHub system with your unity id and password. 
{% endcapture %}
{% include callout.html content=callout_content icon="vcTool" type="tools" title="Tools: Git and GitHub" %} 

{% capture reminder-content %} 
[Configure your local Git setup](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-config.html)
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Reference: Git Configuration"%}

## Git Configuration
Completing a local configuration of Git is useful to streamline usage. We require that commits to NCSU's GitHub are identified by the student's unity id.  [Configure your local Git setup](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-config.html), so that you can ensure that you are using the correct identifiers so that we can give you credit for your work, especially on team assignments.

{% capture reminder-content %} 
[Set up your local system to use SSH to connect to GitHub](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh)
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Reference: Connecting to GitHub with SSH"%}
## [OPTIONAL] Connecting to GitHub With SSH

There are two ways to connect to GitHub: 1) HTTPS and 2) SSH.  

If you connect to GitHub using **HTTPS**, you will connect through secure HTTP connections.  This will require you to enter your username and password with each interaction with the remote NCSU Enterprise GitHub server.

If you connect to GitHub using **SSH**, you will use a secure key on your local system to connect with a public key that you have associated with your GitHub account.  SSH stand for secure shell (it's also Dr. Heckman's initials!) This will serve as your authentication and provide a secure connection; you won't have to enter your user name and password with every interaction.  We strongly encourage you to follow the directions provided by GitHub to [set up your local system to use SSH to connect to GitHub](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh).  

{% capture reminder-content%}
For additional information on cloning a repository, see:

  * [Cloning in Git Bash](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-clone.html#cloning-in-git-bash).
  * [Cloning in EGit](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-clone.html#cloning-in-egit).
{% endcapture %}
{% include mention.html content=reminder-content type="reminder" title="Reference: Cloning a Repository" %}
## Clone the Remote Repository


To work with a new remote repository that is assigned to you for submission of your CSC 216 work, you must first clone the remote repository to your local file system. 

  1. Get your assigned repository's clone URL:
  
      * Go to [NCSU's Enterprise GitHub](https://github.ncsu.edu).
      * Open the dropdown menu under your username in the top left of the page.  Choose the CSC 216 organization for the given semester.  For example, Fall 2021's organization is `engr-csc216-fall2021` and Spring 2022's organization is `engr-csc216-spring2022`.
      * Select the repository for the given assignment.  For example, a repository for Guided Project 1 may be named `csc216-GP1-XXX-YYY`, where `XXX` is your section number and `YYY` is your repository number.
      * First select if you would like to copy the SSH clone URL or the HTTPS clone URL in the drop down menu.  Then click the copy button.  Only select the SSH URL if you have [set up your SSH key](#optional-connecting-to-github-with-ssh).  
	  

      
{% include image.html file="images/CopyCloneURL.PNG" caption="Figure: Getting the GitHub repository's clone URL" %} 

  {:start="2"}
  2. Clone the repository locally.  Do ONE of the following.
  
     * [Clone the repository using Git Bash](#clone-the-repository-using-git-bash)
	 * **[RECOMMENDED]** [Clone the repository using Eclipse EGit](#clone-the-repository-using-eclipse-egit)
  
     
### Clone the repository using [Git Bash](../git-tutorial/git-clone#cloning-in-git-bash)
        
  * Open Git Bash
  * Change directory to the location on your file system where you want your cloned repository to live.  Remember this location!
  * Execute the command:  

            
```bash
git clone <copy clone URL here>
```
            
  * If you are using HTTPS, enter your unity id and password.
  
This will create a directory structure on your file system for the local copy of the Git repository.  However, this does not add the Git repository information to your Eclipse workspace.  To add the repository to Eclipse, do the following:

  * Open the *Git Repositories* view (if it is not already open) by selecting **Window > Show View > Other > Git > Git Repositories.**  Click **OK**.
  * Select the option to *Add and existing local Git repository*.
  
  {% include image.html file="images/GitRepoViewLocal.PNG" caption="Figure: Git Repositories View" %} 
  
  * Eclipse will search your filesystem for folders that are Git repositories (these are folders that contain a `.git/` folder). Select the folder that corresponds to the location where you cloned the repo.
  
  {% include image.html file="images/AddGitRepositories.PNG" caption="Figure: Add existing Git repository to Eclipse workspace" %} 
  
  * Click **Add**.  Your repository will now be in your **Git Repositories** view in your Eclipse workspace.
  
  {% include image.html file="images/GitRepositoriesViewAfter.PNG" caption="Figure: Your repository is listed after adding it to the Eclipse workspace." %} 
      
### Clone the repository using [Eclipse EGit](../git-tutorial/git-clone#cloning-in-egit)
      
  * Open the *Git Repositories* view (if it is not already open) by selecting **Window > Show View > Other > Git > Git Repositories.**  Click **OK**.
  * Select the option to *Clone a Git Repository*.
        
  {% include image.html file="images/GitRepoView.PNG" caption="Figure: Git Repositories View" %} 
           
           
  * The *Clone Git Repository* wizard will display.  If you have the Git URL in your computer's memory, it will populate the *URI*, *Host*, and *Repository path* fields.  If you do not, copy the URL and paste it into the *URI* field.  The *Host* and *Repository* fields will populate.  Click **Next**.
        
  {% include image.html file="images/EGitClone1.PNG" caption="Figure: Cloning a Git Repository - Entering the URL" %} 
            
            
  * Make sure that the `main` branch is selected.  Click **Next**.
        
  {% include image.html file="images/EGitClone2.PNG" caption="Figure: Cloning a Git Repository - Selection of `main` Branch" %} 
            
            
  * Browse for the location where you want the local copy of the repository to be located on your file system.  The default location is a `git/` directory under your home directory.    
        
  {% include image.html file="images/EGitClone3.PNG" caption="Figure: Cloning a Git Repository - Selecting Location of Local Copy" %} 
      
  * After you have selected the location, click **Finish**.  The repository will now be listed in the Git Repositories view.
  
  {% include image.html file="images/GitRepositoriesViewAfter.PNG" caption="Figure: Your repository is listed after adding it to the Eclipse workspace." %} 

{% capture reminder-content %}
For additional information on adding (staging) a project to a repository, see:
  * [Add Files to the Staging Area in Git Bash](../git-tutorial/git-staging#adding-files-to-your-staging-area-using-git-bash)
  * [Add Files to the Staging Area in EGit](../git-tutorial/git-staging#adding-files-to-your-staging-area-using-egit)
{% endcapture %}
{% include mention.html content=reminder-content type="reminder" title="Reference: Adding (Staging) a Project" %}
## Adding (Staging) `WolfScheduler` to a Git Repository
Now that you have a local copy of your remote submission repository, you need to add your project to the local repository.  Since you created the project in Eclipse BEFORE cloning your repository, we recommend using EGit to add (stage) your `WolfScheduler` project to your local Git Repository.  This is because EGit will handle the copying of the `WolfScheduler` project to the repository location on your file system while maintaining the project in Eclipse.  

  1. Right click on the `WolfScheduler` project and select **Team > Share Project...**..
  
  2. Select your repository from the drop down menu and click **Finish**. 
  
{% include image.html file="images/ShareProject.PNG" caption="Figure: Adding a Project to a Git Repository" %} 
  
  {:start="3"}  
  3. The project name in the *Package Explorer* should now be followed with the name of the repository in square brackets.
  
{% include image.html file="images/SharedProject.PNG" caption="Figure: A Shared Project" %} 
   
  {:start="4"}   
  4. To add the files to the index, right click on `WolfSchduler` and select **Team > Add to Index**.
       

       
{% capture reminder-content %}
For additional information on committing staged changes, see:
  * [Commit Using Git Bash](../git-tutorial/git-commit.html#commit-using-git-bash)
  * [Commit Using EGit](../git-tutorial/git-commit.html#commit-using-egit)
  
For additional information on pushing committed changes to the remote, see: 
  * [Push Using Git Bash](../git-tutorial/git-push.html#push-using-git-bash)
  * [Push Using Git Bash](../git-tutorial/git-push.html#push-using-egit)
{% endcapture %}
{% include mention.html content=reminder-content type="reminder" title="Reference: Adding (Staging) a Project" %}
## Committing Local Changes and Pushing to the Remote Repository
Now that your project is staged in the repository, you can commit the changes to the local repository and push the changes to the remote repository and submit your work (so far).

Commit and push your changes.  Do one of the following:

  * [Commit/push using Git Bash](#commitpush-using-git-bash)
  * **[RECOMMENDED]** [Commit/push using EGit](#commitpush-using-egit)
  
### Commit/push using Git Bash
  
  * Change directory to your repository in Git Bash
  * First, commit your changes using the following command:
    
```bash
git commit -am "Submitting a skeleton of WolfScheduler."
```
        
  * Second, push the changes to the remote repository using the following command:

```bash
git push
```

  * In Eclipse, click the refresh button in the *Git Repositories view* for the commit to be recognized by Eclipse.

### Commit/push using EGit

  * Right click on `WolfScheduler` and select **Team > Commit**.
  * In the *Git Staging* view, do the following:
     * Check that all files you want pushed to the remote repository are in the *Staged Changes* window.  Select any files that should be committed/pushed in the *Unstaged Changes* window, right click and select **Add to Index**.
     * If there are any files that you do not want pushed to the remote repository in the *Staged Changes* window, right click on the files and select **Remove from Index**.
     * Make sure that the following files (at least) are staged:
        * `.classpath`
        * `.gitignore`
        * `.project`
        * `Course.java`
     * Enter a commit message like "[Skeleton] Submitting a skeleton of WolfScheduler".
     * Click **Commit and Push**.
  * If your files aren't showing up in the Staged Changes window, click the refresh button (in the red circle) in the upper left of the view.
       
{% include image.html file="images/EGitCommitPush.PNG" caption="Figure: Git Staging View" %} 


 
       
  * After the push completes, there will be a confirmation window to show that the project was pushed to the remote correctly.  If you see a message about `fast-forward`, there was an error.  You have a merge conflict and [you will need to resolve the conflict](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-merge.html).
  
{% include image.html file="images/ConfirmPush3.PNG" caption="Figure: Push Confirmation" %} 

           

## Check Your Progress
{% include iconHeader.html type="glance" %}
You should ALWAYS verify that your pushed changes are on the remote repository.  You can do this by going to your repository on the GitHub website.

  1. Log into [NCSU's GitHub](https://github.ncsu.edu)
  
  2. Select the appropriate organization and repository.
  
  3. Verify that your latest commit message is listed and that all pushed files are in the repository.
  
{% include image.html file="images/GitHubVerify.PNG" caption="Figure: Verifying a Submission on GitHub" %} 
     
You will follow this process every time you want to submit your code.  We recommend frequent pushes to the remote repository to save your work or when you have a problem.  It is ok to push code that doesn't compile or pass all of the tests.  When the teaching staff helps you, it is easiest for us to check the code on your repository (assuming you provide a link to your repo for us to use).

