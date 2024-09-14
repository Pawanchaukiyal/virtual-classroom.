Project Setup and Code Walkthrough
1. Installation and Setup
npm install
Environment Variables:

Create a .env file in the root directory. Add the following variables:

env
Copy code
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
Run the Application:

bash
Copy code
npm run dev

2. Project Structure Overview
/models: Contains Mongoose models for User, Class, and other entities.
/controllers: Contains logic for handling routes and business logic, including admin.controller.js.
/middleware: Holds middlewares for authentication (Auth.Middleware.js) and role-based access control (admin.middleware.js).
/routes: Defines express routes, such as admin.route.js for admin-specific functionalities.
/utils: Utility functions like asyncHandler for error handling.


3. Key Features and Walkthrough
Admin Access to Stats
Purpose: Admin users can access statistics like the number of students, teachers, and courses available.
Admin Controller (/controllers/admin.controller.js):

getAdminStats: Fetches and returns the total count of students, teachers, and courses.
Admin Routes (/routes/admin.route.js):

GET /api/v1/admin/stats: Protected route accessible only by admin users, returns platform stats.
Admin Middleware (/middleware/admin.middleware.js):

isAdmin: Verifies if the user is an admin and restricts access if not.
Authentication
JWT: Secures routes using JWT tokens.
Middleware (Auth.Middleware.js): Ensures that only authenticated users can access protected routes.



4. Testing API Endpoints
You can use Postman or any API testing tool to test the following routes:

Admin Stats (Admin Only):
GET /api/v1/admin/stats
Requires: JWT token of an admin.



5. Notes
Only admins can access the /admin/stats route, other users will receive a 403 Forbidden response.
Ensure MongoDB is running and properly connected using the MONGO_URI in your .env file.
