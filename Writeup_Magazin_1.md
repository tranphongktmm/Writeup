First, let's go to website, overview how it actions.

![image](https://github.com/user-attachments/assets/08a82f25-04ab-4834-875e-9d8312c0cbca)

Simple, website allows us to comment, attach a file whose extensions is 'jpg, png, txt' and dowload the file.

![image](https://github.com/user-attachments/assets/011b92fb-125d-4c20-a281-de73f34da5ac)

Use burpsuit, see the packets

![image](https://github.com/user-attachments/assets/11c65888-d7c6-47e0-b573-ef4c7eccef20)
Oh, when dowload the file, we can see link of file : '/upload/.../file_name'

Overview source code, detect the cookie variable fall into a sink(**include**) that that data is mutable --> Path traversal vulnerability

![image](https://github.com/user-attachments/assets/fbbcdfff-4d66-46c8-9013-b7f1d82142cf)

Let's try to make a hypothesis, so what if we upload a txt file but inside is a webshell, and change the path to **include** to execute the webshell?

Use burptsuit to post a file.txt which has content:

![image](https://github.com/user-attachments/assets/ef5306b5-c543-462a-971a-78f0a5578977)

Access to link file, upload file successfully
Next, change cookie and get parameter 'cmd' in payload

![image](https://github.com/user-attachments/assets/6475ebf6-af57-4ace-b296-810d051d97c6)

Finish,we **rce** successfully and cat flag

![image](https://github.com/user-attachments/assets/0f58bfda-c747-443b-a855-dee97963ebf0)
