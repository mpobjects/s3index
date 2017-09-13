# S3 Index

A simple script which will produce nice looking S3 bucket content listings much in the way you get with most webservers.

## Prerequisite 

This functionality depends on the `s3:ListBucket` action for the targetted bucket. If the script is not hosted in the bucket itself you also need to set up a proper CORS configuration for the bucket.

The easiest way is to simply give *Everyone* the *List Objects* option is the *Access Control List*. But a similar more finegrained solution is possible by using a bucket policy. For example:

```json
{
    "Statement": [
        {
            "Action": [
                "s3:GetObject"
            ],
            "Effect": "Allow",
            "Resource": "arn:aws:s3:::BUCKET/*",
            "Principal": "*"
        },
        {
            "Action": [
                "s3:ListBucket"
            ],
            "Effect": "Allow",
            "Resource": "arn:aws:s3:::BUCKET",
            "Condition": {
                "StringLike": {
                    "s3:prefix": "FOOBAR/*"
                }
            },
            "Principal": "*"
        }
    ]
}
```

This would only allow listing of the contents of the `FOOBAR` directory of the bucket. The root bucket URL would then simply respond with a *Access Denied*. The standard `index.html` request would fail to list a bucket, but using `index.html#FOOBAR/` would list the contens of the `FOOBAR` directory.

## Installation

Just drop the `index.html` in your S3 bucket and it should work automatically when opening the page. If you place it in a sub-directory it will automatically list the contents of that directory.

Alternatively you can put it anywhere where and specify the URL parameter `?bucket=` with the bucket URL, or edit the HTML and change the `config` object at the end.

## Example

[Example](https://mpobjects.github.io/s3index/?bucket=https://s3-eu-west-1.amazonaws.com/data.openspending.org)

![](http://i.imgur.com/eoFeupQ.png)
