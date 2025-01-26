# Setting up a dev container for Go
*Primary author: Nabiha Choudhury https://github.com/chnabi

*Reviewer: Yohan Choi

## Prerequisties: 
Before you get started make sure you have all of these: 

1. **Visual Studio Code (VS Code):** Download and install [here](https://code.visualstudio.com/)

2. **Git installed:** [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

3. **Create a GitHub Account:** if you don't already have one, you can sign up at [GitHub](https://github.com/)

4. **Docker installed:** This is necessary for running the dev container. [Get Docker Here](https://www.docker.com/products/docker-desktop/)

5. **Install the VS Code Extension for Go:** Install link provided [here](https://code.visualstudio.com/docs/languages/go)   

## Project Setup: Create your Repository
## 1. Create a local directory and initialize Git

a. Open your terminal or Command prompt 

b. Create a new directory for the project in a convienent place for you, using the commands below. 

``` {.cli .copy}
mkdir go-dev-container-setup
cd go-dev-container-setup
```
c. Initilize a new Git repository: 

```{.cli .copy} 
git init
```

d. Create a README file: 
``` {.cli .copy} 
echo "# Creating a Go dev contianer" > README.md
git add README.md
git commit -m "Initial commit with README"
```
#Step 2. Create a Remote Repository on GitHub

a. Login into your Github account and go to the [Create New Repository](https://github.com/new) page.

b. Fill in the details as shown below: 

* Repository Name: `go-dev-contianer-setup`

* Description: Give your repository a meaningful
 description. ex "Creating a dev container for Go"  

* Do not initilize the repository with a README, .gitignore, or license.

* Click Create Repository


