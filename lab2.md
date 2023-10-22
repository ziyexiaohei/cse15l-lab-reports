# Lab Reprot 2

## Source Code For `StringServer.java`

```
import java.io.IOException;
import java.net.URI;
import java.net.URLDecoder;
import java.lang.Object;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    int num = 0;
    String s = new String();
    int i = 0;

@Deprecated
public static String decode(String s)
{
    return URLDecoder.decode(s);
}


public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {

        return decode(s);      
        }

        else {
            if (url.getPath().contains("/add")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    i += 1;
                    s = s + i+"."+parameters[1]+"\n";
                    return decode(s);
                }
            }
            return "404 Not Found!";
        }
    }
}






class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}

```

## Screenshouts of  using `/add-message` 
1. ![Hello](laba21.png)
 * Once the code is being run, under the `Handler` class, method `handleRequest`, and `decode` has been called and also the `main` method under class `StringServer` is being called.
 * The `main` method takes a array of string as argument, and convert it into interger and store in port inorder for the Server to start. The `decode` method takes String as argument. And the `handleRequest` method takes URI as argument. The value of relevant file of the class are `int num`, `String str`, and `int i`.
 * Once the request has been processed, a new string will be stored in `String str` which contains the string requested, and i as the counter. The `int i` value is mean to keep track of how many string has been requested, the valuen of i will change with every `/add` request. If there is no value got changed then it either return to the decode of `String str` (when the path is "/"), or  `return "404 Not Found!"` for path that is unknow.
<br>
![Howareyou](laba22.png)
    * Once the code is being run, method `handleRequest`, and `decode` is being called, inroder to store string enter by user, and print them to the screen.
    * The revelent argument to method `handleRequest` and `decode` is the `String s`
