## TEST CASE: ID 4

- Use Case: Users should be able to add new Planets to the Planetarium.
- Actors:
  - Existing User: Batman

### Test Data

#### Test Requirements

1. Only logged in Users should be able to access the Planetarium home page. *Given*
2. Planets and moons should have unique names.

    |Planet Name|Planet Created|Action|
    |-|-|-|
    |Earth|No planet created|User is alerted that such planet already exists|
    |Earth 2|Planet created|Table of celestial bodies refreshes with "Earth 2"|

3. Planets should be “owned” by the user that added it to the Planetarium.
    - Under the owner column, all planets should show the username of the user that created it.

4. Planets and Moons should allow adding an associated image, but an image should not be required for the data to be added to the database.

    |Planet Name|Image Included|Action|
    |-|-|-|
    |Earth|No planet created|User is alerted that such planet already exists|
    |Earth 2|Planet created|Table of celestial bodies refreshes with "Earth 2"|


#### Acceptance Testing Data

Only pass if all [requirements](#test-requirements) met and all test cases in the [decision table](#decision-table-for-adding-planets).

#### Environment Data

- Browser: Edge
- Operating System: Windows 10
- Version of Planetarium: 1.0
- Background Data:
  - Home Page for Planetarium: http://localhost:8080/planetarium
- Default database is initialized. No other data has been inputted. Reset database between test cases.
- Valid image repository:
  - ...\Foundation Project\Celestial Images

### Test Scenarios

#### Decision Table for adding planets

|Planet Name|Image included|Planet Creation Result|Alert|
|-|-|-|-|
|Earth 2|Yes|New planet created|No alert, table refreshes|
|Earth 2|No|New planet created|No alert, table refreshes|
|Earth|Yes|No planet created|User alerted that planet already exists|
|Earth|No|No planet created|User alerted that planet already exists|

### Parametrized Test Scanario

|Step|Actor|Data|Result|
|-|-|-|-|
|given that the user is on their homepage|existing user|http://localhost:8080/planetarium||
|when the user selects "Planet"|existing user|-||
|when the user inputs a {planet name} in the "Enter Planet Name" textbox|existing user|{planet name}||
|(optional) when the user also inputs an {image}|existing user|optional {image}||
|when the user selects the "Submit Planet" button|existing user|||
|then the user should see the table refresh with their new planet with its {planet name} with the inputted {image} (if added) and their {username} along with an {ID}|existing user|{planet name}, *opt.* {image}, {username}, {ID}|Table refreshes with new planet|Table refreshes|
|then the user should see all other celestial bodies that have been previously added|existing user|||


