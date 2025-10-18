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
