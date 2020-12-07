---
id: node1
title: Building a RESTfulAPI
sidebar_label: RESTfulAPI
---

for source code go to https://github.com/DanCaldera/NodeJS-Master

## Basic Scaffolding

```js
console.log('Hello World')
```

## Starting a Server

```js
// Dependencies
var http = require('http')

// Configure the server to respond to all requests with a string
var server = http.createServer(function (req, res) {
  res.end('Hello World!\n')
})

// Start the server
server.listen(3000, function () {
  console.log('The server is up and running now')
})
```

## Parsing Request Paths

```js
// Dependencies
var http = require('http')
var url = require('url')

// Configure the server to respond to all requests with a string
var server = http.createServer(function (req, res) {
  // Parse the url
  var parsedUrl = url.parse(req.url, true)

  // Get the path
  var path = parsedUrl.pathname
  var trimmedPath = path.replace(/^\/+|\/+$/g, '')

  // Send the response
  res.end('Hello World!\n')

  // Log the request/response
  console.log('Request received on path: ' + trimmedPath)
})

// Start the server
server.listen(3000, function () {
  console.log('The server is up and running now')
})
```

## Parsing HTTP Methods

```js
// Dependencies
var http = require('http')
var url = require('url')

// Configure the server to respond to all requests with a string
var server = http.createServer(function (req, res) {
  // Parse the url
  var parsedUrl = url.parse(req.url, true)

  // Get the path
  var path = parsedUrl.pathname
  var trimmedPath = path.replace(/^\/+|\/+$/g, '')

  // Get the HTTP method
  var method = req.method.toLowerCase()

  // Send the response
  res.end('Hello World!\n')

  // Log the request/response
  console.log('Request received on path: ' + trimmedPath + ' with method: ' + method)
})

// Start the server
server.listen(3000, function () {
  console.log('The server is up and running now')
})
```

## Parsing Query Strings

```js
// Dependencies
var http = require('http')
var url = require('url')

// Configure the server to respond to all requests with a string
var server = http.createServer(function (req, res) {
  // Parse the url
  var parsedUrl = url.parse(req.url, true)

  // Get the path
  var path = parsedUrl.pathname
  var trimmedPath = path.replace(/^\/+|\/+$/g, '')

  // Get the query string as an object
  var queryStringObject = parsedUrl.query

  // Get the HTTP method
  var method = req.method.toLowerCase()

  // Send the response
  res.end('Hello World!\n')

  // Log the request/response
  console.log(
    'Request received on path: ' + trimmedPath + ' with method: ' + method + ' and this query string: ',
    queryStringObject
  )
})

// Start the server
server.listen(3000, function () {
  console.log('The server is up and running now')
})
```

## Parsing Headers

```js
// Dependencies
var http = require('http')
var url = require('url')

// Configure the server to respond to all requests with a string
var server = http.createServer(function (req, res) {
  // Parse the url
  var parsedUrl = url.parse(req.url, true)

  // Get the path
  var path = parsedUrl.pathname
  var trimmedPath = path.replace(/^\/+|\/+$/g, '')

  // Get the query string as an object
  var queryStringObject = parsedUrl.query

  // Get the HTTP method
  var method = req.method.toLowerCase()

  //Get the headers as an object
  var headers = req.headers

  // Send the response
  res.end('Hello World!\n')

  // Log the request/response
  console.log('Request received with these headers: ', headers)
})

// Start the server
server.listen(3000, function () {
  console.log('The server is up and running now')
})
```

## Parsing Payloads

```js
// Dependencies
var http = require('http')
var url = require('url')
var StringDecoder = require('string_decoder').StringDecoder

// Configure the server to respond to all requests with a string
var server = http.createServer(function (req, res) {
  // Parse the url
  var parsedUrl = url.parse(req.url, true)

  // Get the path
  var path = parsedUrl.pathname
  var trimmedPath = path.replace(/^\/+|\/+$/g, '')

  // Get the query string as an object
  var queryStringObject = parsedUrl.query

  // Get the HTTP method
  var method = req.method.toLowerCase()

  //Get the headers as an object
  var headers = req.headers

  // Get the payload,if any
  var decoder = new StringDecoder('utf-8')
  var buffer = ''
  req.on('data', function (data) {
    buffer += decoder.write(data)
  })
  req.on('end', function () {
    buffer += decoder.end()

    // Send the response
    res.end('Hello World!\n')

    // Log the request/response
    console.log('Request received with this payload: ', buffer)
  })
})

// Start the server
server.listen(3000, function () {
  console.log('The server is up and running now')
})
```
