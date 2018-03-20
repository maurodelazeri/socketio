# SocketIO .9
[![Build Status](https://travis-ci.org/h00kwurm/socketio.svg?branch=master)](https://travis-ci.org/h00kwurm/socketio)

This is a super minimal implementation of my SocketIO needs. If you do find yourself wanting to use it, go right ahead. Be forewarned! It is really underdeveloped. Want to submit a pull request and help out others stuck in a shit mode of point-nine-age?

Yeah, I know there are [two](https://github.com/googollee/go-socket.io) [other](https://github.com/oguzbilgic/socketio) options for socketio. Both are backed by websockets provided by [code.google.com](https://code.google.com/p/go/). This is backed by [gorilla websockets](https://github.com/gorilla/websocket). Thank you [gorilla](https://github.com/gorilla).

If it wasn't clear by now, this only supports websockets. Maybe you're thinking to yourself, why socketio if it always uses just websockets. Because reasons. That's why.

## Example: 

    package main

    import (
      "fmt"
      "github.com/h00kwurm/socketio"
    )

    const remoteServer = "http://127.0.0.1:8088"

    func onConnect(output chan socketio.Message) {
      output <- socketio.CreateMessageEvent(`{"msg":"test message"}`)
    }

    func main() {

      socket := socketio.SocketIO{
        OnConnect: onConnect,
      }

      err := socketio.ConnectToSocket(remoteServer, &socket)
      if err != nil {
        fmt.Println(err)
        return
      }

    }

