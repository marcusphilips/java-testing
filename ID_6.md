## TEST CASE: ID 6

- Use Case: Users should be able to add Moons to the Planetarium associated with a Planet.
- Actors:
  - Existing User: Batman
  - New User: Robin

### Test Data

#### Test Requirements

1. Only logged in Users should be able to access the Planetarium home page. *given*
2. Planets and moons should have unique names.

    |Moon Name| Moon Creation|Alert|
    |-|-|-|
    |Pandora|Moon created|No alert, table refreshes|
    |Luna|No moon created|User alerted moon already exists|

3. Moons should be “owned” by the Planet the User adding the moon associated it with.

    |Moon Name|Planet Id|Result|
    |-|-|-|
    |Pandora|1|Pandora Owner Column points to Earth (id: 1)|
    |Pandora|3|User is alerted that no planet of such id exists|

4. Planets and Moons should allow adding an associated image, but an image should not be required for the data to be added to the database.

    |Moon Name|Image Attached|Alert|
    |-|-|-|
    |Pandora|No|No alert, table refreshes|
    |Pandora|Yes|No alert, table refreshes|

5. Users should only be able to interact with resources they have added to the Planetarium.
    - i.e. the user cannot add moons to planets they do not have ownership.

    |User|Planet ID|Moon Creation|Result|
    |-|-|-|-|
    |Batman|1|Moon created|No alert, table refreshes|
    |Robin|1|No moon created|User alerted that they cannot interact with planets that they did not create|

#### Acceptance Testing Data

Only pass if all [requirements](#test-requirements) met and all test cases in the [decision table](#decision-table-for-adding-moons).

#### Environment Data

- Browser: Edge
- Operating System: Windows 10
- Version of Planetarium: 1.0
- Background Data:
  - Home Page for Planetarium: http://localhost:8080/planetarium
- Default database is initialized. New user "Robin" is created.
- Valid image repository:
  - ...\Foundation Project\Celestial Images

### Test Scenarios

#### Decision Table for adding moons

|User|Moon Name|Image Attached|Planet ID|Moon Created|Alert|
|-|-|-|-|-|-|
|Batman|Pandora|Yes|1|Moon created|No alert, table refreshes|
|Batman|Pandora|No|1|Moon created|No alert, table refreshes|
|Batman|Luna|Yes|1|No moon created|User alerted moon already exists|
|Batman|Luna|No|1|No moon created|User alerted moon already exists|
|Batman|Pandora|Yes|3|No moon created|User alerted no planet with such ID exists|
|Batman|Pandora|No|3|No moon created|User alerted no planet with such ID exists|
|Robin|Pandora|Yes|1|No moon created|User alerted that they cannot add moon to a planet not under their ownership|
|Robin|Pandora|No|1|No moon created|User alerted that they cannot add moon to a planet not under their ownership|
|Robin|Luna|Yes|1|No moon created|User alerted moon already exists|
|Robin|Luna|No|1|No moon created|User alerted moon already exists|
|Batman|Luna|Yes|3|No moon created|User alerted moon already exists|
|Batman|Luna|No|3|No moon created|User alerted moon already exists|

### Parametrized Test Scanario

|Step|Actor|Data|Result|
|-|-|-|-|
|given that the user is on their homepage|existing user|http://localhost:8080/planetarium||
|when the user selects "Moon"|existing user|||
|the user inputs a valid {moon name} in the "Enter Moon Name" textbox and inputs a valid {planet ID} in the "Enter Orbited Planet Id" textbox, optionally adding an {image}|existing user|{moon name}, {planet ID}, {image}||
|when the user selects the "Submit Moon" button|existing user|||
|then the user should see the table refresh with new moon|existing user||table refresh, new moon entry added to table|
