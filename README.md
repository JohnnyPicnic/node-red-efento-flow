# node-red-efento-flow
Process Efento COAP payloads in Node-Red
![2023-08-16_14-30-15](https://github.com/JohnnyPicnic/node-red-efento-flow/assets/5553884/80931afd-3d3f-4d8c-9f1c-15e9cb3d1215)


Requires node-red-contrib-coap and node-red-contrib-protobuf
Find the protobuf files here https://github.com/efento/Proto-files

For node-red-contrib-coap there is a small modification needed so that the payload and response are not formatted into strings.
Neceassary changes can be found at:
https://github.com/JohnnyPicnic/node-red-contrib-coap/blob/main/coap/coap-in.js



