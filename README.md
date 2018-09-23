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
Return a list of up to 50 users in JSON, or up to 50 users matching the search string, if a query is provided with a <code>search</code> parameter. Must be logged in.

## /users/{id}

#### GET
Return the user matching the provided <code>id</code>.

#### PATCH
Update the user matching the provided <code>id</code>. <code>id</code> cannot be updated. Must be logged in as user being patched.

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
Return a list of up to 50 companies in JSON, or up to 50 companies matching the search string, if a query is provided with a <code>search</code> parameter. Must be logged in.

## /companies/{id}

#### GET
Return the company matching the provided <code>id</code>.

#### PATCH
Update the company matching the provided <code>id</code>. <code>id</code> cannot be updated. Must be logged in as company being patched.

#### DELETE
Delete the company matching the provided <code>id</code>. Must be logged in as company being deleted.


## /jobs

#### POST
Create a new job listing. Must be logged in as a company, not a user. <code>title</code>, <code>salary</code>, and <code>company</code> are required ,and <code>company</code> must match the posting company's <code>handle</code>. <code>equity</code> is optional. <code>salary</code> (and <code>equity</code> if provided) should be integers. Returns the new job in JSON with an <code>id</code> assigned.

```json
{
	"title": "___",
	"salary": "___",
	"equity": "___",
	"company": "___"
}
```

#### GET
Return a list of up to 50 jobs in JSON, or up to 50 jobs matching the search string, if a query is provided with a <code>search</code> parameter. Must be logged in.

## /jobs/{id}

#### GET
Return the job matching the provided <code>id</code>.

#### PATCH
Update the job matching the provided <code>id</code>. <code>id</code> cannot be updated. Must be logged in as company that posted the job initially.

#### DELETE
Delete the job matching the provided <code>id</code>. Must be logged in as company that posted the job initially.

## /jobs/{id}/applications

#### POST
Create an application for a job matching the provided <code>id</id>. Must be logged in as a user.

#### GET
If logged in as a user, returns a list of any applications the user has created for that job. If logged in as the company that posted the job, returns a list of any applications created for that job, by any user.

## /jobs/{id}/applications/{app_id}

#### GET
Return the job application matching the provided <code>app_id</code>.

#### PATCH
Update the job application matching the provided <code>app_id</code>. Must be logged in as company that posted the job initially, or as the user that posted the particular application.

#### DELETE
Delete the job application matching the provided <code>app_id</code>. Must be logged in as company that posted the job initially, or as the user that posted the particular application.


