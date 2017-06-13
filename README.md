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
var AWS = require("aws-sdk");
var dynamodb = new AWS.DynamoDB();
var docClient = new AWS.DynamoDB.DocumentClient();
    exports.handler = (event, context, callback) => {
        console.log("PARAMS---:"+parseInt(event.params.querystring.bookid));
        var params = {
            TableName: "books",
            Key:{
                "bookid": parseInt(event.params.querystring.bookid)
            }
        };

        docClient.get(params, function(err, data) {
            if (err) {
                console.error("Unable to read item. Error JSON:", JSON.stringify(err, null, 2));
            } else {
                callback(null, JSON.parse( JSON.stringify(data, null, 2)));
            }
        });
    };
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
