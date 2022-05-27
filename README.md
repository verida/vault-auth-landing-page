# Landing page for the vault app

## AWS Amplify Redirects

AWS assumes that files without an extension are folders, so appends a `/` to the end. This means requests for `/.well-known/apple-app-site-association` end up going to `/.well-known/apple-app-site-association/` which is wrong. 

We fix this by renaming the `apple-app-site-association` to `apple-app-site-association.json` and the creating a rewrite rule to rename it. 

Additionally, we want `/request?param=123` and `connection-success?param=123` to be both served by the index file. We use rewrites for that too. 


Paste this into the AWS Redirect Console (switch to "Text Editor" for access to the JSON):

```
[
    {
        "source": "</\\/request.*/>",
        "target": "/index.html",
        "status": "200",
        "condition": null
    },
    {
        "source": "</\\/connection-success.*/>",
        "target": "/index.html",
        "status": "200",
        "condition": null
    },
    {
        "source": "/.well-known/apple-app-site-association",
        "target": "/.well-known/apple-app-site-association.json",
        "status": "200",
        "condition": null
    }    
]
```

