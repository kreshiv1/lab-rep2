# lab-rep2
lab report - 2

CODE:
~~~
import java.io.IOException;
import java.net.URI;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileWriter;

class ChatHandler implements URLHandler {
  String chatHistory = "";

  public String handleRequest(URI url) {

    // expect /chat?user=<name>&message=<string>
    if (url.getPath().equals("/add-message")) {
      String[] params = url.getQuery().split("&");
      String[] shouldBeUser = params[1].split("=");
      String[] shouldBeMessage = params[0].split("=");
      if (shouldBeUser[0].equals("user") && shouldBeMessage[0].equals("s")) {
        String user = shouldBeUser[1];
        String message = shouldBeMessage[1];
        this.chatHistory += user + ": " + message + "\n\n";
        return this.chatHistory;
      } else {
        return "Invalid parameters: " + String.join("&", params);
      }
    }

    return "404 Not Found";
  }
}

class ChatServer {
  public static void main(String[] args) throws IOException {
    int port = Integer.parseInt(args[0]);
    Server.start(port, new ChatHandler());
  }
}
~~~

![Image](AB708786-FA12-4310-96CB-BA010E188574_4_5005_c.jpeg)

![Image](1986CE3B-7E53-4E9E-B96F-B2C9A06A9DBD.jpeg)


