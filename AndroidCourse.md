Android 之keystore的获取

首次使用需要创建密钥

命令如下：

keytool -genkey -alias doutuian -keystore dotuian.keystore

doutuian 是自己创建的名字  dotuian.keystore 是密钥的保存文件

执行上一个命令后会出现一些信息
输入密钥口令：（自己设置的密码）
再次输入密码：（验证密码）

之后是个人信息填入
你的名字和姓是什么？
你的单位名称是什么？
你的组织名称是什么？
你所在的城市区域是什么？
国家的双字地区代码是什么？
照填就行（所有信息不会认证的）
填完后出现 你所填的信息   确认 y

之后出现输入（你创建的名称（dotuian））口令（刚才创建的密码）


如果输入正确就会出现下面的情况

C:\Program Files\Java\jre1.8.0_151\bin>keytool -genkey -alias dotuian -keystore
dotuian.keystore -keyalg RSA
输入密钥库口令:
再次输入新口令:
您的名字与姓氏是什么?
  [Unknown]:  mark
您的组织单位名称是什么?
  [Unknown]:  pks
您的组织名称是什么?
  [Unknown]:  sos
您所在的城市或区域名称是什么?
  [Unknown]:  China
您所在的省/市/自治区名称是什么?
  [Unknown]:  贵阳
该单位的双字母国家/地区代码是什么?
  [Unknown]:  zh-cn
CN=mark, OU=pks, O=sos, L=China, ST=贵阳, C=zh-cn是否正确?
  [否]:  y

输入 <dotuian> 的密钥口令
        (如果和密钥库口令相同, 按回车):

Warning:
JKS 密钥库使用专用格式。建议使用 "keytool -importkeystore -srckeystore dotuian.k
eystore -destkeystore dotuian.keystore -deststoretype pkcs12" 迁移到行业标准格式
 PKCS12。

C:\Program Files\Java\jre1.8.0_151\bin>keytool -list -v -keystore dotuian.keysto
re
输入密钥库口令:
密钥库类型: JKS
密钥库提供方: SUN

您的密钥库包含 1 个条目

别名: dotuian
创建日期: 2018-2-1
条目类型: PrivateKeyEntry
证书链长度: 1
证书[1]:
所有者: CN=mark, OU=pks, O=sos, L=China, ST=贵阳, C=zh-cn
发布者: CN=mark, OU=pks, O=sos, L=China, ST=贵阳, C=zh-cn
序列号: 53fba81f
有效期为 Thu Feb 01 11:01:25 CST 2018 至 Wed May 02 11:01:25 CST 2018
证书指纹:
         MD5:  B5:CF:52:50:3B:06:6B:F4:D0:A0:FA:8D:A1:F0:DC:47
         SHA1: 14:10:BA:F4:CF:0A:ED:A9:D1:A7:E6:3B:4C:DB:96:8F:07:E9:3F:14
         SHA256: 7D:73:69:F9:44:77:F3:2A:AE:5E:5B:FA:9C:28:0E:6B:41:9F:54:10:F0:
F0:1F:FF:63:D4:D0:E1:6A:C4:DD:58
签名算法名称: SHA256withRSA
主体公共密钥算法: 2048 位 RSA 密钥
版本: 3

扩展:

#1: ObjectId: 2.5.29.14 Criticality=false
SubjectKeyIdentifier [
KeyIdentifier [
0000: D9 44 47 67 22 13 93 6E   88 20 95 3A 44 F2 9A 22  .DGg"..n. .:D.."
0010: 6A 22 CE D3                                        j"..
]
]



*******************************************
*******************************************



Warning:
JKS 密钥库使用专用格式。建议使用 "keytool -importkeystore -srckeystore dotuian.k
eystore -destkeystore dotuian.keystore -deststoretype pkcs12" 迁移到行业标准格式
 PKCS12。

C:\Program Files\Java\jre1.8.0_151\bin>

现在就完成获取：SHA1了

若下次再去取得的话 输入：keytool -list -v -keystore dotuian.keystore
就会出现SHA1的信息
