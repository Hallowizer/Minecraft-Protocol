Minecraft Protocol
==================

Data Formats
------------

Before we begin to discuss the format and use of each packet in the Minecraft Protocol,
we need to set some bounds on what data and field types are available to be sent in each packet.
These types and their uses are outlined in the table below.
The more complex data types such as `varint`, `itemstack` and `metadata` will have their own section detailing parsing and handling below.

Data Type    | Description
------------ | -----------
Byte         | Single byte consiting of 8 bits. This has a range of -127 to 127 signed, or 0 to 255 unsigned.
Byte Array   | An array of bytes. This is serialized as the length field, followed by the bytes.
String       | A byte array where the bytes represent the characters in the String.
String Array | An array of Strings. Similar to byte arrays, this is the length field, followed by the bytes.
UUID         | An id. This is serialized as two longs, the most significant bits coming first.


Packet Format
-------------

Each packet in the Minecraft protocol comes sent in a vary distinct data format.
First, each frame begins with a varint that signifies the entire length of the following data.
This varint contains both the length of the `Packet ID` and the length of the `Packet Data`.

Field Name  | Type
----------- |-------
Length      | varint
Packet ID   | varint
Packet Data | varies
