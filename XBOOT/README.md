
## ���Խ���

XBOOT��һ��TI C2000ƽ̨��bootloader��������USBTTL��USBCAN��Ӳ��������ʵ��
C2000ϵ��DSP�̼�IAP���ܡ�

XBOOT��Ϊ�����汾�Ͷ��ư汾�������汾��ѣ������������޼���֧�֣����ư汾
��������ҵ���ϣ��ṩ���޵ļ���֧�֡�

### �����汾����

- ֧��TMS320F28335/TMS320F28035��
- 28335ֻ֧��30M�ⲿ����28035ʹ���ڲ�10M����
- ֧��һ��CAN�ӿڣ�3��TTL���ڣ�28035Ϊ1����������ͨѶ��GPIO�̶���
- CAN�ӿڲ����ʹ̶�500kbps��
- ���ڲ����ʹ̶�115200bps��
- �޹̼����ܹ��ܡ�
- ֻ֧��1���û�������ڵ�ַ�̶���
- ֧���û��̼����¡�

### ���ư汾����

- ֧��C2000ϵ������оƬ��������FLASH��С��оƬ���⣩��
- �ⲿ����Ƶ�ʿ�ѡ��
- ֧��һ��CAN�ӿڣ�3��TTL���ڻ���485�ӿڣ�����ͨѶ��GPIO��ѡ��
- CAN�ӿڲ����ʿɶ�ֵ��Ĭ��500kbps��
- ���ڲ����ʿɶ��ƣ�Ĭ��115200bps��
- ���Դ��̼����ܹ��ܣ�ȷ���û��̼���ȫ��
- �ɶ�ȡFLASH��SRAM���������ݡ�
- ֧�����6���û����򡣿��������ϵ���Զ����е��û�����
- ֧���û��̼����¡�
- �ɷ�������ģ��EEPROM��
- ����������ȫ��ΨһID�����ڲ�Ʒ���кţ��̼����ܵȳ��ϡ�

### Ӳ����Դռ��

- FLASH��FLASHA��FLASHB����ַ0x330000-0x33FF80
- ��ʱ����CpuTimer0
- ͨ�Žӿ�
  1. SCIA��GPIO28��GPIO29��
  2. SCIB��GPIO22��GPIO23��
  3. SCIC��GPIO62��GPIO63��
  4. ECANA��GPIO30��GPIO31��
- ������ת�û������Ժ�XBOOT�������У����SRAM���û������޳�ͻ��

## ����ԭ��

### C2000�ϵ���������

C2000ϵ��DSP�ϵ��Ժ���ڲ�BOOTROM�������ϵ縴λ�Ժ�DSP��ת��0x3FFFC0ִ���ڲ�
BOOTROM�еĴ��룬�����ض�GPIO״̬���ж�����ģʽ��һ���ʹ��FLASH����ģʽ��
��BOOTROM�д���ִ�����֮�󽫿���Ȩ����FLASH�еĴ��롣

������������ͼ��ʾ��
 
![28335�ϵ���������](PIC/image1.png "28335�ϵ���������")

### XBOOT����ԭ��

C2000����BOOTROMͨ��GPIO���ж�����ģʽ���������ʱ��Ҫ����������ߣ�ÿ�θ��³���
Ҫ������ߣ�ʹ�ò��㡣ͬʱ�ڲ�BOOTROM�еĴ���ֻ��ִ�м򵥵Ĵ�����¹��ܡ�
 
![XBOOT����ԭ��](PIC/image2.png "XBOOT����ԭ��")

ʵ����C2000ϵ��DSP��FLASH�ռ�����ʮ�ֳ��㣬��FLASH��������(sector)����Ϊ�����֣�
FLASHA������BOOTROM����ת��ַ0x33FFF6���������XBOOT����FLASHB����ģ������EEPROM��
ʣ�µ�����FLASH����û�����

