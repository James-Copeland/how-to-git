# Setup for Git

Git is a wonderful programming tool that acts as a version control system. This means that Git will track changes made to your code, allow you to save 'snapshots' (called commits) of what your code looked at a particular time, revert your code to a previous commit, or create branches or parallel versions of your code base allowing you to modify one branch without affecting the other. The document will explain the basic setup for Git on your work-machine.
<br>
<br>
All Git-related knowledge can be found at this [link](https://git-scm.com/).
<br>
<br>
A quick cheatsheet for using Git on the command-line can be found [here](https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet).
<br>

## Setting Up Your Working Environment with Git

<br>

### Installing Git

1. Check to see if already installed by running	the following command in terminal

    ```
    git --version	
    ```

2. If not installed, you can use this [link](https://git-scm.com/download/mac) for Mac installation

3. Set your username and email in Git so that you can be authenticated

	* Run the following command with your username in terminal

    ```
    git config --global user.name "James Copeland"
    ```

    * Run the following command with your PKI email in terminal 

    ```
    git config --global user.email "james@pkinformation.com"
    ```

    * (optional) You can check to make sure they were set correctly by running the following command in terminal

    ``` 
    git config --list --show-origin
    ```

4. Authenticate your computer with Github using an ssh key

	1. First check to see if you already have an ssh key on your computer with the following code in terminal

		```
		cd ~/.ssh
		```

	2. If no such directory exists, move on to step 5

	3. If the directory does exist (no error message), then run the next line

		```
		ls
		```

	4. If a id_rsa.pub is listed, then you already have an ssh key and you can move on to step 6

	5. Create a new ssh key with the following line of code in terminal and follow the prompts given

		```
		ssh-keygen -o
		```

	6. View your ssh key with the following line of code

		```
		cat ~/.ssh/id_rsa.pub
		```

	7. Copy the entire block of text that is returned beneath the line you just executed


5. Log into Github and go to your personal Settings->SSH and GPG keys and click "New SSH key". Paste in your SSH key into the key field and click "Add SSH key"

### Setting up your text editor for better Git visualization (optional)

* VS Code

	1. VS Code also has a built-in Git source control manager that is great for making new commits quickly and easily

	2. For more advanced use, go to the extensions and search for "GitLens -- Git supercharged" and click install

* Sublime Text 3 

	1. If you do not have the Package Control installed, use this [link](https://packagecontrol.io/installation) for the installation

	2. Open the command palette ("Ctrl+Shift+P" for Windows/Linux, "Cmd+Shift+P" for Mac OS)

	3. Search for Package Control: Install Package and hit "Enter"

	4. Type "GitGutter" into the command palette and press "Enter" to install it (you may have to open the command palette again). This package helps to visualize uncommitted changes 

	5. For more advanced use, you can install "SublimeGit". Repeat steps 2-3 and then type "SublimeGit" into the command palette

	6. Take a look at the package documentation [GitGutter](https://packagecontrol.io/packages/GitGutter) and [SublimeGit](https://packagecontrol.io/packages/SublimeGit)

* Atom

	1. Atom already has some Git features that can be accessed by clicking "Git" or "GitHub" at the bottom bar on the app

	2. For more advanced use, you can also install the "Git-Plus" package by going to Preferences->Install and then searching for it. There is documentation available [here](https://atom.io/packages/git-plus)

### Installing GitKraken 
![img](https://pbs.twimg.com/profile_images/714866842419011584/LRrR48qp_400x400.jpg "GitKraken")
<br>
<br>
GitKraken is a Git User Interface that allows full use of Git source control without having to constantly interact with the terminal. It also helps to guide users through a specific workflow that is known as GitFlow. For more information on GitFlow, see this [link](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow).

1. Download GitKraken for Mac [here](https://www.gitkraken.com/download/mac)

2. Either sign-in with your PKI Github credentials or create an account with your PKI email

3. Go to menu->Preferences->Authentication->GitHub.com

4. If an ssh key is listed, you are good-to-go. Otherwise, click the button to authenticate yourself and log into Github if necessary

5. Once you have a repo opened in GitKraken, make sure you go back to preference and turn on the Git Flow option setting the branch options to Master=>master and Develop=>dev

6. (optional) Check-out their [support page](https://support.gitkraken.com/) if necessary

7. (optional) Check-out their GitKraken [cheatsheet](https://www.gitkraken.com/downloads/gitkraken-cheat-sheet-219.pdf)

### Setting up a local repository from a GitHub repository

1. Go to GitKraken and select the "Clone a repo" button

2. Click on "GitHub.com", browse for the local you want it cloned to, and click "Clone the Repo!"

3. After the cloning is done, you should be able to open the repo in both your text editor and GitKraken

### Creating a new repository from scratch

1. Go to GitKraken and select the "Start a Local Repo" button

2. Click on "GitHub.com", chose the "PKInfo" Account, chose a Name for the repo, change the Access to "Private", and browse for the location on your computer that you want the local version to be created in

3. Click the "Create Repository and Clone" button. After the cloning is done, you should be able to open the repo in both your text editor and GitKraken

### Understanding the basic workflow

1. After you have either opened the repo you wish to change in GitKraken, make sure you go back to preference and turn on the Git Flow option setting the branch options to Master=>master and Develop=>dev

2. If you are working on a new feature for the dev branch, use the "Feature" option of the GitFlow panel. 

	* Make as many edits in your text editor as you need and commit your changes as necessary.

	* Once you believe that your changes are adequate, use the GitFlow panel to finish the Feature.

	* To move your changes to GitHub, first make sure that you have the "dev" branch selected (checked-out). Then, if the Github version (remote) is ahead of your local version, you must preform a Pull operation to update your code with the changes on Github. Then, you can perform a Push operation to update Github with your changes.

3. If you are working hotFix on the "master" (production) branch, use the "Hotfix" option of the GitFlow panel. 

	* Make as many edits in your text editor as you need and commit your changes as necessary.

	* Once you believe that your changes are adequate, use the GitFlow panel to finish the Hotfix.

	* Since the Hotfix feature performs a merge on both the "dev" and "master" branches, you must perform the next step twice.

	* To move your "dev" changes to GitHub, first make sure that you have the "dev" branch selected (checked-out). Then, if the Github version (remote) is ahead of your local version, you must preform a Pull operation to update your code with the changes on Github. Then, you can perform a Push operation to update Github with your changes.

	* To move your "master" changes to GitHub, first make sure that you have the "master" branch selected (checked-out). Then, if the Github version (remote) is ahead of your local version, you must preform a Pull operation to update your code with the changes on Github. Then, you can perform a Push operation to update Github with your changes.
