# Report #2 For CSE 15L

The grep command has many uses. Four of these uses are listed below.

1. The grep command can be used to search for lines in a file without a certain string. The format  to use grep in this way is `grep -v [string] *` where [string] is the string that you input directly without quotes (if it is a single-word string). The asterisk is specific to this case, and means that the grep command should search on all the files in the working directory.

Example 1
```
$ grep -v e Server.java




}

    }
        try {
        }
    }
}



    }
}

```
Example 2
```
$ grep -v ";" Server.java
// A simple web server using Java's built-in HttpServer

// Examples from https://dzone.com/articles/simple-http-server-in-java were useful references



interface URLHandler {
}

class ServerHttpHandler implements HttpHandler {
    ServerHttpHandler(URLHandler handler) {
    }
    public void handle(final HttpExchange exchange) throws IOException {
        // form return body after being handled by program
        try {
            // form the return string and write it on the browser
        } catch(Exception e) {
        }
    }
}

public class Server {
    public static void start(int port, URLHandler handler) throws IOException {

        //create request entrypoint

        //start the server
    }
}

```
2. The grep command can also be used to return files that end or begin with a certain string. For example, the format for finding lines that start with the letter b, in a file named list is `grep ‘^b’ list`. For finding lines that end with b: `grep ‘b$’ list`.

Example 1
```
$ grep '^p' Server.java
public class Server {
```

Example 2
```
$ grep 'r$' Server.java
// A simple web server using Java's built-in HttpServer
            // form the return string and write it on the browser
        //start the server
```
3. Sometimes, a user may want to search for special characters.Special character, or metacharacters, are characters that are often used in commands. For example, the `^` and the `$` are used to represent the beginning or end of a line, as seen in the previous bullet point.To make the computer understand that you want to literally search for those characters as strings in a file, you need to put a backslash before the metacharacter. For example,  `grep ^\.` gives all the lines that begin with a period.(The caret means search the beginning of the line, and because the dot has a backslash before it,the computer searches for the dot,rather than the caret `^`.If the backslash was put before both the caret and the dot, then it would search for both the caret and dot, and it would search everywhere in the file not just at the beginning.)

Example 1
```
$ grep '\.' Server.java
// Examples from https://dzone.com/articles/simple-http-server-in-java were useful references
import java.io.IOException;
import java.io.OutputStream;
import java.net.InetSocketAddress;
import java.net.InetAddress;
import java.net.URI;
import com.sun.net.httpserver.HttpExchange;
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpServer;
      this.handler = handler;
            String ret = handler.handleRequest(exchange.getRequestURI());
            exchange.sendResponseHeaders(200, ret.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(ret.getBytes());
            os.close();
            String response = e.toString();
            exchange.sendResponseHeaders(500, response.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(response.getBytes());
            os.close();
        HttpServer server = HttpServer.create(new InetSocketAddress(port), 0);
        server.createContext("/", new ServerHttpHandler(handler));
        server.start();
        System.out.println("Server started at http://" + InetAddress.getLocalHost().getHostName() + ":" + port);
        System.out.println("(Or, if it's running locally on this computer, use http://localhost:" + port + " )");
```

Example 2

```
$ grep '\^' TestDocSearch.java
```


4. The grep command can be used as a filter.The format for this is `ls -l *.txt | grep Sep`. This command finds all text files with the “Sep” string in the description of the file that the `ls -l *.txt` command prints to the terminal, but it does not find this string within the file itself.

Example 1
```
Vaseem@User-PC MINGW64 ~/Downloads/docsearch-main (1)/docsearch-main
$ ls -l *.java
-rw-r--r-- 1 Vaseem 197611 2655 Feb  7 12:02 DocSearchServer.java
-rw-r--r-- 1 Vaseem 197611 2055 Feb  7 12:02 Server.java
-rw-r--r-- 1 Vaseem 197611  888 Feb  7 12:02 TestDocSearch.java

Vaseem@User-PC MINGW64 ~/Downloads/docsearch-main (1)/docsearch-main
$ ls -l *.java | grep Sep
```

Example 2

```
Vaseem@User-PC MINGW64 ~/Downloads/docsearch-main (1)/docsearch-main
$ ls -l *.java | grep 265
-rw-r--r-- 1 Vaseem 197611 2655 Feb  7 12:02 DocSearchServer.java
```


All of these command-line options were found in a [Java Oracle document](https://docs.oracle.com/cd/E19253-01/806-7612/filesearch-99633/index.html).

URL: https://docs.oracle.com/cd/E19253-01/806-7612/filesearch-99633/index.html
