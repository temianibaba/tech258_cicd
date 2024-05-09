# CICD demo
![alt text](images/breakdown.png)<br>

- [CICD demo](#cicd-demo)
  - [Creating your first job](#creating-your-first-job)
    - [1. Login](#1-login)
    - [2. New item](#2-new-item)
    - [3. Name](#3-name)
    - [4. Description](#4-description)
    - [5. Copy github https clone link](#5-copy-github-https-clone-link)
    - [6. Restrict where project can be run: sparta-ubuntu-node](#6-restrict-where-project-can-be-run-sparta-ubuntu-node)
    - [7. Source code: copy ssh github link](#7-source-code-copy-ssh-github-link)
    - [8. Provide private key](#8-provide-private-key)
    - [9. Change branch to main](#9-change-branch-to-main)
    - [10. Tick Provide Node \& npm bin/ folder to PATH](#10-tick-provide-node--npm-bin-folder-to-path)
    - [11. Go to build and change to execute shell](#11-go-to-build-and-change-to-execute-shell)
    - [Done](#done)
  - [How to create webhook](#how-to-create-webhook)
  - [CI plan](#ci-plan)
- [CD](#cd)
  - [Delivery](#delivery)
  - [Deploy](#deploy)
## Creating your first job
### 1. Login 
![alt text](images/jenkins_login.png)
### 2. New item
![alt text](images/new_item.png)
### 3. Name
![alt text](images/name_freestyle.png)
### 4. Description
![alt text](images/description.png)
### 5. Copy github https clone link
![alt text](images/git_https_link.png)<br>
![alt text](images/git_https_link_jenkins.png)
### 6. Restrict where project can be run: sparta-ubuntu-node
![alt text](images/label_expression.png)
### 7. Source code: copy ssh github link
![alt text](images/ssh_link_git.png)<br>
![alt text](images/ssh_link_jenkins.png)
### 8. Provide private key
In terminal cd to ssh keys and use: `cat <private key>`<br>
Click on add key and switch the kind to SSH<br>
**GIVE YOUR KEY AN USERNAME**
![alt text](images/enter_priv_key.png)
Paste private key into area
### 9. Change branch to main
![alt text](images/change_branch_main.png)
### 10. Tick Provide Node & npm bin/ folder to PATH
![alt text](images/tick_node.png)
### 11. Go to build and change to execute shell
```bash
cd app
npm install
npm test
```
![alt text](images/bash_input.png)<br>
### Done
**Click build to execute job**

## How to create webhook
https://www.blazemeter.com/blog/how-to-integrate-your-github-repository-to-your-jenkins-project<br>
Use **http://jekins_IP/github-webhook/**

## CI plan
![alt text](images/plan1CI.png)<br>
We would like to combine and test codes made by different developers quickly.To do this we would have to check the code works first then merge it to the main working branch.
1. Create dev branch using `git checkout -b dev` **we do not work in the main or master branch** then push on dev branch to update github
2. Make first job: this will have a webhook to build whenever code is pushed on dev branch, and post build option of triggering second job
![alt text](images/ci-post-build-actions.png)
3. Create second job called "merge to main" use post build "git publisher" and merge before build option to merge 
![alt text](images/ci-merge-source-code-behave.png)
![alt text](images/ci-merge-post-build-actions.png)

# CD
![alt text](images/plan3CD.png)
Firstly we want to get 
## Delivery
1. Create ec2 instance
2. Allow 8080 22 for now (we will need port 80 and 3000 later)
3. Run these commands
```bash
cd app
npm install
npm test
```
![alt text](images/plan2CD.png)
## Deploy
1. Automate so Jenkins SSH into instance
2. 
git publisher - plugin to be used to merge code from dev to main
**Avoid using git commands in execute shell**
- git merge conflict - related issues - branches issues
