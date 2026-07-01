# Kata Users Practice

For Spanish, see [README.es.md](README.es.md) 
### What it is and why
This repository is my deliberate practice of the Clean Architecture principles covered
in the **[Clean Architecture course by Jorge Sánchez](https://xurxodev.com/curso-clean-architecture/)**.
I'll do this through the exercise we worked on during the course: the [Users Kata](kata-users.en.md).

My intention in repeating the exercise on my own (in the course we did it in groups) is to internalize
the core principles of Clean Architecture, as well as to take on the challenge of solving the kata by
myself. In my particular case, it also includes the challenge of practicing writing tests based on the
exercise's specifications.

This repository contains a deliberate practice exercise. It is not the basis for a production app.
### Scope


To begin with, I'm going to focus on the first two parts of the kata: Entities and Use Cases.
#### Part 1 - Entities
- Define entities and value objects.
- The enterprise rules must be tested by creating unit tests.
  - Rules:
    - A user must have:
     - Name.
     - Email. 
     - Password 
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
  - Two instances of the same email must be equal.
  - Two instances of the same password must be equal when compared.
  - Two instances of user with the same id must be equal when compared.

**Bonus**
- Add the address, made up of:
  - Address
  - Street.
  - Number.
  - [Optionally] floor and/or door.
  - Postal code.
  - City.
 as part of the information required for the user.

#### Part 2 - Use cases
- Define the use cases and repository for:
  - Show list of users.
  - Add a new user.
- The application rules must be tested by creating unit tests.
- In the unit tests you may use manual fake objects.
- Rules:
    - The application must not allow adding two users with the same email.
**Bonus**
- Only one user per domain may exist (1 user with gmail.com, etc.)

#### N/A
- Deployment instructions.
- Using environment variables.
- Using a test library, whether my own or external.
- TypeScript: forcing generics/union types just to show them off.
- Using a linter.

### Architecture
#### Folder structure        
We'll group the folders by layers:
  - `domain` includes:
    - `entities`
    - `value-objects`
    - `core`: this is where the abstract classes live, the ones the base classes for entities and value objects inherit from. It contains the shared value-equality logic, along with its tests.
  - `use-cases`


Each layer will include its own `__tests__` folder.

```
── src
    ├── use-cases
    │   └── __tests__
    ├── domain
    │   ├── core
    │   │    └── __tests__
    │   ├── entities
    │   │    └── __tests__
    │   └── value-objects
    │        └── __tests__
```

#### Principles and design decisions

The Clean Architecture dependency rule applies: the domain does not depend on the outer layers.

The outer layers depend on the inner layers. And the domain sits in the innermost layer.


Value objects are favored to represent strings such as the name or the email, in order to avoid the code smell **Primitive Obsession**.

Validation must return all the errors made at once.

For the presentation layer, the [MVP pattern](https://learn.microsoft.com/en-us/archive/msdn-magazine/2006/august/design-patterns-model-view-presenter) will be implemented.
Conventions:
- `kebab-case` will be used both for directory names and file names. Reasons:
  - To try out this approach and see how it goes.
  - It improves the readability of multi-word folder names.
  - To avoid case-insensitivity problems. Day to day I use macOS, which is case-insensitive. Occasionally I use other machines running Linux, which are case-sensitive. And I want to be able to work on both systems without trouble.

### (later on) How to run and tests   ← skeleton, don't write yet
### Implementation details
- Use of TypeScript.
- npm as the package manager.
- Prettier as the code formatter.
