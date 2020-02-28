# AWS KMS

WS Key Management Service (AWS KMS) is a managed service that makes it easy for you to create and control the encryption keys used to encrypt your data. The master keys that you create in AWS KMS are protected by FIPS 140-2 validated cryptographic modules. AWS KMS is integrated with most other AWS services that encrypt your data with encryption keys that you manage. AWS KMS is also integrated with AWS CloudTrail to provide encryption key usage logs to help meet your auditing, regulatory and compliance needs.

![alt](../images/encrypt-with-data-key.png)

The scenario mentions that you have to encrypt the data before writing it to disk for storage. What this means is that you will have to temporarily store the data in memory and not persist it on the disk, then encrypt it on the fly before finally storing it. The end result would be an encrypted data in your disk EBS Volume, and the EBS Encryption would be the secondary layer of protection/encryption for your sensitive data.

You can configure your application to use the KMS API to encrypt all data before saving it to disk.
