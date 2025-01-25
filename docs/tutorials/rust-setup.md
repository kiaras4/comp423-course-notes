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


##Part 2: Development(Dev) Container Set Up and Configuration

1. Open the directory you created in VS Code.
    - Can be done like so: File > Open folder

2. Create a .devcontainer directory at the root of the project with a file name "devontainer.json" Path should look like this:

    ```
    .devcontainer/devcontainer.json
    ```

3.

