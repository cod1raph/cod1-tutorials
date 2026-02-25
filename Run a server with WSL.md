To run a proper online server, you need to use the Linux OS instead of Windows, for 2 main reasons:

1. The mods created by the community, to fix bugs and security issues, are made for Linux.
2. It takes less ressources and it's more reliable to run on a remote computer, like a VPS.

To spend even less ressources, and increase reliability even more, we will use Linux without GUI: we will not manage files using the mouse.

In this tutorial we will run the server on our own computer, not reachable online,  
later, it would take just few aditional steps to make it reachable by players on internet, this part would be covered in another tutorial.

Now, we will run Linux on our Windows PC, thanks to WSL, which is a light and reliable tool.  
There is many different Linux versions, we will use the basic "Debian".

Let's install WSL, for this, right click the Windows start button, then click "Terminal (Admin)"

<img width="319" height="721" alt="Screenshot 2026-02-24 015707" src="https://github.com/user-attachments/assets/ff4abe93-03ba-40c6-83f8-001102f6b64a" />

Then enter `wsl --install --no-distribution`

<img width="745" height="343" alt="Screenshot 2026-02-24 020342" src="https://github.com/user-attachments/assets/1db187bf-8026-4923-bd84-3d258cf99aaa" />

Now, we will install Debian,  
for clarity, we will first list available versions, for this enter: `wsl --list --online`

<img width="745" height="799" alt="Screenshot 2026-02-24 020711" src="https://github.com/user-attachments/assets/fff556fa-8450-4991-bb25-b04f0ee90f3d" />

Now, enter `wsl --install Debian --no-launch`, and wait for completion:

<img width="808" height="343" alt="Screenshot 2026-02-24 022307" src="https://github.com/user-attachments/assets/8f21bfa9-7149-45bd-8c2d-e8380b15e521" />

You can now close the window.  
In the future, if you want to restart from scratch, you can erase your Debian using `wsl --unregister Debian`, then you can install again.

---
---
---
---

# Start Linux
Find "Debian" in your Windows Start Menu:

<img width="376" height="427" alt="Screenshot 2026-02-24 022712" src="https://github.com/user-attachments/assets/9b73940d-035a-45bb-93e3-ffc304f7aadf" />

On first launch, you will have to chose a username:

<img width="681" height="368" alt="Screenshot 2026-02-24 022920" src="https://github.com/user-attachments/assets/fa19b4b1-bc4d-4320-bd24-aae78dc8e95b" />

Then, a password, it will not appear when typing, it's normal,  
you will have to enter it twice:

<img width="637" height="363" alt="Screenshot 2026-02-24 023012" src="https://github.com/user-attachments/assets/9ba557c7-c487-4119-bdee-694a93fa9384" />

Then, you will be active at your user directory:

<img width="658" height="385" alt="Screenshot 2026-02-24 023318" src="https://github.com/user-attachments/assets/c9089af0-cfbb-466b-aeb5-283b789d736b" />

Before setting up the server, look how to stop Debian, enter `exit`

<img width="615" height="383" alt="Screenshot 2026-02-24 024108" src="https://github.com/user-attachments/assets/f9fe8441-e1ea-4719-9567-4bd72acc6c32" />

... the window will close.

---
---
---
---

# Place the game files

Run Debian, again, you will become active at your user directory.  
There, we will create 2 folders, one to hold the CoD base files, and the other one specific to your server stuff.  

One important thing when using Linux, is to "know where you are", enter `pwd`, it will display your working directory

<img width="399" height="180" alt="Screenshot 2026-02-24 025632" src="https://github.com/user-attachments/assets/08bd6ea8-0cfc-47c9-b738-2abb035471da" />

See this:

<img width="295" height="61" alt="Screenshot 2026-02-24 025846" src="https://github.com/user-attachments/assets/b1b7f0bd-e9f8-43e6-abb1-d65bdbb9628a" />

This part already shows your working directory.  
`~` is your user folder.  `~` is equivalent to `/home/raph`.

---
### Notes about few commands
- `mkdir`: to create a folder  
- `cd`: to navigate  
- `cp`: to copy

Using `cd`, you can either specify an absolute path, or a relative path.  
Using an absolute path allows to reach the destination no matter from where you entered the command, and using a relative path allows to reach the destination according to where you were when you entered the command.  
In fact, this system applies to other commands too.  
`..` means the parent folder of your working directory (where you are), so you can do `cd ..` to go "above".  
`/` is the root, there is nothing above it.  
When you press the tab key, it auto completes with available filenames/directories, it's usefull to save time, avoid typos, verify that what you expect is actually there etc.

---

