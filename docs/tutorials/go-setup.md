# Setting up a dev container for Go
* Primary author: [Nabiha Choudhury](https://github.com/chnabi)

* Reviewer: [Yohan Choi](https://github.com/YummyYohan)
## Prerequisties: 
Before you get started make sure you have all of these: 

1. **Visual Studio Code (VS Code):** Download and install [here](https://code.visualstudio.com/)

2. **Git installed:** [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

3. **Create a GitHub Account:** if you don't already have one, you can sign up at [GitHub](https://github.com/)

4. **Docker installed:** This is necessary for running the dev container. [Get Docker Here](https://www.docker.com/products/docker-desktop/)
  

# Project Setup: Create your Repository
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
##Step 2. Create a Remote Repository on GitHub

a. Login into your Github account and go to the [Create New Repository](https://github.com/new) page.

b. Fill in the details as shown below: 

* **Repository Name:** `go-dev-contianer-setup`

* **Description:** Give your repository a meaningful
 description. ex "Creating a dev container for Go"  

* **Visibility:** Public

c. Do not initilize the repository with a README, .gitignore, or license.

d. Click **Create Repository.**

## Step 3. Link your Local Repository to GitHub

a. Add the GitHub repository as a remote: 

```{.cli .copy}
git remote add origin https://github.com/<your-username>/go-dev-container-setup.git
```
Be sure to replace `<your-username>` with your GitHub username. 

b. Check your default branch name with the subcommand `git branch`. If it's not `main`, rename it to `main` with the following command: `git branch -M main`. Old versions of `git` choose the name `master`, but we will prefer to use `main` as the standard branch name.

c. Push local commits to the GitHub repository: 

```{.cli .copy} 
git push --set-upstream origin main
```
> "Understanding the --set-upstream Flag"
    
>`git push --set-upstream origin main`: This command pushes the main branch to the remote repository origin. The `--set-upstream` flag sets up the main branch to track the remote branch, meaning future pushes and pulls can be done without specifying the branch name and just writing `git push origin` when working on your local `main` branch. This long flag has a corresponding `-u` short flag.

d. Back in your web browser, refresh your GitHub repository to see that the same commit you made locally has now been *pushed* to remote. You can use `git log` locally to see the commit ID and message which should match the ID of the most recent commit on GitHub. This is the result of pushing your changes to your remote repository.

# Setting Up the Development Environment
## Step 1. Add Development Container Configuration 

1. In VS Code, open the `go-dev-container-setup` directory. You can do this via: File > Open Folder.

2. Install the **Dev Container** extension for VS Code.

3. Create a `.devcontainer` directory in the root of your project with the following file inside of this "hidden" configuration directory:

`devcontainer/devcontainer.json`

The `devcontainer.json` file defines the configuration for your development environment. Here's how to set it up:

### Configuration Details:

- **`name`**: A descriptive name for your development container. 
- **`image`**: The Docker image to use. In this case, we use the latest Go development environment image. [Microsoft provides pre-built images optimized for various programming languages.](https://hub.docker.com/r/microsoft/vscode-devcontainers)
- **`customizations`**: Adds useful configurations to Visual Studio Code. This includes installing extensions (like the Go extension) and applying specific settings.
- **`postCreateCommand`**: Commands that run automatically after the container is set up. For Go projects, this could include installing dependencies using `go mod tidy`.

Example `devcontainer.json`

```{.json .copy}
{
  "name": "Go Development Environment",
  "image": "mcr.microsoft.com/devcontainers/go:latest",
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": ["golang.Go"]
    }
  },
  "postCreateCommand": "go mod tidy"
}
```
## Step 2. Add `go.mod` Go Dependency Configuration 

`go.mod`

The `go.mod` file lists the Go dependencies needed for the project. It should be in your project's root directory. Here we will include our project name and a version of Go to use.

```{.go .copy} 
module go-dev-container-setup

go 1.20
```
## Step 3. Reopen the Project in a VSCode Dev Contianer

Reopen the project in the container by pressing `Ctrl+Shift+P` (or `Cmd+Shift+P on Mac`), typing "Dev Containers: Reopen in Container," and selecting the option. This may take a few minutes while the image is downloaded and the requirements are installed.

Once your dev container setup completes, close the current terminal tab (trash can), open a new terminal pane within VSCode, and try running `go version` to see your dev container is running a recent version of Go without much effort!

# Part 3. Creating a Simple "Hello World" Program in Go

## Step 1. Write the Code 

Create a file in your root directory called `main.go`. In this file write the following code which will print `Hello COMP 423!` to the console. 

```{.go .copy}
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP 423!")
}
```
> The fmt package is one of the standard library packages in Go. 

## Step 2. Two Ways to Run 

a. `go run main.go`: This command will compile and run your program all in one step. 

b. Build a binary file, then execute after. This approach is reminicent of the gcc compliation commands we used in COMP 211. 

* To build the binary file use `go build -o <filename>` in the terminal

* To execute the file use `./<filename>` in the terminal

Here is an example
``` {.cli .copy} 
go build -o hello
./hello
```
Both methods will result in `Hello COMP 423!` being printed to the console.
> **Compilation Process**
> 
> Generally, the compilation steps are as follows:
> 
> - **Compile**: Converts the human-readable program to an assembly file.
> - **Assemble**: Converts the assembly file to an object file.
> - **Linking**: Combines object files to create the final executable.
> 
> Since Go is a compiled language, when we call `go build -o <filename>`, the Go code is directly compiled into an executable file. Then, we can execute the file using `./<filename>`.

# Conclusion 

Congratulations! You’ve successfully created a simple Go program in a configured development environment. Now you will be able to set up container for future projects in Go. 





