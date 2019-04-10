
# PCweixinHook.md

```xml
<?xml version="1.0" encoding="utf-8"?>
<CheatTable>
  <CheatEntries>
    <CheatEntry>
      <ID>0</ID>
      <Description>"log等级"</Description>
      <LastState Value="0" RealAddress="10DC8280"/>
      <VariableType>4 Bytes</VariableType>
      <Address>WeChatWin.dll+0x111F8280-0x10000000</Address>
    </CheatEntry>
    <CheatEntry>
      <ID>1</ID>
      <Description>"log输出dbgview"</Description>
      <LastState Value="1" RealAddress="10E2298D"/>
      <VariableType>4 Bytes</VariableType>
      <Address>WeChatWin.dll+0x1125298D-0x10000000</Address>
    </CheatEntry>
  </CheatEntries>
</CheatTable>
```
### https://www.52pojie.cn/thread-924687-1-1.html?tdsourcetag=s_pctim_aiomsg

# 微信多开方法-low逼的方法

* emmm这样还得挨个扫码
```cmd
@echo off
start /d "C:\Program Files (x86)\Tencent\WeChat\" WeChat.exe

start /d "C:\Program Files (x86)\Tencent\WeChat\" WeChat.exe

start /d "C:\Program Files (x86)\Tencent\WeChat\" WeChat.exe

start /d "C:\Program Files (x86)\Tencent\WeChat\" WeChat.exe
exit

```
