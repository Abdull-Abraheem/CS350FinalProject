### Relational Database Schema 

KEY NOTATION

PK means primary key.

FK means foreign key.
---
## 1. Users, organizations, and roles

`USER_ACCOUNT`(Cases 1, 7, 12)

- user_id INT PK
- first_name VARCHAR
- last_name VARCHAR
 -email: VARCHAR(255), NN, UQ
- password_hash VARCHAR, NN
- created_at TIMESTAMP
- is_care_eligible: BOOLEAN, NN, default FALSE
- delivery_address: VARCHAR(255), nullable
- delivery_city: VARCHAR(100), nullable
- delivery_zip_code: VARCHAR(10), nullable
- created_at: TIMESTAMP, NN

`ORGANIZATION_MEMBER` (joining and leaving a group)
- organization_id: INT, FK -> ORGANIZATION.organization_id
- user_id: INT, FK -> USER_ACCOUNT.user_id
- joined_at: TIMESTAMP, NN
- PK (organization_id, user_id)
- Leaving a group deletes the row.
  
`ORGANIZATION` (organizations/groups)
- organization_id: INT, PK
- name: VARCHAR(200), NN
- description: TEXT
- created_by_user_id: INT, NN, FK -> USER_ACCOUNT.user_id
- created_at: TIMESTAMP, NN

 `PANTRY_VOLUNTEER` (volunteer requests and roles, Case 12)
- pantry_volunteer_id: INT, PK
- pantry_id: INT, NN, FK -> PANTRY.pantry_id
- user_id: INT, NN, FK -> USER_ACCOUNT.user_id
- status: VARCHAR(10), NN, one of `pending`, `approved`, `declined`, `removed`
- requested_at: TIMESTAMP, NN
- decided_at: TIMESTAMP, nullable
- decided_by_user_id: INT, nullable, FK -> USER_ACCOUNT.user_id
  
---  
## 2. Pantries  


`ORGANIZATION` (organizations/groups)
- organization_id: INT, PK
- name: VARCHAR(200), NN
- description: TEXT
- created_by_user_id: INT, NN, FK -> USER_ACCOUNT.user_id
- created_at: TIMESTAMP, NN


`VOLUNTEER_PROFILE`(Cases 3, 12)

 - user_id  INT PK FK -> USER_ACCOUNT.user_id
 - can_deliver: BOOLEAN, NN, default FALSE
 - availability: VARCHAR(255), nullable (for example "Weekends, evenings")
 - is_available: BOOLEAN, NN, default TRUE

`DONATION`

donation_id: INT, PK
pantry_id: INT, NN, FK -> PANTRY.pantry_id
recorded_by_user_id: INT, NN, FK -> USER_ACCOUNT.user_id (the Volunteer)
donor_name: VARCHAR(200), nullable
received_at: TIMESTAMP, NN

`DONATION_LINE`

donation_line_id: INT, PK
donation_id: INT, NN, FK -> DONATION.donation_id
food_item_id: INT, NN, FK -> FOOD_ITEM.food_item_id
quantity: INT, NN, CHECK (quantity > 0)
expiration_date: DATE, nullable


PANTRY (Cases 4, 5, 6, 9, 11)

- pantry_id: INT, PK
- organization_id: INT, nullable, FK -> ORGANIZATION.organization_id
- manager_id: INT, NN, FK -> USER_ACCOUNT.user_id (the Facility Manager)
- pantry_name: VARCHAR(200), NN
- address: VARCHAR(255), NN
- city: VARCHAR(100), NN
- state: VARCHAR(2), NN
- zip_code: VARCHAR(10), NN
- latitude: DECIMAL(9,6), nullable (used by pantry search, Case 5)
- longitude: DECIMAL(9,6), nullable
- phone: VARCHAR(20)
- offers_delivery: BOOLEAN, NN, default FALSE
- auditing_enabled: BOOLEAN, NN, default FALSE (Case 11)
- check_interval_hours: INT, nullable, CHECK (check_interval_hours > 0)
- expiration_warning_days: INT, NN, default 3, CHECK (expiration_warning_days >= 0)
- last_audit_at: TIMESTAMP, nullable
- created_at: TIMESTAMP, NN

