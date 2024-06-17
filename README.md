![image](https://github.com/iahalkhatib/Azure-Network-File-Share-Permissions-/assets/170050432/597fd2b2-f896-4daf-ab61-9e5cda307a24)

# Azure-Network-File-Share-Permissions-


# 1. Create Sample File Shares with Various Permissions

1.1. Connect to DC-1 as Domain Admin

Log into DC-1 using your domain admin account: mydomain.com\jane_admin.

1.2. Connect to Client-1 as a Normal User

Log into Client-1 using a normal user account: mydomain\<someuser>.

1.3. Create Folders on DC-1

On DC-1, navigate to the C:\ drive.
Create the following folders:
read-access
write-access
no-access
accounting

1.4. Set Permissions on the Folders

Right-click on each folder, go to Properties, and then to the Sharing tab. Click on Share.
Set the following permissions for the “Domain Users” group:
Folder: read-access, Group: Domain Users, Permission: Read
Folder: write-access, Group: Domain Users, Permissions: Read/Write
Folder: no-access, Group: Domain Admins, Permissions: Read/Write
(Skip setting permissions for the accounting folder for now)

# 2. Test Access to File Shares as a Normal User

2.1. Navigate to Shared Folders from Client-1

On Client-1, press Start, then Run, and enter \\dc-1.

2.2. Test Access and Permissions

Try to access the folders you just created. Check the following:
Which folders can you access?
Which folders can you create stuff in?
Does the access align with the permissions set?

# 3. Create an “ACCOUNTANTS” Security Group, Assign Permissions, and Test Access

3.1. Create a Security Group on DC-1

On DC-1, open Active Directory Users and Computers.
Create a new security group named ACCOUNTANTS.

3.2. Set Permissions for the “accounting” Folder

On DC-1, go to the accounting folder properties.
Set the following permissions:
Folder: accounting, Group: ACCOUNTANTS, Permissions: Read/Write

3.3. Test Access as a Normal User

On Client-1, try to access the accounting folder using the <someuser> account. It should fail.

3.4. Add User to “ACCOUNTANTS” Security Group

On DC-1, add <someuser> to the ACCOUNTANTS security group.

3.5. Re-test Access

Sign back into Client-1 as <someuser> and try to access the accounting share in \\DC-1\.

Verify if the access works now.

# Summary of Steps

Created sample file shares with specific permissions on DC-1.

Tested access to the shares from Client-1 as a normal user.

Created a security group, set permissions, and verified access changes by adding the user to the group and re-testing access.
