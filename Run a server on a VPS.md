If you have never run a server using Linux before, I first recommend to do it using your Windows PC, with WSL, following [this tutorial](https://github.com/cod1raph/cod1-tutorials/blob/main/Run%20a%20server%20with%20WSL.md).

In this tutorial, we will run a server using Linux, without GUI.  
We will not run it on our own machine, we will use a remote machine: a VPS.

It has some advantages compared to using our own machine:
- VPS provide a reliable and fast internet.
- You don't have to keep your PC running for your server to stay online.

VPS access is not free: that would cost you about $7/month.

We will use AWS Lightsail (Amazon Web Services).

Create an AWS account by going to this address: https://aws.amazon.com/.

<img width="626" height="337" alt="Screenshot 2026-02-26 120632" src="https://github.com/user-attachments/assets/d50c71ae-ee22-4df7-9d8e-a38667bcd883" />

If AWS ever ask you to enable MFA, I recommend you to use the Google Authenticator app on Android.

Once your AWS account is created, go to this address: https://console.aws.amazon.com/.

Do log in if needed

<img width="423" height="259" alt="Screenshot 2026-02-26 120942" src="https://github.com/user-attachments/assets/23646caf-e97c-479c-8c6d-91238cf0226d" />

Then, open Lightsail

<img width="822" height="720" alt="Screenshot 2026-02-26 121246" src="https://github.com/user-attachments/assets/2aa9e2b3-792e-46b1-b9f7-307b1e2938d9" />

Click on "Create instance"

<img width="788" height="482" alt="Screenshot 2026-02-26 121614" src="https://github.com/user-attachments/assets/f0affdff-612f-4285-94db-a482d65e62eb" />

Change the region if needed

<img width="665" height="398" alt="Screenshot 2026-02-26 121735" src="https://github.com/user-attachments/assets/d4d2f265-d5c7-499d-83d1-4eef87906098" />

Choose OS only for Linux, and select the latest Debian version available

<img width="813" height="614" alt="Screenshot 2026-02-26 121942" src="https://github.com/user-attachments/assets/42836e2a-ecae-4582-912a-0a5c4f63064f" />

Leave these as default:

<img width="625" height="594" alt="Screenshot 2026-02-26 122334" src="https://github.com/user-attachments/assets/f251744a-43bd-4100-b589-8ada41c37d02" />

Now we will choose some specs, such as RAM and storage capacity,  
keep these as default:

<img width="716" height="371" alt="Screenshot 2026-02-26 122653" src="https://github.com/user-attachments/assets/85bb7bf0-adf2-44b1-b9f9-a0fe1338a33a" />

For now, go for the cheapest size. If later you see you miss ressources, you could create a new instance and delete this one.

<img width="700" height="471" alt="Screenshot 2026-02-26 122753" src="https://github.com/user-attachments/assets/a1f60f6f-a710-43ab-8035-0fdf400138ef" />

Finally, you can change default name. Then click the create button.

<img width="1069" height="661" alt="Screenshot 2026-02-26 123212" src="https://github.com/user-attachments/assets/48123600-6022-485e-a9ed-d60490a01829" />

Then, you will have to wait a bit for your VPS to become ready to use

<img width="764" height="365" alt="Screenshot 2026-02-26 123647" src="https://github.com/user-attachments/assets/ec86bf04-af53-4d2a-a924-cf4117802159" />

...

<img width="272" height="164" alt="Screenshot 2026-02-26 123809" src="https://github.com/user-attachments/assets/15157c0a-8675-4004-87bb-e850f3d7cb25" />

---
---
---
---

# Prepare access

We will attach a static IP to the instance, this way, if players add your server to favorites, it will never disappear because the IP will never change.  
Click the Manage button

<img width="519" height="249" alt="Screenshot 2026-02-26 233133" src="https://github.com/user-attachments/assets/89054a18-54d7-439f-9be4-64b2492f9620" />

Go to the Networking tab, then click "Attach static IP"

<img width="762" height="489" alt="Screenshot 2026-02-26 233234" src="https://github.com/user-attachments/assets/d08fa16c-f5de-456b-b3c4-58b8b7c7db95" />

You can change default name. Then click the Create button

<img width="639" height="297" alt="Screenshot 2026-02-26 233418" src="https://github.com/user-attachments/assets/aed26abf-7a86-4c5a-9d5c-09dccfc8fdd0" />

Still in the Networking tab, disable IPv6 networking, then delete the IPv4 HTTP rule

<img width="786" height="578" alt="Screenshot 2026-02-26 233642" src="https://github.com/user-attachments/assets/2d123598-eb32-40e7-bf5a-403e1ddba1fc" />

Now, we will open the required port for players to be able to join your server, click the "Add rule" button

<img width="379" height="255" alt="Screenshot 2026-02-26 233935" src="https://github.com/user-attachments/assets/dfd9ed4a-6884-4312-bcd5-8ec2c8f7682f" />

Add the 28960 UDP port, then click the Create button

<img width="755" height="138" alt="Screenshot 2026-02-26 234148" src="https://github.com/user-attachments/assets/65a740f0-058c-4b3a-a99c-30241d05aa43" />

Now, go to the Connect tab

<img width="694" height="271" alt="Screenshot 2026-02-26 234349" src="https://github.com/user-attachments/assets/9c586f83-428e-4de1-a1a3-557cf8ae20f7" />

Download your key file

<img width="575" height="241" alt="Screenshot 2026-02-26 234505" src="https://github.com/user-attachments/assets/25541fc7-7924-4ea5-aa3a-1b2ea1a923a9" />

To connect to the VPS, we will use PuTTY, download it from the official address: https://www.chiark.greenend.org.uk/~sgtatham/putty/

<img width="443" height="218" alt="Screenshot 2026-02-26 235044" src="https://github.com/user-attachments/assets/6f160d9e-fe3d-4144-9bd7-fe2b4b8dd7c8" />

For Windows 64-bit:

<img width="522" height="148" alt="Screenshot 2026-02-26 235212" src="https://github.com/user-attachments/assets/3ea514b8-bc88-438a-a000-937ae8d61964" />

Once installed, we will have to convert the key we downloaded, to the ppk format.  
Open PuTTYgen

<img width="692" height="750" alt="Screenshot 2026-02-26 235643" src="https://github.com/user-attachments/assets/bfc8eb67-9501-4595-b959-1ecc238c9449" />

Click the Load button, then display all files

<img width="913" height="568" alt="Screenshot 2026-02-26 235959" src="https://github.com/user-attachments/assets/ba3b92ae-4aa0-4d4b-b187-5608b87cbb4b" />

Open the key file you downloaded previously, then click OK

<img width="331" height="185" alt="Screenshot 2026-02-27 000104" src="https://github.com/user-attachments/assets/0b5db30f-a138-4985-9c82-01afd6ce0676" />

Finally, click the "Save private key" button and confirm

<img width="596" height="307" alt="Screenshot 2026-02-27 000233" src="https://github.com/user-attachments/assets/2345f5b2-4634-49a2-b46c-5283003bab45" />

I recommend to add the country of the VPS in the filename, like `key-codserver-singapore`.  
Once saved, close PuTTYgen.

# Access the VPS

Now we will connect to the VPS, open PuTTY

<img width="690" height="726" alt="Screenshot 2026-02-27 001131" src="https://github.com/user-attachments/assets/80c88ecf-4dde-4b6a-ba9c-34cafd623967" />

Go copy your static IP from Lightsail website

<img width="544" height="327" alt="Screenshot 2026-02-27 001413" src="https://github.com/user-attachments/assets/a141d9ed-345b-4d96-9dd3-ee897f0d2df9" />

Paste your IP, then open the Credentials window

<img width="452" height="442" alt="Screenshot 2026-02-27 001621" src="https://github.com/user-attachments/assets/5c6db147-1c8e-4077-bf3f-fdd9f812d86d" />

Select your ppk key file

<img width="335" height="151" alt="Screenshot 2026-02-27 001755" src="https://github.com/user-attachments/assets/9ab853cc-0aec-4034-bf11-7e57ad49dc9d" />

Then, go back to the Session window, and click Open

<img width="381" height="422" alt="Screenshot 2026-02-27 002033" src="https://github.com/user-attachments/assets/ee34db9f-9cea-4c26-b643-25403f4eb0af" />

Do accept

<img width="690" height="251" alt="Screenshot 2026-02-27 002159" src="https://github.com/user-attachments/assets/1ee10c36-540a-4176-ab59-f290cae7b671" />

Enter `admin`

<img width="281" height="125" alt="Screenshot 2026-02-27 002253" src="https://github.com/user-attachments/assets/bd89180b-2d22-45e4-ad63-115ecb0e9827" />

You are now connected to the VPS, as the `admin` user. Your working directory is your user directory, as you can see by entering `pwd`

<img width="293" height="70" alt="Screenshot 2026-02-27 002627" src="https://github.com/user-attachments/assets/a0644766-2587-413f-869e-97a7eda395f4" />

To close the session, enter `exit`.

---
---
---
---

# Place the game files

We're gonna place the game files for our server.  
If you are not comfortable with basic Linux usage, see some notes [here](https://github.com/cod1raph/cod1-tutorials/blob/main/Run%20a%20server%20with%20WSL.md#notes-about-few-commands).

Now, in your user directory, we we will create 2 folders, one to hold the CoD base files, and the other one specific to your server stuff.  
Enter `mkdir -p cod_basefiles/main`, then enter `mkdir -p myserver/main`.

Let's verify, enter `ls`

<img width="497" height="141" alt="Screenshot 2026-02-27 005442" src="https://github.com/user-attachments/assets/285e77dd-3b32-4d6f-9527-cdca941a7bba" />

Let's start by adding the server executable file, and the game library.  

There is no more official link. On your PC, download the archive from [dvotx/cod.pm](https://de.dvotx.org/dump/cod1/cod-lnxded-1.1d.tar.bz2) or [vcodmods](https://vcodmods.com/server/cod-lnxded-1.1d).  
Extract the archive.

We will send `cod_lnxded` and `game.mp.i386` to the VPS, using WinSCP. Download it from the official address: https://winscp.net/  
Once installed, open it.

Enter the static IP, the username, then click "Advanced..."

<img width="608" height="413" alt="Screenshot 2026-02-27 010421" src="https://github.com/user-attachments/assets/5d343b69-284e-4021-8b9f-0f8daedf57d6" />

Go to "Authentication", select your ppk file, and confirm.

<img width="686" height="490" alt="Screenshot 2026-02-27 010817" src="https://github.com/user-attachments/assets/e102969e-27e5-4460-b5fb-5e86c20ddf5f" />

Do log in

<img width="396" height="119" alt="Screenshot 2026-02-27 010934" src="https://github.com/user-attachments/assets/d59341b8-7683-4b7e-9093-44c25951781f" />

Do accept

<img width="494" height="198" alt="Screenshot 2026-02-27 011517" src="https://github.com/user-attachments/assets/e73a0c3e-e5c6-42bd-8110-9cfb5391fa04" />

Once connected, you will see on the left part your PC files, and on the right the VPS files, by default in your user directory.  
Do drag the 2 files mentionned above, from the left to the right, but not in the directories we created previously, we will move them manually afterwards.  
The result should look like this:

<img width="763" height="375" alt="Screenshot 2026-02-27 011924" src="https://github.com/user-attachments/assets/879f6a8d-1f5f-4d84-a024-346b555da2a5" />

You can close WinSCP.

Now, in PuTTY, we will move the 2 files at the proper location.  
First, let's do `ls` for clarity

<img width="483" height="85" alt="Screenshot 2026-02-27 013917" src="https://github.com/user-attachments/assets/81bcdad6-e2cb-480a-9ffd-4620f778222c" />

Note: To paste text in PuTTY, copy the text from your PC, then when you will right click in the PuTTY window, the text will be pasted.

Enter:
1. `mv cod_lnxded myserver/`
2. `mv game.mp.i386.so cod_basefiles/main/`

For clarity, `ls` again

<img width="551" height="116" alt="Screenshot 2026-02-27 014254" src="https://github.com/user-attachments/assets/1e89f807-ddaf-482c-a851-a6e73602334f" />

Now, we miss the original pk3 files: pak0.pk3, pak1.pk3, pak2.pk3, pak3.pk3, pak4.pk3, pak5.pk3, pak6.pk3, localized_english_pak0.pk3 and localized_english_pak1.pk3.  
We will have to put them in `cod_basefiles/main`.  
If you have a fast internet connection, like optical fiber, you can probably send these files from your client `main` folder to the VPS using WinSCP.

Here, we will download the files directly from the VPS, thanks to this link: https://de.dvotx.org/dump/cod1/downloads.php?get=basefilesfull.

To achieve this, from our user directory, we enter this: `wget https://de.dvotx.org/dump/cod1/downloads.php?get=basefilesfull`.  
And wait for completion

<img width="1113" height="240" alt="Screenshot 2026-02-27 015511" src="https://github.com/user-attachments/assets/0fb8888b-64c5-458f-9fe6-62d7dcc694af" />

Again, do `ls`

<img width="530" height="80" alt="Screenshot 2026-02-27 015559" src="https://github.com/user-attachments/assets/0ad8a9c4-7880-4f37-8e6d-ad1266e41ab1" />

To extract, we need to install `unzip`, enter:
1. `sudo apt update -y`
2. `sudo apt install unzip -y`

Now, enter `unzip 'downloads.php?get=basefilesfull'`, and wait for completion

<img width="582" height="225" alt="Screenshot 2026-02-27 015943" src="https://github.com/user-attachments/assets/398a7739-1dd7-4cee-9417-5c5338c29ea7" />

Do `ls`

<img width="899" height="111" alt="Screenshot 2026-02-27 020037" src="https://github.com/user-attachments/assets/ea95a82d-3661-44eb-9eb4-9b961b95cdb4" />

We can now delete the archive, enter `rm 'downloads.php?get=basefilesfull'`.

Then, let's move the pk3 files to the proper location, enter:
```
mv pak* localized_english_pak* cod_basefiles/main/
```

Don't hesitate to enter `ls` after moving files, it helps to visualize the results.  
Also, it's comfortable to use `clear` (or Ctrl+l), to hide old stuff.

---
---
---
---

# Start the server

Begin by doing like for the WSL tutorial [here](https://github.com/cod1raph/cod1-tutorials/blob/main/Run%20a%20server%20with%20WSL.md#start-the-server), then come back here when you reach the start script content.

So, for the start script, paste this content:
```sh
#!/bin/sh
SVR_DIR="$HOME/myserver"
"$SVR_DIR/cod_lnxded" +set fs_basepath "$HOME/cod_basefiles" +set fs_homepath "$SVR_DIR" +set net_ip 172.26.12.66 +map_rotate
```
Replace the IP by your own private IP, you can find it on the Lightsail website here:

<img width="535" height="348" alt="Screenshot 2026-02-27 021858" src="https://github.com/user-attachments/assets/4e481380-14b5-417b-9234-3539e9975728" />

Notes:
- When using other VPS providers, you might have to use the static IP instead.
- Static IP = Public IP = External IP
- Private IP = Internal IP

Now, make the `cod_lnxded` file executable, enter: `chmod +x cod_lnxded`.

Finish by going back to the WSL tutorial, after the start script content, but ignore the part about `hostname -I`: you will see your server appearing directly in the client server browser.
