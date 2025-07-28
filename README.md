<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Group Policy and Managing  Accounts in Active Directory</h1>
This project demonstrates how I created Group Policy Objects and managed accounts in Active Directory..<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (22H2)

<h2>Walkthrough</h2>

<p>
<img src="https://github.com/user-attachments/assets/81e4d9b1-ebdb-4524-9052-cb786d4325c8" />
</p>
<p>

  - To begin the project, I logged into DC-1 as jane_admin (mydomain.com\jane_admin).
  - Once logged, I right-clicked the start menu and selected "Run".
  - I entered "gpmc.msc" to open the Group Policy Management Console.

</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/6f131d59-f45c-4148-a5f1-d78e091d67a9" width=800/>
</p>
<p>

  - Under mydomain.com, I right-clicked the "Default Domain Policy" and selected "Edit".
  - This opened the Group Policy Management Editor.

</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/5649c4ab-2135-4807-b625-210fe8753d95" width=800
</p>
<p>

  - Once there, I navigated to the "Account Lockout Policy" section.

</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/1d9915c4-9973-44a1-96d0-274ba24336fb" />
</p>
<p>

  - For the "Account Lockout Duration", I set the time to 30 minutes.
  - For the "Account Lockout Threshold", I set the login attempts to 5.
  - This means that the user's account will be locked after 5 failed login attempts and can't be used for 30 minutes (unless an admin manually unlocks it).

</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/ee6edd4b-46a8-412c-b03d-ec13f19be9af" width=800/>
</p>
<p>

  - After applying the settings, I went back into DC-1 as jane_admin and selected a random user (bib.tel) in Active Directory to test the new Group Policy settings.

</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/75cefbf6-3710-4c2b-8a25-4f70a7f8d82d" />
</p>
<p>

  - Next, I attempted to log into Client-1 as "bib.tel" 5 times with an invalid password.
  - After 5 unsuccessful login attempts, the user account (bib.tel) was locked.

</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/8061e158-349b-4017-abc0-2b1f4f38f16a" />
</p>
<p>

  - After locking the account, I went back into DC-1 as jane_admin and navigated to Active Directory Users and Computers
  - From there, I located the user "bib.tel" and navigated to the "Account" tab where I unlocked the account.

</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/1b33f254-82d5-49a4-adea-384c7b6b4f98" />
</p>
<p>

  - After unlocking the account, I was able to successfully login to Client-1 as "bib.tel".
  - I went into Powershell and entered "whoami" to confirm that the account was unlocked.

</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/709fff9e-8423-46d4-a44b-8cb8cc05b9d2" width=500/>
</p>
<p>

  - Back in DC-1, I located the user "bib.tel" and navigated to the password reset settings to ensure I understood where to apply changes if needed in a real scenario.

</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/08df2dc9-c594-442f-82ef-6cbc59ae0b47" width=800/>
</p>
<p>

   - To finish the project, I went back into Client-1 as jane_admin and opened the Event Viewer.
   - From there, I was able to view the security logs showing the failed login attempts from the user "bib.tel".


