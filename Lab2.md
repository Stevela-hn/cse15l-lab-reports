# A Simple Showcase of playing with Servers and Bugs at CSE 15L
This report aims to have a showcase about the topics of Servers and Bugs, covered in CSE15L at Week2 to Week3. There're mainly two parts, the first one (Part 1) discussed a technical example of implementing web server; the second one (Part 2) provides a case of the "pipeline" for bugs and debugging. An extra place (Part 3) is set to offer some personal comments of the lab experience by the author.

## Part 1
This practice goes based on the *NumberServer.java* and *Server.java* in lab activities, and re-implements the *URLHandler* interface as *Handler* class to achieve a brand new web server called `StringServer`.

### Server Implementation
Below attached the codes for the revised handler. Compared with the original one for numbers, the structure is **eased** to accomodate a simpler and clearer logic, that it handles the following cases of requests
1. `/add-message?s=<string>`: concatenate a new line the requested string to the current running string, and display the running string.
2. `/`: Display the running string. Note the author deviates from the lab instruction to add this case, because usually a user will not directly have a request, they will instead go to kind of "home page" first, then do something. To accomodate this mute habit, the author added this case to prevent error happening.
3. Other: other requests would trigger a "404 Not Found!" to let the user know they're off the track.

```
class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String s = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return s;  // show a whiteboard or current string when input nothing
        } else {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    s += parameters[1];
                    s += "\n"; // accumulate s
                    return (s);
                }
            }
            return "404 Not Found!";
        }
    }
}
```
