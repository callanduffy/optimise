# optimise

Here is documentation for all API endpoints in your backend:

Auth
POST /auth/signup
Description: Registers a new user.
Body:
{
  "email": "string (required)",
  "password": "string (required)"
}
Response:
The created user object (excluding password).
POST /auth/login
Description: Logs in an existing user.
Body:
{
  "email": "string (required)",
  "password": "string (required)"
}
Response:
{ "access_token": "string" }
User
GET /user/me
Description: Get details of the currently logged-in user.
Headers:
Authorization: Bearer <JWT>
Response:
The user object.
List
POST /list/create
Description: Create a new list for the logged-in user.
Headers:
Authorization: Bearer <JWT>
Body:
{
  "name": "string (required)",
  "tasks": ["string"]
}
Response:
The created list object.
DELETE /list/delete/:id
Description: Delete a list by its ID.
Headers:
Authorization: Bearer <JWT>
Params:
id (number, required) - List ID
Response:
List of remaining lists for the user.
PATCH /list/edit/:id
Description: Edit a list's details.
Headers:
Authorization: Bearer <JWT>
Params:
id (number, required) - List ID
Body:
{
  "name": "string (optional)",
  "tasks": ["string"]
}
Response:
The updated list object.
GET /list/get/:id
Description: Get a specific list by its ID.
Headers:
Authorization: Bearer <JWT>
Params:
id (number, required) - List ID
Response:
The list object.
GET /list/get-all
Description: Get all lists for the logged-in user.
Headers:
Authorization: Bearer <JWT>
Response:
Array of list objects.
Task
POST /tasks/create
Description: Create a new task for the logged-in user.
Headers:
Authorization: Bearer <JWT>
Body:
{
  "name": "string (required)",
  "description": "string (optional)",
  "deadline": "ISO date string (optional)",
  "listId": "number (optional)"
}
Response:
The created task object.
GET /tasks/get-all-tasks
Description: Get all tasks.
Headers:
Authorization: Bearer <JWT>
Response:
Array of task objects.
PATCH /tasks/list/:listId/task/:taskId/add
Description: Add a task to a list.
Headers:
Authorization: Bearer <JWT>
Params:
listId (number, required), taskId (number, required)
Response:
The updated list object.
PATCH /tasks/list/:listId/task/:taskId/remove
Description: Remove a task from a list.
Headers:
Authorization: Bearer <JWT>
Params:
listId (number, required), taskId (number, required)
Response:
The updated list object.
PATCH /tasks/list/:listId/tasks/add
Description: Add multiple tasks to a list.
Headers:
Authorization: Bearer <JWT>
Params:
listId (number, required)
Body:
{
  "taskIds": [number, ...]
}
Response:
The updated list object.
PATCH /tasks/list/:listId/task/:taskId/completed
Description: Mark a task as completed.
Headers:
Authorization: Bearer <JWT>
Params:
listId (number, required), taskId (number, required)
Response:
The updated task object.
If you need example curl commands for any endpoint, let me know!
