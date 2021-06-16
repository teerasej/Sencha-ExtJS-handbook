
# การสร้างโปรเจค



## การลงทะเบียน 

การลงทะเบียนจะมี 2 แบบ 

1. [แบบผ่านหน้าเว็บ](https://www.sencha.com/products/extjs/evaluate/) ซึ่งจะกรอกข้อมูลเยอะกว่าแบบที่ 2 
2. แบบเปิดใช้งานผ่าน Visual Studio Code

**** การลงทะเบียนจะถือว่าเป็นการเปิดใช้งานในโหมดทดลองใช้ (trial) มีระยะเวลา 30 วัน**


### แบบผ่าน Visual Studio Code Extension 


1. ถ้ายังไม่ได้ติดตั้ง Extension ให้ติดตั้งก่อน 
   - ค้นหา **extjs** ในส่วนการติดตั้ง extension 
   - หรือ[คลิกดู extension จากที่นี่](https://marketplace.visualstudio.com/items?itemName=Sencha.vscode-extjs)
2. หลังจากติดตั้งจะมี dialog แสดงให้ลงทะเบียน ExtJS ให้เราเลือกเป็น Trial 
3. กรอก email และกด enter 
4. จะมีการส่งรหัสไปยัง email ที่เราลงทะเบียนไว้ ใหันำรหัสมากรอก
5. กด enter เป็นอันเสร็จเรียบร้อย 

**** ช่วง trial จะมีระยะเวลาทดลองใช้ 30 วัน**

## การสร้างโปรเจค

รันคำสั่ง 

```
ext-gen app -i
```

จะเป็นการเริ่มการสร้างโปรเจคแบบค่อยๆ กรอกข้อมูล 

```bash
? would you like to see the defaults for package.json? No
? Would you like to create a package.json file with defaults? No
? What would you like to name your Ext JS app? CounterApp
? What type of Ext JS template do you want? make a selection from a list
? What Ext JS template would you like to use? moderndesktopminimal
? What is the Template folder name? ~/extjs-templates/Application/moderndesktop
? What would you like to name the npm Package? counter-app
? What version is your Ext JS application? 0.0.1
? What is the description? counter-app description for Ext JS app CounterApp
? What is the GIT repository URL? https://github.com/
? What are the npm keywords? Ext JS Sencha HTML5
? What is the Author's Name? Sencha, Inc.
? What type of License does this project need? ISC
? What is the URL to submit bugs? https://github.com/
? What is the Home Page URL? http://www.sencha.com
```

### การรันทดสอบโปรเจค

เราสามารถรัน web server ขึ้นมา จากภายในโฟลเดอร์โปรเจคได้ โดยรันคำสั่งด้านล่างจากภายในโปรเจค

```
cd counter-app
npm start
```