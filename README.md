# google-bard-logger
Extract data from a current active session and print it to the console log.

Sometimes a conversation with your neural network buddy can be really productive and you want to save it. Instead of scrolling over hundreds of messages and manually take screenshots, just put the code below in a console of your browser. It will extract a conversation data in a `question N : answer N` format and will print in to the console. Then you'll be able to just select and copy conversation logs.
```
function getElementByXpath(path) {
  return document.evaluate(path, document, null, XPathResult.FIRST_ORDERED_NODE_TYPE, null).singleNodeValue;
}
var i = 1;
for (;;) {
  try {
    console.log("=================================================================================\n");
    console.log(`Question ${i}\n`);
    console.log(getElementByXpath(`/html/body/chat-app/side-navigation/mat-sidenav-container/mat-sidenav-content/main/chat-window/div[1]/div[1]/div/div[${i}]/user-query/div/div[2]/h2`).innerHTML+"\n");
    console.log(`Answer ${i}\n`);
    console.log(getElementByXpath(`/html/body/chat-app/side-navigation/mat-sidenav-container/mat-sidenav-content/main/chat-window/div[1]/div[1]/div/div[${i}]/model-response/response-container/div/div[2]/div/message-content/div`).innerText+"\n");
    i++;
  }catch(e){
    break;
  }
}
```
