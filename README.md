GAME VAULT — MINI MERN PROJECT
===============================

Goal
Build one small, fun full-stack MERN project that revises the most important
MERN concepts without repeating the same work across multiple projects.

Project idea
A personal game library, like a very small Steam/PlayStation library.

Users can:
- Register / Login
- Add a game
- Edit a game
- Delete a game
- Search games
- Filter games by status
- Give a rating
- Change game status
- View their own game library
- Logout

Keep the UI simple. The purpose is MERN revision, not UI design.


1. GAME DATA
------------

{
    title: "Forza Horizon 5",
    genre: "Racing",
    rating: 9,
    status: "Playing"
}

MongoDB document additionally contains:

{
    _id,
    title,
    genre,
    rating,
    status,
    userId,
    createdAt
}

Allowed status:
- Playing
- Completed
- Wishlist


2. USER DATA
------------

{
    name,
    email,
    password,
    role
}

Roles:
- user
- admin


3. FRONTEND
-----------

Stack:
React
Vite
Tailwind CSS
React Router
fetch() or Axios

Pages:
/login
/register
/games
/games/:id

Suggested components:

App
 |
 +-- Navbar
 +-- Login
 +-- Register
 +-- Games
 |    +-- SearchBar
 |    +-- Filter
 |    +-- GameForm
 |    +-- GameList
 |         +-- GameCard
 +-- GameDetails

Simple UI:

------------------------------------------------
GAME VAULT                    Search     Logout
------------------------------------------------

[ + Add Game ]

All | Playing | Completed | Wishlist

+------------+  +------------+  +------------+
| GTA V      |  | Forza      |  | Minecraft  |
| Action     |  | Racing     |  | Sandbox    |
| Rating: 9  |  | Rating: 8  |  | Rating: 10 |
| Playing    |  | Completed  |  | Playing    |
| Edit Delete|  | Edit Delete|  | Edit Delete|
+------------+  +------------+  +------------+


4. OPTIONAL SMALL DASHBOARD
---------------------------

Total Games:       12
Currently Playing: 3
Completed:          7
Average Rating:    8.4

Top Rated:
1. Red Dead Redemption 2 — 10
2. Minecraft — 9.5
3. Forza Horizon 5 — 9

Useful for revising:
filter()
reduce()
sort()


5. BACKEND
----------

Node.js
Express
MongoDB
Mongoose

Structure:

backend/
|
+-- server.js
|
+-- config/
|   +-- db.js
|
+-- models/
|   +-- User.js
|   +-- Game.js
|
+-- routes/
|   +-- authRoutes.js
|   +-- gameRoutes.js
|
+-- controllers/
|   +-- authController.js
|   +-- gameController.js
|
+-- middleware/
    +-- auth.js
    +-- admin.js


6. API ENDPOINTS
----------------

Authentication:

POST   /api/auth/register
POST   /api/auth/login

Games:

GET    /api/games
GET    /api/games/:id
POST   /api/games
PUT    /api/games/:id
DELETE /api/games/:id

GET     -> read
POST    -> create
PUT     -> update
DELETE  -> delete


7. COMPLETE MERN FLOW
---------------------

                         FRONTEND
                    React + Vite
                         |
                         | HTTP / JSON
                         v
                  Express REST API
                         |
                    Middleware
                    /          \
               JWT Auth       RBAC
                    \          /
                     Controller
                         |
                      Mongoose
                         |
                         v
                      MongoDB


Response flow:

MongoDB
   |
   v
Mongoose
   |
   v
Controller
   |
   v
Express
   |
   v
JSON response
   |
   v
React
   |
   v
setState()
   |
   v
UI updates


8. AUTHENTICATION FLOW
----------------------

REGISTER

React
  |
  | POST /register
  v
Express
  |
  v
Hash password with bcrypt
  |
  v
MongoDB


LOGIN

React
  |
  | POST /login
  v
Express
  |
  v
Find user
  |
  v
Compare password
  |
  v
Create JWT
  |
  v
Return token


PROTECTED REQUEST

React
  |
  | Authorization: Bearer TOKEN
  v
Auth Middleware
  |
  v
Verify JWT
  |
  v
req.user
  |
  v
Controller


9. RBAC FLOW
------------

Roles:
USER
ADMIN

Example:
Admin can access:
GET /api/admin/games

Normal user cannot.

Flow:

Request
   |
   v
