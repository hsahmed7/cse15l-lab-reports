# Report #3 For CSE 15L

## Part 1: Bugs
The buggy program does not have the reverseInPlace method implemented correctly. The results of a Junit Test are shown below:

The JUnit test code:
```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
  @Test 
	public void testReverseInPlace2() {
    int[] input1 = {8,3,4,6 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 6,4,3,8 }, input1);
	}
}

```

The code for the method implementation:

```
public class ArrayExamples {
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
}

```

The command-line input and the output:

```
JUnit version 4.13.2
.E
Time: 0.008
There was 1 failure:
1) testReverseInPlace2(ArrayTests)
arrays first differed at element [2]; expected:<3> but was:<4>
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:418)
        at org.junit.Assert.assertArrayEquals(Assert.java:429)
        at ArrayTests.testReverseInPlace2(ArrayTests.java:16)
        ... 30 trimmed
Caused by: java.lang.AssertionError: expected:<3> but was:<4>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
        ... 36 more

FAILURES!!!
Tests run: 1,  Failures: 1

```

Some poorly written test cases might pass with the buggy code. An example is shown below.

The JUnit test code:

```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
}

```

The command-line input and the output:

```
JUnit version 4.13.2
.
Time: 0.005

OK (1 test)
```

The buggy code for the implementation of the method is the same as shown in the code block for the failed test.

The symptoms of the two tests are shown below:

The JUnit test code for testReverseInPlace and testReverseInPlace2:

```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}

  @Test 
	public void testReverseInPlace2() {
    int[] input1 = {8,3,4,6 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 6,4,3,8 }, input1);
	}

}

```
The command-line input and the output:

```
JUnit version 4.13.2
.E.
Time: 0.011
There was 1 failure:
1) testReverseInPlace2(ArrayTests)
arrays first differed at element [2]; expected:<3> but was:<4>
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:418)
        at org.junit.Assert.assertArrayEquals(Assert.java:429)
        at ArrayTests.testReverseInPlace2(ArrayTests.java:16)
        ... 30 trimmed
Caused by: java.lang.AssertionError: expected:<3> but was:<4>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
        ... 36 more

FAILURES!!!
Tests run: 2,  Failures: 1

```







## Part 2: Researching Commands

The grep command has many uses. Four of these uses are listed below.

1. The grep command can be used to search for lines in a file that do not contain a certain string. The format to use grep in this way is `grep -v [string] [filename]` where the string can be inputted directly without quotations if it is a single-word string. In Example 1, the grep command is used to find the lines in Server.java that do not contain the letter "e". In Example 2, the grep command is used to find all the lines in Server.java that do not contain a semicolon(;). This command-line option is useful because it allows the user to filter the output and look for something specific.

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
2. The grep command can also be used to return files that end or begin with a certain string. The general format for finding lines that begin with a certain string is `grep '^[string]' [filename]`. For finding lines that end with a certain string: `grep '[string]$' [filename]`. In Example 1, the grep command is used to find lines in Server.java that start with a lowercase "p". In Example 2, the grep command is used to find lines that end with the letter "r". This grep command-line option is useful because it further enables the user to filter search results. If the user remembers that one of the lines of code starts with the word "System", but is having trouble finding that code snippet manually, then the user can use this method to easily find the code.

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
3. Sometimes, a user may want to search for special characters. Special character, or metacharacters, are characters that are often used in commands. For example, the `^` and the `$` are used to represent the beginning or end of a line, as seen in the previous bullet point.To make the computer understand that you want to literally search for those characters as strings in a file, you need to put a backslash before the metacharacter. In Example 1,  `grep ^\.` gives all the lines that begin with a period.(The caret means search the beginning of the line, and because the dot has a backslash before it, the computer searches for the dot, rather than the caret `^`. If the backslash was put before both the caret and the dot, then it would search for both the caret and dot, and it would search everywhere in the file not just at the beginning.) In Example 2, the grep command is used to find the caret (^) symbol in the file TestDocSearch.java, and because there are no lines containing this symbol, no lines are returned. This grep command-line option is useful for searching for metacharacters properly.

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


4. The grep command can be used as a filter. The format for this is `[command] | grep [String]`. This use of grep takes the output of any command, and gives it over to grep command to search the text for the String. In Example 1, the grep command finds all text files with the “Sep” string in the description of the file that the `ls -l *.txt` command prints to the terminal. The grep command here is used to find files that were created in September. In Example 2, the grep command is used to search for a specific number, which is only in one line of the `ls` output. This grep command-line option is useful because it allows you to not only search the text within files, but also search text printed to the terminal by other commands (which may print out a lot of text, so it can be useful to search for specific keywords).

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