�ϵ��Ժ�FLASHA�е�XBOOT��������ִ�У����ݴ��ڻ���CAN�ӿ��������жϽ����û�����
����XBOOT shell�����0.5����ĳ�������������յ�5����ĸ��e��������XBOOT shell��
��������û����򡣸���ƻ�����ϵ�0.5����ϵ���ʱ��һ������¿��Խ��ܣ������ĺô�
��Ӳ����������������ߡ�XBOOT shell�п���ִ���û��̼�IAP���¹��ܡ�

## ʹ�÷���

### ����XBOOT shell����

XBOOT�ϵ������Ժ���0.5���ڼ�⴮�����룬����յ�����5����ĸ��e���������XBOOT shell��
�������ģ��EEPROM��ȡ�û�������ڵ㣬����û�������Ч��ִ���û����򣬷������XBOOT shell��

ʹ�ó����ն����Ӵ��ڣ�`������115200��8λ���ݣ�1λֹͣ����У�飬������`����ס������
����ĸ��e����������ư��ϵĸ�λ���������߸����ư������ϵ硣���Խ���XBOOT shell��

CAN�ӿڽ���UARTCAN����USBCANӲ�������ù���ģʽΪ�Ž�ģʽ������ʹ�÷����봮����ȫ��ͬ��

�����ն�ΪWindows XP�Դ�����ͨ��`��ʼ->���г���->����->ͨѶ->�����ն�`�򿪡�
Windows7ϵͳ���������նˣ����Խ�Windows XPϵͳ�ĳ����ն����������ȥֱ��ʹ�á�

### �����û������ϸ����

��������XBOOT shell��ʹ��empty����鿴Ҫд���FLASH�Ƿ�Ϊ�գ������Ϊ�գ�ʹ��
`erase x`��������������FLASH������xΪFLASH���֣�ȡֵ`a��b��c��`.

ʹ��ymodem��������û������

**ע��**��erase a�����������XBOOT��������FLASH���ݣ�Ҳ�����������룬��������
FLASH�����Ժ����֮ǰ��XBOOT��Ȼ�������в��Ҹ��³�����������Ժ���磬ֻ��ʹ��
��������XBOOTд��DSP�����û�����д��δ������FLASH���н�����ǲ�ȷ���ġ�

## ��������

���ڶԻ�����XBOOT�ṩ���������������

### empty

FLASH�������޲�������������û�FLASH�Ƿ�Ϊ�ա�

``` 
empty
 FLASHA is NOT empty @ 0x338000.
 FLASHB is NOT empty @ 0x330000.
 FLASHC is NOT empty @ 0x328000.
 FLASHD is empty @ 0x320000.
 FLASHE is empty @ 0x318000.
 FLASHF is empty @ 0x310000.
 FLASHG is empty @ 0x308000.
 FLASHH is empty @ 0x300000.
```

**ע��**��C2000ϵ��DSP��FLASH��С������λ��һ��������д��֮ǰ����ȷ��Ϊ�գ�������Ҫ�Ƚ��в�����

### erase 

FLASH�������
erase�������һ���ַ���������abcdefgh���ֱ��Ӧ8��FLASH����������ͬʱָ��
���FLASH��������`erase bcd`��������b c d����flash������

**ע��**��erase a�����������XBOOT��������FLASH���ݣ�Ҳ�����������룬��������
FLASH�����Ժ����֮ǰ��XBOOT��Ȼ�������в��Ҹ��³�����������Ժ���磬ֻ��ʹ��
��������XBOOTд��DSP�����û�����д��δ������FLASH���н�����ǲ�ȷ���ġ�
 
```
empty
 FLASHA is NOT empty @ 0x338000.
 FLASHB is NOT empty @ 0x330000.
 FLASHC is NOT empty @ 0x328000.
 FLASHD is empty @ 0x320000.
 FLASHE is empty @ 0x318000.
 FLASHF is empty @ 0x310000.
 FLASHG is empty @ 0x308000.
 FLASHH is empty @ 0x300000.
erase c
 erase flash sector 0x04 OK.
empty
 FLASHA is NOT empty @ 0x338000.
 FLASHB is NOT empty @ 0x330000.
 FLASHC is empty @ 0x328000.
 FLASHD is empty @ 0x320000.
 FLASHE is empty @ 0x318000.
 FLASHF is empty @ 0x310000.
 FLASHG is empty @ 0x308000.
 FLASHH is empty @ 0x300000.
```

