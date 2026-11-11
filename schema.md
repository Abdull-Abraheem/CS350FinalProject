### Relational Database Schema 

KEY NOTATION

PK means primary key.

FK means foreign key.

Tables:

`ORGANIZATION`
-organization_id: BIGINT, PK
-name: VARCHAR(200)
-description: TEXT
-created_by_user_id INT
-created_at: TIMESTAMP

`USER_ACCOUNT`

`VOLUNTEER_PROFILE`

`DONATION`
-Donation_ID INT PK
-received_at TIMESTAMP

`PANTRY`

`PANTRY_MANAGER`

`PANTRY_HOURS`

`FOOD_ITEM`
-food_item_id Pk
-name VARCHAR
-Quantity INT
-Unit VARCHAR  can be box, pound, gallon etc

`DONATION`
 -donation_id INT
 -pantry_id    INT    FK → `PANTRY.pantry_id
 -received_at TIMESTAMP
 
RELATIONSHIPS
UserAccount → Donation: one user can record multiple donations.

UserAccount → VolunteerProfile: a user may have one volunteer profile

Pantry → Donation: one pantry can receive multiple donations.

FoodItem → DonationLine: one food item can appear on multiple donation lines.
