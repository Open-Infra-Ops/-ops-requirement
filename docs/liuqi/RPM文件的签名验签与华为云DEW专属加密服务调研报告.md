## RPM文件的签名验签与华为云DEW专属加密服务调研报告

#### RPM文件的签名、验签流程（RSA）

以下使用的是SJJ1310接口（北京江南天安 金融加密机），版本号为1.0.9

```
import java.io.File;
import java.io.IOException;
import java.nio.file.Files;
import java.util.ArrayList;
import java.util.Arrays;
import cn.tass.exceptions.TAException;
import cn.tass.hsmApi.hsmGeneralFinance.hsmGeneralFinance;
import cn.tass.kits.Forms;

// 1. 实例化接口
hsmGeneralFinance hsm = hsmGeneralFinance.getInstance("D:\\cacipher.ini");

-- cacipher.ini
[LOGGER]
logsw				=			error
logPath				=			./
[HOST 1]
hsmModel			=			SJJ1310
linkNum				=			-3
host				=			124.127.49.180
port				=			8018
timeout				=			3
encodetype			=			0
msgheadlength			=			0
--

// 2. 随机生成RSA密钥对
ArrayList<byte[]> rsa = hsm.genRSAKeyPair(keyUserWay: 0, keyLen: 2048, exponent: 65537, storeindex: 1, keyLable: "RsaKeyPair-1");

RSA密钥对生成后，会保存在加密机内，通过索引可完成数字签名以及查询公钥

// 3. 将文件转化为Byte数组
public static byte[] fileConvertToByte(String filePath) throws IOEcception {
	File file = new File(filePath);
	return Files.readAllBytes(file.toPath());
}

当需要签名的文件为大文件时（如RPM文件），先将文件转为byte数组，对该数据进行摘要运算，再用摘要计算签名

// 4. 计算数据得到数据摘要（采用国密SM3算法进行摘要运算）
byte[] indata = hsm.generateHASH(fileData);
return Forms.byteToHexString(indata); 

// 5. RSA计算签名（EW）
int hashFlag = 5;
int padFlag = 1;
byte[] fileData = fileConvertToByte("D:\\JNTA\\signature\\src\CUnit-2.1.3\21.oe1.src.rpm");
byte[] indata = hsm.generateHASH(fileData);
byte[] genRsaSignature = hsm.genRsaSignature(hashFlag, padFlag, indata, key: 1);
return Forms.byteToHexString(genRsaSignature);

// 6. 根据密钥索引获取RSA公钥
byte[] publicKey = hsm.getRSAPublicKey(1);
return Forms.byteToHexString(publicKey);

// 7. RSA公钥验签
boolean verifyRsaSignature = hsm.verifyRsaSignature(hashFlag, padFlag, indata, publicKey, genRsaSignature);
return verifyRsaSignature;
```

#### 购买与使用

- 上述签名、验签的流程可通过在华为云DEW购买专属加密实例实现。加密实例须至少购买2个，费用为初装费（￥90,000.00 * 2）+ 租金（￥100,000.00 * 2 / 年）。
- 在购买专属加密服务后，激活专属加密实例，可获取加密机的IP地址。加密机通过VPC代理的方式起到隔离的效果，仅为配置的VPC代理提供专属通道。
- 在购买专属加密服务后，华为云还会发放专属的服务管理工具以及配套的SDK，并邮寄一张包含用户重要信息的卡片（其中的UK在进行服务配置的时候需要用到）

#### 注意
由于受疫情影响，金融加密机的定制时间延长，预计华为云接单的2~3个月后能正式使用专属加密服务。
