# node-red-contrib-aws-sdk

A function block where you can write your own code to execute aws-sdk nodejs library.

**Example of using aws-sdk inside this function block:**
	
```javascript
// Create a bucket using bound parameters and put something in it.
// Make sure to change the bucket name from "myBucket" to something unique.
var s3bucket = new AWS.S3({params: {Bucket: 'myBucket'}});
s3bucket.createBucket(function() {
  var params = {Key: 'myKey', Body: 'Hello!'};
  s3bucket.upload(params, function(err, data) {
    if (err) {
      console.log("Error uploading data: ", err);
      msg.payload = err;
    } else {
      console.log("Successfully uploaded data to myBucket/myKey");
      msg.payload = data;
    }
  });
});

return msg;
```

Reference: http://docs.aws.amazon.com/AWSJavaScriptSDK/guide/node-examples.html