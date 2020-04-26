
GIT Workshop - STAC Era: COVID-19
=========================================
  # Refer to the video walkthrough posted in Google Drive at any point you need guidance.
## Outline
1. Setting up Git on Your Computer
2. Creating Your Github Account 
3. Linking Your Github Account With Git on Your Computer
4. Creating and Pulling Your First Repository from Github
5. Adding files, Making Changes, and Pushing these Changes to Github 
6. Intro to Branching
7. Additional Resources & Comments
# 1. Setting up Git on Your Computer
1. First, check to see if you already have Git installed on your machine.
	1a). Type the command ```git --version```in your terminal. If you have it installed, the git version is shown.
2. If you do not have it installed, go to [[https://sourceforge.net/projects/git-osx-installer/files/](https://sourceforge.net/projects/git-osx-installer/files/)] and download Git the .dmg.
3. Once Git is installed, you can check to see if the installation worked correctly by typing ```git --version``` 
4. Finally, we are going to set your name and email associated with using Git on your computer.
	4a). Type ```git config --global user.name "<Your name here>"```into your terminal.
	---> For your ```user.name```, you can use your real name or really whatever you want.
	4b). Type ```git config --global user.email "<youremail@whatever.whatever"```
	--->For your ```user.email```, please use the same email associated with your Github account.

# 2. Creating your Github Account
 1. If you do not have a Github account already, go to [[https://github.com/](https://github.com/)] and sign up.
# 3. Linking Your Github Account With Git on Your Computer
 1. In your terminal, type ```ssh-keygen -t rsa -C "<youremail@whatever.whatever>"```
	 1a). Make sure to use the same email as in previous steps.
2. Now, copy your public key that was generated from the following command to your clipboard with the following command --->```pbcopy < ~/.ssh/id_rsa.pub```
3. Now, go to [https://github.com/settings/keys](https://github.com/settings/keys) and click *New SSH Key*
4. Paste the public key that was copied to your clipboard and give the *New SSH Key* a label (doesn't really matter what it is). Click *Add SSH Key*.

*Now that the setup is over, we can get to the fun stuff!*

# 4. Creating and Pulling Your First Repository from Github
 1. Go to [https://github.com/](https://github.com/), make sure you are logged in, and click *New* that is to the right of **Repositories** on the left side of the webpage.
 2. Give the repository whatever name you want and give it a description if you want. You probably want to click the private option for the repository. **Make sure to click the checkbox called "Initialize this repository with a README**. Finally, click *Create Repository*.
 3.  You should now be taken to your newly created repository on github located at [https://github.com/<your_username>/<your_repository_name>](https://github.com/ejbraun/stac-git-ws).
 4. While you can create and upload files directly within the Github webpage, that's rarely used. Instead, we want to *clone* this remote repository, creating a local copy on our own machine.
 5. To do this, click the green button labeled *Clone or download* and click on the clipboard icon. This will copy the ssh path that we will use to copy the remote repository to your clipboard.
 6. Now, go to your terminal and type the following command -->  ```git clone git@github.com:<your_username>/<your_repository_name>.git```. Make sure you set your current working directory to where you want to place this repository on your local machine.
 7. Since it is the first time you have used your *SSH key*, you will most likely be prompted with a y/n authentication request. Type y and press enter. After some scrolling text, the repository will be created. If you type ```ls -l``` in your terminal , you will see the folder with *<your_repository_name>* created! Congratulations :)
 # 5. Adding files, Making Changes, and Pushing these Changes to Github 
 *Currently, our repository is looking a little sad with how empty it is :(((( Let's change that!*
1. To start, let's add a file to our repository. It can be a .txt, .pdf, .docx, or anything else. For now, we are going to create a simple text file and add it to our repository.
2. First, with your preferred text editor, create a text file with an arbitrary name and arbitrary contents inside of your *<your_repository_name>* folder.
3. Once that is done, type ```git status``` in your terminal with your current working directory being set to  *<your_repository_name>* folder. 
4. You should see the file you just added listed in red with a header above stating that it is unadded and unstaged for a commit. This means that if we were to try to push our text file right now, nothing would be pushed since the text file has not been recognized as something that we want to be committing (we aren't even bothering to track it either!). 
5. To fix this, we must first add the file to be a tracked file. This can be accomplished by typing the following command ---> ```git add <your_file_name>.txt```.
6. After typing this command, if you type ```git status```, you should now see that the file is being tracked but still not committed!
7. To fix this, we must now perform a commit message. This can be accomplished by typing the following command ---> ```git commit -m "<your_random_commit_message>"```. The commit message can be whatever you want, it does not matter.
8. If we had multiple files all being tracked in the repository with changes, this commit would include those in addition to our .txt file creation! 
9. Now, we are finally ready to make our local changes reflected in the remote repository located on Github. Type ```git push origin master```. Since it is the first time you have used your *SSH key* for a push command, you will most likely be prompted with a y/n authentication request. Type y and press enter. After some scrolling text, your local repository's changes should be pushed to the remote repository on Github.
10. Now go to [https://github.com/<your_username>/<your_repository_name>](https://github.com/ejbraun/stac-git-ws). You should see your newly added text file in the repository. Congrats :0 :)
# 6. Intro to Branching
 *Now that you have mastered the basics of Git, we will move on to one of the major advantages of using Git: branches! With branches, person A can be working on their PersonA branch and person B can be working on their PersonB branch. Person A can work on their branch with no fear of messing up any of the changes that person B makes due to their own separate branches. 
 When either person wants their local changes reflected on main branch (often called the master branch), they can merge their personal branch with master. Thus, the only thing that the person who did not merge first must do is to pull the other person's changes from master before merging their own branch. Let's take a look and see how this works!*
1. If you type ```git branch``` in your terminal, you will see only one branch: the *master* branch. This is usually treated as the main version of the repository. Working directly on the *master* branch is normally not ideal, especially in real project environments.
2. To create your own branch, type the following --->```git checkout -b <your_branch_name_here>```
3. Now, if you type ```git branch```, you will see that you are now currently on the branch named *<your_branch_name_here>*. Now, any future changes you make while you remain on this branch will stay on this branch!
4. Go ahead and modify the contents of the text file you created in the previous step. Add a bunch of copypasta, 10 page essays that you hated writing, or whatever you want.
5. Now go ahead and commit these changes. (command: ```git commit -m "<your_random_commit_message>"```)
6. Now, to demonstrate the power of branches, let's hop back on over to the master branch. Type the following command --->```git checkout master```.
7. If you type ```git branch```, you will now see that we have switched back over to the master branch. Now, go ahead and open your text file. Surprised? You shouldn't be! Now that we are no longer on your *<your_branch_name_here>* branch, none of the changes you made are visible in the master branch.
8. Say you are confident that these changes you made are bug-free and worthy to be viewed by everybody. It's time to merge! Type the following command to merge *<your_branch_name_here>* into the *master* branch ```git merge <your_branch_name_here>```. After some scrolling text, you should see that the merge was performed successfully.
9. Now that *<your_branch_name_here>* is essentially useless since it is the same as your master branch, you can go ahead and delete it with the following command ---> ```git branch -d <your_branch_name_here>```
10. Well done :) 
# 7. Additional Resources & Comments
There is so many more useful things to Git that can't all be explored in this workshop. I encourage you to check out the below links to continue your learning and knowledge of Git. That's it from me. Good luck in whatever you've got going on at the moment!

[https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf](https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf)
[https://githowto.com/getting_old_versions](https://githowto.com/getting_old_versions)
[https://try.github.io/](https://try.github.io/)
