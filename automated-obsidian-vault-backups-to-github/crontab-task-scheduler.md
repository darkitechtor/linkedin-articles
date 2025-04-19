# Automated **Obsidian** Vault backups to **GitHub** with **crontab**

1. Add a SSH Key to **GitHub** if you haven't done it yet. [There's an instruction how to do that](use-ssh-key-for-github.md).
2. Create a bash script with a bunch of commands to stage, commit and push changes (I push them directly to the `main` branch, however you can use any):

    ```sh
    #!/bin/bash

    cd /path/to/your-vault
    git add .
    git commit -m "Auto commit on $(date '+%Y-%m-%d %H:%M:%S')"
    git push origin main
    ```

3. Make the script executable:

    ```sh
    chmod u+x /path/to/your-script.sh
    ```

4. Add new task to **crontab**:
   1. Open **crontab**: `crontab -e`
   2. Add a new line with following command:

       ```sh
       0 * * * * sh /path/to/your-script.sh >> /path/to/your-script.log 2>&1
       ```

       *Don't forget to adjust this command and set proper schedule and paths!*

       This command runs iur bash script. Despite `>> /path/to/your-script.log 2>&1` part is optional, I highly recommend to add it since it simplifies the process of debugging your task in case of any issues. Actually, it's just a command to write down the output into the file, and `2>&1` is an instruction to write down errors too.

   3. Save it, confirm, and do a test run. I recommend to have some uncommitted changes before the testing, otherwise the test can't be decided as "full".

[Back to main page](/automated-obsidian-vault-backups-to-github/main_page.md)
