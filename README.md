# Upgrading Node.js on Linux using NVM

If you're trying to upgrade Node.js from version 12 to a more recent version (e.g., 18 LTS) on a Linux distribution like Parrot OS and encountering issues along the way, this guide is for you. We'll cover each step in detail, including common problems and solutions.

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Installing NVM](#installing-nvm)
3. [Upgrading Node.js](#upgrading-nodejs)
4. [Troubleshooting Common Issues](#troubleshooting-common-issues)
    1. [NVM Command Not Found](#nvm-command-not-found)
    2. [Node.js Version Rolls Back to 12](#nodejs-version-rolls-back-to-12)
    3. [Issues with .bashrc](#issues-with-bashrc)

## Prerequisites

Before you begin, make sure you have the following:

- A Linux distribution (e.g., Parrot OS)
- An existing installation of Node.js version 12
- Administrative access to your system

## Installing NVM

1. **Check your package manager**: Update your package manager to ensure you have the latest package information.

    ```bash
    sudo apt update
    ```

2. **Install NVM (Node Version Manager)**: NVM will allow you to easily switch between Node.js versions.

    ```bash
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
    source ~/.bashrc # Source NVM in your current session
    ```

3. **List available Node.js versions**: See the available Node.js versions for installation.

    ```bash
    nvm ls-remote
    ```

## Upgrading Node.js

4. **Install Node.js version 18**: Replace `18` with the version you want.

    ```bash
    nvm install 18
    ```

5. **Set Node.js 18 as the default version**:

    To set it as the default:

    ```bash
    nvm alias default 18
    ```

    Or, for the current session:

    ```bash
    nvm use 18
    ```

6. **Update npm (Node Package Manager)**:

    ```bash
    npm install -g npm@latest
    ```

## Troubleshooting Common Issues

### NVM Command Not Found

If you encounter the "nvm command not found" error:

- Source NVM in your shell profile (e.g., `~/.bashrc` or `~/.zshrc`) or use the correct shell-specific configuration file.

### Node.js Version Rolls Back to 12

If Node.js version rolls back to 12 after closing the terminal:

- Check that the NVM sourcing commands are present and correctly placed in your shell profile.
- Ensure the shell profile is sourced when opening a new terminal session.

### Issues with .bashrc

If you face issues with `~/.bashrc`:

- Create the `~/.bashrc` file if it doesn't exist.
    ```bash
    touch ~/.bashrc
    ```
- Add the NVM sourcing commands to `~/.bashrc`.
    ```bash
    nano ~/.bashrc
    ```
- Source `~/.bashrc` to apply changes to your current session.
    ```bash
    export NVM_DIR="$HOME/.nvm"
    [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
    [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
    ```
- After you've saved the ~/.bashrc file, you need to source it to apply the changes to your current terminal session.
    ```bash
    source ~/.bashrc
    ```
    
- Verify NVM installation and set the default Node.js version.
    ```bash
    nvm --version
    ```
    
These steps should help you upgrade Node.js and address common problems that may arise during the process. Remember to test your Node.js projects to ensure compatibility with the new version.

If you encounter specific issues or need further assistance, please feel free to reach out for help.
