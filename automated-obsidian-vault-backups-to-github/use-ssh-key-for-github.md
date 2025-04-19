# How to use SSH key for **GitHub**

1. Open terminal and command

    ```sh
    ssh-keygen -t rsa -b 4096 -C "your-email@example.com"
    ```

2. Copy public key

    ```sh
    cat ~/.ssh/id_rsa.pub
    ```

3. Add key to **GitHub**:
    1. Profile > Settings > SSH and GPG keys
    2. Click **New SSH key**
    3. Give it a name
    4. Paste the key

4. Test SSH Access to **GitHub**:

    ```sh
    ssh -T git@github.com
    ```

    You should see something like: `Hi your-username! You've successfully authenticated, but GitHub does not provide shell access.`

    In case if `Permissions 0777 for '.ssh/id_rsa' are too open` error appears you have to set proper permissions by running the following commands in terminal:

    ```sh
    chmod 600 ~/.ssh/id_rsa
    chmod 644 ~/.ssh/id_rsa.pub
    chmod 700 ~/.ssh
    ```

   Then test the SSH access again.

5. Make sure that Git uses SSH to connect:

    ```sh
    cd /path/to/your-repo
    git remote -v
    ```

    If you see a HTTPS URL, change it to SSH:

    ```sh
    git remote set-url origin git@github.com:your-username/your-repo.git
    ```

    After that you will be able to push to **GitHub** without using your password/token.

[Back to main page](/automated-obsidian-vault-backups-to-github/main_page.md)