### reboot

����ϵͳ����һ����ʱ��������λms��ִ��reboot 1000����ʱ1���Ժ�����������
�޲���Ĭ��10ms��ʱ�Ժ�����������

```
reboot
 rebooting ...
reboot 500
 rebooting ...
```


### ymodem

ʹ��ymodemЭ������û������

ִ��ymodem��������ն���ʾ�ַ�`C`�Ժ�ѡ��˵�`����->�����ļ�`���ļ���ѡ��
�û������hex�ļ���Э��ѡ��Ymodem��������ͼ��ɡ�
 
![ѡȡ���͵�hex�ļ�](PIC/image5.png "ѡȡ���͵�hex�ļ�")
 
![APP�̼����͹���](PIC/image6.png "APP�̼����͹���")

```
ymodem
 warning: flash address 0x330000 is not empty, do not use it.
 ymodem update firmware, press A to abort ...
 CCCCCCC
  Update firmware OK!
  File Name: APP.hex
  File Size: 148517
  End Addr:  0x32F874
```

ִ��ymodem�����Ժ󣬳����ն���ʾCʱ�����԰���ĸaȡ�����

�û����͵�APP�̼���**����ʹ��FLASHA����FLASHB**�����򽫻���XBOOT�̼���

### help 

��ʾXBOOT������Ϣ��

```
help
 empty -> empty Check flash sector is empty or not.
 erase -> erase [abcdefgh] Erase flash sector.
 entry -> entry [hex addr] Get/Set user app entry.
 memrd -> memrd [hex addr] [hex len] Show Memory.
 goto -> goto [hex addr] to execute.
 eeprom -> eeprom [load|save|read|write] [addr] [data] Operate Int. EEPROM.
 uuid -> uuid [128bits hex string] Show/Setup UUID.
 reboot -> reboot [delay ms] Restart xboot.
 ymodem -> update user APPs.
 help -> help Info.
 version -> version display bootloader Info.
```

**ע��**�������汾��֧��entry��memrd��goto��eeprom��uuid���

### version

��ʾXBOOT�汾�Ͱ�Ȩ��Ϣ��
 
```
version
 xboot v18.03.17 SN: 6D53150634C24E7C907C685707910F63
 for TMS320F28335 by ECHO Studio <echo.xjtu@gmail.com>.
 All Rights Reserved.
```

**ע��**��û��д��ΨһID��DSPоƬ�����к�SN����ΪȫFF��

## �߼�����

���ư�XBOOT����֧�ָ߼����ܣ�ͨ�������ṩ�ĸ߼��������֧�֡�

### entry

���á��鿴�û�������ڵ㡣

Ĭ���޲����鿴��ǰ�û�������ڵ㣬��һ������Ϊ�����û�������ڵ㡣
 
```
entry
 user app entry is 0x328000.
entry 320000
 set user app entry to 0x320000 .
entry
 user app entry is 0x320000.
```

### memrd 

��ȡDSP�ڴ档�ڴ��ַ����SRAM��FLASH����ַ��

memrd�������������������һ��ΪҪ��ȡ���ڴ��ַ���ڶ���ΪҪ��ȡ�����ݳ��ȣ�
Ĭ��128��ȫ��Ϊʮ�����ơ�
 
