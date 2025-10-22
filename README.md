# group4 
Group 4 MIST 4610 Project #1

# Team Members
@morganlemmings 
@melissatran0 
@clarkfarrell2 
@jasongold3 
@mrb74060

# Problem Description

The task at hand is to model and build a relational database for the general workings of Disney. The central entities to our data model is the park entity, which represents the physical location of Disney World, and the movie entity. The park entity is relational to the employees who manage the park, the various attractions present at the park, employees who operate the park, disney themed stores at the park, and maps out the relationship to customers who visit the park. The movie entity consists of characters, actors, movie themed merchandise, and casting process. We are interested in accurately modeling these relationships and generating sample data, so that we can operate the disney park efficiently and effectively. The movie aspect of disney is also mapped out to help maximize profit, help with franchise growth, and most importantly help with cross-division coordination. We established a link between the movie and park entities to demonstrate the influence movies have on physical elements in disney stores.

# Data Model

Explanation of the Data model:

Our model is based on the Disney Corporation’s key revenue streams, which have represented Disney since its beginning: its famous movies and Disney World.

The first entity we created was the movie entity, which contains general information about the movie, such as its release date, genre, etc. Inside each movie, many characters can be a part of many movies in the form of sequels. To show this many-to-many relationship, we created an associative entity “Appearance” to show which fabled Disney characters appeared in which movies.

Characters are voiced by people, so an Actor entity was created with a one-to-many non-identifying relationship with “Character” to show who voices what characters. The modality for the Actor in this relationship is 1 because we are only including characters who have speaking parts and not just every character seen in the movie. Many Disney movies have real people in them, so we created a “Casting” associative entity to relate “Movies” with “Actors” to record what actors are present in different movies.

Disney makes a lot of revenue from the different merchandise it sells at Disney World, and this merchandise largely contains attributes that come from Disney movies. The merchandise does not have to include these attributes, so we made a non-identifying one-to-many relationship between “Merchandise” and “Movie.” Disney sells their merchandise at different stores across Disney World, so a one-to-many non-identifying relationship was constructed between store and Merchandise. Disney wants to track the facts such as quantity in stock, unit cost, and selling price of each item, so an Inventory table was created; however, inventory is different at each store, so “Store” must become a foreign key through a one-to-many relationship with “Inventory.”

There are different parks at Disney World, such as Epcot, Animal Kingdom, Magic Kingdom, etc., that we want to have information about, such as location and opening date, resulting in the “Park” entity being created. Each park also has different stores and attractions, so one-to-many relationships were created between “Park” and “Store” and “Park” and “Attraction.” Attraction holds information about its name and type, as well as what area of the park it is in.

Parks are staffed by employees, and we are assuming Disney keeps its employees working in the same park since Disney heavily values consistency and effectiveness. So, “Park” has a one-to-many relationship with “Employee.” “Employee” also holds general information such as title, name, and tenure.

People who come to Disney World are tracked through the “Customers” entity. Many customers purchase many different merchandise while at Disney World, resulting in an associative entity to track this called “Purchase.” Customers’ visits and other information about the visit are tracked through the “Visit” entity and a one to many relationship is modelled between “Customer” and “Visit.” Lastly, since Disney values its Customers, they like to know which park each customer likes the most so a one to many relationship is mapped between “Customer” and “Park.”

<img width="507" height="510" alt="Screenshot 2025-10-22 at 3 46 41 PM" src="https://github.com/user-attachments/assets/f9a008b8-5f18-4400-82f7-616ac6142786" />

# Data Dictionary

