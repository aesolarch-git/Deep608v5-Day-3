# Chapter 2: Update the Block Page Container
### Overview
Our `Block Page` container code has a link in the block web page that takes the user to the `Request Unblock` page if they want to submit an unblock request. That link is currently unconfigured. In this chapter we will update the URL for that link in the `Block Page` container code, rebuild our container image, and deploy the new image to Kubernetes.

### Edit the Code

 - [ ] In VS Code, on the `main` branch, browse to `services/block-page`.
 - [ ] Open `index.html`.
 - [ ] On line 131 there is a link that looks like this: `<a href="">here</a>`
 - [ ] Inside the quotes, put `https://request.edl.###.deep608lab.com/` where `###` is your lab id (ex: 021).
 - [ ] Save the file.

### Commit, Push, & Build
Let's commit our change and build a new container image!

 - [ ] Commit your local changes to Git.
 - [ ] Push your commit to GitHub.
 - [ ] Browse to your repository on GitHub and go to the `Actions` tab.
 - [ ] Select the `Block Page` Workflow on the left.
 - [ ] Monitor the Workflow run that kicked off from your push and make sure it completes successfully (green check).

### Verify
Let's verify that we have a new container image in our Container Registry!

 - [ ] Log into the GCP Portal.
 - [ ] Use the hamburger menu or the search bar up top to browse to the Google Container Registry (GCR) page.
 - [ ] On the `Images` tab, click on the `block-page` image.
 - [ ] You should see at least two images listed. One should have a recent `Created` timestamp (column on the right) and have the `Latest` tag assigned to it.
 - [ ] If you don't see the new container image, we will need to troubleshoot.

### Force Image Pull
Since we configured Kubernetes to use the `latest` tag for simplicity, it won't automatically pull our new image. There are better ways to handle this in production, but for this lab we will keep it simple and just force Kubernetes to pull our new image.

 - [ ] In the GCP Portal, go to GKE.
 - [ ] Browse to the `Workloads` tab.
 - [ ] Open the `block-page` Workload.
 - [ ] In the `Managed Pods` section, click into each of the 3 Pods one at a time and use `Delete` to delete the Pod (make sure you delete the Pod, NOT the Deployment). Kubernetes will automatically recreate it with the new container image.

When you are done, all 3 of your Pods will have a new `Created on` date.

All set, on to Chapter 3!

## Continue to [Chapter 3](chapter3.md) (Ambassador Configuration)