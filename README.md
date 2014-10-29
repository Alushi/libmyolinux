HackUMBC
=========

This hack allows the user to interface with a Myo armband from a Linux host.
It parses the raw packets used in Myo's transmission protocol to identify the 
current gesture with the potential for other data fields.

## License
This project is licensed under the MIT License.

Parts of it, however, rely on [MYO-python](https://github.com/smartin015/MYO-python), which has its own license(s).

libmyolinux is currently a proof of concept, and so takes a bit of effort to get running. Our software handles the bytecode generated by the MYO, but doesn't include support for the bluetooth dongle, which means you will need a Windows machine to act as a networked usb drive and send packets to your Linux machine. We will be integrating a driver for the bluetooth driver soon hopefully.

Here are the steps to get it running today:
1. clone the repo https://github.com/f825f5242ed81a32cd04e5269665f40a/libmyolinux to both the Windows machine and the Linux Machine
2. In Windows, open libmyolinux/MYO-python/MyoTestSend.py
3. On line 15 adjust sock.connect(("10.123.41.113", 6969)) to use the public ip address of your Linux machine.
4. Plug the bluetooth dongle into your Windows machine and run MyoTestSend.py
5. On Linux, run libmyolinux/src/libmyolinux/game1.py and you should get a simple game running that is controlled by your armband.
6. Copy the format of game1.py to accept data from the socket and make whatever you like.

