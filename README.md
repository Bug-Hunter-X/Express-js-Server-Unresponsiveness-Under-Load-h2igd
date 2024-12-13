# Express.js Server Unresponsiveness Under Load

This repository demonstrates a common issue in Express.js applications where the server becomes unresponsive or slow to respond, particularly under heavier loads.  The problem stems from blocking the event loop with long-running synchronous operations within request handlers.

## Problem

The `bug.js` file contains an Express.js server with a route handler that simulates a 5-second delay using `setTimeout`.  While seemingly innocuous, this delay blocks the event loop. If multiple requests arrive during this delay, they will queue up and experience significant latency.

## Solution

The `bugSolution.js` file provides a solution by using asynchronous operations (promises or async/await) to avoid blocking the event loop. Asynchronous operations allow the server to handle other requests concurrently, maintaining responsiveness even under stress.

## How to reproduce the bug:

1. Clone this repository.
2. Navigate to the directory containing `bug.js`.
3. Run the server using `node bug.js`.
4. Open multiple browser tabs and access the server simultaneously.  Notice the delay in response. 

## How to implement the solution:

1. Replace `bug.js` with `bugSolution.js`
2. Restart the server using `node bugSolution.js`
3. Observe how the server remains responsive and provides near-instant feedback, irrespective of multiple requests.