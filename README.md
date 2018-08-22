# aws-style-guide
Style guide for your AWS account

## Setting up a new account

### Create account + configure root account
* Use strong password for root account
* Enable 2fa for root account

### Setup High-Level Auditing
* Chnage to your preferred region and create a new CloudTrail. Record all events for all regions. Choose whether you alos want to record S3 object events and Lambda invoke's. Write to a dedicated s3 bucket, do log validation, use a KMS key. Confirm settings for the underlying S3 bucket
* enable AWS Config region-by-region for all regions you use

### Configure User Logins
* create a new IAM user for yourself, and attach the AdminstratorAccess policy. Then logout from the root account (and never login to the root account again!), login as the IAM user (dont forget to change to your preferred region) and setup MFA.
* Create groups to manage permissiosn, and migrate yourself into a relevant group
* Setup a password policy: Minimum length, required characters, password expiry, 
* Deactivate STS tokens (IAM->Account Settings) for all regions you don't intend to use. For some AWS accounts (eg. master account or loggign account), this may be all regions because STS should not be used.


### Multi-Account
* Create an Organization
  * Setup Service Control Policies to limit access to services
  * Enable trusted access for services we want to use, so they can create service-linked roles in all accounts
