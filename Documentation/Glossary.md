# Glossary
## Actors
### User:
Non-specific **User** of the system.
### Volunteer:
**User** who operates food bank. Extends **User**.
### Facility Manager
Manages Food Bank. Responsible for inventory. Extends **User**
## Data
### LoginInfo
**Data** used to authenticate **User**
### DistributionRecord
**Data** of incoming or outgoing *Inventory*
## Components
### LoginScreen
Screen(or Page) shown when **User** needs to perform initial authentication.
### HomeScreen
Screen(or Page) shown after **User** performs initial authentication.
### Authenticator
**Component** used to perform authentication.
### Validator(Maybe?)
**Component** used to perform validation.
## Data Storage
### Inventory
**Database** containing the records of current *Inventory*
### Distribution 
**Database** containing records incoming and outgoing(includes loss) *Inventory* 
