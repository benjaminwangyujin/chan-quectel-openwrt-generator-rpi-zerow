Thanks be to God from Whom are all good things.

This repo helps you to generate a <a href="https://github.com/IchthysMaranatha/asterisk-chan-quectel"> chan-quectel </a> openwrt binary for any platform by running a github action. Fork this repository and then run the github action providing link to openwrt sdk for the platform required. For example to generate binary for the we826 router running on openwrt 22, you would have to provide sdk link https://downloads.openwrt.org/releases/22.03.3/targets/ramips/mt7620/openwrt-sdk-22.03.3-ramips-mt7620_gcc-11.2.0_musl.Linux-x86_64.tar.xz and choose Ast18 from dropdown for version. You can browse and obtain link for the needed sdk [here](https://downloads.openwrt.org/releases/) 

This will generate chan-quectel binary for the master branch of the chan-quectel repo. However, you can edit the makefile to generate the binary for any repo or branch. For eg, to generate binary for the quectel dtmf branch for openwrt 22, edit the file [here](https://github.com/IchthysMaranatha/chan-quectel-openwrt-generator/blob/main/openwrt/urlmakefile/current/Ast18/chanq/Makefile) and change foll lines

PKG_SOURCE:=master.zip <br>
PKG_SOURCE_URL:=https://github.com/IchthysMaranatha/asterisk-chan-quectel/archive/refs/heads/

to 

PKG_SOURCE:=QuectelDTMFforIMS.zip <br>
PKG_SOURCE_URL:=https://github.com/IchthysMaranatha/asterisk-chan-quectel/archive/refs/heads/

The link is the zip download link found in the <> Code dropdown broken up into filename and the rest of the link

Asterisk version must correspond to the asterisk version packaged with the openwrt version of your device. For example

Openwrt 19 - Asterisk 16
Openwrt 22 - Asterisk 18
Openwrt 23 - Asterisk 20 and so on

The openwrt minor version is not very important, if facing issues with a particular minor version, you can try with another.

Provide link to sdk, choose the correct Asterisk version and run the workflow action, in about 10 minutes the ipk should be ready for download within a zip file. This can be installed or you can use 7zip to manually extract chan_quectel.so for lib replacement

if using other branchs of openwrt, you need to change regex,such as  using  immortalwrt， yaml should be changed to regex: '^.+immortalwrt-sdk-([\d]*).*?-([a-z,0-9]*)-.+$' 

