# XSS is when an attacker injects code into a website that runs in someone else’s browser, letting them steal data or perform actions as the victim.

# Reflected cross-site scripting
attacker’s code runs in the victim’s browser immediately after clicking a malicious link ( immediate upon victim's click)
A lot of phishing campaigns are renown for using this attack --> Vulnerability is on the server.

##### Examples:
    Normal URL: https://insecure-website.com/status?message=All+is+well
    Malicious: https://insecure-website.com/status?message=<script>alert(1)</script>

#  Stored cross-site scripting
Stored XSS happens when malicious code is saved on a website and automatically runs in every user’s browser when they view the affected page.
1.An attacker submits malicious code (like JavaScript) into a website (for example through comments  a blog  )
2.The website saves it in the database
3.Every time other users visit that page, the code runs in their browser

##### Examples:
    Normal message : <p>Hello, this is my message!</p>
    Malicious message:<p><script>stealStuff()</script></p>



# DOM-based cross-site scripting
When JavaScript takes user input and inserts it into the webpage without checking it, allowing attackers to run malicious code.Similar to reflected XSS, it is usually delivered via a crafted URL sent to the victim.
In this attack ,the browser’s JavaScript inserts malicious input into the page-->  Vulnerability is in client-side JavaScript
The DOM is just what the browser displays.

# 🧠 **Additional notes**
•'Same-Origin Policy (SOP)'- Every website in my browser has its own “sandbox”. Shis sandbox prevents one website from reading data from another website. XSS can let an attacker break that rule and steal information from my browser, like cookies or session tokens.
•CSP (Content Security Policy) - CSP is a browser security feature that tells the browser which scripts and resources are allowed to run. It helps reduce the impact of XSS by blocking malicious scripts from executing.

 • 'document.cookie' is a JavaScript way to: Read cookies & Write cookies. if JavaScript takes something from document.cookie and inserts it into the page unsafely, it can cause DOM XSS. So we set HttpOnly flag as a soluttion
##### Example:
    var data = document.cookie;
    element.innerHTML = data;

 • 'setTimeout' - runs code after a delay. BUT can also run a string ( ex: setTimeout("alert('hi')", 1000); )

 •🔎 How Do You Find XSS? Burp suit for example or  manual testiing (for ex: for stored/reflected xss: Put a simple unique string in every input field,Look at the page response,Does the input appear anywhere in the page? If yes → that’s a reflection point)