```
memrd 328000

0x328000 0072 E301 761F 030D E801 D418 E2C4 0106
0x328008 E808 9378 E700 0040 7700 E68A 0000 7700
0x328010 761F 0305 BFA9 0F12 0F22 6905 0201 5601
0x328018 0022 6F09 761F 0312 0200 1A07 1000 761F
0x328020 0305 1E22 761F 030D E801 E118 E2C4 0106
0x328028 E80E B850 E700 0040 7700 E68A 0000 7700
0x328030 761F 0305 BFA9 0F12 0F24 6905 0201 5601
0x328038 0024 6F0D 761F 0312 1A07 0010 0200 1A07
0x328040 0080 1A07 0020 761F 0305 1E24 761F 030D
0x328048 E2C4 0006 7700 E68A 0000 7700 761F 0305
0x328050 BFA9 0F12 0F26 6905 0201 5601 0026 6F0B
0x328058 761F 0312 0200 1A07 0040 1A07 0800 761F
0x328060 0305 1E26 761F 030D E801 F260 E2C4 0106
0x328068 E80E 6668 E700 0040 7700 E68A 0000 7700
0x328070 761F 0305 BFA9 0F12 0F28 660A 8F00 C480
0x328078 44F4 6C03 1AFC 2000 0200 1E28 0006 0201
```

### goto

��ת���µ�ִַ�С�
����һ����λ������Ϊ������28335ƽ̨��goto 33fff6��������XBOOT����ͼ 11��
 
```
goto 33FFF6
 goto address 0x33FFF6 to execute...
```

### eeprom

��дDSP�ڲ�ģ��EEPROM�����ĸ������`read��write��load��save`��

- ��eeprom��eeprom read [��ַ] [����]�����е�ַΪ��Ҫ���������ȿɲ��Ĭ��128�֣����ڲ������ȡ���ݡ�
- дeeprom��eeprom write [��ַ] [����]�����е�ַ�����ݾ�Ϊ��Ҫ����������д���ڲ����档
- ����eeprom��eeprom load�����ݴ�FLASH���ص��ڲ����档
- �洢eeprom��eeprom save��eeprom���ݴ��ڲ�����д��FLASH�����籣�档

����ģ��eeprom�ܹ�255��16λ�֣�ǰ16����Ԥ����XBOOT����ʹ�ã������û�������á�
 
```
eeprom read 0

0x0000  8000 0032 FFFD 01F4 FFFF FFFF FFFF FFFF
0x0008  FFFF FFFF FFFF FFFF FFFF FFFF FFFF FFFF
0x0010  0003 0001 0028 FFFF 00F3 FFFF 0009 FFFF
0x0018  FFFF FFFF FFFF FFFF FFFF FFFF FFFF FFFF
0x0020  0002 0001 0028 FFFF 00F3 FFFF 0009 FFFF
0x0028  FFFF FFFF FFFF FFFF FFFF FFFF FFFF FFFF
0x0030  FFFF FFFF FFFF FFFF FFFF FFFF FFFF FFFF
0x0038  FFFF FFFF FFFF FFFF FFFF FFFF FFFF FFFF
0x0040  0002 0001 0028 FFFF 00F3 FFFF 0009 FFFF
0x0048  FFFF FFFF FFFF FFFF FFFF FFFF FFFF FFFF
0x0050  FFFF FFFF FFFF FFFF FFFF FFFF FFFF FFFF
0x0058  FFFF FFFF FFFF FFFF FFFF FFFF FFFF FFFF
0x0060  FFFF FFFF FFFF FFFF FFFF FFFF FFFF FFFF
0x0068  FFFF FFFF FFFF FFFF FFFF FFFF FFFF FFFF
0x0070  FFFF FFFF FFFF FFFF FFFF FFFF FFFF FFFF
0x0078  FFFF FFFF FFFF FFFF FFFF FFFF FFFF FFFF
```

### uuid

�鿴��������оƬ��ΨһID��оƬ��ΨһID��������оƬ���кš��������кš��豸���кš�
�������������ܹ̼�������ִ�MCU��STM8��STM32��STC�����ṩ��ΨһID��TI C2000ϵ��
MCUû���ṩΨһID��XBOOT����OTP�洢�ռ���ʵ��ΨһID���ܡ�

����������uuid���������ʾ��ǰDSP��uuid��������ʾ�� 

