# Fidelity Card Management
The project uses MuleSoft technology and the Anypoint Platflorm development environment.
## Scenario
The scope of the project is a supermarket loyalty card management system.
## Existing system
An external system takes care of all the part of registering users and activating the cards, as well as the association between them.
Every day this system exports a massive CSV file that contains the list of users and the number of the associated card, as well as information on whether the card is active or not. This file is always placed in the same folder and always has the same name, so MuleSoft only needs to read it when it needs it, without worrying about anything else. [Here](https://github.com/michelelagreca/Fidelity-Card-Management/blob/main/user-card-association.csv) an example of the CSV file.
## Missing system
On the other hand, the system that deals with point management is missing. We therefore want to implement two fundamental APIs:
- Add points
- Remove points
These APIs will be called by the checkout systems of the stores. Customers are not required to carry the card with them, but can simply provide their social security number.
## API logic
- Validate the request: the points inserted have to be greater than 0 and the fiscal code must respect a regex typical of a tax code, otherwise return http 400 and a specific error message.
- If the validation goes well, read the CSV file to obtain the card number from the fiscal code inserted, as well as verify that the card is active. Manage the possibility of not finding a card, or that it is not active, with appropriate error messages.
- If all goes well, increase / decrease the points balance for that card, as well as record the datetime of the last operation performed. To store this data in a persistent way use "Object Store V2" by mulesoft (a DB would be better, but for educational purposes the object store will be fine).
## Extra API
Subsequently, the customer reports the need for an additional API: Card summary.
Errors should be handled in a similar way to the previous API:
- Formal validation of the fiscal code.
- Existence of an associated card.
