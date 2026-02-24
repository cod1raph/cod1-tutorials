CoD1 is not maintained by its developers anymore, bugs and security issues remain unfixed by them.

But there is still a solution to fix these issues without needing their intervention: injecting a library into the `cod_lnxded` process.

Using reverse engineering, you can examinate it to figure out where issues occur and how to fix them.

The injected library will interact with the memory of the process to modify the original behavior.

Let's say you already have a server, that you run using a script, now you will have to download the iw1x-server library.

Download `iw1x.so` from the latest release here: https://github.com/cod1raph/iw1x-server-r/releases

Then, copy the file in the same directory of your `cod_lnxded`.

We have to modify your start script, here is my script that don't use iw1x:

```sh
#!/bin/sh
SVR_DIR="$HOME/myserver"
"$SVR_DIR/cod_lnxded" +set fs_basepath "$HOME/cod_basefiles" +set fs_homepath "$SVR_DIR" +map mp_harbor
```
To make it inject the iw1x lib, we need to add `LD_PRELOAD="$SVR_DIR/iw1x.so"`, so it becomes like this:
```sh
#!/bin/sh
SVR_DIR="$HOME/myserver"
LD_PRELOAD="$SVR_DIR/iw1x.so" "$SVR_DIR/cod_lnxded" +set fs_basepath "$HOME/cod_basefiles" +set fs_homepath "$SVR_DIR" +map mp_harbor
```

This library requires `libstdc++6:i386`, here is how to install it:
1. `sudo dpkg --add-architecture i386`
2. `sudo apt update`
3. `sudo apt install libstdc++6:i386`

Now you can execute your start script as usual.  
Verify that the library gets injected by searching for this line:

<img width="726" height="313" alt="Screenshot 2026-02-24 080837" src="https://github.com/user-attachments/assets/1624b86d-490f-4cad-948b-5b66ac8a4e06" />

---
---

## Using the features

To use the features, we use cvars. The iw1x-server repository has a dedicated cfg file here: https://github.com/cod1raph/iw1x-server-r/blob/main/iw1x.cfg.  
Download this file and copy it in your server main folder (in the same folder of your config file, `autoexec_mp.cfg` in my case).  
Open your config file, and add this line at the end: `exec iw1x.cfg`.

Edit iw1x.cfg to suit your needs.
