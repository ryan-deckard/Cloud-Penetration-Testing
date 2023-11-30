# DNS

- https://crt.sh
- https://www.shodan.io

  - Shodan query examples:
    - org:”Target Name”
    - net:”CIDR Range”
    - port:”443”

- https://search.censys.io/

- https://github.com/lanmaster53/recon-ng
- https://github.com/aboul3la/Sublist3r
- https://dnsdumpster.com
- https://whois.arin.net/ui/

### DNS List:

https://github.com/danielmiessler/SecLists/tree/master/Discovery/DNS

### Google Dorks:

`site:targetdomain.com -site:www.targetdomain.com`

# Comapany IP addresses <--> AWS/Azure

- https://github.com/oldrho/ip2provider
  - Create a list of IP addresses you want to check one per line
  - `cat iplist.txt | python ip2provider.py`

## AWS Netblocks

• https://ip-ranges.amazonaws.com/ip-ranges.json

## Azure Netblocks

• Public: https://www.microsoft.com/en-us/download/details.aspx?id=56519

## O365 Usage

### Determine if Org uses 1. Password Hash Sync, 2. Pass Through, or 3. ADFS

- https://login.microsoftonline.com/getuserrealm.srf?login=username@acmecomputercompany.com&xml=1

### Get Tenant ID (Supposedly)

- https://login.microsoftonline.com/<target domain>/v2.0/.well-known/openid-configuration

## S3 Bucket Discovery

- Proxy web app traffic through burp and look for calls to S3
- Navigate application like you normally would and then check for any requests to: - https://[bucketname].s3.amazonaws.com
- https://s3-[region].amazonaws.com/[OrgName]

# Box.Com Usage

- https://companyname.account.box.com

# Usernames/Passwords

- Dehashed
- HaveIBeenPwned

### Metadata (Find Company docs on the web and look for metadata including info such as subdomains,usernames)

- https://github.com/dafthack/PowerMeta
- https://github.com/ElevenPaths/FOCA

### User enumeration on Azure can be performed at

- https://login.Microsoft.com/common/oauth2/token
- https://aadinternals.com/aadinternals/

### External Recon Modules:

- Invoke-AADIntReconAsOutsider
- Invoke-AADIntUserEnumerationAsOutsider
