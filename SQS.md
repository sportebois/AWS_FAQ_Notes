**SQS**

[AWS SQS FAQ](https://aws.amazon.com/sqs/faqs/)

Simple Query Service

* SQS now provides FIFO (first in, first out)
* Standard queues provide loose FIFO that attempts to preserve the order of the messages but is not guaranteed
* SQS Guarantees a message will be delivered AT LEAST ONCE
* FIFO queues provide Exactly Once processing. Duplicates are NOT introduced
* FIFO queues are currently available in US WEST (Oregon) and US EAST (Ohio) - coming soon to more Regions
* FIFO queues are designed to NEVER introduce duplicate messages
* SQS Standard queues still exist.
* You can still create SQS Standard Queues
* Standard queues are NOT automatically converted to FIFO queues
* An existing Standard queue CAN NOT be converted to a FIFO queues
* The following services are NOT compatible with FIFO queues 
    * CloudWatch Events
    * S3 Event Notifications
    * SNS Topic Subscriptions
    * Auto Scaling Lifecycle Hooks
    * IoT Rule Actions
    * Lambda Dead Letter Queues
* FIFO queues are NOT compatible with SQS Buffered Async Client, SQS Extended Client Library for Java, and Amazon SQS Java Message Service
* CloudWatch Metrics supported by FIFO queues
    * ApproximateNumberOfMessagesDelayed - The number of messages in the queue that are delayed and not available for reading immediately.
    * ApproximateNumberOfMessagesVisible - The number of messages available for retrieval from the queue.
    * ApproximateNumberOfMessagesNotVisible - The number of messages that are in flight (sent to a client but have not yet been deleted or have not yet reached the end of their visibility window).
* FIFO queues are grouped into distinct ordered bundles
* FIFO queue messages are sent and received in strict order
* You must associate a message group ID with a message, otherwise, the action fails
* If multiple hosts send messages to same message group ID, SQS will deliver them in the order they were received
* Multiple producers can send messages to a FIFO queue - again, order of received
* By default, SQS FIFO queues do NOT serve messages from the same message group to more then 1 consumer. Use parallel consumers to do this.
* You MUST use a FIFO dead letter queue with a FIFO queue
* FIFO queues can support 300 transactions per second
* Standard queue has unlimited throughput
* A FIFO queue name just end in .fifo - the suffix is counted towards the 80 character queue name
* FIFO queues are not currently supported by the JMS client.
* All SQS messages must have a global unique ID
* Use the receipt handle from the response to delete a message
* Use the API to handle dead letter queues
* If a queue is a dead letter queue, it receives messages after a maximum number of processing attempts cannot be completed.
* SQS queues have a configurable visibility timeout
* The maximum visibility timeout for an SQS message is 12 hours
* SQS Messages can contain up to 10 metadata attributes
* Metadata attributes are in the form of name - type - value
* Supported types include String, Binary and Number including integer, floating-point and double
* Use the SentTimestamp attribute to determine the time-in-queue value
* Latency for an SQS queue is in the hundreds of milliseconds
* If an anonymous user sends a message, the SenderID is the IP address of the sender
* SQS Queues can be long polled
* Regular Short polling returns immediately
* Long polling doesn't return a response until a message is received in the queue OR the long poll times out
* Long polling results in higher performance at a reduced cost
* 20 seconds is the recommended timeout for a long-poll
* All AWS SDKS default to 20 seconds
* Use the AmazonSQSBufferedAsyncClient for Java
* SQS is PCI-DSS level 1 certified
* SQS is NOT yet HIPAA compliant
* SQS Message Retention can be configured from 1 minute to 14 days, with the default being 4 days. Once the retention period is hit, the message is automatically deleted
* Use the console OR SetQueueAttributes to set MaximumMessageSize
* A message size can be between 1KB and 256KB
* Reference an S3 payload to send messages > 256KB up to 2GB
* A message can contain text, XML, JSON, and unformatted text
* You can create as many message queues as you need (unlimited)
* Queue names are limited to 80 characters - don't forget, if it's a FIFO queue, the .fifo is apart of that 80 character limit
* A message queue name can ONLY be re-used after it's deleted. The queue name must be unique within an Account and Region
* Use an Access Policy Statement to share Message queues
* The queue owner pays the shared queue bill!
* Anonymous users can access message queues
* An SQS message queue is specific to it's Region
