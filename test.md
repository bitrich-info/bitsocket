# On-line tools for demo

You can feel our demo using on-line tools without need to hack anything.

## WebSocket client

Use our spartan [WebSocket javascript client](http://bitsocket-demo.bitrich.info/ws-client.html).

You can open it multiple times. You will see incoming messages in each tab.

## REST client

Use [hurl.it](https://www.hurl.it/) - on-line REST client.

Send POST message to

    http://bitsocket-demo.bitrich.info:8080/publish/order_book
   
with some JSON body
   
    {"test": 1}
        
As you can see on the following screenshot.
   
   [![rest client screenshot](assets/images/rest.png "Rest client screenshot")](assets/images/rest.png)
