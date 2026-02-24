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

...
