# Jobbotron
LinkedIn backend clone

All methods at all endpoints require authentication except as noted.

## /users

#### POST
Create a new user. <code>username</code> and <code>email</code> must be unique, and are required. <code>first_name</code>, <code>last_name</code> and <code>password</code> are also required. <code>current_company</code> should be a given company's handle if it already exists, and <code>null</code> otherwise. <code>photo</code> is optional and should be a URL if provided. Returns the new user in JSON with an <code>id</code> assigned and with the password hashed.

```json
{
      "first_name": "___",
      "last_name": "___",
      "username": "___",
      "email": "___",
      "password": "___",
      "current_company": null,
      "photo": "___"
  }
```

#### GET
Return a list of up to 50 users in JSON, or up to 50 users matching the search string, if a query is provided with a "search" string parameter. Must be logged in.

## /users/{id}

#### GET
Return the user matching the provided <code>id</code>.

#### PATCH
Update the user matching the provided <code>id</code>. <code>username</code> and <code>id</code> cannot be altered. Must be logged in as user being patched.

#### DELETE
Delete the user matching the provided <code>id</code>. Must be logged in as user being deleted.

## /companies

#### POST
Create a new company account. <code>handle</code> and <code>email</code> must be unique, and are required. <code>name</code> and <code>password</code> are also required. <code>logo</code> is optional and should be a URL if provided. Returns the new company in JSON with an <code>id</code> assigned and with the password hashed.

```json
{
	"name": "___",
	"logo": "___",
	"email": "___",
	"handle": "___",
	"password": "___"
}
```

#### GET
Return a list of up to 50 companies in JSON, or up to 50 companies matching the search string, if a query is provided with a "search" string parameter. Must be logged in.



/jobs/{id}
