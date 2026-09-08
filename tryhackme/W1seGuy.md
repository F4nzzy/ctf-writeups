First I connected to the port with netcat 
<img width="871" height="97" alt="image" src="https://github.com/user-attachments/assets/a6afa3cf-4948-460f-b56c-727f673187e0" />

Then I wrote this script to find the key that is used to decrypt the hex string
<img width="824" height="370" alt="image" src="https://github.com/user-attachments/assets/4cae77ca-eb97-471d-b6c8-564dff040edb" />

Running the script gave the key
<img width="217" height="97" alt="image" src="https://github.com/user-attachments/assets/0a35e62d-0052-49c4-b32c-d966441727bd" />

Then taking this key to an online XOR decoder gave me the first flag
<img width="1095" height="624" alt="image" src="https://github.com/user-attachments/assets/7b8ac95c-04dd-4e72-a347-da794515854b" />

Then going back to the netcat terminal and entering the key I discovered gave me the second flag.
<img width="853" height="93" alt="image" src="https://github.com/user-attachments/assets/df5b8792-c6fd-4cd7-8eee-8aa0c468efb6" />