`PANTRY_HOURS` (Cases 5, 6)
- pantry_id: INT, FK -> PANTRY.pantry_id
- day_of_week: VARCHAR(9), one of Monday to Sunday
- opening_time: TIME, nullable
- closing_time: TIME, nullable
- is_closed: BOOLEAN, NN, default FALSE
- PK (pantry_id, day_of_week)

---
 
## 3. Food items and inventory
`FOOD_ITEM`

- food_item_id: INT, PK
- name: VARCHAR(200), NN, UQ
- unit: VARCHAR(30), NN (box, pound, gallon, can, and so on)
- is_perishable: BOOLEAN, NN, default FALSE
- value_per_unit: DECIMAL(10,2), nullable (Case 10; NULL means the cost report is marked incomplete)

`INVENTORY`

`ITEM_THRESHOLD` (minimum stock per item per pantry, Cases 4 and 11)

## 4. Transfers
`TRANSFER_REQUEST` (Case 2 path 6A, Case 9 flow 4A; one item per row)
- transfer_id: INT, PK
- from_pantry_id: INT, NN, FK -> PANTRY.pantry_id
- to_pantry_id: INT, NN, FK -> PANTRY.pantry_id, CHECK (to_pantry_id <> from_pantry_id)
- food_item_id: INT, NN, FK -> FOOD_ITEM.food_item_id
- inventory_id: INT, nullable, FK -> INVENTORY.inventory_id (source batch)
- quantity: INT, NN, CHECK (quantity > 0)
- requested_by_user_id: INT, NN, FK -> USER_ACCOUNT.user_id
- reason: VARCHAR(20), NN, one of `donation_overflow`, `expiring_stock`, `pantry_need`
- status: VARCHAR(10), NN, one of `pending`, `set_aside`, `completed`, `cancelled`
- created_at: TIMESTAMP, NN
- completed_at: TIMESTAMP, nullable
- When a transfer completes, the receiving pantry gets a new `INVENTORY` row with `source = 'transfer'`.
  
---
## 5. Delivery requests
`DELIVERY_REQUEST`

`DELIVERY_REQUEST_ITEM`
- delivery_request_item_id: INT, PK
- delivery_request_id: INT, NN, FK -> DELIVERY_REQUEST.delivery_request_id
- food_item_id: INT, NN, FK -> FOOD_ITEM.food_item_id
- quantity: INT, NN, CHECK (quantity > 0)
  
---
## 6. Distribution and waste
`DISTRIBUTION_RECORD` (in-person pickup, Case 8; one item per row)
- distribution_id: INT, PK
- pantry_id: INT, NN, FK -> PANTRY.pantry_id
- food_item_id: INT, NN, FK -> FOOD_ITEM.food_item_id
- quantity: INT, NN, CHECK (quantity > 0)
- recorded_by_user_id: INT, NN, FK -> USER_ACCOUNT.user_id (the Volunteer)
- distributed_at: TIMESTAMP, NN
- Submitting a form with several items inserts several rows with the same `distributed_at`, all in one database transaction together with the `INVENTORY` update.
`WASTE_RECORD` (Case 9 flow 4B; one item per row)
- waste_id: INT, PK
- pantry_id: INT, NN, FK -> PANTRY.pantry_id
- food_item_id: INT, NN, FK -> FOOD_ITEM.food_item_id
- quantity: INT, NN, CHECK (quantity > 0)
- expiration_date: DATE, nullable
- recorded_by_user_id: INT, NN, FK -> USER_ACCOUNT.user_id
- discarded_at: TIMESTAMP, NN
- reason: VARCHAR(255), nullable
 
---

RELATIONSHIPS
UserAccount → Donation: one user can record multiple donations.

UserAccount → VolunteerProfile: a user may have one volunteer profile

Pantry → Donation: one pantry can receive multiple donations.

FoodItem → DonationLine: one food item can appear on multiple donation lines.
