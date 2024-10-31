---
title: "How to Push Code from Your Local Machine to Remote GitHub Using PAT and SSH"
seoTitle: "Pushing Code to GitHub via PAT and SSH"
seoDescription: "Learn how to push code from your local machine to GitHub using Personal Access Tokens (PAT) and SSH with step-by-step guidance"
datePublished: Wed Oct 30 2024 18:27:17 GMT+0000 (Coordinated Universal Time)
cuid: cm2w7l64z000109jtdqjo4blv
slug: how-to-push-code-from-your-local-machine-to-remote-github-using-pat-and-ssh
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1730312757687/724612e9-1e0e-4eb8-9909-f1b97bd560e7.png
tags: github, git, devops, 90daysofdevops

---

In the world of software development, version control is crucial for managing code changes. GitHub, one of the most popular platforms for version control, offers several methods to push your code from a local machine to a remote repository. In this article, we’ll explore two methods: using a Personal Access Token (PAT) and using SSH. Each method has its use cases, advantages, and steps, so let’s dive in!

---

## 1\. Introduction to GitHub

GitHub is a web-based platform for version control and collaboration. It uses Git, a distributed version control system, to allow developers to manage their code and collaborate with others. By pushing code to GitHub, you can share your work, maintain a history of changes, and collaborate effectively.

## 2\. Prerequisites

Before you start, ensure you have the following:

* A GitHub account.
    
* Git installed on your local machine.
    
* Basic knowledge of command-line operations.
    

## 3\. Method 1: Pushing Code Using a Personal Access Token (PAT)

### Step 1: Create a Personal Access Token

1. **Sign in to your GitHub account.**
    
2. **Go to Settings**: Click on your profile picture at the top right corner, then click on "Settings."
    
3. **Developer Settings**: Scroll down and click on "Developer settings."
    
4. **Personal Access Tokens**: Click on "Personal access tokens" and then "Tokens (classic)."
    
5. **Generate New Token**: Click on "Generate new token."
    
6. **Configure Token**:
    
    * Add a note (e.g., "Local Development").
        
    * Select scopes (permissions) for your token. For pushing code, check `repo`.
        
7. **Generate Token**: Click "Generate token." `Important:` *Copy the token as you won't be able to see it again*.
    

### Step 2: Set Up Your Local Repository

1. **Open your terminal.**
    
2. **Navigate to your project directory** using the `cd` command:
    
    ```bash
    cd /path/to/your/project
    ```
    
3. **Initialize a Git repository** if you haven't already:
    
    ```bash
    git init
    ```
    
4. **Add your files** to the staging area:
    
    ```bash
    git add .
    ```
    
5. **Commit your changes**:
    
    ```bash
    git commit -m "Initial commit"
    ```
    

### Step 3: Push Your Code

1. **Set the Remote URL with Your PAT:** If you need to set or update the remote URL to include your PAT, use the following command:
    
    ```bash
    git remote set-url origin https://<PAT>@github.com/<username>/<repository>.git
    ```
    
    Replace `<PAT>` with your personal access token, and `<repository>` with the name of your repository.
    
2. **Add the remote repository** (replace `<USERNAME>` and `<REPOSITORY>`):
    
    ```bash
    git remote add origin https://github.com/<USERNAME>/<REPOSITORY>.git
    ```
    
3. **Push your code** using the following command. When prompted for a username and password, use your GitHub username and the PAT you generated:
    
    ```bash
    git push -u origin main
    ```
    

## 4\. Method 2: Pushing Code Using SSH

### Step 1: Generate an SSH Key

1. **Open your terminal.**
    
2. **Run the following command** (replace [`your_email@example.com`](mailto:your_email@example.com) with your email):
    
    ```bash
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    ```
    
3. **Save the key**: When prompted, press Enter to save the key in the default location (`~/.ssh/id_rsa`).
    
4. **Add your SSH key to the ssh-agent**:
    
    ```bash
    eval "$(ssh-agent -s)"
    ssh-add ~/.ssh/id_rsa
    ```
    

### Step 2: Add Your SSH Key to GitHub

1. **Copy the SSH key** to your clipboard:
    
    ```bash
    pbcopy < ~/.ssh/id_rsa.pub   # Mac
    xclip -sel clip < ~/.ssh/id_rsa.pub  # Linux
    clip < ~/.ssh/id_rsa.pub  # Windows (Git Bash)
    ```
    
2. **Go to GitHub** and navigate to Settings &gt; SSH and GPG keys.
    
3. **Click on "New SSH key"**.
    
4. **Paste your key** and give it a title, then click "Add SSH key."
    

### Step 3: Set Up Your Local Repository

Follow the same steps as in Method 1 to set up your local repository.

### Step 4: Push Your Code

1. **Add the remote repository** using the SSH URL (replace `<USERNAME>` and `<REPOSITORY>`):
    
    ```bash
    git remote add origin git@github.com:<USERNAME>/<REPOSITORY>.git
    ```
    
2. **Push your code**:
    
    ```bash
    git push -u origin main
    ```
    

## 5\. Use Cases

* **Using PAT**: This method is useful for users who prefer HTTPS and are more comfortable with using tokens instead of SSH keys. It’s straightforward, especially for those who might not have SSH configured.
    
* **Using SSH**: SSH is a great option for users who regularly interact with GitHub. Once set up, it allows for a seamless and secure way to push and pull changes without entering credentials repeatedly.
    

## 6\. Conclusion

Pushing code to GitHub is an essential skill for any developer. Whether you choose to use a Personal Access Token or SSH depends on your workflow preferences and security considerations. By following the steps outlined in this article, you can easily push your local code to GitHub and keep your projects organized and collaborative. Happy coding!

---

Thank you for reading! 🚀 If you found this guide helpful or have any suggestions, tips, or questions about Linux Permissions, please feel free to leave a comment below. I’d love to hear from you and learn together!

Don't forget to follow my blog for more awesome insights on development topics, and connect with me on [LinkedIn](https://www.linkedin.com/in/ahireshubham/) and [GitHub](https://github.com/Shubham-Ahire) to stay updated on all things tech and coding! 🎉
