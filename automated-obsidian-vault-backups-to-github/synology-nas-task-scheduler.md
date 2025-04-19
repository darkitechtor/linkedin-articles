# Automated **Obsidian** Vault backups to **GitHub** with **Synology** NAS **Task Scheduler**

1. Add a SSH Key to **GitHub** if you haven't done it yet. [There's an instruction how to do that](use-ssh-key-for-github.md).
2. Create a bash script with a bunch of commands to stage, commit and push changes (I push them directly to the `main` branch, however you can use any):

    ```sh
    #!/bin/bash

    cd /path/to/your-vault
    git add .
    git commit -m "Auto commit on $(date '+%Y-%m-%d %H:%M:%S')"
    git push origin main
    ```

3. Go to **Control Panel** > **Services** > **Task Scheduler** and create a new task:
    1. Create > Scheduled Task > User-defined script
    2. Give it a suitable name (`Task`) and select *the same user who owns the repo* as `User`, otherwise you are going to face `fatal: detected dubious ownership in repository` error while trying to push to the repo. In fact, there're some other ways to avoid this issue, but this one is the simplest and suits cases of most users.
    3. Set schedule on `Schedule` tab
    4. Go to `Task Settings` tab and paste a command:

        ```sh
        sh /path/to/your-script.sh >> /path/to/your-script.log 2>&1
        ```

        This command runs iur bash script. Despite `>> /path/to/your-script.log 2>&1` part is optional, I highly recommend to add it since it simplifies the process of debugging your task in case of any issues. Actually, it's just a command to write down the output into the file, and `2>&1` is an instruction to write down errors too.

    5. Save it, confirm, and do a test run. I recommend to have some uncommitted changes before the testing, otherwise the test can't be decided as "full".

[Back to main page](/automated-obsidian-vault-backups-to-github/main_page.md)
