# เริ่มโปรเจคท์ javascript

#### อัพเดทเมื่อ 17/9/2018

### `รายการ`
* [ศึกษา ES6](#ศึกษา-ES6)
* [ติดตั้ง Node และ Yarn](#ติดตั้ง-node-และ-yarn)
* [ติดตั้ง Webpack](#ติดตั้ง-webpack)
* [ติดตั้ง Babel](#ติดตั้ง-babel)

### `ศึกษา ES6`
ต้องทวนบ่อย ๆ เพราะมันจะลืมง่ายมากว่าเรียกว่าอะไร รวมไปถึง ES7/ES8/TC39
* [Babel ES6 Learning](https://babeljs.io/docs/en/next/learn)
* [Javascript Fundamental](https://developer.mozilla.org/bm/docs/Web/JavaScript)
* [ES6 Features](https://github.com/lukehoban/es6features#readme)
* [ECMA2015 Specification](http://www.ecma-international.org/ecma-262/6.0/index.html)
* [Web technologies](https://developer.mozilla.org/en-US/docs/Web)


### `ติดตั้ง Node และ Yarn`
ติดตั้ง [node](https://nodejs.org/en/download/) หรือทางเลือกจะลง [yarn](https://yarnpkg.com/lang/en/docs/install/#windows-stable) เพิ่มด้วยก็ได้

จัดการโปรเจคท์ด้วย node
นอกจากนั้นยังมีคำสั่งที่เกี่ยวกับ node เช่น

> `npm install`

จะทำการ download libs ไฟล์ที่ยังไม่มีใน package.json เข้ามายังโปรเจคท์

> `npm update`

ตัวอย่าง libraries ที่เคยใช้เพิ่มเติม หลัก ๆ จะมี

* กลุ่ม babel ( babel-cli, babel-core, babel-polyfill, babel-preset-env )
* กลุ่ม eslint ตัวนี้แล้วแต่ว่าจะใช้หรือไม่ใช้ก็ได้ ใช้สำหรับตรวจ code ว่าเขียนถูกต้องตามที่กำหนดหรือไม่
* กลุ่ม jsdoc กรณีต้องการเขียนเอกสารจาก coding
* กลุ่ม webpack ( webpack, webpack-cli ) อยากให้ webpack start server ก็ลง webpack-serve ถ้าอยากวิเคราะห์ขนาดไฟล์ที่ได้หลังจาก pack แล้วก็ webpack-bundle-analyzer
* กลุ่มอื่น ๆ คือ กลุ่มที่ใช้เพิ่มเติมในงานเช่น date-fns ที่หากต้องการแค่แปลงเวลานิดหน่อยไฟล์ขนาดเล็กใช้ได้ใกล้เคียง moment.js ลงตัวนี้ได้

การมีเครื่องหมาย `^` นำหน้าเลขเวอร์ชันหมายถึงหากรันคำสั่งที่อัพเดท
โปรเจคท์ npm ก็จะ download ตัวที่ใหม่กว่ามาลงให้ทันที หากไม่ต้องการก็ให้เอา `^` ออก

```
    "babel-cli": "^6.26.0",
    "babel-core": "^6.26.3",
    "babel-jest": "^23.0.1",
    "babel-loader": "^7.1.4",
    "babel-polyfill": "^6.26.0",
    "babel-preset-env": "^1.6.1",
    "date-fns": "^1.29.0",
    "eslint": "^4.19.1",
    "eslint-config-standard": "^11.0.0",
    "eslint-plugin-import": "^2.11.0",
    "eslint-plugin-node": "^6.0.1",
    "eslint-plugin-promise": "^3.7.0",
    "eslint-plugin-standard": "^3.0.1",
    "jest": "^23.0.1",
    "jsdoc": "^3.5.5",
    "webpack": "^4.1.1",
    "webpack-bundle-analyzer": "^2.11.1",
    "webpack-cli": "^2.0.11",
    "webpack-serve": "^0.3.1"
```

### `ติดตั้ง webpack`

> `npm install webpack webpack-cli --save-dev`

ถ้าลง webpack แล้วจะต้องสร้างไฟล์ชื่อว่า webpack.config.js เพื่อเซ็ตค่า config ตามเอกสารของ webpack แต่โดยพื้นฐานก็ใช้ประมาณนี้

```
module.exports = {
    entry: {},
    output: {},
    mode: production/development,
    module: {},
    optimization: {},
    plugins: {}
}
```
ใช้ [webpack plugins](https://webpack.js.org/plugins/) เพิ่มเติมเช่น path, HtmlWebpackPlugin, ZipPlugin, UglifyJsPlugin, webpack.DefinePlugin

### `ติดตั้ง Babel`

หากต้องทำงานร่วมกับ browser เก่าหรือ device เก่า จะต้องลง babel เพิ่ม

> `npm install babel-core babel-cli babel-preset-env babel-polyfill --save-dev`

หลังจากลง babel แล้วจะต้อง config babel ให้กับโปรเจคท์ เพื่อให้โปรเจคท์รู้ว่าใช้ babel preset ตัวใด (เช่น env, react) โดยระบุได้ 2 แบบ คือ

ฺBabel 6 -> Babel 7
* อัพเกรดผ่าน `npx babel-upgrade`
* ใช้ babel-preset-env อย่างเดียว ไม่มีรุ่นปีเหมือน v.6
* พวก stage-0 / 1 / 2 โดนยกเลิกเช่นเดียวกันให้ stage ตามนี้ [Ref.](https://github.com/babel/babel/tree/master/packages/babel-preset-stage-0#babelpreset-stage-0)
* หากเป็น v.6 จะต้องสร้าง .babelrc แล้วระบุดังตัวอย่าง

```
{
  "presets": ["env"]
}
```
แต่ v7 สามารถเขียนให้อยู่ในรูปแบบของ js ได้ ชื่อว่า `babel.config.js`

## เลือก Framework
### `No Framework`

เริ่มโปรเจคท์
> `npm init`

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