**การติดตั้ง (installation)**
**วิธีนี้ใช้ได้กับชิพ EC25-A และ EC25-E**

1.ทำการเช็คว่าบอร์ด Raspberry Pi มองเห็นตัวโมดูล EC25 หรือไม่ โดยใช้คำสั่ง 

`lsusb`

--> Quectel Wireless Solutions Co., Ltd. EC25 LTE modem




2.ทำการติดตั้งโปรแกรม putty โดยใช้คำสั่ง

`sudo apt install putty -y`




3.ทำการเปิดโปรแกรม putty โดยตั้งค่า port ไปที่ /dev/ttyUSB2 และ baudrate 115200
![image](https://user-images.githubusercontent.com/8803501/149867323-2bff3c62-6d1e-4731-a850-fba884233e9e.png)




4.ใช้ AT command เพื่อเปิดใช้งานอินเตอร์เน็ตดังนี้

`AT+QCFG="usbnet",1`

`AT+CGDCONT=1,"IP","internet"`




5.ทำการ Reboot โมดูลโดยใช้คำสั่ง และรอ reboot โมดูลประมาณ 30 วินาที
`AT+CFUN=1,1`

6 เพิ่มคำสั่งลงใน File--> /etc/network/interfaces
ดังนี้
- เปิดFile--> sudo nano /etc/network/interfaces

- เพิ่มคำสั้ง
  auto usb0
  allow-hotplug usb0
  iface usb0 inet dhcp

- Save and Exit

7 Restart--> sudo reboot

8 จากนั้นให้ทำการเช็คการเชื่อมต่ออินเตอร์เน็ตโดยการใช้คำสั่ง `ping 8.8.8.8` ที่หน้า Terminal




หากต้องการปิดการใช้งานโหมดนี้ สามารถใช้คำสั่ง 

`AT+QCFG="usbnet",0`

ทำการ Reboot โมดูลโดยใช้คำสั่ง 
`AT+CFUN=1,1`
