# ng-leaderboard-subs
Mutliple subscriptions with ng-angular http://ng-leaderboard-subs.meteor.com/

so what is in here? 
I am showing how meteor (and angular) is handling multiple subscriptions to the same collection. 

If you check the server DB (your mongo instance) - the players collection has 9 documents.  score is generated randomly on first creation. 

The "top players" subscription brings the top 2 players by score. 
The "first players" subscription brings the first 3 players by name (alphabetically). 

You can start and stop the subscriptions dynamically. at any point you may check the client lcoal database by placing on the console: 
```
console.table(Players.find().fetch())
```

Your local DB should have 0 documents if both subscriptions are inactive, and between 3 and 5 documents if both subscriptions are active (2 if both subscriptions fully overlap, 5 if totally not overlap). 

When you will stop the top subscription you will be left with 3 documents. 
You will still see 2 players in the list but they will be the top 2 by scores from the first 3 alphabetically sort (Einstein, Gauss, Shannon).

Stopping the buttom subscription will leave you with 2 records (only one subscription is active and it returns 2 documents). Both documents will be shown at the top and bottom, but sorted accordingly (score, name).  

This explains how to use subscriptions to get only part of the data to your client. 
