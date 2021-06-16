
# การสร้างโปรเจค



## การลงทะเบียน 

การลงทะเบียนจะมี 2 แบบ 

1. แบบผ่านหน้าเว็บ ซึ่งจะกรอกข้อมูลเยอะกว่าแบบที่ 2 
2. แบบเปิดใช้งานผ่าน Visual Studio Code

### แบบผ่านหน้า


1. จะมี dialog แสดงให้ลงทะเบียน ExtJS ให้เราเลือกเป็น Trial 
2. กรอก email และกด enter 
3. จะมีการส่งรหัสไปยัง email ใหันำรหัสมากรอก


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