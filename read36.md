# Amplify and Cognito
## Getting started
* an interface for authenticating a user provided by Amplify Auth category
* The Amplify CLI helps to create and configure the auth category with an authentication provider.

### Goal
* To setup and configure your application with Amplify Auth and go through a simple api to check the current auth session

### Prerequisites
* at least Android SDK API level 16 with Amplify libraries integrated

### Configure Auth Category
* execute the command: `amplify add auth`
* Enter the following when prompted:

>? Do you want to use the default authentication and security configuration?
>
>    `Default configuration`
>
>? How do you want users to be able to sign in?
>
>    `Username`
>
>? Do you want to configure advanced settings?
>
>    `No, I am done.`
>
*push your changes to the cloud by: `amplify push`

* To Install Amplify Libraries: in ` build.gradle` add : ` implementation 'com.amplifyframework:aws-auth-cognito:1.35.4'`

>// Add this line, to include the Auth plugin.
>
>Amplify.addPlugin(new AWSCognitoAuthPlugin());
>
>Amplify.configure(getApplicationContext());

*  call `Amplify.configure`
* Check the current auth session : run this from MainActivity's onCreate method:
>Amplify.Auth.fetchAuthSession(
>
>    result -> Log.i("AmplifyQuickstart", result.toString()),
>
>    error -> Log.e("AmplifyQuickstart", error.toString())
>
>);

## Sign in
### Register a user
* requires a username, password and a valid email id as parameters to register a user.
* confirm the user after run some lines of code
* A confirmation code will be sent to the email id provided during sign up. Enter the confirmation code received via email in the `confirmSignUp` call.

### Sign in a user
*  the user enters the username and password 
*  start the sign 

### Multi-factor authentication
*  navigate to your project directory in Terminal, run `amplify auth remove` and when that completes, `amplify push ` to remove it.
* run `amplify add auth` then  `amplify push `
* confirm signup, sign in, and get back a nextStep in the sign in result of type `CONFIRM_SIGN_IN_WITH_SMS_MFA_CODE`