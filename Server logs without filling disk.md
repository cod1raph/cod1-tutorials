Keeping logs is very important to examinate events in order to try to fix issues after they occured.

CoD1 has a `logfile` cvar, when enabled, it writes the content of the console to a file named `console_mp_server.log`, in `main` folder.

A concern would be that if you keep your server running for months without deleting old logs manually, maybe that would fill the disk and cause issues.

A solution is to use the `logrotate` Linux tool.  
What will happen is that after some time, the log file will be archived, and its content will be cleared for the new logs to come.  
Again and again, but we will choose to keep max 3 archives: the oldest one will keep getting replaced by the one that got archived just before itself.

This system will allow us to keep the most recent logs, and automaticaly delete the oldest ones, so we will not have to worry about filling the disk.

Let's create the logrotate config file for our server, go to `/etc/logrotate.d/`.  
Enter `sudo nano mycodserver`, then paste this:
```
/home/raph/myserver/main/console_mp_server.log
{
    # before rotating
    size 200M
    # amount of logs to keep
    rotate 3
    compress
    missingok
    notifempty
    # prevent original file renaming
    copytruncate
}
```
Edit the path for your setup.  
Finally, save and close nano.

Now we will verify if it works, first be sure to have a non-empty `console_mp_server.log` file in your main folder, you can just start then stop your server to generate it.

Let's ensure the `logrotate` command is available, enter:
1. `sudo apt update -y`
2. `sudo apt install logrotate -y`

Then, enter this: `sudo logrotate -f /etc/logrotate.d/mycodserver`

Finally, check in your main folder to see if an archive got created:

<img width="1024" height="267" alt="Screenshot 2026-02-24 100643" src="https://github.com/user-attachments/assets/932b982c-0c6f-49c7-80ef-ce6d777078b7" />

---

Be careful:

- When you stop your server, be sure to enter `quit` instead of Ctrl+c, or you would lose some logs at the end of the file.
- When you start your server, the new logs will not get appended to the file: the old content gets cleared.

