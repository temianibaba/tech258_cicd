# How to make a Jenkins job
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
![alt text](images/ bash_input.png)<br>
### Done
**Click build to execute job**

# How to create webhook
https://www.blazemeter.com/blog/how-to-integrate-your-github-repository-to-your-jenkins-project<br>
Use **http://3.9.14.9:8080/github-webhook/**