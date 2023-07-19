# node-red-efento-flow
Process Efento COAP payloads in Node-Red
![2023-07-19_10-26-12](https://github.com/JohnnyPicnic/node-red-efento-flow/assets/5553884/af4320de-4f6a-42f7-9c96-a429b1b1ff36)

Requires node-red-contrib-coap and node-red-contrib-protobuf
Find the protobuf files here https://github.com/efento/Proto-files

For node-red-contrib-coap there is a small modification needed in order to send an unformatted response back to the Efento sensor.
In file coap-in.js you need to change:

    function _constructPayload(msg, contentFormat) {
        const payload = msg.payload;

        if (payload == null) {
            return null;
        }

        if (_checkContentFormat(contentFormat, "text/plain")) {
            return msg.payload.toString();
        } else if (_checkContentFormat(contentFormat, "json")) {
            return JSON.stringify(msg.payload);
        } else if (_checkContentFormat(contentFormat, "cbor")) {
            return cbor.encode(msg.payload);
        } else {
            return msg.payload.toString();
        }
    }

To:

    function _constructPayload(msg, contentFormat) {
        const payload = msg.payload;

        if (payload == null) {
            return null;
        }

        if (_checkContentFormat(contentFormat, "text/plain")) {
            return msg.payload;
        } else if (_checkContentFormat(contentFormat, "json")) {
            return JSON.stringify(msg.payload);
        } else if (_checkContentFormat(contentFormat, "cbor")) {
            return cbor.encode(msg.payload);
        } else {
            return msg.payload;
        }
    }



