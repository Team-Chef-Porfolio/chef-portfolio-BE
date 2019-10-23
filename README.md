## chef-portfolio-BE

### API Base URL: https://chef-portfolio-buildweeks-be.herokuapp.com

The post will have this basic format:

```json
   {
      "chef_name": "Erica",
      "recipe_title": "Pizza",
      "item_photo":
        "https://images.unsplash.com/photo-1528137871618-79d2761e3fd5?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80",
      "chef_location": "Boston, Massachusetts",
      "item_ingredients": "Pizza Dough, Pizza Sauce, Cheese, Basil",
      "user_id": 2
    },
    {
      "chef_name": "Mitsuki",
      "recipe_title": "Soup",
      "item_photo":
        "https://images.unsplash.com/photo-1529692236671-f1f6cf9683ba?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80",
      "chef_location": "Austin, TX",
      "item_ingredients": "Water, Tomatoes, Cream, Basil",
      "user_id": 2
    },
    {
      "chef_name": "Sam",
      "recipe_title": "Steak",
      "item_photo":
        "https://images.unsplash.com/photo-1529692236671-f1f6cf9683ba?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80",
      "chef_location": "Colonie, NY",
     "item_ingredients": "Cut of Steak",
      "user_id": 2
    }
```

https://chef-portfolio-buildweeks-be.herokuapp.com/api/auth/register

- A POST request will register a new user and provide an JSON web token

- <strong>Required</strong>: username, password, email and location

	*example:

	- Body:

			{
				"username": "testy",
				"password": "mctestface",
				"email": "testy@mctestface.com",
				"location": "Chicago, IL"
			}

	- Response:

			{
			  "id": 6,
			  "username": "testy",
			  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWJqZWN0Ijo2LCJ1c2VybmFtZSI6InRlc3R5IiwiaWF0IjoxNTY2MzEzMzk5LCJleHAiOjE1NjYzOTk3OTl9.AIQFmgV0DyDshbq1VchMqwbHZ72aVmDSWRWTgdFFyYE"
			}

https://chef-portfolio-buildweeks-be.herokuapp.com/api/auth/login

- A POST request will login a registered user and will provide the JSON web Token.

- <strong>Required</strong>: username and password

	*example:

	- Body:

			{
				"username": "testy",
				"password": "mctestface"
			}

	- Response:

			{
			  "message": "testy is logged in.",
			  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWJqZWN0Ijo2LCJ1c2VybmFtZSI6InRlc3R5IiwiaWF0IjoxNTY2MzEzNDQxLCJleHAiOjE1NjYzOTk4NDF9.B0a-Z1zPHiBjmG3qN8glvvp00IQGn556kvSfTxd0T-Q"
			}

https://chef-portfolio-buildweeks-be.herokuapp.com/api/posts

- a GET request to return all post by logged-in user.

	*example:

	- Response:

			[
				{
				  "id": 5,
				  "chef_name": "testy",
				  "recipe_title": "Steak",
				  "item_photo": "https://images.unsplash.com/photo-1529692236671-f1f6cf9683ba?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80",
				  "chef_location": null,
				  "item_ingredients": "Cut of Steak",
				  "user_id": 6
				},
				{
				  "id": 6,
				  "chef_name": "testy",
				  "recipe_title": "Burger",
				  "item_photo": "https://images.unsplash.com/photo-1529692236671-f1f6cf9683ba?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80",
				  "chef_location": "Memphis, TN",
				  "item_ingredients": "Ginormous Burger",
				  "user_id": 6
				}
			]



https://chef-portfolio-buildweeks-be.herokuapp.com/api/posts/:id

- a GET request to return the post with the specific ID.

	*example:

	- Response:

			{
			  "id": 5,
			  "chef_name": "testy",
			  "recipe_title": "Steak",
			  "item_photo": "https://images.unsplash.com/photo-1529692236671-f1f6cf9683ba?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80",
			  "chef_location": null,
			  "item_ingredients": "Cut of Steak",
			  "user_id": 6
			}


https://chef-portfolio-buildweeks-be.herokuapp.com/api/posts

- a POST request that will let the logged in user create a new chef post
- <strong>Required</strong>: chef_name

	*example:

	- Body:

			{
				"chef_name": "testy"
			}

	- Response:

			{
			  "id": 6,
			  "chef_name": "testy",
			  "recipe_title": null,
			  "item_photo": null,
			  "chef_location": null,
			  "item_ingredients": null,
			  "user_id": 6
			}


https://chef-portfolio-buildweeks-be.herokuapp.com/api/posts/

- a PUT request to edit the post that the user created
- <strong>Required</strong>: User needs to be logged in

	*example:

	- Body:

			{
				"chef_location": "Chicago, IL"
			}

	- Response:

			{
			  "chef_location": "Chicago, IL"
			}


https://chef-portfolio-buildweeks-be.herokuapp.com/api/posts/:id

- a DELETE request to this route will delete the post id of that route for a logged in user.
