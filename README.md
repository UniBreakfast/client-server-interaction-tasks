# [Tasks to learn Client-Server interaction](https://github.com/UniBreakfast/client-server-interaction-tasks)

1. Try to open page with url: http://localhost:8080/ - it shouldn't work, because there is no server running at that address/port.
   
2. Create server. Create file index.js and put it in the same folder as this file. In index.js file put the following code:
   
```javascript
  const http = require('http');
  const server = http.createServer();

  server.listen(8080);
```

3. Run server.

```shell
node.exe index.js
```

You can omit ".exe" (it is used by default). You can omit ".js" (it is used by default).


4. Open page with url: http://localhost:8080/ - it won't tell you there is no server now, because now there is a server and it does receive your request. It does not answer though. So browser will act like it is loading page. Indefinitely.

5. The server object we created above is an event emitter. It is an object that emits events, for example it emits 'request' event every time browser requests http://localhost:8080/. We can add event listener to it. We can pass a handler function into createServer() method.

```javascript
  const server = http.createServer(handleRequest);

  function handleRequest() {
    console.count('request');
  }
```

Remember to restart server after you change the code.

Now we can see in console that every time browser requests http://localhost:8080/ it will emit 'request' event. Pay attention to the console.count() method. It is a counter that counts how many times it was called. And you have two consoles now - one in the browser and one in the terminal or debugger console of your editor.

6. Now we need it (server) to answer to our request. There is a standard signature for a handleRequest() function.

```javascript
  function handleRequest(request, response) {
    response.end('Hello World!');
  }
```

`response.end()` is a method that ends the response. It sends passed argument (string) to the client.
Now browser will finally get an answer. Remember to restart server after you change the code.
