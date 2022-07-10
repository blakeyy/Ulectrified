# Ulectrified - A mobile app for trading renewable energy surplus

This app is built to enable private renewable energy producers to offer their renewable energy surplus in an easy way and at a fair price. Electric vehicle users can find the offers via this app and buy the offered energy. If the buyer books the offer, he charges the energy at the producers place.

## Repository

The app was built with Adalo. The repository can be cloned here: https://previewer.adalo.com/b9e550ab-4a6a-40ac-a41d-a261036a0efa

## Tools & frameworks used for this project

### Miro (https://miro.com/):

- Collaborative work on the blueprint of the app and description of the desired functions

### Adalo (https://www.adalo.com/): 

- No-code tool to build native mobile apps or web apps
- Drag-&-drop to add screens and components
- Prebuilt screens (e.g. navigation screens, info screens, list screens, etc.)
- Prebuilt components (e.g. text fields, buttons, forms, input fields, etc.)
- Integrated database to store app data
    - Consists of database collections (e.g. users, energy offers, etc.) which store records (e.g. a user or an energy offer)
    - Each database collection has its own properties like name (text), profile picture (image), price (number) or relationships (e.g. each energy offer has a user/seller and possibly a user/buyer)
- Add actions to screens or components
    - Link to other screens
    - Create new records or update existing ones
    - Conditions (e.g. perform action only if certain values are fulfilled)
- API integrations (e.g. Google Maps API)
- Apps can be made available in the Apple Store and the Google Play Store

### Google Maps API (https://developers.google.com/maps):
    
- Provides a map where current location and other location pointers can be placed
- Filtering for locations
- Info windows for pointers

## Step-by-step guide

### Create blueprint via Miro
As a first step we created the basic structure of our app in Miro and wrote down the features we want to include. The image below shows the blueprint of the app. 

<img width="597" alt="app_structure" src="https://user-images.githubusercontent.com/53949039/177563295-df998f85-fe06-445d-9ccc-9057e1b7ce57.png">

