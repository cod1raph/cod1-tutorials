(under construction)

If your server doesn't automaticaly start when the OS boots, it can be a concern. If the machine reboots for some reason, you could notice it only after quite some time.  
It's also just convenient to have the server starting automaticaly when the machine (re)boots.

Let's handle this simply, using `cron`.

In this tutorial, I assume you use a start script to start your server. Here I will use the start script that uses tmux, covered in [this tutorial](https://github.com/cod1raph/cod1-tutorials/blob/main/Run%20the%20server%20in%20background.md).

Enter `crontab -e`.  
If it's the first time you enter this command, you will be asked to choose a text editor, I recommend nano.  
If you've never used nano before, see notes [here](https://github.com/cod1raph/cod1-tutorials/blob/main/Run%20a%20server%20with%20WSL.md#notes-about-nano-usage).

Now, go at the end of the file, and add this line:
```

```
