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
        this.chatHistory += user + ": " + message + "\n\n";
        return this.chatHistory;
      }
    }else{
      return "Error"
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
