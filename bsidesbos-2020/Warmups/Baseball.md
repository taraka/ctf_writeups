## Baseball

We're provided with a file the content of which looks like its base64 encoded, decoding that we're presented with something simmilar.

The easiest way to solve this one is to throw it in to CyberChef and apply the magic filter it'll very quickly show you that to decode it you need to:

* Base64 decode
* Base32 decode
* Base58 decode

With that you have the flag