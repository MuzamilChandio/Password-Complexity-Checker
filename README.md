# Password-Complexity-Checker
a tool that assesses the strength of a password based on criteria such as length, presence of uppercase and lowercase letters, numbers, and special characters. Provide feedback to users on the password's strength.

import re

def check_password_complexity(password):
    # Define criteria for password strength
    length_criteria = len(password) >= 8
    uppercase_criteria = any(char.isupper() for char in password)
    lowercase_criteria = any(char.islower() for char in password)
    digit_criteria = any(char.isdigit() for char in password)
    special_char_criteria = bool(re.match(r'[!@#$%^&*(),.?":{}|<>]', password))
    
    # Calculate overall strength based on criteria
    strength = sum([length_criteria, uppercase_criteria, lowercase_criteria, digit_criteria, special_char_criteria])
    
    # Define feedback messages based on strength level
    if strength == 5:
        feedback = "Strong password"
    elif strength >= 3:
        feedback = "Moderate password"
    elif strength >= 1:
        feedback = "Weak password"
    else:
        feedback = "Very weak password"
    
    return feedback

# Example usage
password = input("Enter your password: ")
result = check_password_complexity(password)
print("Password strength:", result)
