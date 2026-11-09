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
## Case 1: Alternative Flow 3B
### Description:
This scenario describes the situation where *LoginInfo* is not authenticated and **User** does not attempt to continue.
### Steps:
1. system fails to authenticate *LoginInfo*.
2. system informs **User** of the failure to authenticate.
3. **User** closes/leaves *LoginScreen*.
### Termination:
**User** closes/leaves *LoginScreen*.

## Case 2: Donation Intake

### Actor(s):
**Volunteer**

### Description
**Volunteer** access the System using a form, sending a *PantryInfo* to the System.
The System stores the *Pantry Info* information to the food bank's *Inventory*, System also Check the good if need to transfer over to other pantries.
*System* update the information.

### Pre-Condtion(s):
- Food Bank recives donations

### Post_Condtion(s):
- 

### Main Success Path:
1. **Volunteer** access the System using a form

2. Using said form, **Volunteer** adjusts the quantities of incoming donations and logs expiration dates

3. **Volunter** submits adjusted data as *Pantry Info*, sending it to the System

4. System saves and stores the *Pantry Info* infomation into the food banks *Inventory*

5. System checks neighboring distribution center to check if goods from donation should be transfered to other pantries
   
6. System dectects no transfer is required to other food pantries

### Termination:
Donation has now been fully logged and updates into food banks inventory

### Alternative Path 6A
- 6A1. System dectects that a neighboring distribution center needs recived goods from donation
- 6A2. System informs **Volunteer** of required transfer to other food pantry
- 6A3. **Volunteer** sets aside required goods that will be transfered to other food pantry 
- 6A4. **Volunteer** informs System that required goods have been set aside for transfer

### Termination:
System will see that food pantry that required a transfer of goods, no longer requires transfer of goods

## Case 3: Volunteer Distribution
### Description:
### Preconditions:
Venue offers a delivery service.
User was signed in and filled out form for a delivery.

### Trigger
User submits a request for a food package through the client interface 

### Main Success Scenario (Happy Path)
1. **User** requests a food package with specific dietary preferences or drop-off notes.

2. System validates the request, creating a *DeliveryRequest* that is pending

3. System adds the DeliveryRequest to the *GigQueue*.

4. **Volunteer** opens the dashboard and views deliveries in the *GigQueue*.

5. **Volunteer** selects and claims a specific *DeliveryRequest*.

6. System locks the request and updates its status to assigned.

7. **Volunteer** delivers the package, marking *DeliveryRequest* as complete.

Alt path 5a. If two volunteers attempt to claim the same request simultaneously, the System grants it to the first, or whoever wins the race.

### Case 3a
1. *DeliveryRequest* has remained unclaimed for x amount of time
2. System increases priority for *DeliveryRequest*
3. After y amount of time, *DeliveryRequest* is cancelled and notified to **User**


## Case 4: Inventory Auditing
Precondition(s):
Facility opted to use this aspect
Inventory was recorded

Trigger:
Should be occurring on some time interval or manually requested.

1. System checks *Inventory* every X
2. When certain attributes of *Inventory* are below a threshold, they are marked
3. System sends *InventoryReport* to **Facility Manager**

## Case 5: Pantry Discovery
### Description:
**User** is at *PantryDiscoveryScreen* and wants to locate a nearby food bank. **User** enters *LocationInfo*. The system searches for nearby food banks and retrieves pantry info, including address, operating hours, and current food inventory. The system displays a list of food banks to **User**. **User** then selects a food bank to view available items.
### Actor: 
**Local Resident / Food Assistance Client**
### Preconditions
1. The Food Bank and Inventory are operational 
2. Food banks have registered their locations, hours of operation, and available services in the system
3. User provides a location  
4. Inventory information is available for food banks that report their stock
### Happy Path
1. The user opens the system and navigates to  PantryDiscoveryScreen.
2. The user enters their *LocationInfo* 
3. The system searches for nearby registered food banks
4. The system retrieves *PantryInfo*.
5. The system displays a list of nearby food banks to the user
6. The user selects a food bank  to view its details and available food items  
7.  The user identifies an item they need  and checks whether the selected food bank offers delivery
8. If delivery is available and the user wishes to request it, the user submits a FoodRequest
9. The system records the request and adds it to the queue
10. The system displays a confirmation message
    
