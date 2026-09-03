First thing I did was to access the web app and view the source. 

<img width="799" height="398" alt="image" src="https://github.com/user-attachments/assets/b92f3f3f-41fb-46b7-bca1-302fadfd157e" />

This revealed the username.
The next thing i did was use gobuster to find any hidden directories. 

<img width="669" height="455" alt="image" src="https://github.com/user-attachments/assets/19807131-a36e-4fed-b277-9eb4e651a30f" />

Accessing the robots.txt reveals

<img width="177" height="42" alt="image" src="https://github.com/user-attachments/assets/ed36e37b-1175-4414-ab1d-de941c0750bc" />

which i made a note of as it may come in useful. 
Then navigating to the login page, i tried some common passwords ('password', 'admin', '123456' etc.) before trying the text from the robots file, which worked. 

<img width="534" height="269" alt="image" src="https://github.com/user-attachments/assets/daac3c70-f086-4134-9aa6-77291d78eb36" />

Once logged in, I was given access to an admin panel.

<img width="432" height="416" alt="image" src="https://github.com/user-attachments/assets/e63a4f8c-f83d-49f9-a63f-4ef6b472e7c0" />

and I can see a file named 'Sup3rS3cretPickl3Ingred.txt'

<img width="536" height="334" alt="image" src="https://github.com/user-attachments/assets/6e30f032-f807-4cb9-bd3a-2e0dd43d8ce9" />

However its not readable with a simple cat. 

<img width="357" height="233" alt="image" src="https://github.com/user-attachments/assets/688ce91b-24ac-4056-bdb8-3c719c59eaf6" />
<img width="429" height="258" alt="image" src="https://github.com/user-attachments/assets/f8f34a5b-6e91-4b0d-9a3c-6991cb4e5714" />

To work around this, i printed the contents of the file as base64 and then decoded it with the BurpSuite decoder. 
This gave me the first flag: mr. meeseek hair

<img width="299" height="326" alt="image" src="https://github.com/user-attachments/assets/54d876b0-fbda-41bb-bca6-e49b92d9e0bb" />

Next i opened the clue.txt file

<img width="232" height="26" alt="image" src="https://github.com/user-attachments/assets/01ebd8b4-91f3-4f4e-bd4e-4da53c435597" />

<img width="407" height="26" alt="image" src="https://github.com/user-attachments/assets/5f55d676-1b09-4ba4-8867-e1c41b53ce25" />

This gave the hint to keep searching in the file system for the next flag. 
so in the command panel i searched for any files with ingredient in the name

<img width="363" height="193" alt="image" src="https://github.com/user-attachments/assets/6bb0cd7a-ffdb-4d6b-9094-bf4225ed293d" />

So using the same trick from earlier i read the file in base64 and converted it to get the second flag: 1 jerry tear

<img width="454" height="241" alt="image" src="https://github.com/user-attachments/assets/46c8850d-b103-4b8c-bb59-c991fe8146eb" />
<img width="301" height="286" alt="image" src="https://github.com/user-attachments/assets/18949d97-fec8-4778-a4be-b3ea6733824f" />

Then for the final flag i tried to use sudo 

<img width="627" height="389" alt="image" src="https://github.com/user-attachments/assets/1325727f-6523-427d-8f54-3fb0dea1a6c7" />

Then accessing the root directory 

<img width="284" height="263" alt="image" src="https://github.com/user-attachments/assets/a1a2d9cf-a1db-45a0-87ba-5e2cc3d3cefc" />

I found the last flag file, using the same trick of base64 and converting, I found the flag: fleeb juice

<img width="421" height="207" alt="image" src="https://github.com/user-attachments/assets/bf35797b-32d9-4131-9aa7-4693ad03ecbe" />
<img width="416" height="282" alt="image" src="https://github.com/user-attachments/assets/c65a056c-8dda-427f-b1cb-bcbb97aecaaa" />
