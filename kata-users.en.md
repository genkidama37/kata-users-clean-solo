# Users kata app

Based on the slides by [Jorge Sánchez (aka xurxodev)](https://xurxodev.com/).

## Overview
### Functional requirements
- Show list of users.
- Add a new user.
- A user must contain:
  - Name.
  - Email. 
  - Password. 
  as mandatory fields.
- The email must be a valid email. That means it:
 - Contains a username.
 - Contains a host name.
 - Contains the host's domain.
 - Has the username separated from the host name by an '@' character.
 - Has the host name separated from the host's domain by a period ('.').

- The password must:
 - Be at least 8 characters long.
 - Contain at least one letter.
 - Contain at least one number.

- The app should show an error if someone tries to add two users with the same email.

**Bonus**
- Add the address, made up of: 
 - Address
   - Street.
   - Number. 
   - [Optionally] floor and/or door.
 - Postal code.
 - City.
 as part of the information required for the user.
- Only one user per domain may exist (1 user with gmail.com, etc.).

### Development platform
- The UI will be a command-line or terminal app.
- All data in memory, with no persistence between runs.
- The data source may in the future be an API or a database.
- The UI may in the future change to a web app, mobile app, or desktop app.
- The business rules must be validated through unit tests.
- In the tests, dependencies will be replaced by manual fake dependencies.
- Equality tests for the value objects and entities must also be created.
- Use MVP for the presentation layer.
