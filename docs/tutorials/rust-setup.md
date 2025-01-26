# Setting up a dev container for Rust 

* Primary author: [Kiara Smith](https://github.com/kiaras4)
* Reviewer: [Krisha Malkan](https://github.com/kdmalkan/comp423-course-notes)

**Welcome!** This is the tutorial for creating a basic "Hello, COMP423!" using Rust.

## Prerequisites:

- **Visual Studio Code (VS Code)**

- **Docker installed**

- **Git installed**

- **GitHub account**

- **Dev Containers extension for VS Code**

## Part 1: Getting Started

Let's start with creating the directory and initialize our Git repository.

1. Open your terminal or command prompt.

    By default, you will be in your user's home directory. If you wish you put this in another location, switch into that directory now.

2. Create a new directory for your hello COMP423 program.

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
    echo "# Hello COMP423 in Rust" > README.md
    git add .
    git commit -m "Initial commit with README"
    ```

Now that your local repository is set up, let's create a remote GitHub repository.

1. Log into your GitHub account and head straight to the Create a New Repository page.

2. Fill in the following details:

    * **Repository Name:** ``hello-comp423-rust``

    * **Description:**  "Hello COMP423 in Rust"

    * **Visibility:** Public

3. Do not initialize the repository with a README, .gitignore, or license

4. Click **Create Repository**

Perfect! Now both the local and remote repositories are set up! Let's connect them.

1. Add GitHub repository as a remote:

```
git remote add origin https://github.com/<your-username>/hello-comp423-rust.git
```

Change ``<your-username>`` with the username you have set up in GitHub.

2. Ensure your default branch name is ``main`` by using ``git branch`` in your terminal. If it's not ``main``, rename it using ``git branch -M main``.

3. Push local commits to your GitHub repository

```
git push --set-upstream origin main
```

4. Using ``git log`` in your terminally will show you the commit ID and message. This should match the ID of the most recent commit on your GitHub after reloading it.


## Part 2: Development(Dev) Container Set Up and Configuration

### Set-up

1. Open the directory you created in VS Code.
    - Can be done like so: File > Open folder

2. Create a .devcontainer directory at the root of the project with a file name "devcontainer.json" Path should look like this:

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
        "image": "mcr.microsoft.com/vscode/devcontainers/rust:latest",
        "customizations": {
            "vscode": {
                "settings": {},
                "extensions": ["rust-analyzer"]
            }
        }
    }
    ```

### Post-Configuration - Reopen Project in a VS Code Dev Container

Here we will reopen the project in the container. You can do this by doing ``Ctrl+Shift+P`` (or ``Cmd+Shift+P`` on Mac), then type "Dev Containers: Reopen in Container," selecting the option once it comes up. The image will be downloaded and any requirements installed. It may take a few minutes.

Once the setup is complete, close the current terminal tab by pressing the trash can button. Open a new terminal in VS Code and run ``rustc --version`` to ensure the dev container is running a recent version of Rust. 

!!! note

    The version of rust should be something similar to 1.83.0.



## Part 3: The Hello COMP423 Program!

We will be creating your hello comp423 program using Cargo. Cargo is the build system and package manager that Rust uses.
We will be creating your hello comp423 program using Cargo. Cargo is the build system and package manager that Rust uses.

1. Run these command lines

    ```
    cargo new hello_comp423 --vcs none
    cd hello_comp423
    ```

    The first command creates a new directory & project named hello_comp423. Cargo will have created one directory, called src, and 2 files, Cargo.toml and main.rs(this one is in the src directory). The second command navigates you into the hello_comp423 directory. ``--vcs none`` prevents the command from creating a git repository, which we have already done. 

    With these lines of code, Cargo has already created the "Hello, World!" in the main.rs file!
    !!! note

        The main.rs file can be found under src. 

    

2. Changing the message
    
    Navigate to the main.rs file. There, you should see this code already generated:

    ```
    fn main() {
        println!("Hello, World!");
    }
    ```

    - Change the message in the double quotes to say "Hello COMP423" The resulting code should look like this:

    ```
    fn main() {
        println!("Hello COMP423");
    }
    ```

3. Compiling and running the program

    In your hello_comp423 directory and in that terminal, run:

    ```
    cargo build
    ```

    You should see this output, or something similar:

    ```
    Compiling hello_cargo v0.1.0 (file:///projects/hello_comp423)
    Finished dev [unoptimized + debuginfo] target(s) in 2.85 secs
    ```

    This creates an executable file in target/debug/hello_comp423 (or target/debug/hello_comp423.exe on windows). It works similarly to using gcc to compile and link a C program:
    
     ```
     gcc -o hello_comp423 hello_comp423.c
     ```
     
     Both create an executable file that can be run. In the gcc command, you specify the file to be compiled, ``hello_comp423.c``, and names the executable, ``hello_comp423``. The ``-o`` is what allows you to name the executable something other than a.out. On the other hand, Cargo manages the project, so it is able to automatically compile the source files. Cargo's process creates an executable with the same name as the project.

    To run the compiled source files(executable), run:

    ```
    ./target/debug/hello_comp423 
    ```

4. Cargo's subcommand 

    Run:

    ```
    cargo run
    ```

    Using ``cargo run`` compiles and runs the code in one step. This differs from using the build command and then running the resulting executable object file separately. It's a convenient shortcut!


5. Now that your code is complete, we can push the changes!

    ```
    git add .
    git commit -m "Hello COMP423 complete!"
    git push origin main
    ```
    
#### Congratulations! You ran your first program using Rust!


[comment]: (add-note-saying-instructions-inspired-from-423-MkDocs-Tutorial-and-rust-tutorial-info-came-from-https://doc.rust-lang.org/book/ch01-03-hello-cargo.html?highlight=cargo%20new#creating-a-project-with-cargo)  
!!! note

    The intial part of this tutorial was inspired by the "Starting a Static Website Project with MkDocs" page on the Comp423 website. 

    The documentation that was used to create the Hello Comp423 program was inspired by a website called the "The Rust Programming Language" which can be found here : https://doc.rust-lang.org/book/ch01-03-hello-cargo.html?highlight=cargo%20new#creating-a-project-with-cargo 