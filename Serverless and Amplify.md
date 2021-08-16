# Intro to Serverless
![](https://www.simform.com/wp-content/uploads/2017/12/serverless-application-2.png)
## What is Serverless Architecture?
- Serverless computing is a cloud computing execution model in which the cloud provider allocates machine resources on demand, taking care of the servers on behalf of their customers.
### some of the currently available cloud services:
- AWS Lambda
- Google Cloud Functions
- Azure Functions
- IBM OpenWhisk
- Alibaba Function Compute
- Iron Functions
- Auth0 Webtask
- Oracle Fn Project
- Kubeless

![Traditional vs. Serverless Architecture](https://thinkpalm.com/wp-content/uploads/2017/01/Traditional-Architecture-versus-Serverless-Architecture.jpg)
### Advantages of using Serverless:
- Pricing
  - The cost model of Serverless is execution-based: you’re charged for the number of executions.
  - The winner here is Serverless Architecture.
- Networking
  -  The downside is that Serverless functions are accessed only as private APIs.
  -  The winner here is Traditional Architecture.
- 3rd Party Dependencies
  - For simple applications with few dependencies, Serverless is the winner.
  - for anything more complex, Traditional Architecture is the winner.
- Environments
  - Setting up different environments for Serverless is as easy as setting up a single environment.
  - The winner here is Serverless Architecture.
- Timeout
  -  Too complex or long-running functions aren’t good for Serverless, but having a hard timeout makes it impossible to perform certain tasks. 
  -  The clear winner here is Traditional Architecture.
- Scale
  - It’s a tie between Serverless and Traditional Architecture.

### What is a function in FaaS (Function-as-a-Service (FaaS))?
-  is a serverless way to execute modular pieces of code on the edge.
-  FaaS lets developers write and update a piece of code on the fly,
-  then be executed in response to an event, such as a user clicking on an element in a web application.
- **Principles of FaaS:**
  - Complete management of servers
  - Invocation based billing
  - Event-driven and instantaneously scalable
- **Key properties of FaaS:**
  - Independent, server-side, logical functions
 >
 > **For**: Benefits of Serverless Architecture ... [check here](https://hackernoon.com/what-is-serverless-architecture-what-are-its-pros-and-cons-cc4b804022e9)
 #
 ## AWS Amplify
 - What is AWS?
   - AWS Amplify is a set of tools and services that can be used together or on their own, to help front-end web and mobile developers build scalable full stack applications, powered by AWS.
- Why use AWS amplify?
  - Amplify facilitates getting started with AWS for web and mobile app development because it is easy to use and flexible. The Amplify libraries accelerate implementation of functionality like user authentication, data storage, analytics, and predictions, using AWS services for the back-end functionality.
  - 
Use cases - onboarding flows, real-time collaboration, AI/ML, and targeted campaigns.
#
## GraphQL Intro 
- What is GraphQL API?
  - GraphQL is a query language and server-side runtime for application programming interfaces (APIs) that prioritizes giving clients exactly the data they request and no more.   - GraphQL is designed to make APIs fast, flexible, and developer-friendly.


### What is GraphQL?
It is tool helps on create backends for your web and mobile applications on AWS.

### Example:

```
type Blog @model {
  id: ID!
  name: String!
  posts: [Post] @connection(name: "BlogPosts")
}
type Post @model {
  id: ID!
  title: String!
  blog: Blog @connection(name: "BlogPosts")
  comments: [Comment] @connection(name: "PostComments")
}
type Comment @model {
  id: ID!
  content: String
  post: Post @connection(name: "PostComments")
}
```



