### Alternative Flows
* A1 Location Unavailable
 Description: The User does not provide a location, or the system cannot recognize a valid location.
  1. The **User** submits their *LocationInfo*
  2. The System cannot validate their location
  3. The System displays an error message and requests their valid location information
  4. The **User** enters a corrected location or leaves the search

* A2 No nearby food bank: No registered food banks are found within the specified area
  1. The System searches for nearby registered banks
  2. The System determines that no matching food banks were found.
  3. The System notifies the user that there are no nearby banks
  4. The System offers to expand the search area
     
* A3 inventory  Unavailable:
  1. The System retrieves the pantry's *PantryInfo*
  2. The System fails to retrieve its current inventory
  3. The System displays the pantry's available information
  4. The System informs **User** that inventory information is not currently avalable
  5. The User may contact the pantry directly or select another bank
     
* A4 Item out of stock
 1. The **User** selects an item from the pantry's inventory
 2. The System checks the item's current stock
 3. The System determines that the item is out of stock
 4. The System informs the **User** that the item is out of stock
 5. The **User** selects another item or another pantry
 
* A5 Delivery Unavailable
 1. The **User** selects an item from the pantry's inventory
 2.  The System determines that delivery is unavailable
 3.  The System informs the **User** that the pantry 
 4.  The System informs the **User** that the item is unavailable
 5.  The **User** selects another item or another pantry
    
* A6 User cancels
 1. The **User**  begins sumbmiting a food request
 2. The **User** cancels before finishing the submission 
 3. The System discards the incomplete request
 4. The System returns the **User** to the pantry details screen
    
* A7 System Error
 1. The System encounters an error
 2. The System displays an error message
 3. The System records the error
 4. The System allows the user to retry the operation
    
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
**Facility Manager** adds their pantry to the system by entering *PantryInfo* (name, address, operating hours, and whether volunteer delivery is offered). System saves the *Pantry* so it can appear in Pantry Discovery. **Facility Manager** can later update the hours or delivery option.
### Related Use Cases:
Pantry Discovery depends on pantries registered here.


> ## Case 7: Create Account - Depreciated
> ### Actor:
> **Resident**, **Volunteer**, **Facility Manager**
> ### Description:
> A new **User** enters *AccountInfo* and chooses a role. System checks that the account does not already exist, saves the *UserAccount*, and the **User** can now log in. A **Resident** only needs an account to request a delivery; searching for pantries does not require one. A **Volunteer** also enters their availability and delivery area.
> ### Related Use Cases:
> Log in uses accounts created here.

## Case 7: Registration
### Actor:
**User**
### Description: 
**User** is at *LoginScreen* and has not logged in. **User** goes to *Registration Screen* and enters their *LoginInfo* for creating an account.
### Related Use Cases:
Log in uses accounts created here.

### Trigger:
**User** accesses *LoginScreen*, then *RegistrationScreen*.
### Preconditions:
**User** is at *LoginScreen*.
**User** has not logged in.
**User** does not have an account
## Case 7: Main Success Path
1. **User** Arrives at *RegistrationScreen*.
2. **User** enters their *LoginInfo* into forms.
3. system checks if *email* is valid
4. system checks if *password* does not meet requirements
5. **User** is brought to *LoginScreen*.
## Case 7: Alternative Flow 3A
1. System detects *email* is invalid
2. System sends invalid request to *RegistrationScreen*
3. **User** receives invalid request
4. Return to main path
## Case 7: Alternative Flow 4A
1. System detects *password* is invalid
2. System sends invalid password request to *RegistrationScreen*
3. **User** receives invalid password request
4. Return to main path