```
uuid
BBF2CE53C8B54062B42C3E8423AD9E88
```

�������û������uuid��uuid�����������δд��uuid�ĵ��壬����ʹ��uuid����д��uuid��
������ʾ��

```
uuid BBF2CE53C8B54062B42C3E8423AD9E88
```

**ע��**��һ�鵥��uuidֻ��д��һ�Σ�Ҫ��֤д���uuid**ÿ�ζ����������ɵ�**�������ظ���
uuidд���Ժ����²�дFLASH������Ӱ�죬����uuid��Ψһ�����Ǹ����µ�оƬ��

## �û������дָ��

### ��λ����

TMS320F28335 FLASH��ڵ�ַΪ0x33FFF6�������ַλ��FLASHA���Ѿ���XBOOTռ�á�
�û�������Ҫʹ������ĸ�λ������XBOOTĬ�ϻὫ��ڵ�ַ���õ�FLASHC��ͷ�����֣�
��ַ0x328000���ϵ��XBOOT������ת��FLASHCִ���û����롣

�û�������Ҫ����λ�����ŵ�����FLASH������ʼ�����֡������û��������FLASHC����λ
����ռ��FLASHC��ʼ�����֡�
 
![�û������λ������28335��](PIC/image14.png "�û������λ������28335��")

���ư�XBOOT�̼�����ʹ��entry�����������ø�λ������ʵ�ֶ�APP֧�֡�
����XBOOT����ʹ��FLASHA��FLASHB���û�������ռ��������FLASH����дcmd�ļ�ʱ��Ҫע�⣬
�û���������ע����map�ļ���ȷ������FLASHû��ʹ�á�
 
![�û�����������ռ��FLASHA��FLASHB](PIC/image15.png "�û�����������ռ��FLASHA��FLASHB")

### ����hex�ļ�

ʹ��hex2000�����й��߽�CCS�������ɵ�.out�ļ�ת��Ϊhex�ļ����������£�

```
hex2000 --intel -romwidth 16 -memwidth 16 TEST.out
```

����TEST.outΪ��Ҫת����.out�ļ�������ʵ����Ҫ�����滻��.hex�ļ�ʵ��Ϊ�ı��ļ���
����ʹ���ı��༭���򿪲鿴��

CCS5�������ñ�������Զ����hex�ļ������÷������£�

�ڹ������ϰ�Alt+Enter����Ŀ��������ҳ��Ȼ������ͼ���ü��ɡ�
 
![CCS5.5�����Զ����hex�ļ�](PIC/image16.png "CCS5.5�����Զ����hex�ļ�")

## uuid����ָ��

UUID������ͨ��Ψһʶ���� (Universally Unique Identifier)����ָ��һ̨���������ɵ�
���֣�����֤����ͬһʱ���е����л�������Ψһ�ġ�ͨ��ʹ��һ��16�����ַ�����ʾ��
�磺`BBF2CE53C8B54062B42C3E8423AD9E88`��

### Linux

Linuxƽ̨�¿���ʹ��uuidgen��������uuid��ע������ʱȥ���м�ġ�-���ָ�����
 
![Linux��ʹ��uuidgen��������uuid](PIC/image17.png "Linux��ʹ��uuidgen��������uuid")

### Windows

Windowsƽ̨�¿���ʹ��PDFFactory���������uuid.
 
![Windows��ʹ��UUIDFactory����UUID](PIC/image18.png "Windows��ʹ��UUIDFactory����UUID")

## ��������

### ������

ʹ�÷�����ο����ĵ������߲��ṩ�κμ���֧���뱣֤��

### ���ư�

��������ҵ���ϡ�ʹ�÷�����ο����ĵ���ͬʱ���߻ᾡ������ͻ����󣬲��ṩ���޵ļ���֧�֡�
����֧�ֽ�������XBOOT�̼������û���Ҫ�����ղ�Ʒ���Ը������߲��ṩ�û���Ʒ��
����֧���뱣֤���û�ʹ��XBOOTĬ�Ͻ����������
