(under construction)

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

When your AWS account is created, go to this address: https://console.aws.amazon.com/.

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

Finally, give a proper simple name to your instance, and click the create button.

<img width="1069" height="661" alt="Screenshot 2026-02-26 123212" src="https://github.com/user-attachments/assets/48123600-6022-485e-a9ed-d60490a01829" />

---
---
---







