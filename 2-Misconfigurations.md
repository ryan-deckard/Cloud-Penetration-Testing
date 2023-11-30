### S3 URL Format:

- https://[bucketname].s3.amazonaws.com
- https://s3-[region].amazonaws.com/[Org Name]

### AWS CLI

- aws s3 ls s3://<bucketname>/

### Azure Blob storage is for unstructured data

- Containers and blobs can be publicly accessible via access policies
- Predictable URL’s at core.windows.net

  - storage-account-name.blob.core.windows.net
  - storage-account-name.file.core.windows.net
  - storage-account-name.table.core.windows.net
  - storage-account-name.queue.core.windows.net

### Blob Enumeration

- https://github.com/NetSPI/MicroBurst

### Cloud Enumeration (A MUST FOR ANY RED TEAM ASSESSMENT)

- https://github.com/initstring/cloud_enum

## Key Discolsure In Public Repositories

- Search through not only current code but also commit history
  - https://github.com/zricethezav/gitleaks
  - https://github.com/michenriksen/gitrob
  - https://github.com/dxa4481/truffleHog
