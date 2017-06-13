Serverless for Databases Library :

1. Create table Dynamodb :
- table = books
- item
bookid, number, 1
bookname, string, serverless architecture
author, string, danni
publisher, string, manning

2. Create Function Lambda
- Choose = blank function
- name Bookdetails
- desc DAO Function for books table
- runtime nodejs
- existing role LambdaDynamoDB
- memory 128
timeout 10 sec


In Tab Code put this code
======================================





======================================

In Tab Actions => Configure test event => paste code this below :
======================================

{
 "params":{
     "querystring":{
         "bookid":"1"
     }
  }
}
======================================
