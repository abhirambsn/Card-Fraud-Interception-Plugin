# Card Fraud Interception Plugin

## Problem:
Prevention of Credit and Debit card frauds and analyse the data obtained from the users. Most of the time fraud happens with credit and debit cards where authorized users carry their cards with themselves and transactions occur. So, in that case many problems arise to get the refund from the bank, one of the solution is to prevent these frauds, our solution helps to prevent these frauds.

## 1. Social Problem:
Whenever a bank fraud occurs, the victim encounters many social problem in the due course of getting the refund from the bank.
- FIR copy needed, but it becomes a hassle for the people to get one, since police officers don’t cooperate with the victims.
- Proper investigation Report from the Police, has to be submitted to the Bank, in order to receive the refund, which takes a lot of time.
- After receiving the report the banks take a lot of time to process the refund due to complex verification procedures.
- Still there is no guarantee if the user gets the refund.

## 2. Technical Problem:
How can card transactions take place without the card being stolen?
- Application Frauds: When the fraudster gains control of the application system by getting to delicate customer nuances like mystery state and username and open a fake record.
- Electronic or Manual Credit Card Imprints: When the fraudster skims information that is put on the alluring bit of the card.
CNP (Card Not Present): When the fraudster knows the expiry date and record number of the card, the card can be used without its certifiable physical having a place.
- Counterfeit Card Fraud: It is usually tried through the route toward skimming. A fake appealing swipe card is made and it holds all the nuances of the principal card. The fake card is totally valuable and can be used to submit trades in future.
- Lost and Stolen Card Fraud: In circumstances when the first card holder loses their card, it can get to the hands of fraudsters and they would then have the option to use it to make portions.


## Requirements:
For the banks to use our system, no additional hardware is required. The software, (which is the application the bank provides), needs to be modified in order to integrate our solution into their current system.

It will be an opt-in option for people with smartphones and good location access as users must have a location-enabled smartphone in order to take advantage of this system.

There are some non-functional requirements which are necessary to provide a seamless experience:
- The solution should allow several users to sign up and perform a variety of tasks simultaneously. 
- The proposed solution should be secure and no unauthorized access of data should take place in the system as it will defeat the purpose of the solution.
- The solution should be scalable i.e. Adding more users and products in the system should not cost too much. 
- The system should be quick to verify and confirm the transactions within a few seconds, as delayed transactions will reduce customer’s will to perform transactions.


## Implementation:
We can’t use a physical ATM or a POS Machine, so we are simulating that behavior in our website built with React.js.

Since every card holder uses the bank’s application for settling the debit/card card bills, we have implemented a feature that accesses the location of the registered device of the user at the start of a transaction (i.e when the user inserts the card into the ATM machine). 

If the location of the device lies within the radius of 5m of the location where the transaction is being carried out, then the transaction gets approved automatically.

In case the location does not lie within the above specified radius, but the transaction is authorized (for eg, you have given your card to your family member to carry out a transaction), then a notification is generated on the user’s registered device asking him/her to approve it, this notification will be valid for a time duration of 10 seconds. If the request is not approved within the specified time limit then the transaction gets canceled and if the user is unaware of the transaction then he/she is alerted to take further action. On the contrary if the user approved the transaction then the transaction can be carried out without any hurdles, in this way we have ensured that an unauthorized transaction does not take place in case of a location mismatch, but if an authorized transaction has to take place in the absence of the user then it can be processed.

We are using the Haversine Formula to calculate the distance between the device’s location and the ATMs location.

Haversine Formula determines the Great Circle Distance between two points on a sphere given their latitude and longitude, it is mainly used in navigation applications, the formula is given below:

<img src="https://user-images.githubusercontent.com/2789198/27240436-e9a459da-52d4-11e7-8f84-f96d0b312859.png" width="550">

