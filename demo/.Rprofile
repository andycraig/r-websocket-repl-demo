library(httpuv)
s <- startServer("127.0.0.1", 8080,
  list(
    onWSOpen = function(ws) {
      # The ws object is a WebSocket object
      ws$onMessage(function(binary, message) {
        ws$send(paste0(toupper(message), " x: ", x))
      })
    }
  )
)

