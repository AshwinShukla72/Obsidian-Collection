##### 1. Heavier Coin Problem ⇒ 8 coins, can only weigh 2 times

Split the coins in 3 coins twice, and 2 coins…
-   Weigh packs of 3, if one side is heavier discard the rest
    -   Further weigh any two coins of from the pack of 3 which was heavier
        -   if one of them is heavier you found the heavier coin
        -   if both weigh the same on scale, then the one left is the heavier one
-   If both packs of 3 weigh the same
    -   Discard the packs of 3 and weigh just the 2 left


##### 2. You are in a hallway lined with 100 lockers. You start with one pass and open the lockers so that, the opened lockers are now with their doors opened out. **You begin by closing every second locker. Then you go by closing every third locker and close it if it’s open or open it if it’s closed. Refer to this action as toggling**. You continue toggling every nth locker locker on pass number ‘n’, after your hundredth pass of the hallway, in which you toggle only locker number 100. How many locker are open?
Can’t Brute force this
So, let’s develop a recursive method for the problem.
Choosing a random locker number let’s choose 14 it will be toggled on the first phase.
On the 1st pass locker number 18 will be open
To start we know that we won’t have to check for all only passes between 2 - 17
- pass 2: We will close 2,4,6,8,10,12,14,16,18
- pass 3: We will close 3,9,15 and **Open 6,9,12,18**
- pass 4: 2,4,8,12,16 **Close 16 No toggle for 18**
- pass 5: 3,5,10,15 **No Toggle on this pass**
- pass 6: 4,6,12,18 **Close 6,12 and 18**
- pass 7: 7,14 **No Toggle on this pass for 18**
- pass 8: 8,16 **No Toggle on this pass for 18**
- pass 9: 9,18 **9 and 18 are closed**
- pass 10: 10
- pass 12: 12
- pass 13: 13
- pass 14: 14
.
.
- pass 17 **No Toggle**

So, going by this narrative we understand that if n is pass then the if the number is a perfect square then it will remain open, therefore ==1,4,9,16,25,36,49,64,81,100== will remain open… total is 10.