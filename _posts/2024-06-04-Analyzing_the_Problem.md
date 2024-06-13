## Analyzing the Problem

First, I tried calling kw drm directly, without any parameters, to see its effect and, surprisingly, it returned an error message, saying that it couldn't access port 22 via root.

As this proved to be different from the problem described, I start to investigate and, after an hour of outputting in suspicious places, I found the reason. Since I didn't type anything as input and I don't have a configuration file, the file automatically invokes the error function, which in turn prints the error on port 22 as the default.

Since this problem can be solved by forcing the user to enter some parameter, which is requested by the issue, I left it out. When I have more time in the future, maybe I'll fix it again.
