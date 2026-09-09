First I ran nmap

<img width="700" height="632" alt="image" src="https://github.com/user-attachments/assets/c3c0aec9-c676-4102-8f55-9239ff4675c6" />

and I saw that HTTP, FTP and SSH are all open.

Navigating to the webpage just shows a picture and looking at the source code gave a hint to check for things hidden in files.

<img width="1558" height="798" alt="image" src="https://github.com/user-attachments/assets/0e8c4ef9-8e2a-453f-b259-d643f87af191" />

So next I checked the meta data of the image:

<img width="428" height="456" alt="image" src="https://github.com/user-attachments/assets/c55da55a-5f95-4a28-9fbe-70fbf1a30e0a" />

but there seems to be no useful information there so I checked for hidden files with gobuster.

<img width="624" height="421" alt="image" src="https://github.com/user-attachments/assets/6784303b-fb42-4bd6-8e5c-6627ab58aa17" />

But there was also nothing there.

Next I checked the ftp port:

<img width="806" height="409" alt="image" src="https://github.com/user-attachments/assets/441124e0-9fa2-4bc2-8010-f3571e7bcbab" />

Where there is a file called 'note_to_jake.txt', so I downloaded this file. Inside there is a clue that Jake's password may be weak. 

<img width="743" height="67" alt="image" src="https://github.com/user-attachments/assets/28f96e3b-7781-457c-8349-3933d2a002fd" />

So I attempted to brute force the password with Hydra and one of the default Kali wordlists.

<img width="838" height="218" alt="image" src="https://github.com/user-attachments/assets/7c34fc2c-15bc-48af-b3c5-bc6a68bfbbab" />

And we can see that the password was successfully found and allowed me to login.

<img width="562" height="186" alt="image" src="https://github.com/user-attachments/assets/4b5e3857-632e-4622-86ba-38524295afbc" />

Once inside, I looked around for anything useful and found that I could access files of other users.

<img width="515" height="581" alt="image" src="https://github.com/user-attachments/assets/bc164be5-ba86-48fd-b518-6a26865d9f39" />

There were no useful files in Amy or Jake's folders but in Holt's there are 2 files that may be useful. User.txt and nano.save.

<img width="384" height="285" alt="image" src="https://github.com/user-attachments/assets/eb0f0988-6b9d-4f0b-9ed8-d5c6340d6a21" />

And there is the first flag. Now I suspected that the second flag might be in nano.save, but I cannot access it. 

As jake I have permission to run the command 'less' with sudo permission, and since 'less' allows you to run shell commands from within it using '!', and I can run it as root, I can use !bash to spawn a root shell.

<img width="843" height="85" alt="image" src="https://github.com/user-attachments/assets/d902f0a6-f474-4f22-8567-0366375a228c" />

<img width="410" height="72" alt="image" src="https://github.com/user-attachments/assets/63098adf-384d-4221-b479-3a6d86efcbe7" />

With this I read the nano.save file, but there was no flag so I searched around for other files that may contain the flag.
Since I was now root, I checked inside the /root directory first and saw a file called root.txt. Reading this yielded the second flag.

<img width="672" height="692" alt="image" src="https://github.com/user-attachments/assets/53ce6d08-38de-45b7-a40b-eb15f141ea22" />
