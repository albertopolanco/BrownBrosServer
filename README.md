Brown Bros. Street Food

Description

This is an E-commerce


User Stories

· 404: As an anon/user I can see a 404 page if I try to reach a page that does not exist so that I know it's my fault.

· Signup: As an anon I can sign up in the platform so that I can start playing into competition.

· Login: As a user I can login to the platform so that I can play competitions.

· Logout: As a user I can logout from the platform so no one else can use it.





Backlog

· Tracking del pedido




REACT ROUTES :
PATH			            COMPONENT		            PERMISIONS		        BEHAVIOR

/			                Home page		            Public	<Route>		    Home Page
-----------------------------------------------------------------------------------------------------------------------
/signup		                SignupPage		            anon only		        Signup Form, link to login, 
                        	                            <AnonRoute>		        navigate to home page after SignUp
-----------------------------------------------------------------------------------------------------------------------
/login			            LoginPage		            anon only		        Signup Form, link to login,
						                                <AnonRoute>		        navigate to home page after SignUp	
-----------------------------------------------------------------------------------------------------------------------
/Profile			        ProfilePage		            UserOnly		        Shows user profile, and links to edit it
						                                
-----------------------------------------------------------------------------------------------------------------------





Components

· Navbar.

· LoginPage.



· Auth Service:

    auth.login(user)
    auth.signup(user)
    auth.logout()
    auth.me()

· User:

    user.detail(id)
    user.add(id)
    user.delete(id)




Server/Backend

Models

MODEL USER 

{
name: String,
firstSurname: String,
secondSurname: String,
password: String,
email: String,
direction: String,
postalCode: Number,
card: Number,
}

MODEL CARTA:

{
title: String,
description: String,
extras: [ String ]
}



API Endpoints (backend routes)

HTTP          URL             REQ.BODY                SUCCES         ERROR         DESCRIPTION          
METHOD                                                STATUS         STATUS

GET       /auth/profile       Saved session             200            404          Check if user is logged in 
                                                                                    and return profile page 

POST      /auth/signup        {email,password}          201            404          Checks if fields not empty (422) 
                                                                                    and user not exists (409), then create user with encrypted password, and store user in session

POST      /auth/login         {email, password}         200            401          Checks if fields not empty (422), if 
                                                                                    user exists (404), and if password matches (404), then stores user in session
                                            
POST      /auth/logout         (empty)                  204            400          Logs out the user

GET           /                (empty)                  200            400          Shows home page

GET       /profile/:id         {id}                     200            404          Shows user profile

PUT       /profile/edit/:id    {user model}             200            404          Edit user 
                               


Links 

Git

· Client: https://github.com/Lexirem/BrownBrosClient

· Server: https://github.com/Lexirem/BrownBrosServer

