# 🍅 Ketchup
### Overview
This GitHub repository has all the work from yesterday's lab already completed. However, there were some tasks yesterday that we can't do for you; those are documented below. Feel free to ask for help if you need it!

You will need several accounts to complete the lab.

| Service | Notes |
|--|--|
| GitHub | If you don't already have a GitHub account, you can sign up here: https://github.com/join<br />We would recommend using a personal account. |
| Google Cloud | Provided for you. Accessible via the Okta portal with the credentials you received. |
| Terraform Cloud | Provided for you. Accessible via the Okta portal with the credentials you received. |
| Prisma Cloud | Provided for you. Accessible via the Okta portal with the credentials you received. |
| Okta | You can log into the Okta Portal here: https://aebs.okta.com/ |

After you have successfully signed into the Okta portal and completed setting up your GitHub account (or if you already have one), you can continue to the next step.

### a. Tools
 - [ ] **Install Git**
	* https://git-scm.com/download/win
	* After installing, run these commands in a terminal (PowerShell or cmd.exe):
		```
		git config --global user.name "John Doe"
		git config --global user.email john@doe.com
		git config --global credential.helper wincred
		```
	*(be sure to replace the values with your name and email!)*
 - [ ] **Install VS Code**
	* https://code.visualstudio.com/download
 - [ ] **Install the VS Code GitHub Extension**
	* [Install Extension](vscode:extension/GitHub.vscode-pull-request-github), or go here:
	* https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github
 - [ ] **Install the VS Code Terraform Extension**
	* [Install Extension](vscode:extension/hashicorp.terraform), or go here:
	* https://marketplace.visualstudio.com/items?itemName=HashiCorp.terraform

### b. Sign VS Code into GitHub
 - [ ] Open VS Code
 - [ ] Select the GitHub Extension (GitHub icon [Octocat] on the left of the window)
 - [ ] Hit the *Sign In* button and follow the prompts

### c. Clone the Template Repo
 - [ ] Go to https://github.com/ae-business-solutions/DEEP608v5-Day-2
 - [ ] Press the `Use this template` button
 - [ ] Fill in a name and description for your repository
	* *Reminder: you should create the repo in your personal account (not your organization if you have one; this can be selected in the drop down menu in front of the repo name)*
 - [ ] Review the contents of the template repository

### e. Local Development Setup
 - [ ] Open VS Code
 - [ ] Press Ctrl+Shift+P; you should see a text field pop up at the top of VS Code
 - [ ] Type 'Git' and select 'Git: Clone' from the dropdown
 - [ ] Select 'Clone from GitHub from the dropdown
 - [ ] Select the repository that you created in the last section from the dropdown
 - [ ] You will be prompted to choose a location to store the repo files
 - [ ] A prompt will appear at the bottom right of VS Code asking you whether you want to open this repository in the current window (choose this one) or a new window
 - [ ] If you select the files tab (the top tab) on the left of VS Code you should see the repository files; you can click any file to open it in the editor on the right
 - [ ] Take a minute to explore the VS Code UI and the repository you just cloned

 ### f. Get your GCP Service Account
 We will need a GCP Service Account to give GitHub and Terraform Cloud access to your GCP environment.

 - [ ] Log into your GCP account.
 - [ ] You may need to select your GCP Project from the `Project Picker` at the top of the screen (immediately to the right of the `Google Cloud Platform` logo). With the `Project Picker` open, select the `ALL` tab and then click on your Lab Id.
 - [ ] Go to the `IAM & Admin` page (use the hamburger menu at the top left). Once there you will see a "devops@" account listed on the IAM tab; this is your service account.
 - [ ] Go to the `Service Accounts` tab.
 - [ ] Click the `...` next to the DevOps account and select `Manage Keys`.
 - [ ] Chose `Add Key` and then `Create new key`. Select the `JSON` option and hit create.
 - [ ] You will see a .json file download. Open this file in your text editor of choice.
 - [ ] Be careful with this step! Carefully remove all newlines from the JSON file. Don't delete any text, but when you are done you should have all the JSON on a single line.
 - [ ] Set this aside for the next chapter! We will refer to this as your GCP Service Account Key from here on out.

### g. Import Terraform Cloud Credentials
In the email with your lab credentials, you should have also received a *Terraform Cloud API Token*. We need to configure this key in GitHub so our CI/CD pipelines can use it!

 - [ ] Go to the GitHub web interface and browse to your repository
 - [ ] Go to the `Settings` tab
 - [ ] Select `Secrets` (at the bottom on the left menu)
 - [ ] Press `New repository secret`
 - [ ] Call your secret `TF_API_TOKEN`
 - [ ] Paste the API Token from your email into the `Value` field; be sure to get rid of any extraneous spaces (before or after the token)

 One last place for credentials -- Terraform Cloud.

 - [ ] Log into your Terraform Cloud account.
 - [ ] Open your `Workspace` (it should be named like `DEEP608v5-Lab-###`).
 - [ ] Go to the `Variables` tab.
	 * You will see two sections: `Terraform Variables` and `Environment Variables`.
	 * `Terraform Variables` are the inputs to our Terraform configuration.
	 * `Environment Variables` can be used to store credentials and other things that Terraform needs to run.
 - [ ] Create a new `Environment Variable`.
	 * The `Key` will be `GOOGLE_CREDENTIALS`.
   * The `Value` will be your GCP Service Account Key from the last chapter (remember: no new lines!).
   * `Description` is optional. You *should* check `Sensitive` so the Key is write-only.

### h. Build Your Environment
The last thing we need to do is manually run your GitHub Actions CI/CD pipelines to build out your environment.

 - [ ] Go to the GitHub web portal. Go to your repository.
 - [ ] Go to the `Actions` tab.
 - [ ] For each of the 5 GitHub Actions Workflows on the left:
    - [ ] Select the Workflow (on the left).
    - [ ] Hit the `Run workflow` dropdown on the right.
    - [ ] Press the green `Run workflow` button.

It will take 10 minutes or so your all 5 workflows to run. You should see a green check mark next to each workflow run indicating that it completed successfully. If any of them do not complete successfully, ask for help.

## Continue to [Chapter 1](chapter1.md) (Deploy Containers)