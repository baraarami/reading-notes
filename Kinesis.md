# Kinesis

![kinesis-lyft-10-638](https://user-images.githubusercontent.com/79080942/130632744-480d3554-486f-4084-874c-868c44d6f6da.jpg)

Kinesis support is currently only available in the Amplify JavaScript library .

#### To set up Analytics backend
- Run the following command in your project's root folder 

``` amplify add analytics 

  Select an Analytics provider (Use arrow keys)
    `Amazon Pinpoint`
? Provide your pinpoint resource name: 
    `yourPinpointResourceName`
? Apps need authorization to send analytics events. Do you want to allow guests and unauthenticated users to send analytics events? (we recommend you allow this when getting started) 
    `Yes`
```

- To deploy the bachend , run :
 ```
 amplify push 
 ```
 
 - Add Analytics by adding these libraries into the dependencies block:

``` 
dependencies {
    // Add these lines in `dependencies`
    implementation 'com.amplifyframework:aws-analytics-pinpoint:1.24.0'
    implementation 'com.amplifyframework:aws-auth-cognito:1.24.0'
}
``` 
and there are several steps you need to followe in these website :
[Kinesis](https://docs.amplify.aws/lib/analytics/getting-started/q/platform/android/#view-analytics-console)
















