# CVE-2019-0708
Unauthenticated CVE-2019-0708 "BlueKeep" Scanner PoC by  [@JaGoTu](https://twitter.com/JaGoTu) and [@zerosum0x0](https://twitter.com/zerosum0x0).

![CVE-2019-0708 Scanner](screenshot.png)

### In this repo

A scanner fork of rdesktop that can detect if a host is vulnerable to CVE-2019-0708 Microsoft Windows Remote Desktop Services Remote Code Execution vulnerability. It shouldn't cause denial-of-service, but there is never a 100% guarantee across all vulnerable versions of the RDP stack over the years. As it is unauthenticated, the scanner will not have reliable results for NLA hosts (which is a confirmed mitigation).

There is also a Metasploit module, which is a current **work in progress** (MSF does not have an RDP library).

### Building and Running

There is a [pre-made rdesktop binary in the repo](https://github.com/zerosum0x0/CVE-2019-0708/blob/master/rdesktop-fork-bd6aa6acddf0ba640a49834807872f4cc0d0a773/rdesktop), but the steps to building from source (X11 GUI Linux environment) are as follows:

```
git clone https://github.com/zerosum0x0/CVE-2019-0708.git
cd CVE-2019-0708/rdesktop-fork-bd6aa6acddf0ba640a49834807872f4cc0d0a773/
./bootstrap
./configure --disable-credssp --disable-smartcard
make
./rdesktop 192.168.1.7:3389
```

Please refer to the normal rdesktop compilation instructions.

### Is this dangerous?

Small details of the vulnerability have already begun to reach mainstream. This tool does not grant attackers a free ride to a theoretical RCE.

Modifying this PoC to trigger the denial-of-service does lower the bar of entry but will also require some amount of effort. We currently offer no explanation of how this scanner works other than to tell the user it seems to be accurate in testing and follows a logical path.

System administrators need tools like this to discover vulnerable hosts. This tool is offered for legal purposes only and to forward the security community's understanding of this vulnerability. As this PoC actively exploits the vulnerability, do not use against targets without prior permission.

### License

rdesktop fork is licensed as GPLv3.

Metasploit module is licensed as Apache 2.0.