## Case 8: Record Distribution
### Actor:
**Volunteer**
### Description:
A client picks up food in person at the pantry. **Volunteer** records which items and how much of each were given out. System subtracts them from the pantry's *Inventory*.
### Related Use Cases:
Inventory Auditing (Case 4) uses these records to detect low stock. Pantry Discovery (Case 5) shows the updated stock.
### Trigger:
A client receives food at the pantry.
### Preconditions:
**Volunteer** is logged in (Case 1) and is a volunteer at this pantry.
The items given out were logged into the pantry's *Inventory* through Donation Intake (Case 2).
## Case 8: Main Success Path
### Description:
This scenario describes the situation where every item given out is in stock.
### Steps:
1. **Volunteer** opens the distribution form for their pantry.
2. **Volunteer** selects each item given out and enters the quantity.
3. **Volunteer** submits the *DistributionRecord* to the System.
4. System checks that each quantity is not more than the amount in *Inventory*.
5. System subtracts the quantities from *Inventory* and saves the *DistributionRecord* with the date.
6. System confirms to **Volunteer** that the distribution was recorded.
### Termination:
The distribution is recorded and *Inventory* is updated.
## Case 8: Alternative Flow 2A
### Description:
This scenario describes the situation where an item given out is not listed in the pantry's *Inventory*.
### Steps:
1. **Volunteer** cannot find the item in the distribution form.
2. **Volunteer** logs the item through Donation Intake (Case 2).
3. Return to main path step 2.
### Termination:
The item is in *Inventory* and can be recorded.
## Case 8: Alternative Flow 4A
### Description:
This scenario describes the situation where a quantity entered is more than the amount in *Inventory*.
### Steps:
1. System detects that a quantity is more than the amount in *Inventory*.
2. System tells **Volunteer** which item is over and how many are recorded.
3. **Volunteer** corrects the quantity.
4. Return to main path step 3.
### Termination:
**Volunteer** submits a quantity that does not exceed *Inventory*.
## Case 8: Alternative Flow 3B
### Description:
This scenario describes the situation where **Volunteer** cancels before submitting.
### Steps:
1. **Volunteer** cancels the distribution form.
2. System discards the unsaved *DistributionRecord*.
### Termination:
Nothing is recorded and *Inventory* is unchanged.
### Postconditions:
**Success:** *Inventory* is reduced by the quantities given out, and the *DistributionRecord* is saved with its items, quantities, and date.
**Failure:** *Inventory* is unchanged.
### Quality Rules:
- Stock for an item can never go below zero.
- Every change to *Inventory* from a distribution can be traced to a saved *DistributionRecord*.

