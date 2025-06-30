# Caeser-Cipher
This project is useful to encrypt or decrypt the data by using shift key. It is very useful to secure the data from hackers and unknown persons.
[Ceaser Cipher.docx](https://github.com/user-attachments/files/20982855/Ceaser.Cipher.docx)
def caesar_cipher(text, shift, mode):
    """
    Encrypts or decrypts text using the Caesar cipher.

    Args:
        text (str): The input text to be processed.
        shift (int): The number of positions to shift.
        mode (str): 'encrypt' for encryption, 'decrypt' for decryption.

    Returns:
        str: The processed text (encrypted or decrypted).
    """
    result = ""
    if mode == 'decrypt':
        shift = -shift  # Reverse the shift for decryption

    for char in text:
        if 'a' <= char <= 'z':
            start = ord('a')
            shifted_char = chr((ord(char) - start + shift) % 26 + start)
            result += shifted_char
        elif 'A' <= char <= 'Z':
            start = ord('A')
            shifted_char = chr((ord(char) - start + shift) % 26 + start)
            result += shifted_char
        else:
            result += char  # Keep non-alphabetic characters as they are
    return result

if __name__ == "__main__":
    while True:
        operation = input("Do you want to 'encrypt' or 'decrypt' a message? (or 'exit'): ").lower()

        if operation == 'exit':
            break
        elif operation not in ['encrypt', 'decrypt']:
            print("Invalid operation. Please choose 'encrypt', 'decrypt', or 'exit'.")
            continue

        message = input("Enter your message: ")
        try:
            key = int(input("Enter the shift key (an integer): "))
        except ValueError:
            print("Invalid key. Please enter an integer.")
            continue

        processed_message = caesar_cipher(message, key, operation)
        print(f"Result: {processed_message}")
