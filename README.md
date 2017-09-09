# S3 Index

A simple script which will produce nice looking S3 bucket content listings much in the way you get with most webservers.

## Prerequisite 

This functionality completely depends on public S3 buckets. Also make sure the CORS configuration allows GET requests from the location where the script is hosted.

## Installation

Just drop the `index.html` in your S3 bucket and it should work automatically when opening the page.

Alternatively you can put it anywhere where and specify the URL parameter `?bucket=` with the bucket URL.

## Example

[Example](https://mpobjects.github.io/s3index/?bucket=https://s3-eu-west-1.amazonaws.com/data.openspending.org)

![](http://i.imgur.com/eoFeupQ.png)
