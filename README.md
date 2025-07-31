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
<h3> Section 1: Accessing the Group Policy Management Console </h3>
<p>
<img src="https://github.com/user-attachments/assets/81e4d9b1-ebdb-4524-9052-cb786d4325c8" />
</p>
<p>

  - To begin the project, I logged into DC-1 as the domain admin (jane_admin) to begin the Group policy configuration process.
  - I accessed the Run dialog and entered "gpmc.msc" to launch the Group Policy Management Console.
  - The Group Policy Management Console allows centralized management of Group Policy Objects (GPOs) across the domain.

</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/6f131d59-f45c-4148-a5f1-d78e091d67a9" width=800/>
</p>
<p>

  - Inside of the console, I accessed the Defaut Domain Poilicy under mydomain.com to begin configuring Group Policies at the domain level.

</p>
<br />

<h3> Section 2: Configuring Account Lockout Policy </h3>
<p>
<img src="https://github.com/user-attachments/assets/5649c4ab-2135-4807-b625-210fe8753d95" width=800
</p>
<p>

  - Once inside of the Group Policy Editor, I navigated to the "Account Lockout Policy" settings to begin configuring security measures related to failed login attempts.
  - This section allows administrators to define how many failed login attempts are permitted before a user account is locked, enhanicng security against brute-force attacks.

</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/1d9915c4-9973-44a1-96d0-274ba24336fb" />
</p>
<p>

  - I set "Account Lockout Duration" to 30 minutes, restricting access after repeated failures.
  - Accounts only be accessed before the lockout period ends if manually unlocked by an administrator.
  - I set Account Lockout Threshold to 5 attempts, locking the account after five invalid login attempts.
  - Other settings, such as Administrator Account Lockout and Reset Counter Time were left at their default values.
 

</p>
<br />

<h3> Section 3: Testing the Account Lockout Policy with a User Account </h3>
<p>
<img src="https://github.com/user-attachments/assets/ee6edd4b-46a8-412c-b03d-ec13f19be9af" width=800/>
</p>
<p>

  - After applying the settings, I logged back into DC-1 as jane_admin and selected a random test user (bib.tel) in Active Directory Users and Computers to verify that the Group Policy was applied successfully.

</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/75cefbf6-3710-4c2b-8a25-4f70a7f8d82d" />
</p>
<p>

  - Next, I attempted to log into Client-1 as "bib.tel" using an invalid password five times.
  - After the 5th failed attempt, the user account (bib.tel) was successfully locked, as expected.

</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/8061e158-349b-4017-abc0-2b1f4f38f16a" />
</p>
<p>

  - After the account was locked, I returned to DC-1 as jane_admin and opened Active Directory Users and Computers
  - Navigated to the Account tab for the user "bib.tel".
  - Confirmed the account was marked as locked and manually unlocked it by checking the "Unlock Account" option.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/1b33f254-82d5-49a4-adea-384c7b6b4f98" />
</p>
<p>

  - After unlocking the account, I was able to successfully login to Client-1 as "bib.tel".
  - I opened Powershell and entered "whoami" to confirm that the account was authenticated and fully restored.

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


