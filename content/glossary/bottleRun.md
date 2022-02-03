---
title: bottle.run()
---

{{< highlight python "linenos=table" "lineNoStart=7">}}
run(reloader=True, debug=True)
{{< /highlight >}}


You can just say `run()`, and it will begin using a set of defaults, but we have customised the server slightly. The `reloader` flag tells the server to restart every time we change a code file, which saves us from turning it off and on again every time we modify our code. Very handy for development! The `debug` flag does a something thing for templates.

## Bonus for the eager

There are a lot of other flags you can use, but two that you might find handy are:

- `host="localhost"`, which sets which addresses the server will listen on