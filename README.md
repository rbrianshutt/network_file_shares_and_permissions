<h1>Network File Shares and Permissions</h1>

<h2>Description</h2>
This project demonstrates setting up file shares with varying permissions and managing access controls in an Azure Active Directory environment. It includes configuring shared folders, testing user access, and using Active Directory security groups to manage access to resources.
<br />

<h2>Techonologies Used</h2>

- <b>Microsoft Azure Virtual Machines (DC-1 and Client-1 VMs)</b>
- <b>Active Directory </b>
- <b>Remote Desktop</b>
- <b>File Sharing & Permissions</b>

<h2>Operating Systems</h2>

- <b>Windows 10</b>
- <b>Windows Server 2022</b>

<h2>Overview:</h2>

- <b>Create some sample file shares with various permissions </b> 
- <b>Attempt to access file shares as a normal user </b>
- <b>Create an “ACCOUNTANTS” Security Group, assign permissions, an test access </b>

<h2>Program Walk-Through:</h2>

<h2>Log in to virtual machines on the network (DC-1 and Client-1 VMs)</h2>

Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)
 <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/1%20rdp%20into%20dc1%20as%20domain%20admin%20account.PNG)
<br />

Connect/log into Client-1 as a normal user (mydomain\ciko.redo)  <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/2%20rdp%20client1%20as%20user.PNG)
<br />

<h2>Create some sample file shares with various permissions</h2>

On DC-1, on the C:\ drive, create 4 folders: <br />

- <b>“read-access”</b> 
- <b>“write-access”</b>
- <b>“no-access”</b>
- <b>“accounting”</b>

 <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/3%20create%20folders%20on%20c.PNG)
<br />

<h3>Set permissions for read access</h3>

Right click on the read-access folder and click Properties <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/4a.1%20right%20click%20properties%20.png)
<br />

Under the sharing tab, click Share  <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/4a.2%20sharing%20tab%20share.PNG)
<br />

We want to add domain users<br/>
We type in "domain users" and click Add <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/4a.3%20domain%20users%20add.PNG)
<br />

Domain Users are now added <br/>
By clicking on its permission level we assign Domain Users only read access <br/>
Click Share <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/4a.4%20set%20domain%20users%20to%20read.png)
<br />

The read-access folder is shared  <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/4a.5%20folder%20is%20shared.PNG)
<br />

<h3>Set permissions for write access</h3>

Right click on the write-access folder and click Properties <br/>
Under the sharing tab, click Share  <br/>
Under permission level we give Domain Users read and write access <br/>
Click Share <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/4b.1%20write%20access%20read%20write.PNG)
<br />

The write-access folder is shared <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/4b.2%20folder%20is%20shared.PNG)
<br />

<h3>Set permissions for no access</h3>

Right click on the no-access folder and click Properties <br/>
Under the sharing tab, click Share  <br/>
We want to add domain admin<br/>
We type in "domain admin" and click Add <br/>
Under permission level we give Domain Admin read and write access <br/>
Click Share <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/4c.1%20no%20access%20domain%20admins%20read%20write.png)
<br />

The no-access folder is shared <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/4c.2%20folder%20is%20shared.PNG)
<br />

<h2>Attempt to access file shares as a normal user</h2>

On CLIENT-1, navigate to the shared folder Network <br/>
Enter \\DC-1 in the directory <br/>
The \\ (double backslash) is used in Windows networking to specify a network path, particularly when accessing shared folders on a remote computer. <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/5.1%20client1%20go%20to%20dc%20shared%20folder.PNG)
<br />

Notice the shared folders that were created  <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/5.2%20folders.PNG)
<br />

<h3>Let's test access to the shared folders</h3>

Open the read-access folder  <br/>
To test, we will try to create a .txt document <br/>
Right click -> New -> Text Document <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/6.1%20read%20access%20test.png)
<br />

When we try to create a .txt document, it doesn't allow us to because domain users only have read access <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/6.2%20read%20access%20denied.PNG)
<br />

Let's open the write-access folder <br/>
To test, we will try to create a .txt document <br/>
Right click -> New -> Text Document <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/6.3%20write%20access%20test.png)
<br />

Domain users have the ability to create a .txt document because they have read and write access  <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/6.4%20write%20access%20success.PNG)
<br />

When we attempt to open the no-access folder, it doesn't allow access because it was assigned only to admin <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/6.5%20no%20access.PNG)
<br />

<h2>Create an “ACCOUNTANTS” Security Group, assign permissions, and test access</h2>

Back in DC-1, in Active Directory, under mydomian.com <br/>
Under mydomian.com, Right click -> New -> Organizational Unit <br/>
Create a new OU called "_GROUPS" <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/7.1%20dc1%20create%20ou%20.png)
<br />

Once the new OU _GROUPS is created <br/>
Right click the _GROUPS folder -> New -> Group

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/7.2%20create%20group.png)
<br />

We will call the new group "ACCOUNTANTS"  <br/>
Ensure Group type is Security  <br/>
Click Ok <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/7.3%20new%20group%20accountants.PNG)
<br />

The new Security group ACCOUNTANTS is created <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/7.4%20accountants%20added.PNG)
<br />

<h3>Set permissions for ACCOUNTANTS group</h3>

We right click the accounting folder we created earlier <br/>
Under the sharing tab, click Share  <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/8.1%20accounting%20properties.PNG)
<br />

We want to add ACCOUNTANTS<br/>
We type in "ACCOUNTANTS" and click Add <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/8.2%20add%20accounting.PNG)
<br />

Under permission level we give ACCOUNTANTS read and write access <br/> 
Click Share  <br/> 

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/8.3%20accountants%20read%20write.PNG)
<br />

The accounting folder is shared  <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/8.4%20folder%20is%20shared.PNG)
<br />

Back in CLIENT-1, as our domain user, we attempt to get access to the accounting folder, domain users do not have access  <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/9%20client1%20accountants%20cannot%20access.PNG)
<br />

As our domain user on CLIENT-1, we sign out  <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/10%20client1%20logout.png)
<br />

<h3>In DC-1, we will make domain user cido.redo a member of the ACCCOUNTANTS group</h3>

Under the _GROUPS OU in the ACCOUNTANTS security group: <br/>
Right click -> Properties<br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/11.1%20dc1%20accountants%20properties.png)
<br />

Under the Members tab  <br/>
Click Add<br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/11.2%20members%20add.PNG)
<br />

Type in our domain user ciko.redo in the object names  <br/>
Click OK<br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/11.3%20add%20user.PNG)
<br />

The user is added to the ACCOUNTANTS group <br/>
We assigned read and write access <br/>
Click Apply and OK <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/11.4%20user%20added.PNG)
<br />

Back in CLIENT-1 as our domain user ciko.redo <br/>
Go to our shared folders <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/12.1%20client1%20accounting.PNG)
<br />

Open the accounting folder and we attempt to create a .txt folder<br/>
It allows us to create a .txt document because the user has read and write access. <br/>

![](https://github.com/rbrianshutt/network_file_shares_and_permissions/blob/main/Network%20File%20Shares%20and%20Permissions/12.2%20accounting%20read%20write%20access.PNG)
<br />
