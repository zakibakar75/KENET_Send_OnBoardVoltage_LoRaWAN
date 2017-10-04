This is the Arduino file meant for LoRaWAN bytes transmission.  Do not forget to change the Keys and Device Address (for ABP) by referring
to what you have during device registration on LoRaWAN server, example TTN.  Copy and paste it to the place in the .ino file here.

In this file, you can see how bytes are constructed and sent out.  This technique is useful to be used with Arduino-based LMIC library.

As you know, Arduino can read its on-board voltage level by reading some registers.  When the result is got in mV, we will split it into
high and low byte, each is one byte.

If you have TTN account, monitor the "Data" section.  You can format the payload so that it can give you the reading in Volts.  Paste this
code at the "Payload Format" section in your TTN Application Dashboard :

function Decoder(bytes, port) {
  // Decode an uplink message from a buffer
  // (array) of bytes to an object of fields.
  var decoded = {};
    decoded.Voltage = (bytes[0] << 8 | bytes[1]) / 1000;
  return decoded;
}
