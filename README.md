# SCRAP Design Proposal

This is a preliminary proposal for the layout of the _Swarm Communication_ and _Routing Assistance Protocol_

Because of our usage of the **nrf24l01**, each packet must be 32 bytes long, we need a custom protocol

# Packet layout

For this protocol proposal, each message must have a header that spans 3 bytes, the first being the Reciever, the second being the sender, and the third being the message id. This allows for 256 bots and 256 messages, along with an ample 29 byres for each message

| 1           | 2         | 3              | 4+               |
| ----------- | --------- | -------------- | ---------------- |
| Reciever ID | Sender ID | Message Number | Message Contents |

# Messages

## 01 - Grid Update

Becuase we are able to transfer data at a more than sufficient speed of 1 mbps, it is proposed that the grid be updated one square at a time. This also facilitates the ability to rapidly respond to changes in the environment. Unfortunately, due to how little data is required for this message, there
is a lot of wasted packet space.
|4 | 5 | 6 |
|- | - | - |
| X Coordinate | Y Coordinate | Pitch Change (signed value) |
