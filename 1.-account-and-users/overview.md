# 1. Account and Users

Account
=======
An **Account** is created when you sign up with Copper. **Users** that you invite will all be members of this Account. In Copper, customer organizations are called "Companies."

**Account Properties**

| Field |  Type  |              Details               |
| ----- | ------ | ---------------------------------- |
| id    | number | Unique* identifier for the Account |
| name  | string | Name of the account                |

**User Properties**

| Field |  Type  |             Details             |
| ----- | ------ | ------------------------------- |
| id    | number | Unique* identifier for the User |
| name  | string | The User's full name            |
| email | string | The User's email address        |

*A note on ids: Unique identifiers are unique within the scope of a single resource type. For example, a given identifier for a Lead will never be assigned to a different Lead, but a different resource such as a Person could use the same identifier.*
