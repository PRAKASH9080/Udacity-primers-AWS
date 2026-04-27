🌐 Static Website Deployment using AWS S3 & CloudFront

This project demonstrates how to host a static website using Amazon S3 and deliver it globally with low latency using Amazon CloudFront.

🚀 Live Demo
S3 Website Endpoint
http://static-website-76a.s3-website-us-east-1.amazonaws.com
CloudFront Distribution
https://d3h2yv7fw08goj.cloudfront.net

⚠️ Note: If you encounter 404 or 504 Gateway Timeout, the content may be unavailable or the origin server might be temporarily unreachable.

📌 Features
Static website hosting using AWS S3
Global content delivery via CloudFront CDN
Improved performance and reduced latency
Scalable and cost-effective hosting
HTTPS support via CloudFront
🏗️ Architecture
User → CloudFront (CDN) → S3 Bucket (Static Website Hosting)
Amazon S3 stores static files (HTML, CSS, JS, images)
CloudFront caches and distributes content globally
🛠️ Setup Instructions
1. Create an S3 Bucket
Enable Static Website Hosting
Upload your website files
Make objects publicly accessible (or use Origin Access Control)
2. Configure Bucket Policy

Allow public read access (if not using OAC):

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::static-website-76a/*"
    }
  ]
}
3. Create CloudFront Distribution
Origin: S3 website endpoint
Viewer Protocol Policy: Redirect HTTP → HTTPS
Default Root Object: index.html
4. Invalidate Cache (if needed)
aws cloudfront create-invalidation --distribution-id <your-id> --paths "/*"
⚠️ Troubleshooting
404 Error
File not found
Incorrect path or missing index.html
504 Gateway Timeout
S3 origin not responding
Incorrect CloudFront origin configuration
Temporary AWS/network issue
