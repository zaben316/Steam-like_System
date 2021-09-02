# Features

**TODO: Add features of the program**



 - We did not implement any working extra features such as a GUI. We did
   try and there are called Login and AdminGUI.
  - We used one desing pattern and it is MVC. Our backend , composed of Data and Transaction manipulate data. Being said a GUI could be
   easily added to our view because of how we used the MVC pattern

## How to use our system
Our system uses two databases, Database.txt and UserLogins.txt, they can be found in the Backend folder. Database keeps track of the the auctionSale , if it either on or off; If the file is empty, when the system startups, it will automatically write to it and set it to off. The UserLogins keeps track of all the users in the system, and their inventories , with all their attributes type etc...

Our system can be turned on from running StartShop.java; This will start the system, create all the objects that were inputted in the UserLogins.txt.

## Format for Database.txt
Database.txt can either be empty, or have the following format:

 - AuctionSale:"STATUS"
 
1. Where "STATUS" is either the string ON or OFF.
2. If the status is ON, the auction will be turned on immediately when the system is booted, if the status is OFF, it will be turned off, the all the games will be listed with their original price
3. If the file does not exist with the specified name and location in the  Backend folder, the system will automatically exit and print a Fatal Error.

## Format for UserLogins.txt
UserLogins.txt contains all the users in the system. We have inputted an initial admin named "admin", and you can either use him or delete him at your discretion. If an invalid input is detected, the system will exit and print a fatal error. An invalid input can either be an empty line or a badly formatted line that does not respect the format.

Our format is of the following regex pattern:

XXXXXXXXXXXXXXX,TT,DDDDDD.DD,GAMESELLING|GAMEOWN|

 1. The first 15 characters represent a name and can be anything, but as per the Piazza post @688, "You can also assume a username will not end in a whitespace character", and "we're gonna go with no whitespace starting names". So a name must either end with a character or start with a character. Unused fields will be padded with whitespaces.
 
 2. The TT represents the type of user, it can either be AA for admin, BS for buyer, FS for standard user or SS for seller.
 
 3. The DDDDDD.DD represents, the credit that user has in his account. Unused numbers will be filled with 0. For example if you want a user to have 20$, you would input 000020.00 in his credit.
 
-The final entries are the games that user owns or is selling. Each game will be separated by a |, and will following the following formats:
## Format for a GAMEOWN
A GAMEOWN represents a game that the user owns, and is not currently selling.
It follows the given format:
XXXXXXXXXXXXXXXXXXXXXXXXX:DDD.DD:NFS|
 4. The first 25 characters is the game name, it follows the same rules as the username format in the UserLogins.
 5. The DDD.DD represents the price that game was bought for, and follows the same format expect for amount of digits, as the credit in a UserLogins input.
 6. The NFS is short for "not for sale" and states that this game is not for sale.
## Format for a GAMESALE
A GAMEOWN represents a game that the user is selling.
It follows the given format:
XXXXXXXXXXXXXXXXXXXXXXXXX:DDD.DD:DD.DD:FS|

-The format is almost the same as GAMEOWN, but it has two crucial differences.

 1. First, we have an extra digit entry with only 2 spaces allowed and 2 decimals; this represents the discount percent that will be applied when an auction-sale is turned on. This input cannot exceed 90.00, or it wont be able to go on sale when auction is enabled.
 2. Second, instead of NFS, we have FS, which represents "for sale", this is the attribute that lets us keep track of a game being able to be bought on any given day.

## Extra clarifications for UserLogins.txt

 - one user is allowed per line
 - a user can have no games, his game section will be empty but a comma will follow his credit
 - A user such as a Admin and Standard can have both types of games in their inventory, but Buyers can only have GAMEOWNs and Sellers can only have GAMESALEs
 - All the length specifications must be followed; you can use the regex pattern that can be found in Data.java and verify your input before adding it to UserLogins.txt
 - As mentioned before, every game in an inventory will separated by a |, as specified in the format; even if theres one game, it should end with a |.

## Clarifications for the system

 - Inputs in daily.txt are verified via a regex pattern and must follow all requirements in README, if they don't, the system will exit
 - Some functions are not JUnit tested because they were previously tested in another JUnit class, please refer to all JUnit tests (Approved by a TA).
 - When a game is put up for sale, it is written in the UserLogins.txt as FS, but it will only have that status the next time the system runs again. 
 - A fatal error will only occur if files are not found, or there is an invalid input in daily.txt or UserLogins.txt, a message will be printed letting you what happened.
 - If any of these patterns or databases are not clear please refer to the regex patterns in the classes; they might help you better understand (sorry if we were not clear enough)
 - When you run StartShop.java, it will first create all the user objects and add them to a userList we created in Transaction.java, then it will check Database.txt and see if an auction-sale should be on, and finally it will loop through daily.txt and process all the transactions.
