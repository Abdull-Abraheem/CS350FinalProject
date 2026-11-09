# Food Bank Discovery and Inventory Manager Requirements

**CS 350-01 Group A**

Abdull Abraheem, Benjamin Mardis, Phillip Schulz, Evan Moeun, Joe Chen, Alexander Villa

---

## Functional Requirements

Our program supports five kinds of users:

- The *guest* is the lowest level, being only able to view locations and search for locations. Is a non-signed-in user.
- The *registered user* has the same permissions as a guest but gains access to putting in orders and joining or leaving an organization/group, as well as being able to upload said organization/group.
- Specializations of a *registered user* are defined as the following:
  - The *volunteer* is able to submit inventory and deliver orders.
  - The *facility manager* can read inventory reports and make judgment calls from them.
  - The *Care Eligible user* is able to make use of the home delivery service.

On the software itself, we support:

- System checks what the facility has in stock.
- Registration and allocation of users into various roles.
- Registration of organizations/groups for food pantries.
- Search that allows users to find locations near them.
- Order management, where we take in orders and make them available for *volunteers* to act upon.

## Non-Functional Requirements

- Straightforward/approachable interface. All users should be able to understand what an action would lead to intuitively.
- Scalability, should allow for quicker search of accounts and saving.
- Method of storage: Database
- Programming language: Python
- Access should be done through a web app
