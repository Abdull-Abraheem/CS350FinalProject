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

## Case 2: Donation Intake

## Case 3: Volunteer Distribution
### Description:
**User** requests for a food package, sending a *DeliveryRequest* to the **System**. **System** adds *DeliveryRequest* to *GigQueue*. **Volunteer** claims a *DeliveryRequest* from *GigQueue* to fufill.

## Case 4: Inventory Auditing

## Case 5: Pantry Discovery
### Description: 
**User** is at *PantryDiscoveryScreen* and wants to locate a nearby food bank. **User** enters *LocationInfo*. The system searches for nearby food banks and retrieves pantry info  including adresses, operating hours, and current food inventory. The system displays a list of food banks to **User**. **User** then selects a food bank to veiw is avalible items. 
