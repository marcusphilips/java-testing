# Cycle 1 Test Summary

## Use Case Defects

- ### ID 1: Users should be able to open a new User account with the Planetarium

    All tests failed because password was exposed in plaintext in the alert.

    Positive test cases, i.e. successful account creation, did not redirect to login page as specified in acceptance criteria.

    Test cases with empty usernames and/or passwords could not create account. Though listed as a bug, it might make more sense as a feature.

- ### ID 2: Users should be able to securely access their account

    All test cases passed.

- ### ID 3: Users should be able to see planets and moons added to the Planetarium

    User cannot see planets they do not own. However, they can see all the moons regardless of ownership.

    Ownership is by Planet ID for moons and User ID for planets which does not make sense as users do not implicitly know their user ID. It would be better to have planet ownership listed as the username and moon ownership as the planet's name.

- ### ID 4: Users should be able to add new Planets to the Planetarium

    User could not add planets without attaching an image. Clicking submit would do nothing. Perhaps rethink the software requirement: "Planets and Moons should allow adding an associated image, but an image should not be required for the data to be added to the database."

    Important to make all planets visible as stated earlier because a new user needs to make sure they are not adding a planet that already exists.

- ### ID 5: Users should be able to remove Planets from the Planetarium

    Predefined user, Batman, cannot delete any planets in the original dataset but can correctly delete newly created planets. This points to some database or environment-setup issue.
  - additionally could not test if oriting moon was removed along with planet

- ### ID 6: Users should be able to add Moons to the Planetarium associated with a Planet

    Ditto for the issue associated with needing to attach image for adding celestial body.

    User could add moons to planets they do not own in violation of ownership.

- ### ID 7: Users should be able to remove Moons from the Planetarium

    User could remove moon regardless of ownership.

### Acceptance Criteria

  Except for [logging in](#id-2-users-should-be-able-to-securely-access-their-account), no use case had all passing acceptance criteria.