## Case 9: Manage Expiring Stock
### Actor:
**Facility Manager** (started on a schedule by the System)
### Description:
System checks *Inventory* each day for perishable items close to the expiration dates logged in Donation Intake (Case 2) and alerts the **Facility Manager**. **Facility Manager** chooses to give the items out first, transfer them to another pantry, or discard them. System updates *Inventory* and logs any waste.
### Related Use Cases:
Uses expiration dates logged in Donation Intake (Case 2). Transfers follow Case 2 Alternative Path 6A.
### Trigger:
The daily expiration check runs.
### Preconditions:
Perishable items were logged with expiration dates through Donation Intake (Case 2).
The pantry has set how many days before expiration it wants to be warned.
## Case 9: Main Success Path
### Description:
This scenario describes the situation where items are close to expiring and can still be given out.
### Steps:
1. System checks *Inventory* for perishable items that expire within the warning period.
2. System finds items close to expiring and sends an *ExpirationAlert* to **Facility Manager**.
3. **Facility Manager** reviews the items in the *ExpirationAlert*.
4. **Facility Manager** marks the items to be given out first.
5. System flags those items in *Inventory* as priority.
### Termination:
Every item in the *ExpirationAlert* is flagged to be given out first.
## Case 9: Alternative Flow 2A
### Description:
This scenario describes the situation where no items are close to expiring.
### Steps:
1. System finds no perishable items within the warning period.
2. System ends the check without sending an alert.
### Termination:
No *ExpirationAlert* is sent.
## Case 9: Alternative Flow 4A
### Description:
This scenario describes the situation where the pantry cannot use the items in time but another pantry can.
### Steps:
1. **Facility Manager** chooses to transfer the items.
2. System follows the transfer steps in Donation Intake (Case 2) Alternative Path 6A.
### Termination:
The items are set aside for transfer to another pantry.
## Case 9: Alternative Flow 4B
### Description:
This scenario describes the situation where items have already expired or cannot be used.
### Steps:
1. **Facility Manager** marks the items as discarded.
2. System removes the items from *Inventory*.
3. System saves a *WasteRecord* with the items, quantities, and date.
### Termination:
The items are out of *Inventory* and logged as waste.
### Postconditions:
**Success:** Every item in the *ExpirationAlert* is flagged to give out first, set aside for transfer, or discarded and logged as waste.
**Failure:** If **Facility Manager** does not respond, the items stay in *Inventory* and appear in the next day's *ExpirationAlert*.
### Quality Rules:
- Expired items are never shown as available stock.
- Discarded food can always be traced to a *WasteRecord*.

## Case 10: Calculate Food Costs
### Actor:
**Facility Manager**
### Description:
**Facility Manager** chooses a time period. System totals the value of food received, given out, transferred, and wasted in that period and shows a *CostReport*.
### Related Use Cases:
Uses donations from Donation Intake (Case 2), transfers from Case 2 Alternative Path 6A, *DistributionRecords* from Record Distribution (Case 8), and *WasteRecords* from Manage Expiring Stock (Case 9).
### Trigger:
**Facility Manager** asks for a cost report.
### Preconditions:
**Facility Manager** is logged in (Case 1).
Each item in *Inventory* has a value per unit.
## Case 10: Main Success Path
### Description:
This scenario describes the situation where the pantry has activity in the chosen period and every item has a value.
### Steps:
1. **Facility Manager** opens the cost report for their pantry.
2. **Facility Manager** chooses a start date and an end date.
3. System gathers the donations, transfers, *DistributionRecords*, and *WasteRecords* in that period.
4. System multiplies each quantity by the item's value per unit.
5. System totals the value received, given out, transferred, and wasted.
6. System shows the *CostReport* to **Facility Manager**.
### Termination:
**Facility Manager** sees the *CostReport* for the chosen period.
## Case 10: Alternative Flow 2A
### Description:
This scenario describes the situation where the chosen period is not valid.
### Steps:
1. System detects that the end date is before the start date or in the future.
2. System tells **Facility Manager** the period is not valid.
3. Return to main path step 2.
### Termination:
**Facility Manager** chooses a valid period.
## Case 10: Alternative Flow 3A
### Description:
This scenario describes the situation where there is no activity in the chosen period.
### Steps:
1. System finds no records in the period.
2. System shows a *CostReport* with all totals at zero and says there was no activity.
### Termination:
**Facility Manager** sees an empty *CostReport*.
## Case 10: Alternative Flow 4A
### Description:
This scenario describes the situation where some items do not have a value per unit.
### Steps:
1. System finds items with no value per unit.
2. System totals the items that have a value.
3. System shows the *CostReport*, marked incomplete, with a list of the items missing a value.
4. **Facility Manager** may set the missing values and return to main path step 3.
### Termination:
**Facility Manager** sees a *CostReport* marked incomplete, or a complete one after setting the values.
### Postconditions:
**Success:** **Facility Manager** sees the total value received, given out, transferred, and wasted for the period.
**Failure:** No *CostReport* is shown.
In both cases *Inventory* is unchanged.
### Quality Rules:
- Calculating a *CostReport* never changes *Inventory*.
- Every total in a *CostReport* can be traced to the records it came from.

