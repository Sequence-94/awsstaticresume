Imlementation:
I created an S3 bucket and enabled static hosting with public access.

WHY : This allows the HTML with css to be displayed as website on the internet and is accessible by anyone.
I then uploaded my html files along with the css and error html file into the bucket.

Error Message:
![Screen Shot 2024-05-16 at 14 25](https://github.com/Sequence-94/awsstaticresume/assets/53806574/8d3748cf-5829-423d-bbe2-6a73a215eabc)

Error Resolution: It seems even though the bucket has pulbic access i still needed to indicate the type of access that is needed and 
this was acheived by a bucket policy that allows getobject by anyone.
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::sequence.com/*"
        }
    ]
}

Result:
![Screen Shot 2024-05-16 at 14 22](https://github.com/Sequence-94/awsstaticresume/assets/53806574/c7dc1d33-b172-4d29-a4a1-b97f62ed387e)

Improvements: Even though the website is displaying it still isn't secure as indicated because S3 doesn't support HTTPS access.

Resolution: I will use CLOUDFRONT for https so that users will use the predefined url provided by cloudfront and be routed to the 
s3 bucket securely.

Error: 
![Screen Shot 2024-05-16 at 14 36](https://github.com/Sequence-94/awsstaticresume/assets/53806574/a18c67a9-9a00-444f-8e05-e9c4d2266abd)

Error resolution:
This was optional but it seems if I do not indicate the root object or file name it gives me an error. 
![Screen Shot 2024-05-16 at 14 41](https://github.com/Sequence-94/awsstaticresume/assets/53806574/695cbad5-1398-4013-a690-94276bbb8c1d)


Result: 
![Screen Shot 2024-05-16 at 14 42](https://github.com/Sequence-94/awsstaticresume/assets/53806574/0996b5f4-7847-4dd7-bb4d-87da8c9038d4)

Improvement:
Although the site is showing up perfectly the url is still predefined by amazon and because of that SSL/TLS certificates are provided by amazon. I have Purcahsed a Domain Name in order to customise the url to make it userfriendly. 

Error:
![Screen Shot 2024-05-16 at 17 39](https://github.com/Sequence-94/awsstaticresume/assets/53806574/b6dfffae-896a-4485-a026-ab922ebd52b9)

With this new custome Domain Name AWS does not provide a SSL/TLS certificate so I have to request one from Amazon and associate it with cloudfront. So even after applying it I still am getting the same error message. So in combination with associating the certificate with cloudfornt I have to give it an Alternate domain name (CNAME) and then the error is resolved.
![Screen Shot 2024-05-16 at 19 03](https://github.com/Sequence-94/awsstaticresume/assets/53806574/dfd1906a-48bb-4b26-9a87-06a89ea2e943)

Result: 
![Screen Shot 2024-05-16 at 19 04](https://github.com/Sequence-94/awsstaticresume/assets/53806574/e1872246-8474-4e94-af64-fcfafdd18115)









