### **Branching Tutorial with GitHub Desktop and VS Code**

Branching is a vital concept in Git, enabling you to develop new features or fix issues separately from the main codebase. This tutorial will guide you on how to create a new branch in GitHub Desktop, switch between branches, and verify your current branch in VS Code.

#### **Step 1 (Option A): Open Your Project in VS Code**

- If you prefer starting with VS Code, ensure your project repository is already cloned to your local machine.
- Launch Visual Studio Code.
- Navigate to File > Open Folder... and select your project folder to open it.

#### **Step 1 (Option B): Open Your Project from GitHub Desktop**

- If you'd like to start with GitHub Desktop, first ensure you've cloned the repository to your local machine. If not, you can clone it directly from GitHub Desktop.
- Open GitHub Desktop and select your repository from the list on the left side.
- With the repository selected, look for the option to Open in Visual Studio Code at the top of GitHub Desktop. This might be found under the Repository menu or as an icon/button depending on your version of GitHub Desktop.
- Clicking Open in Visual Studio Code will launch VS Code and automatically open your project folder.


#### **Step 2: Create a New Branch in GitHub Desktop**

- Open GitHub Desktop.
- Choose your repository from the list on the left side.
- At the top of the GitHub Desktop window, near the middle, you will see the name of the current branch. It is typically `main` or `master` by default.
- Click on the current branch name to reveal a dropdown menu. At the top of this menu, you'll find a text box where you can type the name of your new branch. Use concise, descriptive names for branches. For example, for adding a login feature, you could name it `feature-add-login`.
- After typing the name of your new branch, click `Create Branch` or press `Enter`. GitHub Desktop will create the branch and automatically switch you to it.

> Branch Naming Convention: I find that it's really nice to keep branches sorted by who has created them. Even if you're on a solo project, it might be a good idea to keep this convention to form the habit. The way you do this would be to put your name at the beginning of every branch you create. As an example: `trent/my-new-branch` - where "my-new-branch" 

#### **Step 3: Verify Your Branch in VS Code**

- Return to Visual Studio Code with your project open.
- Look at the bottom left corner of the window. The name displayed there indicates your currently active branch.
- If it hasn’t updated to show your newly created branch, click on the branch name. This action triggers VS Code to refresh its connection with your repository, and it should now display your new branch name.
- If you need to switch to a different branch in VS Code, clicking the branch name at the bottom left will bring up a list of available branches. You can select another branch from this list to switch to it.

#### **Step 4: Work on Your Branch**

- With the new branch checked out, you can now proceed to make changes in VS Code. Your work on this branch will be isolated from the main branch, allowing you to experiment and develop without affecting the main codebase.

#### **Step 5: Commit and Push Your Changes**

- Once you're ready to save your changes, commit them. In VS Code, you can do this by opening the Source Control panel (`Ctrl+Shift+G` or `Cmd+Shift+G` on Mac), typing a commit message, and pressing the checkmark button to commit.
- In GitHub Desktop, enter a summary and optional description for your changes in the bottom left corner, then click `Commit to [your-branch-name]`.
- Finally, push your changes to GitHub by clicking the `Push origin` button in GitHub Desktop. This action will upload your branch and its changes to the remote repository.

#### **Conclusion**

Well done! You've learned how to manage branches using GitHub Desktop and verify them in Visual Studio Code. Branching is a powerful tool that supports parallel development streams, keeping your main codebase stable while you work on enhancements or fixes. With practice, branching will become an integral part of your development process.