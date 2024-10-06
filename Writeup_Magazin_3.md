First, let's go to website, overview how it actions.

![image](https://github.com/user-attachments/assets/4f2e617c-08d5-4200-997e-e305a76e0590)
it allows us to comment, post link image and view image through that link. 
Overview source code, we can see url handling

![image](https://github.com/user-attachments/assets/9f4fde56-8b19-4d5e-9ab9-baef1758f960)
Having **file_get_contents** command allows reading files through protocols as **file://, http://, ftp:// ...**
And, this website has a hidden endpoint '/admin.php' and check access by **$_SERVER['REMOTE_ADDR'] === "127.0.0.1"**
and set value in **config** table through 2 get param

![image](https://github.com/user-attachments/assets/6bf49e88-8e15-47d1-9e07-791915e14e76)
--> **SSRF vulnerability**. 
Let's try to make a hypothesis, so what if we post a webshell to server and
impersonate the server to change **value** of the **config** table to the path to the webshell into the sink **include**

![image](https://github.com/user-attachments/assets/c7ad6a50-42e9-4be1-b257-be273dd20755)

First, create url whose content is a webshell on webhook and post it to server

![image](https://github.com/user-attachments/assets/5de3939f-8ed6-45f6-9db2-239d3ec7d1e9)


![image](https://github.com/user-attachments/assets/05dd8176-9db9-44b3-924a-7ab951d26cb3)


Post successfully!!

![image](https://github.com/user-attachments/assets/150c4f3a-8e7e-4311-b165-2477709beb33)

Next, post url having value is path to uploaded webshell

![image](https://github.com/user-attachments/assets/3a33849d-a3f6-4f50-adef-80bcf1b38779)

Get parameter 'cmd' in payload

![image](https://github.com/user-attachments/assets/b6bb2957-5725-40dd-b294-0fd63c794f2b)

Finish,we rce successfully and cat flag

![image](https://github.com/user-attachments/assets/9b49d145-4a9a-4d12-8736-b3c7f9d6d577)











