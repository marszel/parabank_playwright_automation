# Test case Specification - ParaBank Automation

## TC_AUTH_01: User Registration
* **Description:**
Verify that a new customer can successfully create an account with valid data.
* **Preconditions:**
1. The ParaBank web application is available.
2. The username used for registration is unique and does not exist in the database.
* **Steps:**
1. Click on the "Register" link.
2. Enter all fields from the table.
3. Click "Register" button.

| Case ID | First Name | Last Name | Address | City | State | Zip Code | Phone | SSN | Username | Password | Confirm | Expected Result / Error Message |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| TC_AUTH_001 | `Katarzyna` | `Kowalska` | `Prosta 10` | `Warszawa` | `Mazowieckie` | `00-001` | `500100200` | `12345678901` | `kkowalska` | `Haslo123!` | `Haslo123!` | Welcome kkowalska. Your account was created successfully. You are now logged in. |
| TC_AUTH_002 | `` | `` | `` | `` | `` | `` | `` | `` | `` | `` | `` | First name is required. Last name is required. Address is required. City is required. State is required. Zip code is required. Social Security Number is required. Username is required. Password is required. Password confirmation is required. |
| TC_AUTH_003 | `Jan` | `Nowak` | `Krzywa 20` | `Warszawa` | `Mazowieckie` | `00-002` | `600200300` | `10987654321` | `jnowak` | `Haslo123!` | `Haslo123` | Passwords did not match. |
| TC_AUTH_004 | ` ` | ` ` | ` ` | ` ` | ` ` | ` ` | ` ` | ` ` | ` ` | ` ` | ` ` | Welcome  . Your account was created successfully. |
| TC_AUTH_005 | `John` | `Brown` | `Prosta 10` | `Warszawa` | `Mazowieckie` | `00-001` | `500100200` | `12345678901` | `john` | `Haslo123!` | `Haslo123!` | This username already exists. |
| TC_AUTH_006 | `123` | `123` | `123` | `123` | `123` | `abc` | `abc` | `abc` | `123` | `123` | `123` | Welcome 123. Your account was created successfully. |
| TC_AUTH_007 | `Ąęółżźćń` | `Ąęółżźćń` | `Ąęółżźćń` | `Ąęółżźćń` | `Ąęółżźćń` | `00-001` | `500100200` | `12345678901` | `Ąęółżźćń` | `Ąęółżźćń` | `Ąęółżźćń` | Welcome Ąęółżźćń. Your account was created successfully. |
| TC_AUTH_008 | `Jakub` | `Sowa` | `Prosta 10` | `Warszawa` | `Mazowieckie` | `00-0` | `50010` | `1234` | `jsowa` | `Haslo123!` | `Haslo123!` | Welcome jsowa. Your account was created successfully. |
| TC_AUTH_009 | `Zofia` | `Topola` | `Prosta 10` | `Warszawa` | `Mazowieckie` | `00-0` | `50010` | `1234` | `verylongusernameformestingpurposes1234567890verylong` | `Haslo123!` | `Haslo123!` | Welcome verylongusernameformestingpurposes1234567890verylong. Your account was created successfully. |
| TC_AUTH_010 | `Tomasz` | `Kapot` | `Prosta 10` | `Warszawa` | `Mazowieckie` | `00-0` | `50010` | `1234` | ` tkapot ` | `Haslo123!` | `Haslo123!` | Welcome  tkapot . Your account was created successfully. |
* **Expected Result:**
1. After Step 1, the link leads to the page https://parabank.parasoft.com/parabank/register.htm.
2. The application behavior matches the "Expected Result/Error Message".



