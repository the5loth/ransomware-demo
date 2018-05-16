# ransomware-demo

## Disclaimer

- Be careful when trying this demo. This demo is provided without warranty of any kind.
- This demo is intended to help understanding how cryptography is used in ransomware. I don't expect it to be used in ransomwares "in practice". Creating ransomwares would be illegal. Moreover, this demo is not "practical", since it doesn't provide a way to ensure file erasure nor a way to pay and communicate keys.

# WARNING!! 
- This ransomware will encrypt all files places in /root/Desktop

## Setup
- Place the /downloads folder and all of its contents in /root. NOTE: this is the downloads file contained within this demo, not root/Downloads
- Rename the client and server files
```
~$ mv path/to/downloads  /path/to/root
~$ cd downloads
~/downloads$ mv client .client; mv server .server
```
## Running the Demo

### Running the Ransomware

Run the file named chrome.exe (name can be changed to demo whatever download chosen)

```
~/downloads$ ./chrome.exe
```
This intiailly creates a master private key on the "remote server" (.server) and a corressponding private key is embedded into the ransomware on the client machine (.client)

The ransomware then creates a device key which is used to encrypt the files in /root/Desktop
Once the files are encrypted the device key is encrypted by the private key

```
Ooops, your files have been encyrpted!
```

### "Paying" the Ransom
You will now notice two new files in /downloads
```
~/downloads$ ls
Pay-Ransom
Decrypt
```

Any attempt of using Decrypt before paying the ransom will result in a warning message

Run Pay-Ransom

```
~/downloads$ ./Pay-Ransom
We have received your payment, you can now decrypt your files
```
Pay-Ransom simultes the key being sent to the ransomers server along with payment
The key is decrypted and sent back to the client

### Decryption
Run Decrypt 
```
~/downloads$ ./Decrypt
```




##NOTE
Some code and text in this demo has been taken from qnighy's ransomware demo avalible at https://github.com/qnighy/ransomware-demo#disclaimer
