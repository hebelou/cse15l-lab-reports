# Lab Report 2 
## Part 1 
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
The `main` method and `handleRequest` method are called. The relevant arguments are `3456` for `args` and the url entered for `url`. The relevant values are that `user` = `jpolitz`, `message`  = `Hello`, and `url`. The relevant field of the class is `chatHistory`. Since each of the strings were just created, all of the values of each field were changed from null to the values that were entered. Therefore `chatHistory` was just changed from null to `jpolitz: Hello\n`.

![Image](CSE15L-Lab2-Q1.2.png)
The `main` method and `handleRequest` method are called. The relevant arguments are `3456` for `args` and the url entered for `url`. The revelant values are that `user` = `yash`, `message` = `How+are+you`, and `url`. The relevant field of the class is `chatHistory`. Since each of these relevant values were updated after the first entry, `user` changes from `jpolitz` to `yash`, `message` changes from `Hello` to `How+are+you`, `chatHistory` changes from `jpolitz: Hello\n` to `jpolitz: Hello\nyash: How+are+you\n`, and a new url for `url` is generated.  

## Part 2 
![Image](CSE15L-Lab2-Q2.1.png)
Using VSCode on my computer, the first file is the absolute path to my private key
![Image](CSE15L-Lab2-Q2.2.png)
Using VSCode on my computer, the second file is the absolute file to my public key ending in `.pub`.

![Image](CSE15L-Lab2-Q2-3.png)
Using VSCode on my computer, this is an instance of me logging into my `ieng6` account without having to enter my password. 

## Part 3 
These two weeks I learned how to `ssh` into my remote CSE15L account using the terminal, whether it is in a EdStem workspace or VSCode. I also learned how to set up a server, and that I am able to go and change values of a remote webpage.
