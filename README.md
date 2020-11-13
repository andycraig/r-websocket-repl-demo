# R WebSocket REPL demo

A minimal demo of an R REPL session running a background WebSocket server.

Modified from example at https://github.com/rstudio/httpuv#websocket-server

## Instructions

Start an R session in the directory `demo`:

```
cd demo
R
```

The `.Rprofile` file in `demo` starts a WebSocket server. You can still use it as a normal R session by typing in the prompt. Set the variable `x`:

```r
x <- 1
```

In a NEW window, in the base directory (not in `demo`), start R and run the following code to connect to the running WebSocket server:

```r
ws <- websocket::WebSocket$new("ws://127.0.0.1:8080/")
ws$onMessage(function(event) { cat("Client received message:", event$data, "\n") })
```

Wait for a moment before running the next line:

```r
ws$send("hello world")
```

You should see the output:

```
Client received message: HELLO WORLD x: 1
```

The result uses both the input from the client ('hello world') and a value from the first R session (`x`).

You can still use the R session in the first window as normal.
