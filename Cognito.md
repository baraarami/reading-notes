
# Amplify and Cognito
![](https://d2908q01vomqb2.cloudfront.net/0a57cb53ba59c46fc4b692527a38a87c78d84028/2020/11/02/Amplify_Blogpost-1024x713.png)
- The Amplify Auth category provides an interface for authenticating a user.
- provides the necessary authorization to the other Amplify categories.
- The Amplify CLI helps you to create and configure the auth category with an authentication provider.
### Why we use Amplify and Cognito?
- setup and configure your application to check the current auth session
### How does amplify work with Cognito?
- Amplify interfaces with `Cognito to` store user data,
-  including federation with other `OpenID` providers like Facebook & Google.
-   The `Amplify CLI` automates the access control policies for these `AWS` resources as well as provides fine grained access controls via `GraphQL` for protecting data in your `APIs`.
### Configure Auth Category
#### check the code Example starting feom  [here](https://docs.amplify.aws/lib/auth/getting-started/q/platform/android#configure-auth-category)
1. go to your project directory and execute the command:
2. Install Amplify Libraries
3. Initialize Amplify Auth
4. Check the current auth session



### How To Install Amplify Libraries?

put the following dependency in the  app‘s `build.gradle` file:

```
dependencies {
    implementation 'com.amplifyframework:aws-auth-cognito:1.17.4'
}
```

After the installing we need to Initialize Amplify Auth for that we can add  => 
```
// Add this line, to include the Auth plugin.
Amplify.addPlugin(new AWSCognitoAuthPlugin());
Amplify.configure(getApplicationContext());
```
and then call `Amplify.configure`
