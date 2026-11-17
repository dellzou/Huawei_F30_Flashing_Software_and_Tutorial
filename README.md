# 华为 F30 光猫使能工具与教程

用于华为星光 F30 系列光猫（V173、V173-50、V175 等）的维修使能、开启 Telnet、获取超级密码、修改 SN 与 MAC。

## 配套教程

完整命令、判断依据和回退步骤在这篇文章：

[华为 F30 光猫使能教程：修改 SN、修改 MAC、获取超密](https://xiaozou123.cn/huawei-f30-ont-enable-sn-mac-super-password/)

## 文件清单

| 文件 | 大小 | 用途 |
|---|---|---|
| `ONT_V500R19C00.exe` | 3,503,060 | ONT 使能工具，支持 V3/V5 使能和升级刷包 |
| `HW_Dollar2.exe` | 161,280 | 编辑 `hw_boardinfo`，2.2.0.2104 |
| `Huawei_Config_Crypto.exe` | 1,794,560 | `hw_ctree.xml` / cfg 配置加解密 |
| `Huawei_Password_Decrypt.exe` | 7,213,568 | `$2` 开头的密码解密 |
| `tftpd64.exe` | 146,656 | TFTP 服务端，导出/导入配置文件 |
| `putty.exe` | 574,976 | Telnet / SSH 客户端 |

### SHA256

```
a3dfc3daaf05fbff5b0da523dbb50b0753d12313c0a0f0f89175fa9c84f1e681  ONT_V500R19C00.exe
d3110469d8cccc7ca479105393e047faef74c74cfb34d174deece84153ac1cc8  HW_Dollar2.exe
8f005af234f73a456f5e4a127ed4624c40992445caf264d5f7566cbf3ee80808  Huawei_Config_Crypto.exe
615cafc0ed01d9beaabcec311424371a6b08bd49825dc3b3d22a83eed3abb444  Huawei_Password_Decrypt.exe
988292db5e71fa50b090ce2bfe66813791d944cde64c19b7f0ecda8892392a15  tftpd64.exe
a92c1d668f6d060db06535ad346221d23dec11f897d79115673206462906f698  putty.exe
```

`ONT_V500R19C00.exe` 与常见的 `ONT组播配置工具V3-V5 2.0.exe` 是同一个二进制文件，哈希一致，只是文件名不同。

## 使能包不在这个仓库

F30 是系列名，具体型号要单独配使能包：

- V173（XG-PON / 10G EPON）：[Huawei_V173_Flashing_Software_and_Tutorial](https://github.com/dellzou/Huawei_V173_Flashing_Software_and_Tutorial) 里的 `R22_shell.bin`
- V173-50（GPON / XG-PON，R24）：[Huawei_V173-50_Flashing_Software_and_Tutorial](https://github.com/dellzou/Huawei_V173-50_Flashing_Software_and_Tutorial) 里的 `V173-50_enable_package.bin`
- V175：见 [Huawei_V175_Flashing_Software_and_Tutorial](https://github.com/dellzou/Huawei_V175_Flashing_Software_and_Tutorial)

老固件（R19/R20 一代）可以只用 `ONT_V500R19C00.exe` 的 V3/V5 使能，不刷包。

## 相关仓库

同品牌其它机型，命令体系相近，排障时可以互相参照；每个仓库开头都对应一篇文章：

- [华为 HN8145X6 工具包](https://github.com/dellzou/Huawei_HN8145X6_Flashing_Software_and_Tutorial)：华为 HN8145X6，补全 AllShell、改光模
- [华为 HN8145XR 工具包](https://github.com/dellzou/Huawei_HN8145XR_Flashing_Software_and_Tutorial)：华为 HN8145XR，主猫改公版、从猫组网
- [华为 K662D 工具包](https://github.com/dellzou/Huawei_K662D_Flashing_Software_and_Tutorial)：华为 K662D，从猫改光猫模式
- [华为 V173-50 工具包](https://github.com/dellzou/Huawei_V173-50_Flashing_Software_and_Tutorial)：华为 V173-50，R24 装备包与 OBSCTool 日志
- [华为 V173 工具包](https://github.com/dellzou/Huawei_V173_Flashing_Software_and_Tutorial)：华为 V173 主猫，补全 Shell、改公版、改 boardinfo
- [华为 V175 工具包](https://github.com/dellzou/Huawei_V175_Flashing_Software_and_Tutorial)：华为 V175，R23 固件包开 Telnet

## 注意

- 工具会发原始组播包、监听端口、修改网络配置，被杀毒软件报毒是常态，建议放在虚拟机或冰点还原环境运行。
- 仅用于自己拥有或获得授权的设备。改 SN/MAC 属于修改设备标识，换机克隆前建议先向运营商报备。
- 改任何配置前先备份 `hw_boardinfo`、`hw_boardinfo.bak`、`hw_ctree.xml`。
