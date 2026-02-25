When you start your server, the text you write then goes into the server process: you can't use your Linux normally anymore.

If you run your server in a VPS, closing the SSH window will not stop your server, but when you will reconnect to the VPS, the server console will be gone.

A solution is to run the server in the background, to achieve this, we will use `tmux`.

You will become able to detach from the server console, keeping it running in the background.  
You will also be able to reattach to your server to go back to its console, even after you closed your Linux session.

First, install tmux using this command: `sudo apt install tmux`.

---
### Few notes about tmux
When you are in a tmux session, there is a green bar at the bottom

<img width="682" height="343" alt="Screenshot 2026-02-25 003124" src="https://github.com/user-attachments/assets/9b998d98-4190-4745-b817-51133c807c59" />

To detach from a session, do exactly like this:
1. Ctrl+b
2. Release all keys
3. Press `d`

---

Let's start simple, enter `tmux`: a new session will be created, and you will be attached to it automaticaly.  
Now, detach from it, as explained above. The green bar should disappear.

Do list active sessions: enter `tmux ls`

<img width="682" height="286" alt="Screenshot 2026-02-25 004403" src="https://github.com/user-attachments/assets/6a3bded1-034e-4a96-87f3-5eae2470bc01" />

As you can see, the tmux session is still there, and its id is `0`.

Attach to it: enter `tmux attach -t 0`.  
Now, detach.

Let's kill the session: enter `tmux kill-session -t 0`.  
Now do list active sessions again, you will see it's gone.

You can repeat the process, but do start your server when you are in the session, then detach, and close your Linux session: you could see from the client that your server is still running.  
Then open a new Linux session, and reattach to your tmux session: stop your server. Then detach and kill the session.

---
---
---

## Using a script

Let's make a script that will do everything.  
Assuming you already have a script to start your server, this new script will execute your current start script.

For clarity, go to the directory containing your start script,
in my case, the path is `/home/raph/myserver`, and my start script is named `start.sh` as you can see

<img width="535" height="232" alt="Screenshot 2026-02-25 010231" src="https://github.com/user-attachments/assets/13e9f98a-7265-4794-ad0e-d61943079a33" />

If you've never used nano before, see notes [here](https://github.com/cod1raph/cod1-tutorials/blob/main/Run%20a%20server%20with%20WSL.md#notes-about-nano-usage).  
Enter `nano startbackground.sh`, then paste this:
```sh
#!/bin/bash
SVR_DIR="$HOME/myserver"
SESSION_NAME="myserver-session"
tmux new-session -d -s "$SESSION_NAME"
tmux send-keys -t "$SESSION_NAME" "$SVR_DIR/start.sh" Enter
```
Replace `start.sh` by your current filename if needed.  
Replace `"$HOME/myserver"` by your own path if needed.  
Save and close.

Reminder: By default, `$HOME` contains the path to your user directory, in my case: `/home/raph`. You can verify by entering `echo $HOME`.

Now, make the file executable: enter `chmod +x startbackground.sh`.

Execute the script: enter `./startbackground.sh`.  
The server should now be running, you can list tmux sessions to verify.

---

When you want to do heavy tests on your server, like try to debug stuff etc, use a normal session instead of tmux, it's more reliable and avoids confusions.  
Use tmux when your server is ready to be played on.



