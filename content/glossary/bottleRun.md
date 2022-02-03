---
title: bottle.run()
---

{{< highlight python "linenos=table" "lineNoStart=7">}}
run(reloader=True, debug=True)
{{< /highlight >}}


You can just say `run()`, and it will begin using a set of defaults, but we have customised the server slightly. The `reloader` flag tells the server to restart every time we change a code file, which saves us from turning it off and on again every time we modify our code. Very handy for development! The `debug` flag does a something thing for templates.

There are a lot of other flags you can use, but two that you might find handy are:

`host="localhost"`
: Sets which addresses the server will listen on. Localhost is a magic name that refers to your local machine. By hosting on localhost, only your local machine can access your server, which is ideal for personal things and anything you're developing, which might have bugs or potential weaknesses to exploit. You can choose one of your computer's current IP addresses with, e.g. `host="192.168.1.203"`, and now your computer will be visible to other devices connected to that local network. Finally, you can also choose to listen on all available addresses by using `host="0.0.0.0"`.

`port="8080"`
: Sets which port the server will listen on. You will need administrator access to use a port number below 1024. The default port for HTTP traffic is port 80, and common alternatives are 8080 and 8000.