JWT middleware
   |
   v
Role middleware
   |
   +---- user? ----> 403 Forbidden
   |
   +---- admin? ---> Controller


10. IMPORTANT JAVASCRIPT CONCEPTS
---------------------------------

Revise these while building:

- variables
- data types
- objects
- arrays
- functions
- arrow functions
- conditions
- loops
- array of objects
- map()
- filter()
- find()
- findIndex()
- reduce()
- sort()
- destructuring
- spread operator
- async/await
- try/catch
- JSON
- modules


11. IMPORTANT REACT CONCEPTS
----------------------------

- JSX
- components
- props
- state
- useState
- useEffect
- event handling
- forms
- controlled inputs
- conditional rendering
- lists
- keys
- component communication
- React Router
- API calls
- loading state
- error state


12. IMPORTANT EXPRESS CONCEPTS
------------------------------

- Node.js
- npm
- Express
- server
- routes
- controllers
- middleware
- req
- res
- req.body
- req.params
- req.query
- next()
- REST API
- HTTP methods
- HTTP status codes
- error handling
- CORS
- .env


13. IMPORTANT MONGODB CONCEPTS
------------------------------

- database
- collection
- document
- MongoDB
- Mongoose
- schema
- model
- ObjectId
- CRUD
- references
- userId relationship

Relationship:

User
 |
 | userId
 v
Game


14. IMPORTANT AUTH CONCEPTS
---------------------------

- Authentication
- Authorization
- bcrypt
- password hashing
- JWT
- Bearer token
- middleware
- protected routes
- RBAC
- req.user


15. MINIMUM FEATURES
--------------------

Must have:

[ ] Register
[ ] Login
[ ] Logout
[ ] Add game
[ ] View games
[ ] Edit game
[ ] Delete game
[ ] Search
[ ] Filter
[ ] Rating
[ ] Status
[ ] JWT authentication
[ ] Protected API
[ ] User-specific games
[ ] Basic admin/user role

Do NOT add:

- Redux
- Socket.io
- Payments
- Cloudinary
- AI
- Docker
- GraphQL
- Microservices
- Advanced TypeScript
- Advanced MongoDB aggregation
- Complex animations
- Complicated UI
- Deployment unless time remains


16. 2-DAY BUILD ORDER
---------------------

DAY 1 — FOUNDATION + BACKEND

1. Create Vite React frontend
2. Create Express backend
3. Connect MongoDB
4. Create User model
5. Create Game model
6. Create register API
7. Create login API
8. Hash passwords with bcrypt
9. Generate JWT
10. Create authentication middleware
11. Test APIs with Postman


DAY 2 — FULL-STACK CONNECTION

12. Create React Router pages
13. Build Login/Register forms
14. Build Game List
15. Build Add Game form
16. Connect GET/POST APIs
17. Add Edit/Delete
18. Add JWT to protected requests
19. Add search/filter
20. Add admin/user authorization
21. Add loading/error handling
22. Test complete flow
23. Explain the architecture without notes


17. FINAL CHECK
--------------

You should be able to explain:

1. What is React?
2. Why use Vite?
3. What is a component?
4. Props vs state?
5. What does useEffect do?
6. How does React call an API?
7. What is REST?
8. GET vs POST vs PUT vs DELETE?
9. What is Express?
10. What is middleware?
11. What are req.body, req.params and req.query?
12. What is MongoDB?
13. What is Mongoose?
14. Schema vs model?
15. What is CRUD?
16. Authentication vs authorization?
17. How does JWT work?
18. What is bcrypt?
19. What is RBAC?
20. What happens from clicking "Add Game" until the game appears in MongoDB?
21. How does the MongoDB result get back into React?
22. What is CORS?
23. Why use .env?
24. How do you handle errors?


18. MOST IMPORTANT THING TO REMEMBER
------------------------------------

The project is NOT about memorizing code.

Remember this architecture:

React UI
   |
   v
API request
   |
   v
Express route
   |
   v
Middleware
   |
   v
Controller
   |
   v
Mongoose Model
   |
   v
MongoDB

Then the response travels back:

MongoDB
   |
   v
Mongoose
   |
   v
Controller
   |
   v
Express
   |
   v
JSON
   |
   v
React state
   |
   v
UI

If you can build this small project and explain this flow clearly,
your core MERN development concepts will be refreshed without wasting
your limited preparation time.

END OF DOCUMENT
