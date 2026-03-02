pk3 files are zip archives but with the pk3 extension.

They contain files required for the client, such as images.

## Browsing

You can browse them, and modify their content without needing to extract them, for that, you need to install [7-Zip](https://www.7-zip.org/).

Here is how browsing looks:

<img width="678" height="513" alt="Screenshot 2026-02-22 235440" src="https://github.com/user-attachments/assets/14f96d7f-b740-4ae8-84b7-0a2698f041b7" />

## Creating

First, be sure to make your File Explorer display "File name extensions", like this:

<img width="602" height="604" alt="Screenshot 2026-02-22 235915" src="https://github.com/user-attachments/assets/cf803134-3d34-43e7-bf1e-1456f93adf2e" />

Now, let's take an empty folder, it will be the content of our pk3.  
First, compress it to zip file, like this:

<img width="569" height="439" alt="Screenshot 2026-02-23 000346" src="https://github.com/user-attachments/assets/5e59d233-e8db-4a65-a2f0-ac1224e64fa5" />

Then, rename it, replacing `.zip` by `.pk3`, and confirm, like this:

<img width="646" height="375" alt="Screenshot 2026-02-23 000656" src="https://github.com/user-attachments/assets/d8aae794-5cf6-413f-a88c-f311e10400d6" />

## Adding files

To add files to your pk3, open the pk3 with 7-Zip, then just drag your file (or folder) into the window, then confirm:

<img width="335" height="154" alt="Screenshot 2026-02-23 001312" src="https://github.com/user-attachments/assets/2c5215d1-b1ab-4aae-a399-aa1b669f4bd1" />

## Updating files

To update/replace files in your pk3, do just like explained above for adding files: drag it at the same location as the old one, then confirm.

---

If 2 pk3 files contain a file with same filename and path, the file from the pk3 that comes later alphabetically will replace the file from the pk3 that comes earlier.  
So `qak.pk3` overrides `pak.pk3`, and `pak2.pk3` overrides `pak1.pk3`. You can verify using the `path` command.
