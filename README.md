การติดตั้ง 

sudo apt-get update 

sudo apt-get install usb-modeswitch ppp 

git clone https://github.com/ThaiEasyElec/EFDV782_Mini_PCI-E_3G_4G_Converter_Hat.git

เข้าไปที่โฟลเดอร์ umtskeeper 

cd EFDV782_Mini_PCI-E_3G_4G_Converter_Hat/umtskeeper/

1.การเชื่อม internet สามารถทำได้ 2 วิธีคือ 1.การเชื่อมต่อด้วย Sakis3G โดยใช้คำสั่ง (ค่าตั้งค่าโปรแกรม Sakis3G ดูได้จากเอกสารนี้ตั้งแต่หน้าที่ 25 เป็นต้นไป https://downloads.thaieasyelec.com/ETEE064/3G_Expansion_for_Raspberry_Pi_User_Manual_TH.pdf ) 

sudo ./sakis3g --interactive

2.ใช้คำสั่ง UMTSkeeper สั่ง Sakis3G ให้เชื่อมต่อดังนี้ 
sudo ./umtskeeper --sakisoperators "OTHER='CUSTOM_TTY' CUSTOM_TTY='/dev/ttyUSB3' APN='CUSTOM_APN' CUSTOM_APN='internet' APN_USER='true' APN_PASS='true' " --sakisswitches "--sudo --console" --devicename 'Quectel' --log --nat 'no'

![Capture1](https://user-images.githubusercontent.com/8803501/105302203-d2fb6680-5bed-11eb-8e81-9cc37ecda3c5.JPG)


 
