## Outline

-Command Line Interface
-Take master password, validate and show/save entries
- Automatically copy password to clipboard 

## Implementation

## Configure
-MASTER PASSWORD is first inputted while configuring, and the hash of it is saved in a file
- DEVICE SECRET is generated randomly, also stored in a file which is a SALT to give strength to the Cryptographic key
Master Key

-MASTER PASSWORD + DEVICE SECRET is passed into to a hashing function (pbkdf) to create a valid key for AES-256. This is called
-The Master Key is then used to encrypt/decrypt new entries
-Encrypted fields: email, username, password 
- Plain fields: sitename, url

## Add new entries

- Ask for MASTER PASSWORD
- Validate MASTER PASSWORD by hashing and checking with existing hash 
-Make hash (DEVICE SECRET+ MASTER PASSWORD) = Master Key
Input fields of the entry site name, site url, email, username, password 
-Encrypt email, username and password with MASTER KEY and save the fields into the database

## Get entry

-Input the field to search for. Like site name, site url, email, username
-Display all the entries that match the search. Password hidden by default.
-If user chooses to get the password (with -c flag), then 
- Ask for MASTER PASSWORD

-Validate MASTER PASSWORD by hashing and checking with existing hash
-Make hash (DEVICE SECRET+ MASTER PASSWORD) = Master Key
-Decrypt the password and copy to the clipboard

