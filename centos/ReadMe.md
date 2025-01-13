# Vagrant and Git setup

## Steps Performed

- **Installed vagrant on the system using choco** 
  - Verified the installation using
  ```bash
  vagrant --version
  ```

- **Created a project folder**
  - Created a folder named centOS
    ```bash
    mkdir centos
    cd centos
    ```
- **Initialized Vagrant**
  ```bash
  vagrant init
  ```
- **Initialized GIt**
  - Set up version control
    ```bash
    git init
    git add .
    git commit -m "Inital commit"
    git remote add origin "url"
    git branch -M main
    git push -u origin main
    ```
- **Started and Accessed the VM**
  ```bash
  vagrant up
  vagrant ssh
  ```


