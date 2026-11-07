# Food Bank Discovery and Inventory Manager Problem Statement
CS 350-01 Group A

Abdull Abraheem, Benjamin Mardis. Phillip Schulz, Evan Moeun, Joe Chen, Alexander Villa

## Problem Domain
As it stands, food banks that operate independently outside of state-run networks struggle with two big issues: food bank discoverability and inefficient resource tracking. 
If you are an individual who relies on these services, it presents a major problem as you may not know where a local foodbank is along with its hours, nor what they have in stock. 
This also affects foodbanks as they struggle to track perishable inventory, calculate accurate food costs, and are unable to coordinate volunteer drivers to prevent food waste. 
It would be very useful to implement a unified system that would cover these issues. It would offer a solution on both the front end for the consumers and on the backend for these food pantries
## Scenarios
  1. Donation intake:

     A pantry volunteer uses a form to access the intake module. They adjust the quantities of incoming staples and log the expiration dates.
     The inventory information is stored. The system checks neighboring distribution centers to check if this particular surplus
     requires transferring goods to other pantries.
  2. Volunteer distribution:

     The system monitors the behavior of the delivery queue. When an elderly or homebound client requests a food package, the system logs
     the request and adds the request to a gig system where volunteers can choose to take the delivery.
  3. Inventory auditing:

     The system monitors the information store to detect shortages in essential items. Low stock levels and unusual depletion rates are
     reported to the facility manager, who then plans targeted community food drives. The occurrences of item shortages are logged and analyzed for
     trends, enabling the manager to anticipate specific needs in the future.
  4. Pantry Discovery:

     A local resident can use the system to find nearby foodbanks operating within their area. The system would show nearby options along with
     their	relevant information (address, hours, etc.). It would also show the current stock and allow a stay-at-home resident to request an item
     if said pantry has volunteer delivery drivers.
