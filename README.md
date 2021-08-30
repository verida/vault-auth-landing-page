Landing page for the vault app

Deployed using the `deploy.sh` script

Everything in `/dist/` gets deployed to the website. The zero-byte `/dist/index.html` file lets us setup an object 
redirect in S3: https://docs.aws.amazon.com/AmazonS3/latest/userguide/how-to-page-redirect.html