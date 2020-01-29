# Mongoose Workshop - Exercise #1 - User seeding

In the given server.js file we have a small express app with a user mongoose model and a login route. No forms.

We now want to insert some users (hardcoded) into our system. We will do so by using "seeding". 

Additionally users in our system should also have roles (different roles will have different permissions).

## Task: User seeding

* Extend the User schema
    * Create a field "roles"
    * This field should be able to store an array of strings, e.g. ["Administrator", "Editor", "Reader"]
        * Provide the right Mongoose Datatype for that

* Create a route /users/seed
    * When calling this route we want to create three users in our database. 
    * Create an Array with three user objects
        * Every user should have email, password and at least one role, e.g. `{email: "rob@dci.de", password: "pw1", roles: ['Admin', 'Teacher'] }`
    * For every user in the array: Hash the password using `bcrypt.hashSync(...)`
    * Use Mongoose function `User.insertMany()` to create the users in the database
    * Return the created DB users to the user using res.send

* Test Seeding
    * Call your route via fetch in the browser or using a REST client (like RESTED for Chrome)
    * Check if your three users were created using Mongo Compass
        * Check if passwords are hashed
        * Check if the roles are present

* Test login route
    * Call the POST route /login with data of a user
    * Check if the login of a seeded user works
