# Live DEMO

Want give it a try? There is a simple demo of our implementation:

1. Connect to the WebSocket at

        ws://bitsocket-demo.bitrich.info
   
   It simulates your customer's connection.

2. Send following JSON message to the Web Socket:

    <!-- language: lang-json -->
    
        {"action":"subscribeChannel", "channel":"order_book"}
        
   It is your customer subscribing to a channel called *order_book*.

3. Then send arbitrary JSON message to the REST endpoint:

        http://bitsocket-demo.bitrich.info:8080/publish/order_book
        
   It is your *back-end system* publishing new message to channel *order_book*. This endpoint will be indeed secured not to be reachable from the Internet.

You can [use on-line tools](test.md) to try it.
   
> Note: This is only demo deployment with a lot checks turned off. It is running on low cost server. **But it handles more than [5000 concurent](performance.md) users.**

# How BitSocket works
- BitSocket provides streaming API for common / public data (private messaging is in development).
- Producer (you) publishes messages to channels he defines.
- Consumers (your customers) subscribe to channel they want.
- Consumers receive messages published to channels they are subscribed to (excluding those published prior to their subscription).

> Note: BitSocket can be also run in the polling mode. It will poll your existing REST API and publish messages instead of you. You don't need to implement anything at all. But this solution has its drawnbacks we can discuss with you.

## How channels work?
- BitSocket is multi-channel!
- List of channels is dynamic – by default, any string is a valid channel.
- You can publish for example: 
  - order book updates to *order_book* channel (see above) 
  - filled trades to *trades* channel – just send data to `bitsocket-demo.bitrich.info:8081/publish/trades` instead
- Your customer can subscribe to any channel by `subscribeChannel` action (see above).
- By default, nothing happens if your customer subscribes to channel you are not using; validation against pre-defined list is indeed a customization we offer.
- Multiple subscriptions are supported.
- Incoming message clearly identifies the channel it belongs to:

        {"channel":"order_book", "payload":"...."} 

# Why use it?

- true *push* model
  - alternative to resource-wasting polling mechanism (you know why you apply API limits...)
  - consumer learns about the change much faster (milliseconds instead of seconds)
- pain-free integration – don't mess up with WebSocket implementation, we did it already!
- easy deployment
  - deployed using [Docker](https://www.docker.com/)
  - able to run in your own infrastructure – no need for 3rd-party provider
- performance in the first place
  - serves high number of customers per processing unit – see [performance overview](performance.md)
  - highly scalable solution – just add another server as your business grows 

# What do we offer?

- licence for commercial usage
- customization and integration tailored to your needs 
- documentation how to deploy and run the server
- service support
- adding your exchange to [xchange-stream](https://github.com/bitrich-info/xchange-stream) client library

# What it costs?

Feel free to contact us at [info@bitrich.info](mailto:info@bitrich.info). We'll find right price for everyone.
