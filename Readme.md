# Moving WSL Distribution to Another Drive

This guide explains the process of moving a Linux distribution installed on Windows Subsystem for Linux (WSL) to another drive. In this example, we will be moving an Ubuntu 22.04 distribution, and the steps are outlined below.

## Prerequisites

- Windows operating system with WSL 2 installed.

## Instructions

1. Check the existing WSL 2 installations on your computer by running the following command in a WSL or Command Prompt window:

   ```
   wsl --list -v
   ```

   If the installation you want to move is currently running, you need to stop it. For example, if you want to move Ubuntu 22.04, terminate it using the following command:

   ```
   wsl -t Ubuntu-22.04
   ```

2. Export the WSL distribution to a folder. In this example, we will export Ubuntu 22.04 as `ubuntu-ex.tar` to the `D:\wsl\wsl_export` directory. Run the following command:

   ```
   wsl --export Ubuntu-22.04 "D:\wsl_export\ubuntu-ex.tar"
   ```

3. Unregister the previous WSL installation. This step removes the Ubuntu 22.04 distribution from the WSL 2 list obtained in the previous step. Execute the following command:

   ```
   wsl --unregister Ubuntu-22.04
   ```

4. Import the WSL installation to a new folder and re-register it. In this example, we will import Ubuntu 22.04 to the `D:\wsl_import\ubuntu` directory using the exported `ubuntu-ex.tar` file. Run the following command:

   ```
   wsl --import Ubuntu-22.04 "D:\wsl_import\ubuntu" "D:\wsl_export\ubuntu-ex.tar"
   ```

5. Set default user (optional): This step is only necessary if you're:
   Importing to a new machine or creating a new user for Ubuntu. Setting the default user avoids login prompts each time you launch the distribution.

   Using multiple users on your Windows machine and want different defaults for each. This clarifies which user launches by default for each WSL environment.

   To set the default user, run: `ubuntu.exe config --default-user me` (replace "me" with your actual username).

Congratulations! You have successfully moved your WSL distribution (Ubuntu 22.04) to another drive. You can now start the distribution and continue using it on the new location.
