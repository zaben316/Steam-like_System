
  ## Clarifications we found out on Piazza
  Additional transactions that must be included with your system. The following transactions need to be implemented:
    
removeGame - remove a game from a user's inventory or from being sold
    

1.  The front end will prompt for the game name and if necessary, the game's owner.
    
2.  This information is saved to the daily transaction file
    
3.  Constraints:
    

1.  semi-privileged transaction - Non-admins can only remove their own games. In admin mode, this allows any game to be removed from any user.
    
2.  game can be in the owner's inventory OR one of those the user has put up for sale
    
3.  cannot remove a game that was purchased or put up to sale on the same day
    

  Gift - give a user a game from another user
    

1.  The front end will prompt for the game name, the game's receiver, and if necessary, the game's owner.
    
2.  This information is saved to the daily transaction file
    
3.  Constraints:
    

1.  semi-privileged transaction - Non-admins can only gift their own games to another. In admin mode, this allows any game to be gifted from any user to any other.
    
2.  game must be in the owner's inventory OR one of those the user has put up for sale
    
3.  if the game is one the owner had purchased, it is removed from their inventory when gifted
    
4.  cannot gift a game that was purchased or put up to sale on the same day
    
5.  cannot gift a game to a user who already owns a game with the same name
    

 Lines in the daily transaction file appear like the following:
    

1.  XX IIIIIIIIIIIIIIIIIII UUUUUUUUUUUUUUU SSSSSSSSSSSSSSS
    
 Where:
    

-  XX is a two-digit transaction code: 08-removegame, 09-gift.
    
-  IIIIIIIIIIIIIIIIIII is the game name
    
- UUUUUUUUUUUUUUU is the owner's username
    
-  SSSSSSSSSSSSSSSS is the receiver's username
    

 
    
-  "AAA" and "aaa" are different names
    
10.  a name can contain numbers
    
11.  name rules of users apply to game names too
    
12.  a buyer cannot buy a game he has already bought
    
13.  admin doesn’t need to check if the buyer actually bought any game from the seller before processing a refund?
    
14.  we assume that the max allowed credit can also be a decimal/float of 999,999.99
    
15.  you can have two sellers selling similar games
    
16.  Admin can do any transactions, including buy/sell
    
17.  If you have 999999.99 in your balance and sell a game, your balance stays unchanged
    
18.  Admins never buy back the games from the user?
    
19.  Multiple admins can have the same game, and the price of the game doesn't have to be the same.
    
20.  A sell transaction introduces a new game
    
21.  Let's say I buy a game from a full-Standard user for price X, now this user goes and buys some more games and has a new balance of Y, now when I request for a refund of X but X > Y. Do i transfer the difference and send an error prompt or don't transfer any funds and send an error prompt or transfer X amount and set a negative balance for the full-Standard user? Yes & not necessarily
    
22.  If no admin is present than no refunds can be processed
    
23.  Admins cannot delete their own accounts.
    
24.  Admin can refund themselves.
    
25.  auction sale transaction code - 07
    
26.  a Seller has unlimited copies of games in their inventory
    
27.  An admin cannot put a game up for sale for some other user
    
28.  Sellers can't receive gifts
    
29.  an auction sale can last days (until an admin specifically turns it off)
    
30.  As soon as the auction-sale is enabled, all sales (even those in the same session) should be affected
    
31.  Discount is always percent off
    
32.  If a user buys Game A for 50$ and then later on the day, the auction sale goes on. The buy transaction from the user does not get affected by the auction sale
    
33.  Standard user cannot buy from himself
    
34.  Game does not need to be given back to seller for refund
    
   
 
