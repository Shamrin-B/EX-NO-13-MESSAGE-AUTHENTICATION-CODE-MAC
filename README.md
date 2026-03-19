# EX-NO-13-MESSAGE-AUTHENTICATION-CODE-MAC

## AIM:
To implement MESSAGE AUTHENTICATION CODE(MAC)

## ALGORITHM:

1. Message Authentication Code (MAC) is a cryptographic technique used to verify the integrity and authenticity of a message by using a secret key.

2. Initialization:
   - Choose a cryptographic hash function \( H \) (e.g., SHA-256) and a secret key \( K \).
   - The message \( M \) to be authenticated is input along with the secret key \( K \).

3. MAC Generation:
   - Compute the MAC by applying the hash function to the combination of the message \( M \) and the secret key \( K \): 
     \[
     \text{MAC}(M, K) = H(K || M)
     \]
     where \( || \) denotes concatenation of \( K \) and \( M \).

4. Verification:
   - The recipient, who knows the secret key \( K \), computes the MAC using the received message \( M \) and the same hash function.
   - The recipient compares the computed MAC with the received MAC. If they match, the message is authentic and unchanged.

5. Security: The security of the MAC relies on the secret key \( K \) and the strength of the hash function \( H \), ensuring that an attacker cannot forge a valid MAC without knowledge of the key.

## Program:

```
import hashlib

# Function to generate MAC
def generate_mac(message, key):
    # Combine key and message
    data = key + message
    
    # Create SHA-256 hash
    mac = hashlib.sha256(data.encode()).hexdigest()
    
    return mac

# Input
message = input("Enter message: ")
key = input("Enter secret key: ")

# Generate MAC
mac = generate_mac(message, key)

print("Generated MAC:", mac)

# Verification
recv_message = input("\nEnter received message: ")
recv_mac = input("Enter received MAC: ")

# Recompute MAC
new_mac = generate_mac(recv_message, key)

if new_mac == recv_mac:
    print("Message is Authentic ✅")
else:
    print("Message is Tampered ❌")
```

## Output:
<img width="1659" height="755" alt="image" src="https://github.com/user-attachments/assets/0a2da779-7304-451c-8dfa-c8682f9b58ad" />


## Result:
The program is executed successfully.
