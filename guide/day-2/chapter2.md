# Chapter 2: Deploy Ambassador
### Overview
Now we are going to use `Helm` to deploy the `Ambassador` Load Balancer. Ambassador has many components including multiple micro-service containers that make up its capabilities. We are using Helm to very quickly and easily deploy those components. Helm has the concept of `charts` (noticing a nautical theme here?), which are templates for an entire application that runs on Kubernetes. Helm is a very popular tool in the Kubernetes community and is commonly used to deploy complicated services on Kubernetes.

You can read more about Ambassador and Helm at the links below.

https://helm.sh/
https://www.getambassador.io/products/edge-stack/api-gateway/


### Deploy Ambassador with Helm
We already configured the Helm Terraform `provider` in the previous chapter, so now we just need to configure a Helm `resource` to tell it where to get the Ambassador `chart`. In this chapter we are still working in the git branch you created in the last chapter.

 - [ ] Create a new file called `kubernetes_ambassador.tf`  in the `infrastructure/` folder and add the contents below to it.

We are defining two resources in this Terraform Configuration: a Kubernetes `Namespace` and a Helm `Chart`. A `namespace` is a concept in Kubernetes to divide a cluster into several "virtual" clusters. We are creating one here for Ambassador, to keep it separate from our other applications.

More on Namespaces: https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/

<details>
  <summary>kubernetes_ambassador.tf</summary>
  
```
# Create a Kubernetes Namespace for Ambassador
# https://registry.terraform.io/providers/hashicorp/kubernetes/latest/docs/resources/namespace
# https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/
resource "kubernetes_namespace" "ambassador" {
  metadata {
    name = "ambassador"
  }
}

# Deploy Ambassador via a Helm Chart
# https://registry.terraform.io/providers/hashicorp/helm/latest/docs/resources/release
# https://www.getambassador.io/docs/latest/topics/concepts/architecture/
resource "helm_release" "ambassador" {
  name       = "ambassador"
  repository = "https://www.getambassador.io/"
  chart      = "ambassador"
  namespace  = kubernetes_namespace.ambassador.metadata.0.name
}
```
</details>

### `commit` & `push`
Let's save our changes!

 - [ ] Be sure to save the file you edited.
 - [ ] Go to the *Git* tab in VS Code.
 - [ ] Press the `+` next to the word *Changes* to add all changed files to your commit.
 - [ ] Fill in a *commit message* in the text box near the top.
 - [ ] Press the *check* button at the top to complete your commit.
 - [ ] Push your changes.

### Create a Pull Request
Now we are going to create a `pull request` to get the changes in our branch into the `main` branch. Let's switchover to the GitHub web interface.

![GitHub Pull Request](images/Pull-Request.png)

 - [ ] Go to the `Pull requests` tab.
 - [ ] You should see a `Compare & pull request` button referencing the branch you just pushed.
 - [ ] You will be asked to provide a title and comment for your pull request. Also note that at the bottom of the page it shows you a `diff` of the changes you made: the difference between the files in your branch, and the `main` branch.
 - [ ] As with yesterday, you should again see a GitHub Actions Workflow run to do a `terraform plan` of your changes and show you what infrastructure is going to be deployed!
 - [ ] Once the `terraform plan` Workflow run completes successfully, return to your pull request. If it doesn't complete successfully, we will need to troubleshoot before proceeding further.

### Deploy to GCP
Now we can complete our Pull Request and run our deployments!

 - [ ] Review the comment that has been added to your pull request by the Workflow. You can see all the details of Terraform's plan for the deployments you just configured.
 - [ ] If everything looks good... go ahead and hit `Merge pull request`! This will move your code into the `main` branch and kickoff your Workflow again -- this time to run your deployments, not just `plan` them.
 - [ ] You will be prompted to delete your branch -- go ahead and do so, we are done with it.
 - [ ] Now go back to the `Actions` tab and open the Workflow run that is in progress to watch Terraform do its work! If the Workflow does not complete successfully (green check), we will need to troubleshoot.

## Continue to [Chapter 3](chapter3.md) (Review Deployment)