Let's create the 2 folders in your user directory, enter `mkdir -p cod_basefiles/main`, then enter `mkdir -p myserver/main`.  
(`-p` allows to create the parent directory and the subdirectory simultaneously)

Now let's verify, enter `ls` to see what there is where you are.

<img width="544" height="267" alt="Screenshot 2026-02-24 031512" src="https://github.com/user-attachments/assets/83cc480f-46c0-4518-bb17-da0eb23ec222" />

Let's start by adding the base files, by using the game client we use to play.  
In my case, my client is on my desktop, in a "Call of Duty" folder.  
We will have to copy all the original pk3 files from the main folder.

The path to my main folder is `C:\Users\raphael\Desktop\Call of Duty\main`  
From my Linux, the path is `/mnt/c/Users/raphael/Desktop/Call of Duty/main`  

So to copy all pk3 files from my client to my Linux folder, I do:  
```
cp /mnt/c/Users/raphael/Desktop/Call\ of\ Duty/main/pak* /home/raph/cod_basefiles/main/
```
Then:
```
cp /mnt/c/Users/raphael/Desktop/Call\ of\ Duty/main/localized_english_pak* /home/raph/cod_basefiles/main/
```
I used only absolute paths in this case, if I first went to my client main folder using `cd`, I could have used a single and shorter command instead, thanks to relative paths, like this:  
```
cp pak* localized_english_pak* /home/raph/cod_basefiles/main/
```

While it copies, it can take some time, while you can't write in terminal.

---
Now we will download the server executable file, and the game library.

There is no more official link, so download the archive from [dvotx/cod.pm](https://de.dvotx.org/dump/cod1/cod-lnxded-1.1d.tar.bz2) or [vcodmods](https://vcodmods.com/server/cod-lnxded-1.1d).  
Extract the archive.  
Then from Linux, copy the `game.mp.i386` file from the main folder, here is the command in my case:
```
cp /mnt/c/Users/raphael/Downloads/cod-lnxded-1.1d/main/game.mp.i386.so /home/raph/cod_basefiles/main/
```
Your `cod_basefiles` folder is now ready.

The last game file to copy is the executable, you have to put it in the other folder we created, but not in `main` this time, here is the command for my case:
```
cp /mnt/c/Users/raphael/Downloads/cod-lnxded-1.1d/cod_lnxded /home/raph/myserver/
```

---
---
---
---

# Start the server

First we will create our config file, for that, go in the `myserver/main` directory, we will use the nano editor.

### Notes about nano usage
- Save: Ctrl+o, then Enter
- Close: Ctrl+x, then press `y`, then Enter. (no need to press y if you saved manually before closing)
- To paste text in WSL, copy from Windows, then just press right click in the Debian window.

Let's create the file, enter `nano autoexec_mp.cfg`, then paste this:
```
set sv_hostname "servername"
set sv_maxclients "8"
set rconpassword ""
set g_password ""
set sv_pure "0"
set sv_mapRotation "gametype sd map mp_harbor"
```
Save and close nano.  
Later, reopen this file to customize your server as you want.

Now we will create a script. When you will want to run your server, you will have to execute this script.  
Go back to `myserver` (enter `cd ..`)  
There we will create the script, enter `nano start.sh`, and paste this:
```sh
#!/bin/sh
SVR_DIR="$HOME/myserver"
"$SVR_DIR/cod_lnxded" +set fs_basepath "$HOME/cod_basefiles" +set fs_homepath "$SVR_DIR" +map_rotate
```
Save and close.  
Now we need to make this script executable, for this enter `chmod +x start.sh`

The last step before being able to run the server, is to install `libc6-i386`,  
to achieve this, enter `sudo apt update -y`, then `sudo apt install libc6-i386 -y`.

Now you can finally start your server, by entering `./start.sh`.

To stop the server, enter `quit`.

To join your local server, you need the IP of the Debian, first stop the server if it's running, then enter `hostname -I`.  
To copy the IP, highlight it, then press Enter, the text will now be in your clipboard.  
You can restart the server, and `/connect` to it from the client.

You will see this message:

<img width="666" height="146" alt="Screenshot 2026-02-24 083045" src="https://github.com/user-attachments/assets/db893820-42c1-4814-940b-03c908c23d98" />

To bypass this, you need to setup iw1x-server using [this tutorial](https://github.com/cod1raph/cod1-tutorials/blob/main/Setup%20iw1x-server.md).  
You will have to enable the `sv_cracked` feature.

To run the server in the background, follow [this tutorial](https://github.com/cod1raph/cod1-tutorials/blob/main/Run%20the%20server%20in%20background.md).

---

The server will not appear in the client browser for local source.  
A workaround is to create a new favorite and enter the ip, with any name, then it will appear in the browser.  
Note: The IP might change sometimes.
