# CI
- [CI](#ci)
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
    - [10. Go to build and change to execute shell](#10-go-to-build-and-change-to-execute-shell)
    - [Done](#done)
  - [How to create webhook](#how-to-create-webhook)
  - [CI](#ci-1)

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
### 10. Go to build and change to execute shell
```bash
cd app
npm install
npm test
```
![alt text](images/bash_input.png)<br>
### Done
**Click build to execute job**
test
## How to create webhook
https://www.blazemeter.com/blog/how-to-integrate-your-github-repository-to-your-jenkins-project<br>
Use **http://3.9.14.9:8080/github-webhook/**

## CI
1. Create dev branch using `git checkout -b branch_name` **we do not work in the main or master branch**
2. Change branch in Jenkins from main to dev and config web hook so job builds whenever code is pushed
3. Create new job called "merge to main"
4. Configure first job post build to trigger next job "merge to main" if tests are passed
