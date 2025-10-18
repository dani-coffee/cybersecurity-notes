# 📄 HTML cheat sheet

| Element       | Description                          | Example |
|---------------|--------------------------------------|---------|
| `<!DOCTYPE>`  | Declares document type (HTML5)       | `<!DOCTYPE html>` |
| `<html>`      | Root of the HTML document            | `<html> ... </html>` |
| `<head>`      | Contains metadata/settings           | `<head> ... </head>` |
| `<title>`     | Page title (shown in browser tab)    | `<title>My Page</title>` |
| `<meta>`      | Metadata (charset(how to interpret the text on your page — like letters, symbols, punctuation, etc, UTF-8 supports nearly all languages and symbols) , viewport (Controls page scaling on mobile), etc.)   | `<meta charset="UTF-8">` |
| `<link>`      | Link external resources (CSS,not for the user,the browser uses it silently)        | `<link rel="stylesheet" href="style.css">` (href="style.css" : the name/path of the CSS file to use)|
| `<body>`      | Page content (what users see)        | `<body> ... </body>` |
| `<h1>`–`<h6>` | Headings (largest to smallest)       | `<h1>Welcome</h1>` |
| `<p>`         | Paragraph of text                    | `<p>This is a paragraph.</p>` |
| `<a>`         | Link to another page or site (link for the user)        | `<a href="https://example.com">Click Here</a>` |
| `<img>`       | Displays an image                    | `<img src="image.jpg" alt="A picture">` |
| `<ul>`        | Unordered (bullet point) list        | `<ul> <li>Milk</li> <li>Eggs</li> <li>Bread</li> </ul>` |
| `<ol>`        | Ordered (numbered) list              | `<ol> <li>Wake up</li> <li>Eat</li> <li>Code</li> </ol>` |
| `<li>`        | List item inside `ul` or `ol`        | `<li>Item</li>` |
| `<button>`    | Clickable button                     | `<button>Click Me</button>` |
| `<script>`    |  used to add JavaScript to the HTML page    | `<script src="script.js"></script>` |
| `<div>`       | Block container (for layout/styling) | `<div>Content</div>` |
| `<span>`      |highlighter  | `<p>This is a <span style="color: red;">red word</span> in a sentence.</p>` |
| `<form>`      | For user input forms                 | `<form> <label>Your name:</label> <input type="text" name="username"> <button type="submit">Submit</button> </form>` |
| `<!-- ... -->`  | block of comments | `<!--  TODO:    Remove test credentials!     Username: admin     Password: testpasswd     -->` |
| `getElementById` |` a JavaScript method used to find an HTML element on the page by its unique id attribute | `if i have in html:  <p id="demo">Original text</p> <script> //then i cqan get the element with id 'demo' and change its text document.getElementById("demo").innerHTML = "Hello, world!"; </script>` |

###  ✏️example
    <!DOCTYPE html>
    <html>
      <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>My First HTML Page</title>
        <link rel="stylesheet" href="styles.css"> <!-- Optional CSS file -->
      </head>
    
      <body>
        <h1>Welcome to My Page</h1>
    
       <p>Hello! I'm learning HTML. This is a paragraph.</p>
    
       <h2>Things I Like</h2>
        <ul>
          <li>Coding</li>
          <li>Coffee</li>
          <li>Cats</li>
        </ul>
    
       <h2>My Routine</h2>
        <ol>
          <li>Wake up</li>
          <li>Write code</li>
          <li>Sleep</li>
        </ol>
    
    <p><span style="color: red;">Visit my favorite site:</span>
          <a href="https://tryhackme.com" target="_blank">TryHackMe</a>
        </p>
    
      <img src="cat.jpg" alt="A cute cat" width="200">
    
      <button onclick="alert('Thanks for clicking!')">Click Me</button>
    
      <form>
          <label for="name">Enter your name:</label>
          <input type="text" id="name" placeholder="Your name">
          <button type="submit">Submit</button>
        </form>
    
      <script>
          console.log("This is JavaScript in action!");    ➝seen using developer's tools
        </script>
      </body>
    </html>

---

# 🧠 **Additional notes**


• `JavaScript` is added within the page source code and can be either loaded within <script> tags or can be included remotely with the src attribute

| Method                          | Description                                                                 | Example Code |
|----------------------------------|------------------------------------------------------------------------------|--------------|
| **1. Inline (Directly in HTML)** | JavaScript is written inside the HTML file using `<script>` tags. | `<script>alert("Hello, world!");</script>` |
| **2. External JavaScript File**  | JavaScript is in a separate `.js` file and linked via `src`. | `<script src="script.js"></script>` |


---

• `HTML injection` - Inserting attacker-supplied HTML tags into a page. The injected HTML may only change how the page looks (e.g., add links or formatting) or it may enable script execution (XSS) depending on what is allowed and how the page handles the input.
#####  ✏️example:
    Username: <a href = "http://hacker.com"> diana </a>

---

• ` CDN (Content Delivery Networks)` - system of distributed servers located in many different places around the world. Its job is to deliver web content (like images, videos, scripts, stylesheets) to users faster and more reliably. Problrm: If the server is far away from you, the files take longer to arrive, slowing down the website. CDN solves it by: Storing copies of these files on servers closer to me geographically,Delivering the files from the nearest server, speeding up the loading time,Handling lots of traffic better, improving availability and reliability

 --- 
 
• `Databases` - like a digital storage system that helps I store, organize, and manage data — basically information — so I can easily retrieve and use it later.Relational databases(use of rows and colums) common examples: MySQL, PostgreSQL, SQLite, Microsoft SQL Server. Nosql(other formats like documents,graphs are used to store data) common examples: MongoDB, Redis, Cassandra

---

• `WAF (web application firewall)` - a security tool that protects web applications (websites or online services) by filtering and monitoring HTTP traffic between the internet and the web app
blocks or filters out malicious traffic that tries to exploit security vulnerabilities, like hackers trying to inject harmful code or perform attacks. Helps prevent attacks such as: 
1. SQL Injection (bad code trying to mess with my database)
2.  Cross-Site Scripting (XSS) (injecting malicious scripts into web pages)
3.  Cross-Site Request Forgery (CSRF)

---

• order of how a request to a website works - 
1. request of a website in my browser
2. check local Cache for IP of that website (if found,done)
3. check recursive cache for that IP address (if found,sends it to local cache,done)
4. the DNS server queries the root server to find authorotative DNS server
5. request passes through WAF
6. request goes through Load balancer
7. Connection on port ( 80 HTTP and 443 HTTPS)
8. WEB server receives the GET request
9. Web application talk to database
10. The browser interprets the HTML and turns it into a visual webpage
