Landing page for the vault app

Deployed using the `deploy.sh` script

Everything in `/dist/` gets deployed to the website. The zero-byte `/dist/index.html` file lets us setup an object 
redirect in S3: https://docs.aws.amazon.com/AmazonS3/latest/userguide/how-to-page-redirect.html

# NOTE

We have *manually* deployed a copy of `/request/index.html` to S3 as `/request` served with Content-Type:text/html, and with paths in that file corrected to refer to objects inside the `/request` subdirectory.

This is because HTTP(S) requests to https://vault.verida.io/request?parameter=value get redirected to https://vault.verida.io/request/ without this. This is _sort of_ documented at https://github.com/jariz/gatsby-plugin-s3/issues/51#issuecomment-480112920 and https://docs.aws.amazon.com/AmazonS3/latest/userguide/IndexDocumentSupport.html

At the moment the `deploy.sh` script doesn't do this
