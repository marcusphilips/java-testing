## TEST CASE: ID 7

- Use Case: Users should be able to remove Moons from the Planetarium.
- Actors:
  - Existing User: Batman
  - New User: Robin

### Test Data

#### Test Requirements

1. Only logged in Users should be able to access the Planetarium home page. *given*
2. Users should only be able to interact with resources they have added to the Planetarium.
    - i.e. users should only be able to remove moons if they are removing the moons from planets they "own"

    |User|Moon Name|Moon Deletion|Alert|
    |-|-|-|-|
    |Batman|Luna|Moon deleted|No alert, table refresh|
    |Robin|Luna|No moon deleted|User alerted that they do not have ownership of moon's host planet|

3. Moons should be “owned” by the Planet the User adding the moon associated it with.
    - connects to the previous requirement


#### Acceptance Testing Data

Only pass if all [requirements](#test-requirements) met and all test cases in the [decision table](#decision-table-for-deleting-moons).

#### Environment Data

- Browser: Edge
- Operating System: Windows 10
- Version of Planetarium: 1.0
- Background Data:
  - Home Page for Planetarium: http://localhost:8080/planetarium
- Default database is initialized. New user "Robin" is created.

### Test Scenarios

#### Decision Table for deleting moons

|User|Moon Name|Moon Deleted|Alert|
|-|-|-|-|
|Batman|Luna|Moon deleted|No alert, table refresh|
|Batman|Pandora|No moon deleted|User alerted that no such moon exists|
|Robin|Luna|No moon deleted|User alerted that they do not have ownership of the moon's host planet|
|Robin|Pandora|No moon deleted|User alerted that no such moon exists|


### Parametrized Test Scanario

|Step|Actor|Data|Result|
|-|-|-|-|
|given that the user is on their homepage|existing user|http://localhost:8080/planetarium||
|when the user selects "Moon"|existing user|||
|when the user inputs a {moon name} in the "name for celestial body to be deleted" textbox|existing user|{moon name}||
|when the user selects the "Delete" button|existing user|||
|then the user should see the table refreshed with the moon removed|existing user||No alert, table refreshed|
