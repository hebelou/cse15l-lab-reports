# Lab Report 2
1. 
```
import java.io.IOException;
import java.net.URI;

class ChatHandler implements URLHandler{
  String chatHistory = "";
  public String handleRequest(URI url){
    String query = url.getQuery();
    if(url.getPath().equals("/add-message")){
      if(query.startsWith("s=")){
        String[] parameters = url.getQuery().split("&");
        String message = parameters[0].split("=")[1];
        String user = parameters[1].split("=")[1];
        this.chatHistory += user + ": " + message + "\n";
        return this.chatHistory;
      }else{
        return "Error";
      }
    }else{
      return this.chatHistory;
    }
  }
}

class ChatServer {
  public static void main(String[] args) throws IOException {
    if(args.length == 0){
      System.out.println("Missing port number! For the port number, try any number between 1024 to 49151.");
      return;
    }
    int port = Integer.parseInt(args[0]);
    Server.start(port, new ChatHandler());
  }
}
```
![Image](CSE15L-Lab2-Q1.1.png)
The main method and handleRequest method are called. The relevant arguments are `url` and `/add-message`. The relevant values are that `user` = `jpolitz`, `message`  = `Hello`, `chatHistory`, and 'url'. Since each of the strings were just created, the values were changed from null to the relevant values that were entered.
<br>
![Image](CSE15L-Lab2-Q1.2.png)
The main method and handleRequest method are called. The relevant arguments are `url` and `/add-message`. The revelant values are that `user` = `yash`, `message` = `How+are+you`, `chatHistory`, and `url`. Since each of these relevant values were updated after the first entry, `user` changes from `jpolitz` to `yash, `message` changes from `Hello` to `How+are+you`, the new message is added to `chatHistory`, and a new value for `url` is generated.  
<br>

2. 

