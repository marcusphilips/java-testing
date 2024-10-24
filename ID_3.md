## TEST CASE: ID 3

- Use Case: Users should be able to see planets and moons added to the Planetarium.
- Actors:
  - Existing User: Batman
  - Logged-out User

### Test Data

#### Test Requirements

1. Only logged in Users should be able to access the Planetarium home page.

    |User state|Result after accessing http://localhost:8080/planetarium|
    |-|-|
    |Logged out|the user alerted that they are not logged in and redirected to http://localhost:8080/|
    |Logged in|the user is shown their homepage is not redirected|

2. Planets and moons should have unique names.
3. Planets should be “owned” by the user that added it to the Planetarium.
4. Moons should be “owned” by the Planet the User adding the moon associated it with.
    - The Test Requirements 2-4 are not explicitly tested in the use case, but they are the properties of the table. They are tested in other use cases with addition and deletion operations.

#### Acceptance Testing Data

Only pass if all [requirements](#test-requirements) met while [error guess testing](#error-guess-testing-for-protecting-access) to ensure account protection. Data requirements are tested in other test cases.

#### Environment Data

- Browser: Edge
- Operating System: Windows 10
- Version of Planetarium: 1.0
- Background Data:
  - Home Page for Planetarium: http://localhost:8080/planetarium
- Default database is initialized. No other data has been inputted. Reset database between tests.

### Test Scenarios

#### Error Guess Testing for protecting access

When the logged out user accesses http://localhost:8080/planetarium, the user should be alerted that they are not signed in and should be redirected to the homepage.

### Parametized Test Scenarios

#### Positive Test

|Step|Actor|Data|Result|
|-|-|-|-|
|given that the existing user is logged in|logged-in user|http://localhost:8080/||
|the user directly accesses the planetarium page via the URL|logged-in user|http://localhost:8080/planetarium||
|then the user sees the homepage|logged-in user||User's homepage, no need to sign in|


#### Negative Test

|Step|Actor|Data|Result|
|-|-|-|-|
|given that the existing user is on the login page|logged-out user|http://localhost:8080/||
|the user directly accesses the planetarium page via the URL|logged-out user|http://localhost:8080/planetarium||
|then the user should be alerted they are not logined|logged-out user|-|{Refused entry}|
|then the user should be redirected to the login page|existing user|-|redirect to http://localhost:8080/|
