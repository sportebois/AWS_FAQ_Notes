**SES**

[AWS SES FAQ](https://aws.amazon.com/ses/faqs/)

Simple Email Service

Use this to send or receive email

* SES will scan the outgoing email to make sure the content meets ISP standards
* In-House content filtering scans email content to prevent spam and malware
* If malware is detected, SES prevents the email from going out
* SES supports custom email header fields and many MIME Types
* Request a sending limit increase by filling out this form - http://aws.amazon.com/ses/fullaccessrequest
* You do NOT need to setup a reverse DNS record
* SES provides full SMTP support - to connect to SMTP, you must create SMTP credentials
* SES can be used with MTAs such as Sendmail, Postfix and Exim
* Use the SendRawEmail API for advanced emails such as specifying headers, MIME parts or content types
* Send bulk email via SendEmail or SendRawEmail via EC2, Elastic MapReduce or your own servers
* SES supports mail attachments - make sure to set the appropriate MIME type
* The SMTP requires all data be send in 7-bit ASCII format. 
* SendEmail API accepts UTF-8
* Malformed emails will return an error saying delivery failed and provide a reason
* If SES doesn't know why it failed, it'll be returned as a bounced email with appropriate error code and reason
* SES supports SPF 
* SES supports DKIM
* SES DMARC compliance comes from SPF, DKIM, or both
* If the receiving email server advertises STARTTLS, SES will attempt to upgrade the connection to TLS. Otherwise, it'll fall back to plain text
* Only TLS v1 is supported
* Testing can be accomplished via the SES mailbox simulator
* Dedicated IP address are available at an extra cost. Fill out this form to apply http://aws.amazon.com/ses/extendedaccessrequest/
* SES will attempt to deliver email within a few seconds but due to the nature of email servers, this may not always happen. In these cases, SES will attempt to retry the messages for a length of time.
* Hard bounces are NOT retried
* Delivery notifications can be setup for when SES successfully delivers an email to a recipients mail server
* There is no guarantee if an email will be delivered. 
* Bounce, Complaint and Delivery notifications can be send to you by email
* AWS may suspend any account identified as spam or other unwanted low quality email
* You MUST demonstrate ownership of a domain to use it in the FROM field
* Up to 10,000 email address domains can be used
* SES will accept a emails up to 10MB in size including attachments
* Up to 50 recipients can be specified per each email - sending more requires sending multiple emails
* New SES users start in the SES sandbox and are limited to 200 emails per 24 hour period and 1 email per second
* Check your sending limits via the SES console
* Monitor SES via CloudWatch
* SNS and Kinesis Firehose can also be used to monitor SES
* You can use SES with KMS to encrypt emails on S3
* You can setup SES to REJECT emails not sent via TLS
* You are NOT billed for messages marked as Spam
* SES can receive emails up to 30MB in size including it's headers
* If a message comes in via SNS, the maximum message size is 150KB including headers
* There is no throughput limit to how many messages can be received
* Amazon WorkMail uses SES
