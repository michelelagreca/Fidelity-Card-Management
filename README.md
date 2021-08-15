# Fidelity Card Management
The project uses MuleSoft technology and the Anypoint Platflorm development environment.
## Scenario
The scope of the project is a supermarket loyalty card management system.
## Existing system
An external system takes care of all the part of registering users and activating the cards, as well as the association between them.
Every day this system exports a massive CSV file that contains the list of users and the number of the associated card, as well as information on whether the card is active or not. This file is always placed in the same folder and always has the same name, so MuleSoft only needs to read it when it needs it, without worrying about anything else.
