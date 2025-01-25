# Setting up a dev container for Rust 

* Primary author: [Kiara Smith](https://github.com/kiaras4)
* Reviewer: [Krisha Malkan](https://github.com/kdmalkan/comp423-course-notes)


```title="Example of Code block"
```<code tag> title="optional title"
--code here--
\```
```
!!! note

    The above code block contains a / before the ``` for displaying purposes. The / will not be used in the actual code


**Welcome!** This is the tutorial for creating a basic "Hello, World!" using Rust.

## Prerequisites:

- **Visual Studio Code (VS Code)**

- **Docker installed**

- **Git installed**

- **Dev Containers extension for  VS Code**

##Part 1: Getting Started

Let's start with creating the directory and initialize our Git repositiory.

1. Open your terminal or command prompt.

    By default, you will be in your user's home directory. If you wish you put this in another location, switch into that directory now.

2. Create a new directory for your hello world program.

    ```
    mkdir <name-of-directory>
    cd <name-of-directory>
    ```

3. Initalize your new Git repository.

    ```
    git init
    ```
    
4. Create a README file:

    ```
    echo "# Hello World in Rust" > README.md
    git add .
    git commit -m "Initial commit with README"
    ```

[comment]: (add-note-saying-instructions-inspired-from-423-MkDocs-Tutorial)  


## Part 2: Development(Dev) Container Set Up and Configuration

### Set-up

1. Open the directory you created in VS Code.
    - Can be done like so: File > Open folder

2. Create a .devcontainer directory at the root of the project with a file name "devontainer.json" Path should look like this:

    ```
    .devcontainer/devcontainer.json
    ```

### Configuration

The devcontainer.json file you just created defines the configuration needed for your development environment. We will be adding the following specification:

1. **name:** descriptive name for the dev container

2. **image:** This specifies the Docker image to use. We will use one of Microsoft's base images of the latest version of a Rust environment.

3. **customizations:** Adds important & useful configurations to VS Code, such as installing the Rust extension. Searching for VSCode extensions on the marketplace will bring up the string identifier of each extension in its sidebar. Adding extensions this way is important as it ensures other developers on your project will have those extensions installed in their own dev containers automatically. 

    ```
    {
        "name": "Rust Hello World",
        "image": "mcr.microsoft.com/vscode/devcontainers/rust:latest"
        "customizations": {
            "vscode": {
                "settings": {},
                "extensions": ["rust-analyzer"]
            }
        }
    }
    ```

### Post-Configuration- Reopen Project in a VS Code Dev Container

Here we will reopen the project in the container. You can do this by doing ``Ctrl+Shift+P`` (or ``Cmd+Shift+P`` on Mac), then type "Dev Containers: Reopen in Container," selecting the option once it comes up. The image will be downloaded and any requirements installed. It may take a few minutes.

Once the setup is complete, close the current terminal tab by pressing the trash can button. Open a new terminal in VS Code and run ``rustc --version`` to ensure the dev container is running a recent version of Rust. 


## Part 3: The Hello World Program!