- ![#f03c15](https://via.placeholder.com/15/f03c15/f03c15.png): Future feature (not implemented yet)
- The screens connected by the dashed lines appear only when the user logs in for the first time

### Implement protoype in Adalo

### 1. Set up database collections

First you need to set up the database collections. This includes adding properties to each collection and also initializing some collections (e.g. payment methods or roles). 
The following database collections are used for this app:
  
  - Users: 
    1. This collection is created automatically and comes with mandatory properties like email, password, username and fullname
    2. Add variables like "sold kWhs", "bought kWhs", "credit balance", "profile picture", etc.
    3. Add flags that can be activated to trigger errors (e.g. invalid input) or info windows (e.g. after purchasing energy)
    4. Add temporal storage variables for caching values from input fields
  
  - Roles:
    1. Add "ID" and "Type" variables
    2. Create two role types: seller (ID: 1) and buyer (ID: 0)
    3. Add Relationship property to Users

  - Energy Offers:
    1. Add properties like "ID", "street", "postal code", "start time", "end time", "amount of energy", etc.
    2. Add "booked" flag to know if the offer is still available
 
  - Payment Methods:
    1. Add "Name" variable
    2. Create desired records of payment methods (e.g. PayPal, Apple Pay, Google Pay, etc.)

Relationships that are used between the collections:
- A user can only have one role & A role can have multiple users
- A energy offer can only have one user/seller & A user/seller can have multiple energy offers
- A energy offer can only have one user/buyer & A user/buyer can have multiple energy offers
  

### 2. Create Screens and connect them to each other

This section describes how the screens are connected and what they do. Also the actions that need to be implemented are described.

### *A. Registration & Login:* 

From the **Welcome** screen you can get either to the **Registration** screen or the **Login** screen (Link at the "Create new account" and "Log in" button respectively). In the **Registration** screen the credentials for a new account are filled into the form fields. The "Sign up" button creates a new user with the respective credentials and links to the **Login** screen. If the button "I already have an account" is clicked, you get directly linked to the **Login** screen. In the **Login** screen the login data can be inserted. By pressing "Log in" the user is logged in and moves to the **Transition screen** which is described in the [next section](#b-distinguish-between-seller--buyer-account). The "No account? Sign up" button can be pressed to get back to **Registration** screen. <br />
![image](https://user-images.githubusercontent.com/53949039/177569553-e064694e-76b3-495e-95fd-39c3d7c21f57.png)
<br />

### *B. Distinguish between seller & buyer account:* 

After logging in the **Transition** screen helps to distinguish between seller and buyer. If the logged in user is a buyer, he gets to the [Buyer Homepage](#e-buyer-perspective) (upper screen) otherwise (he is a seller) he gets to the [Seller homepage](#d-seller-perspective) (lower screen).
![image](https://user-images.githubusercontent.com/53949039/177571500-d8ae0e75-b362-497c-a081-b4feb735ee65.png) <br />

### *C. Navigation bar*

The **Navigation bar** is almost the same for both seller & buyer.

- The left icon ("Map" or "Home") it directs you to the respective homescreen ([Buyer](#e-buyer-perspective) or [Seller](#d-seller-perspective)).
- "Invoices" is not impemented yet.
- "My Score" directs you to the [Scoring list](#e-buyer-perspective) (only implemented for the buyer yet). 
- "Profile" links to respective profile of the user ([Seller profile](#d-seller-perspective) or [Buyer profile](#e-buyer-perspective)).
- "More" opens the field shown below which includes a "Logout" button. By pressing it the user gets logged out and directed to the [Login screen](#a-registration--login).

    - Seller: <br />
    ![image](https://user-images.githubusercontent.com/53949039/177968930-d0800fd2-4b84-42b9-94ba-58423f515ec9.png)

    - Buyer: <br />
    ![image](https://user-images.githubusercontent.com/53949039/177967955-3f0d206c-ed1d-4c70-bdff-780a9c338227.png)

    - More (Logout): <br />
    ![image](https://user-images.githubusercontent.com/53949039/177979725-8cd81d75-d424-45dd-b178-8036629468f3.png)


### *D. Seller Perspective:*

This section describes the structure of the app on the seller's side.

- ### Open/Booked offers <br />
If you logged in as a seller, you get directed to the **Seller Homepage** showing a list with open offers (left). The list shows all energy offers of the seller which aren't booked yet (all energy offers associated with current user/seller & booked flag =  0). The **Seller Homepage 2** (right) shows all booked offers of the current seller (booked flag = 1). By pressing the rectangles on the top ("Open offers" and "Booked offers") the user gets directed to the respective screen. The search bar can be used to filter for entries in the respective list. The dark blue button with the "+" icon has a link to the [Offer energy trade screen](#create-new-energy-offer) described next. 

![image](https://user-images.githubusercontent.com/53949039/177573913-349d563b-1981-4b55-80b5-00ce5114567b.png) <br />

- ### Create new energy offer
The **Offer energy trade** screen (left) shows up if the "+" button is clicked. It includes a form component. By clicking the "Place new offer" button the values from the input fields are checked. If they are invalid, the error flags for the respective input fields are set and you get directed to the **Modal test** screen (middle). This screen shows an info that the input values were invalid. By pressing "OK" you get directed back to the left screen which now shows the red text for the invalid inputs. The red text is a so called fake modal. It only shows up when the respective error flags are set. If the values are valid, it directs you to the **Modal offer done** screen (right). Here you can either click "Cancel" (backwards link) or "Yes" (Creates new energy offer and links to the **Seller homepage**).  In the left screen the info button at the upper right side of the price form field has a link to the [Price info screen](#price-info-screen).

![image](https://user-images.githubusercontent.com/53949039/177583874-ed1c2e46-6dec-43aa-85fe-600adb59833d.png) <br />

- ### Price info screen: 
This screen overlays a small window over the previous screen and shows an information for the seller. A action with a link backwards is placed on the whole screen which directs you backwards to the previous screen. <br />

![image](https://user-images.githubusercontent.com/53949039/177584555-1f6bfccd-46d0-4699-8933-47681255a9b2.png) <br /> 

- ### Seller profile 
The **Seller profile** includes a "circular progress bar" component which visually shows how much energy has to be sold to get to the next level. Below the diagram there are some text fields that include custom formulas to calculate for example the level of the user or the amount of energy sold. It also shows the name, email and credit balance of the user. This data comes from the record of the respective user. 

![image](https://user-images.githubusercontent.com/53949039/177580238-d45ef34e-7f11-4f5d-9be5-94e213c1c77f.png) <br />

### *E. Buyer Perspective:*

This section describes the structure of the app on the buyer's side.

- ### Availability map <br />
The **Availability map** screen includes a map component that shows for every open offer that is not expired (booked flag = 0 & current time before end time) the location on the map with a marker. The locations can be filtered with the search bar on the top. The markers have a link (click action) to the [Offer InfoWindow](#book-offer) screen which additionally transfers the data of the current energy offer to the next screen. 
In addition the **Buyer homepage** has a conditioned (if purchased flag = 1) link to the **Purchase info** screen (the purchased flag is set when paying for an offer which is described in the [next section](#book-offer)). 
The **Purchase info** screen includes a text field which uses custom formulas to show how much CO2 and money the buyer saved by purchasing the offer. By clicking somewhere on the screen you get directed backwards and the purchased flag is set to 0.

![image](https://user-images.githubusercontent.com/53949039/178114235-c038a1b2-5d69-44f7-865c-dab58360bd0d.png) <br />

- ### Book offer <br />
In the **Offer InfoWindow** screen (left) the linked data of the energy offer from the [Availability map](#availability-map) is shown in text fields. The "Book" button links to the **Payment** screen (middle). 
Here in addition to the energy offer data a dropdown menu is shown with which the payment method can be selected. The entries of the dropdown menu are from the database collection "Payment methods". 
The "Cancel" button links backwards. The "Pay" button updates the energy offer (sets booked flag to 1 and sets logged in user as buyer), updates the user/seller (increase credit balance and sold energy accordingly with custom formulas), updates the user/buyer (increase bought energy, set purchased flag to 1 and cache amount of energy and price of the offer for the **Purchase info** screen described in the [previous section](#availability-map)) and links to the **Payment success** screen (right).
In the **Payment success** screen the amount of money, seller name, etc. is shown in a text field. The "Done" button links backwards to the [Availability map](#availability-map). <br />

![image](https://user-images.githubusercontent.com/53949039/177584339-3bcc913c-b991-4d09-b038-ae7933dfa717.png) <br />

- ### Scoring list <br />
The **Scoring list** screens include a navigation bar on the top where you can switch between "all time" and "monthly" (currently both lists show the all time score, the monthly score isn't implemented yet). The list shows every user/buyer sorted by its amount of energy bought. For every user/buyer the list shows the profile picture, username and CO2 savings (custom formula). The data comes from the stored records of the respective user/buyer. <br />

![image](https://user-images.githubusercontent.com/53949039/177574710-6758336b-2a70-4052-93f7-5e1986b97837.png) <br />

- ### Buyer profile <br /> 
The **Buyer profile** (left) includes a "circular progress bar" component which visually shows how much energy has to be bought to get to the next level. Below the diagram there are some text fields that include custom formulas to calculate for example the level of the user or the saved amount of CO2 in kg. It also shows the name, email and username. If the avatar icon in the upper right corner is clicked, the screen on the right hand side opens. Here an image can be uploaded which is then stored in the record of the user and shows up in the [Scoring list](#scoring-list).

![image](https://user-images.githubusercontent.com/53949039/177608977-2155dfb0-c67a-4649-be33-cd946be208dd.png) <br />

## Final remarks

This project was done by our group **Ulectrified** for the TechChallenge SS2022 @ TUM. The app is only a prototype and isn't finished yet. However, it contains several features and showcases our idea.

Credits:
- Anna Nikolaichuk ([anna.nikolaichuk@tum.de](anna.nikolaichuk@tum.de))
- Nida Güler ([nida.gueler@tum.de](nida.gueler@tum.de))
- Ingo Blakowski ([ingo.blakowski@tum.de](ingo.blakowski@tum.de))
