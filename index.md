Here is my code for ChatServer!

'''
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList; 

class Handler implements URLHandler {
    ArrayList<String> words = new ArrayList<String>();
    ArrayList<String> names = new ArrayList<String>();
    String errorString = 
    "Invalid format. Format is /add-message?s=<string>&user=<string>";

    public String handleRequest(URI url) {
        if (url.getPath().contains("/add-message")) {
            // try this and catch if its not possible
            // split int s, Hello&user, jpolitx
            String [] parameters = url.getQuery().split("=");
            if (!parameters[0].equals("s") || parameters.length != 3 || 
            !parameters[1].contains("&user")) {
                return String.format("%s", errorString);
            }
            
            parameters[1] = parameters[1].substring(0, parameters[1].length() - 5);
            words.add(parameters[1]);
            names.add(parameters[2]);
        }
        String finalString = "";
        for (int i = 0; i < words.size(); i ++) {
            finalString += names.get(i) + ": " + words.get(i) + "\n";
        }
        if (finalString.length() != 0) {
            return finalString;
        }
        if(url.getPath().equals("/")) {
            return finalString;
        }
        return "Page not found";
        //return "Page not found";
    }
}

class ChatServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}

'''
