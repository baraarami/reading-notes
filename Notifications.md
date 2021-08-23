# Notifications
![](https://d1.awsstatic.com/diagrams/Product-page-diagram-Amazon-SNS_event-driven-SNS-compute%402X_.4b9c0a75aa40bda9cdb12f0176930a12da2872bf.png)
### What is Amazon SNS?
- A managed service that provides message delivery from publishers to subscribers .
- Publishers communicate asynchronously with subscribers by sending messages to a topic, which is a logical access point and communication channel.
- Clients can subscribe to the SNS topic and receive published messages using a supported endpoint type.
### [How do I implement Amazon SNS?](https://docs.aws.amazon.com/sns/latest/dg/sns-getting-started.html)
- Step 1: Create a topic
- Step 2: Create a subscription to the topic
- Step 3: Publish a message to the topic
- Step 4: Delete the subscription and topic
### [Publish Amazon SNS Messages Privately](https://aws.amazon.com/getting-started/hands-on/publish-sns-message-privately-vpc-ec2-cloudformation-lambda/)
 - Some common cases for private networking and messaging include:
   - Isolating development and testing environments
   - Sharing personally identifiable information (PII) about your customers
   - Hosting a PCI-compliant e-commerce website
   - Developing healthcare applications subject to HIPAA
   - Implementing a cryptographic algorithm subject to FIPS 140
   - Processing mortgage applications in a banking system




##### Publish a message to the topic
- In the left navigation pane, choose Topics.
- On the Topics page, choose the topic that you created earlier, and then choose Publish message.
- The console opens the Publish message to topic page.
- (Optional) In the Message details section, enter a Subject, such as:
```
Hello from Amazon SNS!
```
- In the Message body section, choose Identical payload for all delivery protocols, and then enter a message body, such as:
```
Publishing a message to an SNS topic.
```
- Choose Publish message.
- The message is published to the topic, and the console opens the topic's Details page.
- Check your email inbox and verify that you received an email from Amazon SNS with the published message.











