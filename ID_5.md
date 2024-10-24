## TEST CASE: ID 5

- Use Case: Users should be able to remove Planets from the Planetarium.
- Actors:
  - Existing User: Batman
  - New user: Robin

### Test Data

#### Test Requirements

1. Only logged in Users should be able to access the Planetarium home page. *given*
    - A seperate user will need to be created "robin"
2. Users should only be able to interact with resources they have added to the Planetarium.

|User|Planet Name|Planet Deletion Request|Alert|
|-|-|-|-|
|Batman|Earth|Planet Deleted|No alert, table refreshes|
|Robin|Earth|No Planet Deleted|User should be alerted that they do not own the planet|

#### Acceptance Testing Data

Only pass if all [requirements](#test-requirements) met and all test cases in the [decision table](#decision-table-for-deleting-planets).

#### Environment Data

- Browser: Edge
- Operating System: Windows 10
- Version of Planetarium: 1.0
- Background Data:
  - Home Page for Planetarium: http://localhost:8080/planetarium
- Default database is initialized. New user "Robin" is created.

### Test Scenarios

#### Decision Table for deleting planets

Any deleted planets should remove any "orbiting" moons. There should be no "orphan" moons as then they would not qualify as moons.

|User|Planet Name|Planet Deletion Request|Alert|
|-|-|-|-|
|Batman|Earth|Planet deleted|No alert, table refreshes|
|Batman|Jupiter|No Planet deleted|User alerted that no planet exists|
|Robin|Earth|No Planet deleted|User alerted that they do not own planet|
|Robin|Jupiter|No Planet deleted|User alerted that no planet exists|

### Parametrized Test Scanario

|Step|Actor|Data|Result|
|-|-|-|-|
|when given that the user is on their homepage|existing user|http://localhost:8080/planetarium||
|when the user selects "Planet"|existing user|||
|when the user inputs a valid {planet name} in the "name for celestial body to be deleted" textbox|existing user|{planet name}||
|when the user selects the "Delete" button|existing user||Table refreshes|
|then the user should see the table refreshed with the planet and any of its orbiting moons removed|existing user||Planet {planet name} is removed from table|



