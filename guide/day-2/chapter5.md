# Chapter 5: Scan our Terraform Configurations

__Note: This chapter is strongly recommended, but is *not* required to complete tomorrows lab.__

### Overview
Prisma Cloud has an integration with GitHub that can be used to scan Infrastructure-as-Code (IaC) configurations such as Terraform -- directly in your repository. We are going to configure that integration and review the results of a scan!

### Create Config Files
Before we enable Prisma Cloud's IaC scanning, we need to provide it a few configuration parameters.

 - [ ] Open your repository in VS Code.
 - [ ] Make sure you are on the `main` branch using the branch button at the bottom left of the interface.
 - [ ] At the root of your repository, create a new folder called `.prismaCloud` (note the "." prefix).
 - [ ] Inside that directory, create a new file named `config.yml`. This is the Prisma Cloud IaC scanner configuration.
 - [ ] Add two lines to that file and save:
 ```yaml
template_type: TF
template_version: 0.14
 ```
 
 - [ ] Browse to the `.github` folder (NOT the `workflows` folder).
 - [ ] Create a new file called `prisma-cloud-config.yml`.
 - [ ] Add the following YAML to that file:
```yaml
failure_criteria_for_creating_checks:
  high: 1
  medium: 1
  low: 1
  operator: or

failure_criteria_for_creating_issues:
  high: 1
  medium: 1
  low: 1
  operator: or

github_asset_name: "Github Asset Dev"

tags:
- env:Lab
```

 - [ ] Save your files.
 - [ ] Commit your changes.
 - [ ] Push your commit to GitHub.

### Install the Prisma Cloud Extension
Now we are going to install the Prisma Cloud extension from the GitHub Marketplace.

 - [ ] Go to the GitHub web interface.
 - [ ] Select `Marketplace` from the menu at the top of the page.
 - [ ] Search for `Prisma Cloud`.
 - [ ] Click on the `Prisma Cloud` extension (NOT the `Prisma Cloud IaC Scan` extension -- this is an older version)
 - [ ] Press `Set up a new plan`.
 - [ ] Press `Install it for free`.
 - [ ] Press `Complete order and begin installation`.
 - [ ] Authorize Prisma Cloud to access your GitHub account by pressing `Install & Authorize`.
 - [ ] You may be prompted to enter your GitHub password.

Let's configure the integration.

 - [ ] You will be presented with a form requesting some details.
 - [ ] Put `https://api2.prismacloud.io` in the `Prisma Cloud API URL` field. The other fields we will get from the Prisma Cloud portal.
 - [ ] Open a second tab and browse to the Prisma Cloud portal.
 - [ ] Go to `Settings` > `Access Keys` in the menu on the left.
 - [ ] Hit `+ Add New` to create a new API Access Key.
 - [ ] Give the key a name, you can use your lab username.
 - [ ] A box will pop up with the `Access Key ID` and `Secret Key`; paste these into the form on GitHub.
 - [ ] Hit the `Validate` button. If everything was copy/pasted correctly you will see a green check appear next to each field.
 - [ ] Press the `Save` button to continue. You should be taken back to your GitHub home page.

### Review Results
Prisma Cloud will automatically scan the Terraform Configuration in your repository.

 - [ ] Browse to your repository on GitHub.
 - [ ] Go to the `Issues` tab.
 - [ ] You should see a new issue created by Prisma Cloud. If you don't, you may have to wait a bit for Prisma Cloud to complete it's scan. It will be named something like `Prisma Cloud IaC Scan Failed - 8 Issues found in scan`.
 - [ ] Open the `Issue` and review the scan results.

You will note that for each problem identified Prisma Cloud assigns a severity, gives you a link that explains the problem, and tells you which file the problem is in.

### Day 3
That's it for today! We hope you enjoyed deploying some containers and exploring Prisma Cloud's capabilities.

Tomorrow we will be configuring Ambassador to do load balancing, SSL termination, and SSL certificate management for our micro-services. We will also be integrating Ambassador with Okta to provide secure authentication in front of our app. See you then!
