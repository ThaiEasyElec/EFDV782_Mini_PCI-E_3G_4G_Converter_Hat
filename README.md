**การติดตั้ง (installation)**


`sudo apt-get update`

`sudo apt-get install usb-modeswitch ppp` 

`git clone https://github.com/ThaiEasyElec/EFDV782_Mini_PCI-E_3G_4G_Converter_Hat.git`




เข้าไปที่โฟลเดอร์ umtskeeper (go to directory EFDV782_Mini_PCI-E_3G_4G_Converter_Hat/umtskeeper/ )

`cd EFDV782_Mini_PCI-E_3G_4G_Converter_Hat/umtskeeper/`



1.การเชื่อม internet สามารถทำได้ 2 วิธีคือ 1.การเชื่อมต่อด้วย Sakis3G โดยใช้คำสั่ง (การตั้งค่าโปรแกรม Sakis3G ดูได้จากเอกสารนี้ตั้งแต่หน้าที่ 25 เป็นต้นไป  ( 2 ways internet connection  1. connect via Sakis3G and setting config follow file pdf.) [3G_Expansion_for_Raspberry_Pi_User_Manual_TH](https://downloads.thaieasyelec.com/ETEE064/3G_Expansion_for_Raspberry_Pi_User_Manual_TH.pdf).

`sudo ./sakis3g --interactive`

![image](https://user-images.githubusercontent.com/8803501/105305884-b1e74580-5bee-11eb-844d-12134bb698a2.png)



2.ใช้คำสั่ง UMTSkeeper สั่ง Sakis3G ให้เชื่อมต่อดังนี้  ( 2 .connect via UMTSkeeper command)

`sudo ./umtskeeper --sakisoperators "OTHER='CUSTOM_TTY' CUSTOM_TTY='/dev/ttyUSB3' APN='CUSTOM_APN' CUSTOM_APN='internet' APN_USER='true' APN_PASS='true' " --sakisswitches "--sudo --console" --devicename 'Quectel' --log --nat 'no'`

![Capture1](https://user-images.githubusercontent.com/8803501/105302203-d2fb6680-5bed-11eb-8e81-9cc37ecda3c5.JPG)




หากต้องการให้ Raspberry Pi เชื่อมต่อ internet อัตโนมัติ ให้ไปที่ไฟล์ rc.local โดยใช้คำสั่ง (AutoStart connect internet)

`sudo nano /etc/rc.local`


จากนั้นนำคำสั่งด้านล่างไปใส่ไว้ก่อน ```exit 0``` และกด ```Ctrl + X``` จากนั้นกด ```Y``` เพื่อบันทึก (and then paste command below to inside rc.local before exit 0 and Ctrl + X and Y in order to save edit file )

`sudo /home/pi/EFDV782_Mini_PCI-E_3G_4G_Converter_Hat/umtskeeper/./umtskeeper --sakisoperators "OTHER='CUSTOM_TTY' CUSTOM_TTY='/dev/ttyUSB3' APN='CUSTOM_APN' CUSTOM_APN='internet' APN_USER='true' APN_PASS='true' " --sakisswitches "--sudo --console" --devicename 'Quectel' --log --nat 'no' & `

![image](https://user-images.githubusercontent.com/8803501/105316677-c974fd00-5bf3-11eb-993a-d7145fd50690.png)


 ทำการ Reboot โดยใช้คำสั่ง (Reboot Raspberry Pi)
 
 `sudo reboot`
