## TEST CASE: ID 2

- Use Case: Users should be able to securely access their account
- Actors:
  - Existing User: Batman
  - New Actor (no account made)

### Test Data

#### Test Requirements

1. Only logged in Users should be able to access the Planetarium home page

    |Username|Password|
    |-|-|
    |Batman|I am the night|
    |Batman|Incorrectpwd|
    |Robin|I am the night|
    |Robin|Incorrectpws|

2. Passwords should never be visible in plaintext.
    - Passwords should be obfuscated.
    - Done by Exploratory Testing and Error Guess Testing

#### Acceptance Testing Data

Only pass if all [requirements](#test-requirements) met and all test cases in the [decision table](#decision-table-for-logging-in).

#### Environment Data

- Browser: Edge
- Operating System: Windows 10
- Version of Planetarium: 1.0
- Background Data:
  - Login Page for Planetarium: http://localhost:8080/
- Default database is initialized. No other data has been inputted. Reset database between tests.

### Test Scenarios

#### Decision Table for logging in

|Username|Password|Account Login Result|Redirect|
|-|-|-|-|
|Batman|I am the night|valid credentials|User redirected to their homepage|
|Batman|Incorrectpwd|invalid credentials|User remains on the login page|
|Robin|I am the night|invalid credentials|User remains on the login page|
|Robin|Incorrectpwd|invalid credentials|User remains on the login page|

### Parametrized Test Scanarios

|Step|Actor|Data|Result|
|-|-|-|-|
|given that the existing user is on the login page|existing user|http://localhost:8080/||
|when the user provides a {username} and {password}|existing user|{username}, {password}||
|when the user selects the "Login" button|existing user|-||
|then the user should be redirected to the planetarium homepage|existing user|-|redirect to http://localhost:8080/planetarium|
