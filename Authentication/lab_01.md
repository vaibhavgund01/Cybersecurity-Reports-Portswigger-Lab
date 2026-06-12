# Lab 1 - Username Enumeration via Different Responses

## Objective
The objective of this lab is to identify valid usernames by analyzing differences in server responses and subsequently perform password enumeration to gain unauthorized access to the application.

---

## Vulnerability Type
- Username Enumeration  
- Authentication Weakness (Brute Force assisted)

---

## Target Application
- Lab: PortSwigger Web Security Academy  
- Vulnerability: Different responses based on username validation  

---

## Steps to Reproduce

1. Navigate to the application login page.

2. Enter invalid credentials:
   - Username: FGDFGDFGDF
   - Password: 1234567

3. Observe the response message:
   - The application returns: "Invalid username"

4. Capture the login request using Burp Suite Proxy and send it to Intruder.

5. In Intruder:
   - Set the username parameter as the payload position
   - Add a username wordlist in Payloads tab
   - Start the attack

6. Analyze Intruder results:
   - Sort responses by Length
   - Identify different response length indicating valid username

7. Found valid username:
   - Username: apollo

8. Configure second Intruder attack:
   - Set password parameter as payload position
   - Keep username fixed as apollo
   - Add password wordlist

9. Start attack and analyze results:
   - Sort by Status Code
   - Look for 302 response indicating successful login

10. Found valid credentials:
   - Username: apollo
   - Password: moon

11. Login using valid credentials.

---

## Result
Successfully authenticated into the application using valid credentials.

- Username: apollo  
- Password: moon  

---

## Impact
- Attackers can enumerate valid usernames
- Enables brute-force attacks on accounts
- Weak authentication mechanism

---

## Recommendation
- Implement rate limiting on login attempts
- Add account lockout after multiple failed attempts
- Use Multi-Factor Authentication (MFA)
- Use generic error messages for login failures

---

## Conclusion
The application is vulnerable to username enumeration due to different server responses. This allows attackers to discover valid usernames and perform further password attacks.