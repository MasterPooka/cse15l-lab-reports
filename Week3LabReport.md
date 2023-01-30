**Week 3 Lab Report**
---
The StringServer is able to process URL requests to add messages and display them in order of creation.
---

```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler{
    int index = 0;
    String[] messages = new String[1000];

    //handles URL requests; adds messages and displays them
    public String handleRequest(URI url){
        messages[0] = "";
        if (url.getPath().equals("/")){
            return String.format("Start Message: %s ", print());
        } else {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add-message")){
                String[] params = url.getQuery().split("=");
                if (params[0].equals("s")){
                    if (params[1] == null || params[1].equals("")){
                        return String.format("Current Message: %s ", print());
                    }
                    messages[index] = params[1];
                    index++;
                    return String.format("New Message: %s ", print());
                }
            }
            return "404 Not Found!";
        }
    }

    //prints all messages
    public String print(){
        String allMessages = "";
        if (messages == null){
            return allMessages;
        }
        for (int i = 0; i < messages.length; i++){
            if (messages[i] != null){
                allMessages = allMessages + "\n" + messages[i];
            } else {
                return allMessages;
            }
        }
        return allMessages;
    }
}

//instantiate the server
class StringServer{
    public static void main(String[] args) throws IOException {
        if (args.length == 0){
            System.out.println("Usage: java StringServer <port>");
            return;
        }
        int port = Integer.parseInt(args[0]);
        Server.start(port, new Handler());
    }
}
```
---
> The following screenshot demonstrates two messages being saved to the server. The resulting results are the results of two methods called handleRequest and print. The method print prints out all messages saved in the server in a list format, while the handleRequest method parses the url to find the message inside of the url to save to the server. The method searches for the string "/add-message" and "s=" to determine if the client wants to send a message to the server, and where the message starts. "%20" represents a space in each message, while words are written as is. The message "hello this is my second message" is the first in the list beacuse it was the first message, and "hello this is my third20message" is listed after because the user sent this message as their second message, after their first message. The field "/add-message" is important because if the user used any other string in place of this, there would be an error because there is nothing else coded except for this specific URL field.

![Image](https://masterpooka.github.io/cse15l-lab-reports/demo1.png)
---
---
> The following screenshot demonstrates another two messages being saved to the server, along with another two messages sent from before from another user. This screenshot also demonstrates the usager of two methods, the print method and the handleRequest method. The handleRequest method here yet again parses the url for the message to be added and saved to the server, while the print method displays the messages in order of creation, which is why some messages are shown before others. The method searches for the string "/add-message" and "s=" to determine if the client wants to send a message to the server, and where the message starts. "%20" represents a space in each message, while words are written as is. The messages "counting 15 indices" and "seomthing about this is wrong" are added to the server, and are displayed last because they are the most recent messages adeed to the server. The field "/add-message" is important because if the user used any other string in place of this, there would be an error because there is nothing else coded except for this specific URL field.

![Image](https://masterpooka.github.io/cse15l-lab-reports/demo2.png)
---
---

**Bugs from Lab 3**
---

- One failure inducing input for the program, in the form of a JUnit test written in a code block in Markdown.

```
@Test
public void testReverseInPlace2(){
  int[] input1 = { 1, 2, 3, };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 3, 2, 1 }, input1);
}
```

- An input that doesn’t induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)

```
@Test
public void testReverseInPlace3(){
  int[] input1 = { 5, 5, 5, 5, 5 };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 5, 5, 5, 5, 5 }, input1);
}
```

- The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above)

![Image](https://masterpooka.github.io/cse15l-lab-reports/JUnitTests.png)

- The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)

*Before*
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

*After*
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < (arr.length) / 2; i += 1) {
      int temp = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = temp;
    }
  }
```

---
**Something New I Learned**
---
I learned how to create a basic server and connect to it from my web browser.
I also learned how to parse and process URL requests to find out what commands I could implement and include in my personal web server.
In addition to everything else, I learned about Markdown syntax and how to use it to make lab reports look better and more organized than just using a straight up text file without any formatting.
