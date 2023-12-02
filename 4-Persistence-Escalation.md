# Situational Awareness

## General Post-Compromise Recon

- Who are we?
- What roles do we have?
- Is MFA enabled?
- What can we access (webapps,
  storage, etc.?)
- Who are the admins?
- How are we going to escalate to admin?
- Any security protec

- AWS Command Line
- https://aws.amazon.com/cli/
- Boto3 - AWS SDK for Python
- https://aws.amazon.com/sdk-for-python/
- Console Access
- Sometimes easier to navigate

### AWS

- Configure a profile to authenticate with:

  - `aws configure`

- Call the Security Token Service (STS) to test creds

  - `aws sts get-caller-identity`

- List S3 Buckets
  - `aws s3 ls`

IAM Policy Enumeration

- Call the IAM service to enumerate access
- List IAM users
  - `aws iam list-users`
- List IAM roles
  - `aws iam list-roles`
- List IAM groups
  - `aws iam list-groups`
- List attached policies for a user
  - `aws iam list-attached-user-policies --user-name <user>`

### Azure

- Get the current user’s role assignment
- `Get-AzRoleAssignment`

- If the Azure portal is locked down it is still possible to access Azure AD user information via MSOnline cmdlets
- The below examples enumerate users and groups

  - `Get-MSolUser -All`
  - `Get-MSolGroup –All`
  - `Get-MSolGroupMember –GroupObjectId <GUID>`

- Pipe Get-MSolUser –All to format list to get all user attributes

  - `Get-MSolUser –All | fl`

- Resource Groups collect various services for easier management
- Recon can help identify the relationships between services such as WebApps and SQL

  - `Get-AzResource`
  - `Get-AzResourceGroup`

- Azure Runbooks automate various tasks in Azure
- Require an Automation Account and can contain sensitive information like passwords
  - `Get-AzAutomationAccount`
  - `Get-AzAutomationRunbook -AutomationAccountName<AutomationAccountName> -ResourceGroupName <ResourceGroupName>`
- Export a runbook with:
  - `Export-AzAutomationRunbook -AutomationAccountName <account name> -ResourceGroupName <resource group name> -Name <runbook name> -OutputFolder .\Desktop\`

### Other

- Enumerate localhost information, domain information, and find potential escalation paths
- HostRecon - general host situational awareness
  - https://github.com/dafthack/HostRecon
- PowerView - gather domain info
  - https://github.com/PowerShellMafia/PowerSploit/tree/ master/Recon
- BloodHound - find escalation paths
  - https://github.com/BloodHoundAD/BloodHound

## Pacu

An AWS exploitation framework from Rhino Security Labs

- https://github.com/RhinoSecurityLabs/pacu
- Modules examples:
  - S3 bucket discovery
  - EC2 enumeration
  - IAM privilege escalation
  - Persistence modules
  - Exploitation modules

# Privelege Escalation

Privilege Escalation

- General Techniques
  - Searching Compromised Systems for Access Keys
  - Environment variables on VMs
  - Read access to config files
  - IAM permission misconfigurations
  - Metadata Service URL
  - SSH Keys to pivot to other hosts
  - Source code of webapps

### Azure

- User attributes and sensitive information
- Very often find credentials in description or comment fields
- Use this one-liner to search every Azure AD user field for passwords
  `$users = Get-MsolUser; foreach($user in $users){$props = @();$user | Get-Member | foreach-object{$props+=$_.Name}; foreach($prop in $props){if($user.$prop -like "*password*" {Write-Output ("[*]" + $user.UserPrincipalName + "[" + $prop + "]" + " : " + $user.$prop)}}}`

### AzureHound

AzureHound

- https://github.com/BloodHoundAD/AzureHound
- https://bloodhound.readthedocs.io/en/latest/data-collection/azurehound.html
- Azure data collector for use with BloodHound
- Written in Go
- Outputs data to a json file that can be imported into
  BloodHound
- Can then use BloodHound to discover paths of escalation between nodes
