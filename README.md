# Task Manager API

This is an API built using `Express.js`, `Node.js` and `MongoDB`.

## Functions

* User can create a new task.

* User can see a list of all tasks.

* User delete a task.

* User edit a task.

* User can mark a task as completed.

## Running the app locally

Clone this repo:

```bash
git clone https://github.com/0binna/Task-Manager-API.git
```

Open the folder:

```bash
cd Task Manager API
```

Install all dependencies:

```bash
npm install
```

Start the app:

```bash
npm start
```

## API Documentation

Errors are returned as JSON objects in the following format:

```json
{
    "msg": "Route does not exist"
}
```

The API will return these error types when requests fail:
- 400: Bad Request
- 404: Resource Not Found
- 500: Internal  Server Error

### Endpoints

#### GET '/tasks'
- Fetches a list of all tasks.
- Request Arguments: None.

```bash 
curl http://localhost:3000/api/v1/tasks
```
Sample response:

```json
{
  "tasks": [
      {
          "completed": false,
          "_id": "633ce9dad5cae34020a644cb",
          "name": "Meeting with Dave",
          "__v": 0
      },
      {
          "completed": false,
          "_id": "633ce9e5d5cae34020a644ce",
          "name": "Review the project",
          "__v": 0
      },
      {
          "completed": false,
          "_id": "633ce9fad5cae34020a644d1",
          "name": "Walk the dog",
          "__v": 0
      }
  ],
  "total_Task": 3
}
```

#### POST '/tasks'
- Sends a post request to add a new question
- Request Arguments: A json body containing `name` - string, `completed` - boolean (default value is false). 

```bash 
curl -X DELETE http://localhost:3000/api/v1/tasks -X POST -H "Content-Type: application/json" -d '{"name": "Grocery Shopping"}'
```
Sample response:

```json
{
    "task": {
        "completed": false,
        "_id": "633cf500776fd549009aa011",
        "name": "Grocery Shopping",
        "__v": 0
    }
}
```

#### GET '/tasks/${id}'
- Fetches a task specified by the id request argument.
- Request Arguments: `id` - integer.

```bash 
curl http://localhost:3000/api/v1/tasks/633ce9e5d5cae34020a644ce
```
Sample response:

```json
{
    "completed": false,
    "_id": "633ce9e5d5cae34020a644ce",
    "name": "Review the project",
    "__v": 0
}
```

#### PATCH '/tasks/${id}'
- Sends a patch request to update a task (Task is specified by the id request argument).
- Request Arguments: `id` - integer.

```bash 
curl -X PATCH -H "Content-Type: application/json" -d'{"completed": true}' http://localhost:3000/api/v1/tasks/633ce9e5d5cae34020a644ce
```
Sample response:

```json
{
    "completed": true,
    "_id": "633ce9e5d5cae34020a644ce",
    "name": "Review the project",
    "__v": 0
}
```

#### DELETE '/tasks/${id}'
- Deletes a task specified by the id request argument.
- Request Arguments: `id` - integer.

```bash 
curl -X DELETE http://localhost:3000/api/v1/tasks/633ce9dad5cae34020a644cb
```
Sample response:

```json
{
    "task": {
        "completed": false,
        "_id": "633ce9dad5cae34020a644cb",
        "name": "Meeting with Dave",
        "__v": 0
    }
}
```