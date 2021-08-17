# How to run
### Start the vueapp
In your first command line console:
`cd vueapp; yarn serve`

### Start the express https proxy
In your second command line console:
`yarn start`

# Issue
When you proxy the app.js file from `vue-cli-service serve` https->http (https://localhost:3000/api.js -> http://localhost:8080/api.js) the webpacker file will embed http**s**://localhost:8080/ instead of http.  This causes `net::ERR_SSL_PROTOCOL_ERROR` as the `vue-cli-service serve` is responding with http to an SSL connection.

Enabling https with `vue-cli-service serve --https` and allowing the proxy to trust it, causes a `net::ERR_CERT_AUTHORITY_INVALID`.  While you can navigate to a `vue-cli-service` endpoint and manually trust the certificate—and in some cases will supress the error across sessions. This is an extra step that confuses the situation.

I have not been able to test if a proper https->http proxy will cause a mixed-mode warning.