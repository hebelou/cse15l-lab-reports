import java.io.IOException;
import java.net.URI;

class ChatHandler implements URLHandler{

  public String handleRequest(URI url){
    String query = url.getQuery();
    if(url.getPath().equals("/add-message")){
      if(query.startsWith("s="))
      
    }else{
      return "Error!"
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
