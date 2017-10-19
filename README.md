# simulation-api-specification
Repo for storing the specification for the 3DSIM simulation api.

## Technical Specifications

### Platforms Supported
MacOS, Windows, and Linux

## Writing specifications
We are following the swagger 2.0 specification.  Below are some resources to learn how to write swagger 2.0:

* http://swagger.io/specification
* https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md (source repo for link above)

To actually write the source, you can use any editor, but usually works best to use an online swagger 2.0 compliant editor such as:
http://editor.swagger.io

### Gotchas
If a date is nullable, annotate the field in the swagger spec with `x-nullable: true`.  See https://github.com/go-swagger/go-swagger/issues/746.

e.g.
```
completedAt:
  type: string
  format: date-time
  description: completed time stamp
  x-nullable: true
```

## Getting an Aurhorization Token for API Calls
In order to get an authorize token to access the API given a user name password, issue a POST request to the following URL:
```
http://<domain url>/oauth/ro
```

The header should include
```
content-type    application/json
```

And the body of the post should include the following json
```
{
  "client_id": "<Client Id>",
  "username": "<your username>",
  "password": "<your password>",
  "connection": "<connection>",
  "scope": "openid email user_metadata app_metadata picture"
}
```
Values in <> are either login information known to the caller or envrionment settings listed below.

### QA Settings
Domain URL: 3dsim-qa.auth0.com
Client ID: 6xrK3dpRFpnOytcVkN2QsX5iDwfXC7k3
Connection: end-users

### Production Settings
Domian URL: 3dsim.auth0.com
Client ID: OJ4kxgckhpEie9PLpWoAoLFPdCBPNAZA
Connection: product-users

### GovCloud Settings
Domain URL: 3dsim.auth0.com
Client ID: kPXdfrC7G2RJUh7hPsGqrdqHsHQc3AoV
Connection: product-gov-users

## Team
* Tim Sublette
* Ryan Walls
* Chad Queen
* Pete Krull
* Alex Drinkwater

## Original release
November 2016
