# Node.js Server Unresponsiveness Under Load

This repository demonstrates a common issue in Node.js servers where they become unresponsive under heavy load due to a blocking synchronous operation in the request handling logic.  The example uses a simple HTTP server with a simulated 5-second delay to illustrate the problem.  A solution is provided that demonstrates how to address this using asynchronous operations.

## Bug

The `server.js` file contains a Node.js HTTP server that simulates a long-running operation within the request handler.  Under load, this blocking operation prevents the server from accepting new requests, leading to unresponsiveness. 

## Solution

The `serverSolution.js` file demonstrates how to resolve the issue by handling requests asynchronously. This prevents blocking the event loop and allows the server to gracefully handle concurrent requests.

## How to Reproduce

1. Clone the repository.
2. Run `node server.js`.
3. Send multiple requests to `http://localhost:3000` concurrently using tools like `ab` or a browser extension that allows you to fire multiple requests quickly.  You should notice that the server eventually becomes unresponsive. 
4. Now, repeat steps 2 and 3 using `serverSolution.js`. You'll observe that the server can handle requests more efficiently even under high load.

## Technologies Used

* Node.js
* HTTP