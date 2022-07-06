# Ulectrified - A mobile app for trading renewable surplus energy.
This App is built to enable private renewable energy producers to offer their renewable surplus energy in an easy way and at a fair price. EV users can find this offers via this app and buy the offered energy. If the buyer books the offer, he charges the energy at the producers place.


The Adalo repository can be cloned here: https://previewer.adalo.com/15754726-98e4-4b55-9ded-28c1788137c8 


## Tools & Frameworks used for this project
- Miro (https://miro.com/):
    - To create the blueprint of the app and describing desired features 
- Adalo (https://www.adalo.com/): 
    - No-code tool to build Native Mobile Apps or Web Apps
    - Drag-&-Drop to add screens and components
    - Prebuilt screens (e.g. Navigation Screens, Info Screens, List Screens, etc.)
    - Prebuilt components (e.g. Text, Buttons, Forms, Input fields, etc.)
    - Add actions to screens or components
    - Integrated Database to store app data
    - Consists of Database Collections (e.g. Users, Energy offers, etc.) which store records (e.g. a User or an Energy Offer). 
    - Each Database Collection has its own properties like Name (Text), Profile Picture (Image), Price (Number) or Relationships (e.g. each Energy offer has a user/seller and possibly a user/buyer)
    - By using actions in the screens or components either new records can be created or existing records can be updated
    - API integrations (e.g. Google Maps API)
    - Apps can be made available in the Apple Store and the Google Play Store

- Google Maps API (https://developers.google.com/maps):
    - Provides a Map where current location and other location pointers can be placed
    - Filtering for locations
    - Info Windows for pointers

## Step-by-step guide
### Create blueprint
<img width="597" alt="app_structure" src="https://user-images.githubusercontent.com/53949039/177563295-df998f85-fe06-445d-9ccc-9057e1b7ce57.png">

### Implement protoype in adalo
1. #### Set up Database Collections
  First you need to set up the database collections. This includes adding properties to each collection and also preseting some values. The following database collections are used for this app:
  - Users: 
    1. This collection is created automatically and includes Email, Password, Username and Fullname intrinsically.
    2. In addition
  - Roles:

  - Energy Offers:
 
  - Payment Methods:

## Create Screens and connect them to each other
### Registration & Login:
### Seller Part
### Buyer Part








Sources:
https://www.nocode.tech/lessons/adalo-overview
