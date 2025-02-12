import random
import string

def generate_password(length=12):
    if length < 8:
        print("Warning: It's recommended to have a password length of at least 8 characters for security.")
    
    # Define the character sets for the password
    lowercase = string.ascii_lowercase
    uppercase = string.ascii_uppercase
    digits = string.digits
    special_characters = string.punctuation

    # Combine all character sets
    all_characters = lowercase + uppercase + digits + special_characters

    # Ensure that the password contains at least one character from each set
    password = [
        random.choice(lowercase),
        random.choice(uppercase),
        random.choice(digits),
        random.choice(special_characters),
    ]

    # Add random characters to complete the password to the specified length
    password += random.choices(all_characters, k=length - 4)

    # Shuffle the password to ensure randomness
    random.shuffle(password)

    # Join the list into a string and return it
    return ''.join(password)

# Example usage
if __name__ == "__main__":
    length = int(input("Enter the desired password length (recommended 12 or more): "))
    password = generate_password(length)
    print(f"Generated password: {password}")
