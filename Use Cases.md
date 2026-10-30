# Use Cases
These are the typical **Use Cases** of our program

## Case 1: Log in
### Actor:
**User**
### Description: 
**User** is at *LoginScreen* and has not logged in. **User** enters *LoginInfo* into forms. *LoginInfo* is authenticated by system.
If authenticated, **User** is brought to *HomeScreen*.
### Trigger:
**User** accesses *LoginScreen*.
### Precondition 1:
**User** is at *LoginScreen*.
### Precondition 2:
**User** has not logged in.
## Case 1: Main Success Path
### Description:
This scenario describes the situation where the **User** only needs to login.
### Steps:
1. **User** Arrives at *LoginScreen*.
2. **User** enters *LoginInfo* into forms.
3. system authenticates *LoginInfo*.
4. **User** is brought to *HomeScreen*.
### Termination:
**User** successfully logs in.
## Case 1: Alternative Flow 3A
### Description:
This scenario describes the situation where *LoginInfo* is not authenticated and **User** attempts to continue.
### Steps:
1. system fails to authenticate *LoginInfo*.
2. system informs **User** of the failure to authenticate.
3. **User** reenters *LoginInfo* into forms.
4. system authenticates *LoginInfo*.
5. **User** is brought to *HomeScreen*.
### Termination:
**User** successfully logs in.

## Case 2: Donation Intake

## Case 3: Volunteer Distribution
### Description:
**User** requests for a food package, sending a *DeliveryRequest* to the **System**. **System** adds *DeliveryRequest* to *GigQueue*. **Volunteer** claims a *DeliveryRequest* from *GigQueue* to fufill.

## Case 4: Inventory Auditing
**System** checks *Inventory* and sees some stock below a certain threshold, sending a *InventoryReport* to **Facility Manager** 

## Case 5: Pantry Discovery
### Description:
**User** is at *PantryDiscoveryScreen* and wants to locate a nearby food bank. **User** enters *LocationInfo*. The system searches for nearby food banks and retrieves pantry info  including adresses, operating hours, and current food inventory. The system displays a list of food banks to **User**. **User** then selects a food bank to veiw is avalible items.
### Actor: 
**Local Resident / Food Assistance Client**
### Preconditions
1. The Food Bank and Inventory are operational 
2. Food banks have registered their locations, hours of operation, and an avalible services in the system
3. User provides a location  
4. Inventory information is avalable for food banks that report their stock
### Happy Path
1. The user oprns the system and navigates to  PantryDiscoveryScreen.
2. The user enters their *LocationInfo* 
3. The system searches for nearby resistered food banks
4. The system retrieves *PantryInfo*.
5. The system displays a list of nearby food bank to the user
6. The user selects a food bank  to view its details and available food items  
7.  The user identifies an item they need  and checks wether the selected food bank offers delivery
8. If deliverary is avalivle and the user wishes to request it, the user submits a FoodRequest
9. THe system records the request and adds it to the queue
10. The system displays a confirmation message
### Alternative FLows
* A1 Location Unavalible
* A2 No nearby food bank
* A3 inventory  Unavailable:
* A4 Item out of stock
* A5 Delivery unavalible
* A6 user cancels
* A7 System Error
### Postconditions
**Succcess** 
1. the user has viewed a list of nearby food banks and their information  is avalible
2. The user can identify a food bank that meets their needs
3. The sytem stores the *FoodRequest* and adds it to the volunteer delivery queue
4. The system confirms succsesfull request submission to the user
**Failure**
1. If the search fails the system will inform that the requested information cannot be retrieved
2. the user cancels or cancels or cannot complete a delivery request, no new request is created
3. Existing food bank inventory records remain unchanged by the discovery process

## Case 6: Register Pantry
### Actor:
**Facility Manager**
### Description:
**Facility Manager** adds their pantry to the system by entering *PantryInfo* (name, address, operating hours, and whether volunteer delivery is offered). **System** saves the *Pantry* so it can appear in Pantry Discovery. **Facility Manager** can later update the hours or delivery option.
### Related Use Cases:
Pantry Discovery depends on pantries registered here.

## Case 7: Create Account
### Actor:
**Resident**, **Volunteer**, **Facility Manager**
### Description:
A new **User** enters *AccountInfo* and chooses a role. **System** checks that the account does not already exist, saves the *UserAccount*, and the **User** can now log in. A **Resident** only needs an account to request a delivery; searching for pantries does not require one. A **Volunteer** also enters their availability and delivery area.
### Related Use Cases:
Log in uses accounts created here.
