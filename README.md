![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/597fd2b2-f896-4daf-ab61-9e5cda307a24)

# Azure-Network-File-Share-Permissions-


# 1. Create Sample File Shares with Various Permissions

1.1. Connect to DC-1 as Domain Admin

![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/68099247-0b7d-47ec-a88f-5ccef7f8cd05)


Log into DC-1 using your domain admin account: mydomain.com\jane_admin.

![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/897c409e-1a88-43c5-af58-bc7a3607109d)

1.2. Connect to Client-1 as a Normal User

![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/0fac39dd-034b-4934-bc61-0566e60f8e94)

Log into Client-1 using a normal user account: mydomain\<someuser>.

1.3. Create Folders on DC-1



On DC-1, navigate to the C:\ drive.
Create the following folders:
read-access
write-access
no-access
accounting

![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/cfb0e221-307e-4cb7-becb-d28625f1b92e)

1.4. Set Permissions on the Folders

Right-click on each folder, go to Properties, and then to the Sharing tab. Click on Share.
Set the following permissions for the “Domain Users” group:
Folder: read-access, Group: Domain Users, Permission: Read
Folder: write-access, Group: Domain Users, Permissions: Read/Write
Folder: no-access, Group: Domain Admins, Permissions: Read/Write
(Skip setting permissions for the accounting folder for now)


![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/7c99b981-b3c8-45e9-b80f-8f605a0f7e6d)

![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/3bd77c86-d763-4dcf-9280-230f729289b5)


![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/200637d9-111d-4486-91a1-2d7792a3d999)

# 2. Test Access to File Shares as a Normal User

2.1. Navigate to Shared Folders from Client-1

On Client-1, press Start, then Run, and enter \\dc-1.

2.2. Test Access and Permissions

Try to access the folders you just created. Check the following:
Which folders can you access?
Which folders can you create stuff in?
Does the access align with the permissions set?

![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/8278a7d5-bc81-413a-92dc-505c0f28ff0d)
![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/3ee1e9b6-c37b-4575-9d41-141f23d16c24)


# 3. Create an “ACCOUNTANTS” Security Group, Assign Permissions, and Test Access

3.1. Create a Security Group on DC-1

On DC-1, open Active Directory Users and Computers.

![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/0e695c19-e3a5-4d9d-b77c-0869a95880ac)

Create a new security group named ACCOUNTANTS.

![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/f2c831d8-8e48-40ef-afa5-7ef79fe9fcab)

3.2. Set Permissions for the “accounting” Folder

![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/62de6f3f-acc2-4b1f-8357-5695637ab787)

![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/e580cc3c-6c2b-4241-b9a3-6910b8705250)

On DC-1, go to the accounting folder properties.
Set the following permissions:
Folder: accounting, Group: ACCOUNTANTS, Permissions: Read/Write.

![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/7cd8d4f3-9e0d-4bad-a4c7-ae1514e500c0)
![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/5f9eb806-7581-48d9-98f3-513e66a9621e)

3.3. Test Access as a Normal User

On Client-1, try to access the accounting folder using the <someuser> account. It should fail.

![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/84c8ca40-25e1-416e-a09b-6621f4d591ce)
![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/d8c7218c-577b-4195-ba8f-9cfbf4e847ef)

3.4. Add User to “ACCOUNTANTS” Security Group

On DC-1, add <someuser> to the ACCOUNTANTS security group.

![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/863d44a1-8fab-4f04-81c0-96e9a8ef260e)
![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/0460b565-4de3-4e96-8d50-d8cd0aac7cd2)
![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/2e94891f-cd60-433a-9eb3-06e5e3daddaa)

3.5. Re-test Access

Sign back into Client-1 as <someuser> and try to access the accounting share in \\DC-1\.
![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/e502e04a-beba-42e9-acf5-5af3d258bc00)

Verify if the access works now.

![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/bd175ed7-581e-41f6-93dd-53b58c624620)

# Summary of Steps

Created sample file shares with specific permissions on DC-1.

Tested access to the shares from Client-1 as a normal user.

Created a security group, set permissions, and verified access changes by adding the user to the group and re-testing access.
