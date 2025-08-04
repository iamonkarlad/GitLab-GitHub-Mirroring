# GitLab ⇄ GitHub Mirroring
This guide helps you set up **repository mirroring** between **GitLab** and **GitHub**, so changes in one repo automatically sync to the other.
---
##  What is Repository Mirroring?
**Mirroring** allows you to **sync changes between two Git repositories**, typically hosted on different platforms like GitLab and GitHub. You can set up:

- **Push mirroring**: Automatically push changes to another repo
- **Pull mirroring**: Automatically fetch changes from another repo

---
##  Key Differences Between Push & Pull

| Feature              | Push Mirror (GitLab → GitHub) | Pull Mirror (GitHub → GitLab) |
|----------------------|-------------------------------|-------------------------------|
| Initiator            | GitLab                        | GitLab                        |
| Trigger              | On GitLab Push                | Scheduled/Manual              |
| Real-Time            | Yes                           | No (every 5-15 mins)          |
| GitHub Token Needed? | Yes                           | Only if private repo          |

---
## Benefits of Mirroring:
- Maintain code visibility across platforms
- Redundancy and backup
- Showcase work on GitHub for recruiters while working in GitLab
##  Use Case

- Backup your GitLab repo to GitHub  
- Mirror your public GitHub projects to private GitLab  
- Collaborate across different platforms

---

## 🔧 Setup: Mirror from GitLab ➝ GitHub
### Step 1.  Create a GitHub Repository
- Go to ***Github*** console
- Click on Create New Repository
- Create New Repo naming `e.g.,(mirroring github)`
- Tick public or private to create PUBLIC or PRIVATE Repo
 ![alt text](<Screenshot 2025-07-29 202656.png>)

### 🪪 Step 2: Create a GitHub Personal Access Token
- Go to your GitHub account
- Navigate to **Settings → Developer settings → Personal Access Tokens**

→ ***Settings***

 ![alt text](<Screenshot 2025-07-29 202748.png>)

→ ***Developer***

![alt text](<Screenshot 2025-07-29 202813.png>)
- In Developer Settings 
- click on ***Personal Access Tokens***
- In that Click on `Tokens (classic)`

![alt text](<Screenshot 2025-07-29 202839.png>)

***Token (classic):*** Can access all your repositories if you choose `repo` Scope.

***Fined-grained tokens:*** You need limited, read/write access to specific repositories.

- Click on **"Tokens (Classic)" → Generate new token**

![alt text](<Screenshot 2025-07-29 202856.png>)
- After clicking on `generate new token`
- Set expiration if needed

![alt text](<Screenshot 2025-07-29 203052.png>)
- Select the Scopes 
- Click **Generate Token**
- ***Copy this token*** immediately — you won’t be able to see it again

![alt text](<Screenshot 2025-07-29 203122.png>)
### Step 3: Create a GitLab Project
- Go to GitLab console 
- Click on `Projects`

 ![alt text](<Screenshot 2025-07-29 203301.png>)
- In Projects click on `New project`
- Click on ` Blank project `

![](<Screenshot 2025-07-29 213035.png>)
- Give `project name `
- In project url, add Group name or namespace
- In Visibility level, Select Private or Public 
- In Project Configuration, Tick README to create readme.md file with main
- Click on `Create Project`

![alt text](<Screenshot 2025-07-29 213246.png>)

### Step 4: Configure Mirroring Repositories
- Go to your project on **GitLab**
- Go to **Settings → Repository → Mirroring Repositories**
- Go to left side panel and click on `settings`

→ `Settings`

![alt text](<Screenshot 2025-07-29 213246.png>)

→ `Repository`

![alt text](<Screenshot 2025-07-29 213317.png>)

→ `Mirroring Repositories`

![alt text](<Screenshot 2025-07-29 213350.png>)

- On that Mirroring Repositories, click on ` Add new `
- In that add new, it requires ***Git Repository URL***
- Copy the ***HTTPS GitHub repo URL***

![alt text](<Screenshot 2025-07-29 213440.png>)
- Now paste in Mirroring Repositories, Git Repository URL
- Kept default `Mirror direction` & `Authentication method`

![alt text](<Screenshot 2025-07-29 213527.png>)
- In `Username`, Add your Github Username
- In `Password`, Add your ***Access token*** which we copied from Github

![alt text](<Screenshot 2025-07-29 213539.png>)
- And then click on `Mirror Repository` 

![alt text](<Screenshot 2025-07-29 213608.png>)
#### Now your Github Repo and Gitlab project are start Mirroring

### Step 5: Test Mirror
- To check that repo is mirror or NOT, we have add some data to project and see in github, that data also added to Github
- To add File or Data, We have to clone the project to local machine
- Copy the **HTTPS URL** of Gitlab Project
- Go to Git 
```bash
git clone <URL>
```
![alt text](<Screenshot 2025-07-29 214016.png>)
- Go to that created folder, use command
```bash
cd <clone project name>/
```
- Add  files to that clone Project
```bash
vim signup.html #inside it add some data
```
```bash
git add signup.html  # to add the file into Project
```
```bash
git commit -m 'added signup.html file'  #to commit the changes
```
```bash
git push  # to push the file into gitlab project
```
![alt text](<Screenshot 2025-07-29 214932.png>)
- check your commit appers to Gitlab
### Step 6: Check the Mirror test

- Check that file are push to gitlab

![alt text](<Screenshot 2025-07-29 214952.png>)
- And check mirror to Github

![alt text](<Screenshot 2025-07-29 215906.png>)
## 🚀Successfully done,  GitLab ⇄ GitHub Mirroring
## Summary
- GitLab to GitHub (Push Mirroring):
You push your code to GitLab, and it automatically syncs to GitHub using a Personal Access Token (PAT) for authentication. This is ideal when GitLab is your main workspace but you want to maintain a GitHub presence.
- GitHub to GitLab (Pull Mirroring):GitLab periodically pulls changes from a GitHub repo (public or private with auth). It’s slower than push mirroring and not real-time.

