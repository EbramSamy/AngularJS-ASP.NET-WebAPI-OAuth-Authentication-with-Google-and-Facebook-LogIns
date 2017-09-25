# AngularJS-ASP.NET-WebAPI-OAuth-Authentication-with-Google-and-Facebook-LogIns
Authentication using ASP.NET OAuth with AngularJS as UI framework.

This project uses Angular JS 1.5 Components based architecture. ui-router has been used instead of ngRoute.

This is an example of Basic and Bearer Token authentication in ASP.NET WebAPI 2.0 using OAuth. It also includes the code for Google and Facebook Log-In.

Execution: LogIn component is loaded when the application starts. A user may log in using Facebook/Google credentials. Alternatively, a user may register in to the local DB using Register component and use these credentials for logging in. After the successful log in, the user is routed to a protected page which lists employees.

Steps:

Run the DB script EmployeeDB.sql to generate required tables along with seed data

Create Google and Facebook apps for Social Log-In and copy the Client/App Id and Client/App Secret to the respective fields in App-Start/StartUp.Auth.cs

Change the port number from 53907 to the port number on which your application is configured to run in the following files

a. app.controller.js

      // Function to check if a user authenticated through FB or Google is registered in our local DB
        self.signupExternalUser = function () {
            EmployeeService.signupExternalUser(self.accessToken, self.loginProvider)
            .success(function (response) {
                window.location = "/api/Account/ExternalLogin?provider=" + self.loginProvider + "&response_type=token&client_id=self&redirect_uri=http%3A%2F%2Flocalhost%3A53907%2Fapp%2Findex.html&state=zF1ONOVm-aHsg1UIroIE57ZyFgxZkXJXExroH3dH20s1";
            })
            .error(function (err) {
                DisplayErrorMessage(err);
            });
        }

b. LogInComponent.js

                // Google LogIn Function
                self.googleLogIn = function () {
                    window.location = "/api/Account/ExternalLogin?provider=Google&response_type=token&client_id=self&redirect_uri=http%3A%2F%2Flocalhost%3A53907%2Fapp%2Findex.html&state=zF1ONOVm-aHsg1UIroIE57ZyFgxZkXJXExroH3dH20s1"
                }
                
                
                // Facebook Log In Function
                self.facebookLogIn = function () {
                    window.location = "/api/Account/ExternalLogin?provider=Facebook&response_type=token&client_id=self&redirect_uri=http%3A%2F%2Flocalhost%3A53907%2Fapp%2Findex.html&state=zF1ONOVm-aHsg1UIroIE57ZyFgxZkXJXExroH3dH20s1"
                }
    

NOTE: This application was configured to run in http://localhost:53907

Kindly refer http://csharp-video-tutorials.blogspot.in/2016/09/aspnet-web-api-tutorial-for-beginners.html for ASP.NET WebAPI tutorials. This example is based on a similar example illustrated in the above link. Videos from 18 to 29 explain authentication in WebAPI. Kindly refer videos 18 and 19 for setting up your Google and Facebook Log-In apps.

Kindly re-install the nuGet packages if prompted.
