
### Users should be able to open a new User account with the Planetarium.

Account creation is bare bones and not intuitive. The "Create an Account" button is small, and there is no button to return to the login page in the account creation page. When creating an account, no requirements are listed for the user to follow which is important as there is a 30-character limit. The use of a browser alert for account creation feels old-school. There are little background graphics.

### Users should be able to securely access their account.

While functional, there are a few quirks to logging in like how the username is case-sensitive which is not the standard. There is no email address connected to the account which means if you lost your password; you would have to contact the hoster and try to prove your identity. While functional, it does not give much confidence. There is also no way to change the password.

### Users should be able to see planets and moons added to the Planetarium.

The planetarium is functional and straightforward but lacks sophistication and quality of life features. It's visible as soon as one logs in. It is strange for the "Owner" of a planet to be listed by their user ID which is an internal primary key for the users. It would be better if it was their username. It would also be better if moons of a planet were listed right below the planet. There does not appear to be any limits for what one can name their planets other than having to be unique meaning you can name a planet `!@#$%^&*()`, and it works just fine.
Also users cannot see planets not they have no ownership although they can see all moons. The table itself does not scale when changing the size of the window.

### Users should be able to add new Planets to the Planetarium.
Adding planets is straightforward is functional. However, it does not work unless an image is attached. I suspect it's a client-side issue because there is no alert or change in the database when trying to submit without an image. While names have to be unique, it's case sensitive which could cause confusion.

### Users should be able to remove Planets from the Planetarium.

For whatever reason, a user cannot delete planets they have not created in their session if they have ownership. Deleting planets should be more straightforward like the textbox should "auto-fill" names of valid planets or include an additional drop-down menu.

### Users should be able to add Moons to the Planetarium associated with a Planet.

When you login, the selector is set to moon but you cannot add moons. You have to change it planet then back to moon. Moon creation works so long as you attach an image. However, any user can attach moons to any planets regardless of ownership, so this feature is also incomplete. Similar to planetary creation, adding names is case sensitive so you can have "luna" and "Luna".

### Users should be able to remove Moons from the Planetarium.

Moon deletion has the opposite problem of planetary deletion, where any user can delete moons regardless of ownership. It has the similar issues to planetary deletion in that retrospect. The deletion textbox does not adjust the temporary text to what type of celestial body the user is deleting and just defaults to `name for celestial body to be deleted`.
