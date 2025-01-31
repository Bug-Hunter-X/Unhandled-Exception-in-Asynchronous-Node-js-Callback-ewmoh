# Unhandled Exception in Asynchronous Node.js Callback

This example demonstrates a common error in Node.js: unhandled exceptions within asynchronous callbacks.  Improper error handling in such scenarios can lead to server crashes or unexpected behavior.

## Bug Description:
The `bug.js` file contains an HTTP server.  When the server receives a request to `/error`, it throws an exception within the asynchronous `setTimeout` callback.  Because this exception isn't handled, the server crashes.

## Solution:
The `bugSolution.js` file corrects this by attaching an error listener to the server using `server.on('error', ...)`. This ensures that any errors occurring within the server's event loop are caught and logged gracefully, preventing a crash.

## How to reproduce the bug:
1. Run `node bug.js`
2. Make a request to `http://localhost:3000/error`

You'll observe the server crashing.

## How to fix the bug:
1. Run `node bugSolution.js`
2. Make a request to `http://localhost:3000/error`

This time, the server will log the error but remain running.

This example highlights the importance of robust error handling, particularly when dealing with asynchronous operations in Node.js.