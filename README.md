# Ulectrified - A mobile app for trading renewable surplus energy.

This App is built to enable private renewable energy producers to offer their renewable surplus energy in an easy way and at a fair price. EV users can find this offers via this app and buy the offered energy. If the buyer books the offer, he charges the energy at the producers place.

The Adalo repository can be cloned here: https://previewer.adalo.com/15754726-98e4-4b55-9ded-28c1788137c8 

## Tools & Frameworks used for this project

### Miro (https://miro.com/):

- Collaborative work on the blueprint of the app and description of the desired functions.

### Adalo (https://www.adalo.com/): 

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

### Google Maps API (https://developers.google.com/maps):
    
- Provides a Map where current location and other location pointers can be placed
- Filtering for locations
- Info Windows for pointers

## Step-by-step guide

### Create blueprint

<img width="597" alt="app_structure" src="https://user-images.githubusercontent.com/53949039/177563295-df998f85-fe06-445d-9ccc-9057e1b7ce57.png">

### Implement protoype in Adalo

### 1. Set up Database Collections

First you need to set up the database collections. This includes adding properties to each collection and also preseting some values. The following database collections are used for this app:
  
  - Users: 
    1. This collection is created automatically and comes with mandatory properties like Email, Password, Username and Fullname
    2. Add variables like "sold kWhs", "bought kWhs", "credit balance", "profile picture", etc. 
    3. Add relationships like "role" and "energy offers"
    4. Add flags that can be activated to trigger errors (e.g. invalid input) or info windows (e.g. after purchasing energy)
    5. Add temporal storage variables for caching values from input fields
  
  - Roles:
    1. Add "ID" and "Type" variables
    2. Create two role types (seller and buyer)
    3. Relationship to Users

  - Energy Offers:
    1. Add properties like "ID", "street", "postal code", "start time", "end time", "amount of energy", etc.
    2. Add relationships to users (seller and buyer)
    3. Add "booked" flag to know if the offer is still available
 
  - Payment Methods:
    1. Add "Name"
    2. Create desired payment mehtods records

### 2. Create Screens and connect them to each other

This section briefly describes how the screens are connected and what they do. Also the actions that need to be implemented are described.

*Registration & Login:* <br />
    From the welcome you can get either to the registration or the login screen. <br />
    ![image](https://user-images.githubusercontent.com/53949039/177569553-e064694e-76b3-495e-95fd-39c3d7c21f57.png) <br />

*Distinguish between seller & buyer account:* <br />
![image](https://user-images.githubusercontent.com/53949039/177571500-d8ae0e75-b362-497c-a081-b4feb735ee65.png) <br />

*Seller Part:*

- Open/Booked offers <br />
![image](https://user-images.githubusercontent.com/53949039/177573913-349d563b-1981-4b55-80b5-00ce5114567b.png) <br />
- Create new energy offer <br />
![image](https://user-images.githubusercontent.com/53949039/177583874-ed1c2e46-6dec-43aa-85fe-600adb59833d.png) <br />
Price info window: <br />
![image](https://user-images.githubusercontent.com/53949039/177584555-1f6bfccd-46d0-4699-8933-47681255a9b2.png) <br /> 
- Seller Profile <br />
![image](https://user-images.githubusercontent.com/53949039/177580238-d45ef34e-7f11-4f5d-9be5-94e213c1c77f.png) <br />

*Buyer Part:*

- Availability map <br />
![image](https://user-images.githubusercontent.com/53949039/177575467-bd273d74-cd30-4192-a0cd-a5f33c5b2c89.png) <br />
- Book offer <br />
![image](https://user-images.githubusercontent.com/53949039/177584339-3bcc913c-b991-4d09-b038-ae7933dfa717.png) <br />
- Scoring list <br />
![image](https://user-images.githubusercontent.com/53949039/177574710-6758336b-2a70-4052-93f7-5e1986b97837.png) <br />
- Buyer profile <br />
![image](https://user-images.githubusercontent.com/53949039/177579784-5734e673-57ce-411e-8653-7869ae262dca.png)







## Sources:
https://www.nocode.tech/lessons/adalo-overview
