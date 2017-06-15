# Post tagging challenge

In this challenge you will be creating an API for a microblogging platform which have:
* **Posts** and 
* **Users**

## Requirements
These ones are a must:
* CakePHP 3 (Targeting PHP 7.1)
* Integration testing
* Migrations 
* MySQL

Optionally (will grant **extra points**):
* Use [Crud](crud.readthedocs.org/en/latest/) plugin
* Use [Search Plugin](https://github.com/FriendsOfCake/search) to filter data

## Challenge scenario

We are creating an mobile app which depends on an API, and in our microblogging platform the users 
can:
* create an user profile for them
* create new posts.
* tag multiple users on their posts.
* Tag other user even if this other said user is not on the platform
* like other users post. 

## Challenge endpoints

In order to build the app correctly we need to create the following endpoints:

### Create a user
**Request:** `POST /users`

**Body:**
```json
{
  "username": "johndoe",
  "email": "johndoe@gmail.com",
  "biography": "I am UNKNOWN"
}
```

**Response:** up to you, it is part of the avaliation (must be in JSON :wink:).

### Read all users (`GET /users`)

**Request** (can have the following query parameters):
* ?username= : filter users by their username

**Response:** up to you, it is part of the avaliation (must be in JSON).

### Create an post
**Request:** `POST /posts`

**Body:**
```json
{
  "body": "Had a blast with my buddy",
  "users": ["johndoe", "johncena", "non_existing_user"]
}
```

**Response:** up to you, it is part of the avaliation (must be in JSON).

### Like a post
**Request:** `POST /likes`

**Body:**
```json
{
  "user_id": 1,
  "post_id": 1
}
```

**Response:** up to you, it is part of the avaliation (must be in JSON).

### Read all posts

Return all posts, optionally filtering by tagged users.

**Request:** `GET /posts?username={username}`

**Response:**
The response will have to contain **at least** the following fields,
it can have more. The names of the fields may change accordingly with your schema.

```json
{
  "success": true,
  "data": [
    {
      "id": 1,
      "user_id": 10,
      "like_count": 2,
      "users": [
        {
          "id": 1,
          "username": "johndoe"
        },
        {
          "id": 2,
          "username": "johncena"
        }
      ],
      "posts_users": [
        {
          "id": 1,
          "post_id": 1,
          "user_id": 1,
          "user_tag": "johndoe"
        },
        {
          "id": 4,
          "post_id": 1,
          "user_id": 2,
          "user_tag": "johncena"
        }
      ]
    }
  ]
}
```

## Availiation criteria

All submissions will be reviewed, for this review we will involve multiple developers. As a sign of cordiality we inform you that your avaliation will be based on the following criteria:

* **Maintainability**: The code is readable and easy to maintain?
* **Design**: How were responsibilities separated? What techniques were used?
* **Quality**: Do you have tests? How difficult is it to update the tests if it is necessary to change the behavior of the application?
* **Performance**: Wrote a code with adequate performance? It does not have to be perfect, but do you understand what would be the best solution?
* **Coding Standards**: Does the code comply to [CakePHP Coding Standards](https://book.cakephp.org/3.0/en/contributing/cakephp-coding-conventions.html)? Is the code well documented?

Feel free to step up the challenge to show how the outcome of your effort can make it even better!
