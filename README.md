# googleAuth-tests with node and React

## 1-ignacio-nicolas-aguirre
- Esta muy bien, es para google calendar. 
- No usa el componente boton prefabricado de google (npm  react-google-login)
- Tiene persistencia de sesion usando localsotrage?
- !Los JWT los pasa como query parameters
- Implementa refresh tokens
- tiene repo de github


https://levelup.gitconnected.com/handling-access-tokens-for-google-apis-with-react-node-js-tutorial-5ebf94d8f90f
https://github.com/Ignacio1996/google-auth-tokens

--------------------------------------



https://dev.to/shaan_alam/how-to-implement-google-authentication-in-your-react-applications-jb6
https://notangad.medium.com/react-google-login-and-node-js-implementation-32002d8d8d78
https://blog.prototypr.io/how-to-build-google-login-into-a-react-app-and-node-express-api-821d049ee670
https://gist.github.com/jhackett1/ff383ca58d69c8a8d9285e81fc065c08

https://github.com/topics/googleauth
https://github.com/topics/react-google-login







React Google Login and Node.js implementation
Social login is a great way to get new users started on your platform as it takes away all the hassle of filling up those tedious signup forms. In this blog, I will show you how you can implement google social login for your react application the right way via backend token verification. I am going to assume that you have already set up your react frontend and node.js back-end for this tutorial. So without any further ado let's get started.

For this tutorial, you will need the following packages
Backend
* Google Auth Library (https://www.npmjs.com/package/google-auth-library)
Frontend
* react-google-login (https://www.npmjs.com/package/react-google-login)
* react-confetti (https://www.npmjs.com/package/react-confetti)
* react-toastify (https://www.npmjs.com/package/react-toastify)
On your front end firstly we will import all the packages that we will require for this project.

After importing all the packages first, we will focus on the GoogleLogin package. Google Login package allows us to get an OAuth token which will be used in our backend to verify the legitimacy of social login. For using this plugin you will require a client-id which you can get from your google console developer account. For this tutorial, I will assume that you already have a client-id. The code of your Google Login Package should look something like this.

This package requires two functions. One function will run when it will be able to successfully get a client-id. The other will run in case of any errors. In case of success, we will get an OAuth Token which we will send to our API for verification and login. The function of success will look something like this.

The steps for success are as follows:
First, we will check if we have received a token
Once we receive a token we will send it to our API
Our API will provide us with the user details like name, email, and even picture
Once successfully logged in we will show users a toast notifying them that the login attempt was a success.
Also just to make it even better we will throw confetti on the screen for that celebration effect. So our final frontend code would look something like this.

Our render code logic.

The code that will disable the confetti after 5 seconds of login.

Our state logic and failure code of google login.
This was the implementation of our front end. Now let's take a look at our backend.
On your backend first of all import the library that we previously installed.

Once we have imported the library we will now need to create a client instance from this. To create a client instance we will once again need our client-id which we can get from console developers google.

After that, we will create our endpoint which will handle our login logic. Our login logic will constitute of the following steps
First, get the token from the body of the request.
Then we will verify the token and get user details from that token.
Perform database operations on the data that you just retrieved.
Finally, send the data back to the front end.
In this tutorial I have not performed any DB operations as DB operations on logic can vary from platform to platform. I have simply retrieved the data to show you how you can get legitimate login data. Our final code should look something like this.

So our final interaction between front-end and back-end would be as follows.

And our social login should work as follows:

So this is one of the ways on how you can implement social login in your react applications. The link for the code can be found in my git repo.