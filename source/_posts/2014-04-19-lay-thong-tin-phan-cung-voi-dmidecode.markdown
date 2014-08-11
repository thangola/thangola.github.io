---
layout: post
title: "Lấy thông tin phần cứng với dmidecode"
date: 2014-04-19 22:28:02 +0700
comments: true
categories: hardware
---
Lệnh __dmidecode__ đọc bảng DMI hệ thống (SMBIOS) và hiển thị thông tin về phần cứng và BIOS của máy chủ. Bảng DMI lưu rất nhiều thông tin hữu ích của hệ thống như cấu hình của từng thiết bị, số serial, hoặc cấu hình tối đa mà máy chủ có thể hỗ trợ (dung lượng RAM tối đa chẳng hạn).

Tham số hay được sử dụng nhất của `dmidecode` là `--type TYPE`, với `TYPE` là ID của một kiểu DMI cụ thể, hoặc là một trong các từ khoá sau: `bios,  system,  baseboard,  chassis,  processor,  memory,  cache,  connector,  slot.`

Danh sách đầy đủ của các kiểu DMI:
```plain
       Type   Information
       --------------------------------------------
          0   BIOS
          1   System
          2   Baseboard
          3   Chassis
          4   Processor
          5   Memory Controller
          6   Memory Module
          7   Cache
          8   Port Connector
          9   System Slots
         10   On Board Devices
         11   OEM Strings
         12   System Configuration Options
         13   BIOS Language
         14   Group Associations
         15   System Event Log
         16   Physical Memory Array
         17   Memory Device
         18   32-bit Memory Error
         19   Memory Array Mapped Address
         20   Memory Device Mapped Address
         21   Built-in Pointing Device
         22   Portable Battery
         23   System Reset
         24   Hardware Security
         25   System Power Controls
         26   Voltage Probe
         27   Cooling Device
         28   Temperature Probe
         29   Electrical Current Probe
         30   Out-of-band Remote Access
         31   Boot Integrity Services
         32   System Boot
         33   64-bit Memory Error
         34   Management Device
         35   Management Device Component
         36   Management Device Threshold Data
         37   Memory Channel
         38   IPMI Device
         39   Power Supply
         40   Additional Information
         41   Onboard Devices Extended Information
         42   Management Controller Host Interface
```

Mỗi từ khoá dùng với tham số `--type` tương ứng với một hoặc nhiều kiểu DMI:
```plain
       Keyword     Types
       ------------------------------
       bios        0, 13
       system      1, 12, 15, 23, 32
       baseboard   2, 10, 41
       chassis     3
       processor   4
       memory      5, 6, 16, 17
       cache       7
       connector   8
       slot        9
```

Ví dụ, để xem thông tin về chassis, có thể dùng lệnh:
```bash
    dmidecode --type chassis
```
hoặc:
```bash
    dmidecode --type 3
```

Output sẽ có dạng:
```plain
# dmidecode 2.12
SMBIOS 2.7 present.

Handle 0x0300, DMI type 3, 21 bytes
Chassis Information
	Manufacturer: HP
	Type: Rack Mount Chassis
	Lock: Not Present
	Version: Not Specified
	Serial Number: SGH3519Y51
	Asset Tag:
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: Unknown
	OEM Information: 0x00000000
	Height: 1 U
	Number Of Power Cords: 2
	Contained Elements: 0
```

Với DMI type 16, ta có thể lấy thông tin về Physical memory array, với số khe cắm RAM và dung lượng tối đa mà hệ thống hỗ trợ:
```plain
# dmidecode -t 16
# dmidecode 2.12
SMBIOS 2.7 present.

Handle 0x1000, DMI type 16, 23 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: Single-bit ECC
	Maximum Capacity: 384 GB
	Error Information Handle: Not Provided
	Number Of Devices: 12

Handle 0x1001, DMI type 16, 23 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: Single-bit ECC
	Maximum Capacity: 384 GB
	Error Information Handle: Not Provided
	Number Of Devices: 12
```
Như vậy, dung lượng bộ nhớ tối đa mà hệ thống có thể hỗ trợ là 384GB, với 12 khe cắm RAM, mỗi khe cắm một thanh RAM 32GB.

Tương tự, các bạn có thể thử với các type khác để lấy các kết quả mình cần. Nếu cần giúp đỡ, chúng ta có thể dùng `man dmidecode`, dĩ nhiên.