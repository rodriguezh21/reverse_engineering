# Reverse Engineering
## Homework #14

### Business Context

When joining a new team, you will be expected to inspect a lot of code that you have never seen before. Rather than having a team member explain every line for you, you will dissect the code by yourself, saving any questions for a member of your team. 

***

```
AS A developer

I WANT a walk-through of the codebase

SO THAT I can use it as a starting point for a new project
```

***

>> config / middleware / isAuthenticated.js

- This is middleware for restricting routes a user is not allowed to visit if not logged in.
- If the user is logged in, continue with the request to the restricted route.
- If the user isn't logged in, redirect them to the login page.

>> config / config.json

- Contains credentials for connecting to the database.
- Specifies global values, conditional environment, and platform values.

>> config / passport.js
* Required dependencies:  "db"

- This file is used to authenticate information such as: user email and password used for login purposes.
- Checks database for existing information.
- Validates input type i.e. correct email syntax.

>> models / index.js
* Required dependencies:  "db"

- Sequelizes all the files in the models folder to later be imported and used in another file.

>> models / user.js
* Required dependencies:  "bcrypt"

- Creates user models and sets params for proper input.
- Allows user's password to be hashed for better security.

>> public / js / login.js
- Gets reference to form and inputs.
- When the form is submitted, we validate that there's an email and password entered.
- If we have an email and password we run the loginUser function and clear the form.
- loginUser does a post to our "api/login" route and if successful, redirects us the the members page.

>> public / js / members.js
- This file just does a GET request to figure out which user is logged in and updates the HTML on the page.

>> public / js / signup.js
- Collects user information to create new login and if successful it redirects to members page.

>> public / stylesheets / style.css
- Sets the margin-top of the login and signup forms to 50px.

>> public / login.html
* Required dependencies:  "style.css", "login.js"
- Contains a form with inputs for email and password, a login button, and a link to the signup page.

>> public / members.html
* Required dependencies:  "style.css", "members.js"
- Welcome page for members with a welcome header and a logout button.

>> public / signup.html
* Required dependencies:  "style.css", "signup.js"
- Contains a form with inputs for email and password, a signup button, and a link to the login page.

>> routes / api-routes.js
* Required dependencies:  "db", "passport"
- Creates routes for user login POST requests functions, signup POST requests functions, and GET requests for logout functions. 

>> routes / html-routes.js
* Required dependencies:  "path"
- Requiring path so we can use relative routes to our HTML files and using middleware to check if user is logged in.

>> package.json
- List of installed dependencies.

>> server.js
* Required dependencies:  "express", "express-session", "passport", "db"
- Creates express app and configuring middleware needed for authentication.
- We need to use sessions to keep track of our user's login status.

In the server.js file be sure to add your desired PORT.
