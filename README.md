# System-Design-Learning
Build a micro service system for user to login and upload/convert/download audio file using Python, Flask, Docker, Kubernetes, RabbitMQ, and MongoDB

## Architecture Diagram
![image](https://github.com/nhatduy227/System-Design-Learning/assets/53373898/7d7e47a4-dc51-4ee4-aefa-fc275b01f95a)

## Authentication Flow

### 1. Logging In (`/login`)

To authorize, the client should make a `POST` request to the `/login` endpoint.

**Endpoint:**  
```
POST /login
```

**Request Body:**
```json
{
  "username": "example_username",
  "password": "example_password"
}
```

**Response:**  
Upon successful authentication, the server will respond with a JWT token.

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
}
```

### 2. Validating Token (`/validate`)

Before accessing protected resources, the client must validate the JWT token by sending it to the `/validate` endpoint.

**Endpoint:**  
```
POST /validate
```

**Request Header:**
```
Authorization: Bearer <token>
```

**Response:**  
Upon successful validation, the server will respond with a success message.

```json
{
  "message": "Token is valid"
}
```

---

Make sure to replace `example_username` and `example_password` with actual credentials when making requests.

In subsequent requests to the API gateway, include the JWT token in the `Authorization` header as `Bearer <token>` to access protected resources.


## Tech Stack break down
1. Python Flask: Backend code for 3 main services (auth service, notification service, convert video to mp3 service)
2. Docker: Containing intances of 3 services in Docker Containers with specific requirements and versonings
3. Kubernetes:
4. RabbitMQ:
5. MongoDB (GridFS):

