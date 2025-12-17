#W 

A command‑line client for connecting to the Tor privacy network. When you run a CLI command that makes a network call:

```bash
bash$ curl http://12.34.45.67
```

The `connect()` function, where the program establishes a TCP connection and then the communication begins, is invoked to connect the client to the server.  

With this tool, you will write *toralize* in front of every function that makes a network call:

```bash
bash$ toralize curl http://12.34.45.67
```

It will intercept any function and run our function instead, such as *my_connect()*. The traffic will be redirected to a local proxy server that is part of the Tor network.  
So the client first connects to the Tor network and then to the destination server, masking your identity and helping you stay private.


https://www.youtube.com/watch?v=E63YLp_qzkg