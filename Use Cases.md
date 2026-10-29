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

## Case 2: Donation Intake

## Case 3: Volunteer Distribution
### Description:
**User** requests for a food package, sending a *DeliveryRequest* to the **System**. **System** adds *DeliveryRequest* to *GigQueue*. **Volunteer** claims a *DeliveryRequest* from *GigQueue* to fufill.

## Case 4: Inventory Auditing
**System** checks *Inventory* and sees some stock below a certain threshold, sending a *InventoryReport* to **Facility Manager** 

## Case 5: Pantry Discovery
### Description: 
**User** is at *PantryDiscoveryScreen* and wants to locate a nearby food bank. **User** enters *LocationInfo*. The system searches for nearby food banks and retrieves pantry info  including adresses, operating hours, and current food inventory. The system displays a list of food banks to **User**. **User** then selects a food bank to veiw is avalible items. 

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
