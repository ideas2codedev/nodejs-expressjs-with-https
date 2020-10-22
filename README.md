# Welcome to Https demo with nodejs & expressjs!

Its necessary setup our nodejs project for run on https protocol, you can do it follow next steps.

## Sponsor

[![enter image description here](https://www.ideas2code.io/wp-content/uploads/2020/10/bar.fw_.png)](http://adf.ly/23757721/www.ideas2code.io)

## Objetive:

 Setup our nodejs project to run our site on **HTTPS** protocol.

## Requirements

 A simple project in **nodejs** (you can download this repository example [here](https://github.com/ideas2codeweb/nodejs-expressjs-with-https))
-   **.key** & **.cert** files


## Let's code it!  

**Files:**
**bin/www**

    #!/usr/bin/env node
    //main js file
    var app = require('../app');
    //this head debug is for easy identify on console log
    var debug = require('debug')('myhelloapp:server');
    //http library
    var http = require('http');
    //https library
    var https = require('https');
    //library for read files on local drive
    var fs = require('fs');
    //location our server.key file is project's root
    var privateKey  = fs.readFileSync('server.key', 'utf8');
    //location our server.cert file is project's root
    var certificate = fs.readFileSync('server.cert', 'utf8');
    //credential variable with boths files
    var credentials = {key: privateKey, cert: certificate};
    //Get port from environment and store in Express.
    var port = normalizePort(process.env.PORT || '3000');
    app.set('port', port);
    //Create HTTP server.
    var server = http.createServer(app);
    //Create HTTPS server
    var httpsServer = https.createServer(credentials, app);
    //Listen on provided port, on all network interfaces.
    if (process.env.NODE_ENV == "operations") {
      httpsServer.listen(port);
      httpsServer.on('error', onError);
      httpsServer.on('listening', onListening);
    } else {
      server.listen(port);
      server.on('error', onError);
      server.on('listening', onListening);
    }
    //Normalize a port into a number, string, or false.
    function normalizePort(val) {
      var port = parseInt(val, 10);
      if (isNaN(port)) {
        // named pipe
        return val;
      }
      if (port >= 0) {
        // port number
        return port;
      }
      return false;
    }
    //Event listener for HTTP server "error" event.
    function onError(error) {
      if (error.syscall !== 'listen') {
        throw error;
      }
      var bind = typeof port === 'string'
        ? 'Pipe ' + port
        : 'Port ' + port;
      // handle specific listen errors with friendly messages
      switch (error.code) {
        case 'EACCES':
          console.error(bind + ' requires elevated privileges');
          process.exit(1);
          break;
        case 'EADDRINUSE':
          console.error(bind + ' is already in use');
          process.exit(1);
          break;
        default:
          throw error;
      }
    }
    //Event listener for HTTP server "listening" event.
    function onListening() {
      var addr
      if (process.env.NODE_ENV == "operations") {
        addr = httpsServer.address();
      }else{
        addr = server.address();
      }
      var bind = typeof addr === 'string'
        ? 'pipe ' + addr
        : 'port ' + addr.port;
      debug('Listening on ' + bind);
    }

## For Visual Studio Coders:

**.vscode/launch.json**

    {
        // Use IntelliSense to learn about possible attributes.
        // Hover to view descriptions of existing attributes.
        // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
        "version": "0.2.0",
        "configurations": [
            {
                "type": "node",
                "request": "launch",
                "name": "Launch Program",
                "skipFiles": [
                    "<node_internals>/**"
                ],
                "program": "${workspaceFolder}\\bin\\www",
                "env":{
                    "NODE_ENV": "operations",
                    "DEBUG": "myhelloapp*"
                }
            }
        ]
    }

## You can follow this tutorial on: 

[![enter image description here](https://www.ideas2code.io/wp-content/uploads/2020/08/portada-1-590x295.jpg)](https://www.ideas2code.io/setup-node-https-certificate.html)

[https://www.ideas2code.io/setup-node-https-certificate.html](https://www.ideas2code.io/setup-node-https-certificate.html)

## Recommendations

[![enterssasd image description here](https://www.ideas2code.io/wp-content/uploads/2020/08/aws2-590x295.jpg)](https://www.ideas2code.io/https-website-verifed-with-aws.html)

[https://www.ideas2code.io/https-website-verifed-with-aws.html](https://www.ideas2code.io/https-website-verifed-with-aws.html)



[![enter image description here](https://www.ideas2code.io/wp-content/uploads/2020/08/create-https-certificate-openssl.fw_-590x295.png)](https://www.ideas2code.io/create-self-signed-certificate-openssl.html)

[https://www.ideas2code.io/create-self-signed-certificate-openssl.html](https://www.ideas2code.io/create-self-signed-certificate-openssl.html)
