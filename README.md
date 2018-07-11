# aws-style-guide
Style guide for your AWS account

## Setting up a new account

* Use strong password for root account
* Enable 2fa for root account
* enable cloudtrail
* enable AWS Config
* create IAM user with FullAdmin policy and 2FA. Then login as them and avoid the root account for ever after
* Create an Organization
** Setup SCP to limit access to services
** Enable trusted access for services we want to use, so they can create service-linked roles in all accounts
