# node

## Création d'un serveur NodeJS

* Créer le fichier `app.js` :

```
// app.js

const http = require('http');
const jwt = require("jsonwebtoken");

// Create an instance of the http server to handle HTTP requests
let app = http.createServer((req, res) => {
    // Set a response type of plain text for the response
    res.writeHead(200, {'Content-Type': 'text/plain'});

    // Code utile
    <console.log = resultat dans le terminal>
    
    res.end('Hello World!\n');
});

// Start the server on port 3000
app.listen(3000, '127.0.0.1');
console.log('Node server running on port 3000');
```

* Exécuter le fichier `app.js` :

```
node app.js
```
