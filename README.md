# MVC-Exit Exam 1/65 (29/oct/2022)

63050137 Tanawan Wongphetcharat
Computer Science , KMITL

## Framework

Vue3 + Vuetify3 Library + json-server + Axios

## Project Setup

npm install

### Compile and Hot-Reload for Development

npm run db:serve  

npm run dev  

## MVVM Design Pattern

Model - คือส่วนที่ข้อมูลไหลเข้าออกระหว่าง database และ application ส่วนนี้ใช้ Pinia ในการจัดการ state และ Axios ในการทำ HTTP Request ข้อมูลจาก json-sever ส่วนนี้อยู่ใน store/index.js  

View - คือส่วนที่ใช้ในการแสดงผล โดยใช้ HTTP ประกอบด้วย Vuetify library ช่วยในเรื่องความสวยงาม ส่วนนี้อยู่ใน views/*.vue

ViewModel - คือส่วนที่เชื่อมประสาน Model กับ View เข้าด้วยกัน  ส่วนนี้อยู่ใน main.js 
