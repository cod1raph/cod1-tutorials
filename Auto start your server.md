If your server doesn't automaticaly start when the OS boots, it can be a concern. If the machine reboots for some reason, you could notice it only after quite some time.  
It's also just convenient to have the server starting automaticaly when the machine (re)boots.

Let's handle this simply, using `cron`.

In this tutorial, I assume you use a start script to start your server. Here I'll be using a start script that uses tmux, covered in [this tutorial](https://github.com/cod1raph/cod1-tutorials/blob/main/Run%20the%20server%20in%20background.md).

First, let's ensure the `crontab` command is available, enter:
1. `sudo apt update -y`
2. `sudo apt install cron -y`

Now, enter `crontab -e`.  
If it's the first time you enter this command, you will be asked to choose a text editor, I recommend nano.  
If you've never used nano before, see notes [here](https://github.com/cod1raph/cod1-tutorials/blob/main/Run%20a%20server%20with%20WSL.md#notes-about-nano-usage).

Now, go at the end of the file, and add this line:
```
@reboot /home/raph/myserver/startbackground.sh
```
Modify it for your own path.  
It should look like this:

<img width="544" height="222" alt="Screenshot 2026-02-25 020833" src="https://github.com/user-attachments/assets/f6dde672-106e-4c96-81c9-4b6bcd02540c" />

Save and close nano.

Now you should restart your Linux to verify: enter `sudo reboot`.  
Wait a bit, then try to connect to your server.



