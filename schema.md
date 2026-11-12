### Relational Database Schema 

KEY NOTATION

PK means primary key.

FK means foreign key.

`ORGANIZATION`
- organization_id: BIGINT, PK
- name: VARCHAR(200)
- description: TEXT
- created_by_user_id: INT
- created_at: TIMESTAMP

`USER_ACCOUNT`
- user_id INT PK
- first_name VARCHAR
- last_name VARCHAR
- email     VARCHAR
- password_hash VARCHAR
- created_at TIMESTAMP

`VOLUNTEER_PROFILE`
 - user_id  INT PK
 - delivery VARCHAR
 - avalibility VARCHAR
 - is_avalible BOOLEAN

`DONATION`
- Donation_ID INT PK
- received_at TIMESTAMP
- quantity INT

`PANTRY`
- pantry_id       INT PK
- manager_id      INT FK-> manager
- pantry_name     VARCHAR
- address         VARCHAR
- city            VARCHAR
- zip_code        VARCHAR
- phone           VARCHAR
- offers_delivery BOOLEAN 

`PANTRY_MANAGER`


`PANTRY_HOURS`
- pantry_id INT
- day_of_week VARCHAR
- opening_time TIME
- closing_time TIME
- is_closed BOOLEAN

`FOOD_ITEM`
- food_item_id PK
- name VARCHAR
- Quantity INT
- Unit VARCHAR  can be box, pound, gallon etc

`DONATION`
 - donation_id INT
 - pantry_id    INT    FK → `PANTRY.pantry_id
 - received_at TIMESTAMP
 
RELATIONSHIPS
UserAccount → Donation: one user can record multiple donations.

UserAccount → VolunteerProfile: a user may have one volunteer profile

Pantry → Donation: one pantry can receive multiple donations.

FoodItem → DonationLine: one food item can appear on multiple donation lines.
