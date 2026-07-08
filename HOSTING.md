# CntrlEngUtils Hosting Reference

## Site URL

- https://tiny.amazon.com/1f1o1esiz/ControlEngUtils (shareable alias)
- https://d3mvduplrd6arl.cloudfront.net (direct CloudFront URL)

## AWS Account

- Account ID: 040396448492
- Role: admin (via Isengard)
- Region: us-east-1

## Resources

| Resource | ID / Name |
|----------|-----------|
| S3 bucket | cntrlengutils-site |
| CloudFront distribution | E2LD31X2RIXRT2 |
| Origin Access Control | E3E3OGF92OA830 |

## How to Update the Site

### 1. Refresh AWS credentials

```bash
mwinit -s --fido2
isengard credentials 040396448492
```

### 2. Upload updated files

```bash
aws s3 cp index.html s3://cntrlengutils-site/index.html --content-type text/html
aws s3 cp manifest.json s3://cntrlengutils-site/manifest.json --content-type application/json
```

### 3. Invalidate CloudFront cache

CloudFront caches files at edge locations. After uploading, invalidate so users get the new version:

```bash
aws cloudfront create-invalidation --distribution-id E2LD31X2RIXRT2 --paths "/*"
```

Invalidation typically completes in 1-2 minutes.

## Git Remotes

| Remote | URL |
|--------|-----|
| origin (GitHub) | https://github.com/wsneddon/CntrlEngUtils.git |
| code.aws | ssh://git.amazon.com/pkg/ControlsConversion |
