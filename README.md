# aws-style-guide
Style guide and cookbook for your AWS account

## Setting up a new account

### Setup High-Level Auditing
* Chnage to your preferred region and create a new CloudTrail. Record all events for all regions. Choose whether you alos want to record S3 object events and Lambda invoke's. Write to a dedicated s3 bucket, do log validation, use a KMS key. Confirm settings for the underlying S3 bucket
* enable AWS Config region-by-region for all regions you use

### Create account + configure root account
* Use strong password for root account
* Enable 2fa for root account
* Allow billing access to IAM users (if this is the Master Account)
* Setup support plan
* Setup account alias (can do this later)

### Configure User Logins
* create a new IAM user for yourself, and attach the AdminstratorAccess policy. Then logout from the root account (and never login to the root account again!), login as the IAM user (dont forget to change to your preferred region) and setup MFA.
* Create groups to manage permissions, and migrate yourself into a relevant group (detaching the AdminstratorAccess policy)
* Setup a password policy: Minimum length, required characters, password expiry, 
* Deactivate STS tokens (IAM->Account Settings) for all regions you don't intend to use. For some AWS accounts (eg. master account or loggign account), this may be all regions because STS should not be used.

### Multi-Account
If this is the master account for a Multi-Account setup, then you should setup the Multi-Account structure using AWS Organizations
* Create an Organization
* Setup an account structure with Organizational Units, if desired
* Setup Service Control Policies to limit access to services for specific accounts. Note that you can't apply an SCP to the master account (it alwasy allows everything)
* Enable trusted access for services we want to use, so they can create service-linked roles in all accounts.
  * Probably not necessary? Doco suggests you should just do that in the linked service

## Tagging Strategy
