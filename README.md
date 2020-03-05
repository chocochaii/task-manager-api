# task-manager-api
API for task manager application providing simple features plus authentication created by Express.js &amp; MongoDB (Jest included)

## Endpoints
**Create User**

POST https://chocochaii-task-manager.herokuapp.com/users

Payload:

	{
		"name": "Chocochaii",
		"email": "chocochaii@test.com",
		"password": "abc123$!",
		"age": "27" (optional, default = 0)
	}

And you'll get welcome email in your inbox!

**Login**

POST https://chocochaii-task-manager.herokuapp.com/users/login

Payload:

	{
		"email": "chocochaii@test.com",
		"password": "abc123$!"
	}

**Logout**

POST https://chocochaii-task-manager.herokuapp.com/users/logout

**Logout from all devices**

POST https://chocochaii-task-manager.herokuapp.com/users/logoutAll

**Upload Avatar**

POST https://chocochaii-task-manager.herokuapp.com/users/me/avatar

Payload: Form-data

	{
		"avatar": [image file]
	}

**Create Task**

POST https://chocochaii-task-manager.herokuapp.com/tasks

Payload:

	{
		"description": "Rub my dog gently before going to work",
		"completed": false (optional, default = false)
	}

**Read Profile**

GET https://chocochaii-task-manager.herokuapp.com/users/me

Response:

	{
		"age": 0,
		"_id": [user_id],
		"name": "Chocochaii",
		"email": "chocochaii@test.com",
		"createdAt": [timestamp],
		"updatedAt": [timestamp],
		"__v": [revision_number]
	}

**Read All Tasks**

GET https://chocochaii-task-manager.herokuapp.com/tasks

Parameters:

	?sortBy=[field_name]:[asc|desc]
	?completed=[true|false]
	?limit=[number]&skip=[number] (to do pagination)

Response:

	[
		{
			"completed": false,
			"_id": [task_id],
			"description": "Rub my dog gently before going to work",
			"owner": [user_id],
			"createdAt": [timestamp],
			"updatedAt": [timestamp],
			"__v": [revision_number]
		},
		...
	]

**Read a Task**

GET https://chocochaii-task-manager.herokuapp.com/tasks/[task_id]

Response:

	{
		"completed": false,
		"_id": [task_id],
		"description": "Rub my dog gently before going to work",
		"owner": [user_id],
		"createdAt": [timestamp],
		"updatedAt": [timestamp],
		"__v": [revision_number]
	}

**Update User**

PATCH https://chocochaii-task-manager.herokuapp.com/users/me

Payload:

	{
		"name": "Alex",
		"age": 24
	}

Response:

	{
		"age": 24,
		"_id": [user_id],
		"name": "Alex",
		"email": "chocochaii@test.com",
		"createdAt": [timestamp],
		"updatedAt": [timestamp],
		"__v": [revision_number]
	}

**Update Task**

PATCH https://chocochaii-task-manager.herokuapp.com/tasks/[task_id]

Payload:

	{
		"completed": true
	}

Response:

	{
		"completed": true,
		"_id": [task_id],
		"description": "Rub my dog gently before going to work",
		"owner": [user_id],
		"createdAt": [timestamp],
		"updatedAt": [timestamp],
		"__v": [revision_number]
	}

**Delete User**

DELETE https://chocochaii-task-manager.herokuapp.com/users/me

And you'll get the cancelation email :(

**Delete Task**

DELETE https://chocochaii-task-manager.herokuapp.com/tasks/[task_id]

**Delete Avatar**

DELETE https://chocochaii-task-manager.herokuapp.com/users/me/avatar

## Development
Create dev.env and test.env with the following variables in config/ directory

config/dev.env
```
PORT=<your_server_port>
SENDGRID_API_KEY=<your_sendgrid_api_key>
MONGODB_URL=mongodb://127.0.0.1:27017/task-manager-api
JWT_SECRET=<your_jwt_secret_key>
```

config/test.env
```
PORT=<your_server_port>
SENDGRID_API_KEY=<your_sendgrid_api_key>
MONGODB_URL=mongodb://127.0.0.1:27017/task-manager-api-test
JWT_SECRET=<your_jwt_secret_key>
```
