# เริ่มโปรเจค

ติดตั้ง [node](https://nodejs.org/en/download/)
ทางเลือกจะลง [yarn](https://yarnpkg.com/lang/en/docs/install/#windows-stable) เพิ่มด้วยก็ได้


ติดตั้ง webpack

> `npm install webpack webpack-cli --save-dev`

ถ้าลง webpack แล้วจะต้องไฟล์ชื่อว่า webpack.config.js เพื่อเซ็ตค่า config ตามเอกสาร

- Entry
- Output


## เลือก Framework
### `No Framework`

เริ่มโปรเจคท์
> `npm init`

หากต้องทำงานร่วมกับ browser เก่าหรือ device เก่า จะต้องลง babel เพิ่ม

>

### `AngularJS`

### `ReactJS`

### `VueJS`

## ถ้าเริ่มทำ Test

### Install Jest
เหมาะกับ `Unit Test` และ `Intregation Test`
> `npm install --save-dev jest`

ถ้าใช้ `Puppeteer` ด้วย
> `npm install --save-dev jest-puppeteer puppeteer jest`

Document : [Jest with Puppeteer](https://jestjs.io/docs/en/puppeteer)