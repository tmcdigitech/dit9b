---
title: URLs
---

{{< katex display >}}
\overbrace{\text{https}}^{\text{scheme}}\text{://}
\overbrace{\text{tmcdigitech.github.io}}^{\text{address}}
\text{:}\overbrace{\text{8080}}^{\text{port}}
\overbrace{\text{/dit10a/glossary/URLs/}}^{\text{path/endpoint}}
{{< /katex >}}

The **scheme** tells the browser **how** it will connect to the server. This is typically **https**, but could also be http, ftp, mailto, or any number of others.

The **address** tells the browser **where** to send the request, i.e. which address. Addresses can be in the form of domain names like *google.com*, or IP addresses like *192.168.0.1*.

- `google.com` is like saying *Thomas More College*.
- `192.168.0.1` is like saying *35 Amsterdam Crescent, Salisbury Downs*.
- `localhost` is a special value which refers to your own machine. If your server is set to listen to *localhost* it won't be visible to any other computer at all, which is very useful for developing and testing code which is incomplete and potentially buggy.

The **path/endpoint** tells the browser **what** to ask the server for, and the server will return the appropriate response based on the path. A path can be as simple as `/`, or considerably more complicated.
