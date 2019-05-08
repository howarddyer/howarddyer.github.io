
---
layout: post
title:  "Setting up HTTP and HTTPS using Node.JS"
date:   2019-05-15 08:00:00
label: note
---

# Setting up HTTP and HTTPS using Node.JS


## Certificate files

Open a terminal window, and run the following in the root of your project folder to create the required certificate files (key.pem and cert.pem).

``` shell
openssl req -newkey rsa:2048 -new -nodes -x509 -days 3650 -keyout key.pem -out cert.pem
```

When prompted, provide the following inputs:
* Country Name (2 letter code)
* State or Province Name (full name)
* Locality Name (eg, city)
* Organization Name (eg, company)
* Organizational Unit Name (eg, section)
* Common Name (eg, fully qualified host name)
* Email Address


## Modules

Include the required HTTP and HTTPS modules.

```javascript
const http = require("http");
const https = require("https");
```


## HTTP server

Using the HTTP module, instantiate the HTTP server.

```javascript
const httpServer = http.createServer(function (request, response) {
    // serverCallback(request, response);
});
```

## HTTPS server

Do the same for the HTTPS server. The certificate files (created previously) need to be passed for the HTTPS server.

```javascript
const httpsServerOptions = {
    "key": fs.readFileSync("./key.pem"),
    "cert": fs.readFileSync("./cert.pem")
};

const httpsServer = https.createServer(httpsServerOptions, function (request, response) {
    // serverCallback(request, response);
});
```

## Starting the servers

Start the servers using their applicable port — it is convention to set HTTP to listen on 80 and HTTPS to listen on 443. You can log a message when each server is started, but this is optional.

```javascript
httpServer.listen(80, function () {
    console.log("The server is listening on port 80");
})

httpServer.listen(443, function () {
    console.log("The server is listening on port 443");
})
```
