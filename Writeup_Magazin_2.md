First, let's go to website, overview how it actions.

![image](https://github.com/user-attachments/assets/9876419e-acd5-4a64-8539-30379b8ab784)
it allows us to comment, upload a image and view it

![image](https://github.com/user-attachments/assets/481450c7-7b29-4d56-873f-51a30f07cda8)

In URL, have a suspicious variable 'id'. Overview source code, detect untrusted data to fall into query --> SQL injection and
detect the cookie variable to fall into a sink(include) that that data is mutable --> Path traversal vulnerability

![image](https://github.com/user-attachments/assets/c0a72b0f-423b-4aa0-b3a4-9353ebefb76e)
![image](https://github.com/user-attachments/assets/acff3f50-d767-46c1-9aca-7cff346374a5)
![image](https://github.com/user-attachments/assets/920f0d7a-8c54-4664-baf1-6fd7ee3610c1)

Let's try to make a hypothesis, so what if we create a webshell through query, and change the path to include to execute the webshell?

Use burpsuite, change **id** to exploit SQLI and create a webshell in document root

![image](https://github.com/user-attachments/assets/a07f90d3-88b6-4eb8-8d46-056c0b699795)

But, have error **SQLSTATE[HY000]: General error: 1290 The MySQL server is running with the --secure-file-priv option so it cannot execute this statementError**.
Google, see ![image](https://github.com/user-attachments/assets/6b96382f-935e-4e85-911e-c74732e44eeb) and we write the file in directory following server settings.
Can see it through **@@secure_file_priv**

![z5882471844253_138464baa69dc02dcd3bb87a577bcf7b](https://github.com/user-attachments/assets/ed1cca30-4728-44c5-9707-b12180df924f)

It is **/tmp** directory.
OK, change **id** to exploit SQLI and create a webshell in **/tmp**

![image](https://github.com/user-attachments/assets/99b3a8c1-6c9b-4376-9cd2-a43293b90109)
Yeah, website doesn't response error.
Next, change cookie and get parameter 'cmd' in payload

![image](https://github.com/user-attachments/assets/46105afc-5b9b-42bb-835c-03b4df31964b)

Finish,we **rce** successfully and cat flag

![image](https://github.com/user-attachments/assets/a2f3a73e-9e28-465f-8b68-31b400920ec9)










