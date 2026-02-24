(under construction)

# Create a server

To run a proper online server, you need to use the Linux OS instead of Windows, for 2 main reasons:

1. The mods created by the community, to fix bugs and security issues are made for Linux.
2. It takes less ressources and it's more reliable to run on a remote computer, like a VPS.

To spend even less ressources, and increase reliability even more, we will use Linux without GUI, we will not be able to manage files using the mouse.

In this tutorial we will run the server on our own computer, not reachable online,  
later, it would take just few aditional steps to make it reachable by players from internet, this part would be covered in another tutorial.

Now, we will run Linux on our Windows PC, thanks to WSL, it is a light and reliable tool.  
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

---
---

Now, let's start Linux, find "Debian" in your Windows Start Menu:

<img width="376" height="427" alt="Screenshot 2026-02-24 022712" src="https://github.com/user-attachments/assets/9b73940d-035a-45bb-93e3-ffc304f7aadf" />

On first launch, you will have to chose a username:

<img width="681" height="368" alt="Screenshot 2026-02-24 022920" src="https://github.com/user-attachments/assets/fa19b4b1-bc4d-4320-bd24-aae78dc8e95b" />

Then, a password, it will not appear when typing, it's normal,  
you will have to enter it twice:

<img width="637" height="363" alt="Screenshot 2026-02-24 023012" src="https://github.com/user-attachments/assets/9ba557c7-c487-4119-bdee-694a93fa9384" />

Then, you will be active at the home directory of your user:

<img width="658" height="385" alt="Screenshot 2026-02-24 023318" src="https://github.com/user-attachments/assets/c9089af0-cfbb-466b-aeb5-283b789d736b" />

Before setting up the server, look how to stop Debian, enter `exit`

<img width="615" height="383" alt="Screenshot 2026-02-24 024108" src="https://github.com/user-attachments/assets/f9fe8441-e1ea-4719-9567-4bd72acc6c32" />

... the window will close.

---
---

...
