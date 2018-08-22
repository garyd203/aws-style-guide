# aws-style-guide
Style guide for your AWS account

## Setting up a new account

* Use strong password for root account
* Enable 2fa for root account
* Chnage to your preferred region and create a new CloudTrail. Record all events for all regions. Choose whether you alos want to record S3 object events and Lambda invoke's. Write to a dedicated s3 bucket, do log validation, use a KMS key. Confirm settings for the underlying S3 bucket
* enable AWS Config
* create IAM user with FullAdmin policy and 2FA. Then login as them and avoid the root account for ever after
* Create an Organization
  * Setup Service Control Policies to limit access to services
  * Enable trusted access for services we want to use, so they can create service-linked roles in all accounts
