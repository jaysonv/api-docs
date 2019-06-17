# Kreezalid REST API v1 Documentation

**Api endpoint**: `/api/v1/`

Adding the version number in the URL ensures smooth transition to future version (i.e being able to offer multiple API endpoints simultaneously).

## Authentication

First, you need to generate a secret key to authenticate when you make an API call.

To generate this secret key, go to your admin panel -> Settings -> Account.

In the API access section, you have a "Generate secret key" button.

For authentication, we use the Basic Auth authorization type that requires a username and password to access a data resource.

## Sections

- [User management](api-users.md)
- [Listing management](api-listings.md)
- [Order management](api-orders.md)