# Documentation
Home Page - https://mentors-international-app.netlify.com
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Mentor's International API</title>
    <!-- <link rel="stylesheet" href="style.css"> -->
  </head>
  <body>
    <header>
        <h1>Mentor's International API Documentation</h1>
        <h3>Links to the documentation for each route</h3>
        <nav>
            <a href="#Register">Register</a>
            <a href="#Login">Login</a>
            <a href="#User">Login</a>
            <a href="#Users">Login</a>
        </nav>
    </header>
    <div>
        <h2 id="Register">Register</h2>
        <p style="text-indent: 50px">https://mentors-international.herokuapp.com/register</p>
        <h3>User supplies data necessary to make an account. All data is required. Emails are unique so only one email can have an account. Phone numbers will be required in the near future.</h3>

        <h5>POST Method Request Body</h5>
        <pre>
            <code>
            {   
                "email": "dan@dan.com", 
                "firstName":"Dan",
                "lastName":"Mendez",
                "password":"password",
                "countryCode":"1",
                "phoneNumber":"555-678-4321"
            }
            </code>
        </pre>

        <h5>Good Response</h5>
        <p>Status code 201. Currently, an index will be sent back with the user ID will be return. Future implementation will provide a cookie for automatic login.</p>
        <h5>Bad Response</h5>
            <p>Status code 500. This is a catchall server error that could be from missing data, data of the wrong type or not in an object, or the email requested has already been used.</p>
            <p>Future implementation will have more status code with more descriptive error messages detailing the issue.</p>
            <p>Content-Type will be text/html and will be found in the response body</p>
    </div>

    <div>
            <h2 id="Login">Login Route</h2>
            <p style="text-indent: 50px">https://mentors-international.herokuapp.com/login</p>
            <h3>User supplies data necessary to login. All data is required. Sessions are 15 minuites</h3>
            <pre>
                <code>
                {   
                    "email": "dan@dan.com", 
                    "password":"password"
                }
                </code>
            </pre>
            <h5>Good Response</h5>
                <p>Status code 201. Currently, an index will be sent back with the user ID will be return. Future implementation will provide a cookie for automatic login.</p>
                <p>Content-Type will be JSON and data will be found in the response body</p>
                <pre>
                    <code>
                { message: `Welcome ${user.firstName}` }
                    </code>
                </pre>
            <h5>Bad Response - Status Code 401</h5>
                <p>Status code 401. Username and/or password are incorrect</p>
                <p>Content-Type will be JSON and data will be found in the response body</p>
                <pre>
                    <code>
                { message: `Username and/or password are incorrect` }
                    </code>
                </pre>

            <h5>Bad Response - Status Code 500</h5>
                <p>Status code 500. This is a catchall server error that could be from missing data, data of the wrong type or not in an object.</p>
                <p>Future implementation will have more status code with more descriptive error messages detailing the issue.</p>
                <p>Content-Type will be JSON and data will be found in the response body</p>
                <pre>
                    <code>
                { message: `Server error`, error: err }
                    </code>
                </pre>
        </div>

        <div>
                <h2 id="User">User Route</h2>
                <p style="text-indent: 50px">https://mentors-international.herokuapp.com/api/user</p>
                <h3>Login is required. Returns the logged-in user's data</h3>
                <pre>
                    <code>
                GET Method. No data needs to be sent. The cookie will allow an authorized user access to this route.
                    </code>
                </pre>
                <h5>Good Response</h5>
                    <p>Status code 200. Currently, an object with the user's data will be returned. Future implementation will provide messages sent, messages received and schedule information.</p>
                    <p>Content-Type will be JSON and data will be found in the response body</p>
                    <pre>
                        <code>
                    {
                        "id": 1,
                        "email": "dan@dan.com",
                        "firstName": "Dan",
                        "lastName": "Mendez"
                    }
                        </code>
                    </pre>
                <h5>Bad Response - Status Code 401</h5>
                    <p>Status code 401. Not Authorized or Not Logged in</p>
                    <p>Content-Type will be JSON and data will be found in the response body</p>
                    <pre>
                        <code>
                    {
                        "message": "Not Authorized or Not Logged in"
                    }
                        </code>
                    </pre>
    
                <h5>Bad Response - Status Code 500</h5>
                    <p>Status code 500. This is a catchall server error. This may mean that something is wrong with the hosted server. Please contact the admin for help.</p>
                    <p>Future implementation will have more status code with more descriptive error messages detailing the issue.</p>
                    <p>Content-Type will be JSON and data will be found in the response body</p>
                    <pre>
                        <code>
                    { message: `Server error`, error: err }
                        </code>
                    </pre>
            </div>

            <div>
                    <h2 id="Users">Users Route</h2>
                    <p style="text-indent: 50px">https://mentors-international.herokuapp.com/api/user</p>
                    <h3>Login is required. Returns the all users data and their data. This route will limit type of data sent or will be disabled. Only admin should have access to this data or data sent will be specific to a users contact list.</h3>
                    <pre>
                        <code>
                    GET Method. No data needs to be sent. The cookie will allow an authorized user access to this route.
                        </code>
                    </pre>
                    <h5>Good Response</h5>
                        <p>Status code 200. Currently, an object all users and their data.</p>
                        <p>Content-Type will be JSON and data will be found in the response body</p>
                        <pre>
                            <code>
                        {
                            "id": 1,
                            "email": "dan@dan.com",
                            "firstName": "Dan",
                            "lastName": "Mendez"
                        }
                            </code>
                        </pre>
                    <h5>Bad Response - Status Code 401</h5>
                        <p>Status code 401. Not Authorized or Not Logged in</p>
                        <p>Content-Type will be JSON and data will be found in the response body</p>
                        <pre>
                            <code>
                        {
                            "message": "Not Authorized or Not Logged in"
                        }
                            </code>
                        </pre>
        
                    <h5>Bad Response - Status Code 500</h5>
                        <p>Status code 500. This is a catchall server error. This may mean that something is wrong with the hosted server. Please contact the admin for help.</p>
                        <p>Future implementation will have more status code with more descriptive error messages detailing the issue.</p>
                        <p>Content-Type will be JSON and data will be found in the response body</p>
                        <pre>
                            <code>
                        { message: `Server error`, error: err }
                            </code>
                        </pre>
                </div>


  </body>
</html>
