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

## Cross Rerence Comapany IP addresses with AWS/Azure lists to identify matches

- https://github.com/oldrho/ip2provider
  - Create a list of IP addresses you want to check one per line
  - `cat iplist.txt | python ip2provider.py`

### AWS Netblocks

• https://ip-ranges.amazonaws.com/ip-ranges.json

### Azure Netblocks

• Public: https://www.microsoft.com/en-us/download/details.aspx?id=56519

## O365 Usage

### Determine if Org uses 1. Password Hash Sync, 2. Pass Through, or 3. ADFS

- https://login.microsoftonline.com/getuserrealm.srf?login=username@acmecomputercompany.com&xml=1

### Get Tenant ID (Supposedly)

- https://login.microsoftonline.com/<target domain>/v2.0/.well-known/openid-configuration
