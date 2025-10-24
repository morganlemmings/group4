# group4 
Group 4 MIST 4610 Project #1

# Team Members
[@morganlemmings](https://github.com/morganlemmings) 
[@melissatran0](https://github.com/melissatran0) 
[https://github.com/mrb74060/Disney.git](https://github.com/mrb74060)
[https://github.com/jasongold3/MIST4610Disney](https://github.com/jasongold3)
[@clarkfarrell2 ](https://github.com/clarkfarrell2)



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
<img width="616" height="281" alt="Screenshot 2025-10-22 at 9 48 30 PM" src="https://github.com/user-attachments/assets/0fc26c74-fc4b-409c-8d7c-3f322fbe5d65" />

<img width="656" height="359" alt="Screenshot 2025-10-22 at 9 48 49 PM" src="https://github.com/user-attachments/assets/eb1cac89-9b66-4b3c-95cd-59333fd38592" />

<img width="646" height="244" alt="Screenshot 2025-10-22 at 9 49 08 PM" src="https://github.com/user-attachments/assets/7582fc06-5227-4470-b323-86ecc0d1d86f" />

<img width="704" height="321" alt="Screenshot 2025-10-22 at 9 49 46 PM" src="https://github.com/user-attachments/assets/b35b7037-3b3b-4385-8d59-b58c460694b9" />

<img width="717" height="449" alt="Screenshot 2025-10-22 at 9 50 03 PM" src="https://github.com/user-attachments/assets/bdb17556-6e8d-4ad8-8e3b-6ef6e38046fe" />

<img width="701" height="448" alt="Screenshot 2025-10-22 at 9 50 17 PM" src="https://github.com/user-attachments/assets/17f5b42b-25a3-41fd-a734-f27036a9413d" />

<img width="677" height="295" alt="Screenshot 2025-10-22 at 9 50 41 PM" src="https://github.com/user-attachments/assets/cfaa3dcf-eaf0-4f1c-b2f2-a3deba93041b" />

<img width="630" height="426" alt="Screenshot 2025-10-22 at 9 50 58 PM" src="https://github.com/user-attachments/assets/154c1034-6a9f-46ad-85b3-586b30b666da" />

<img width="631" height="183" alt="Screenshot 2025-10-22 at 9 51 32 PM" src="https://github.com/user-attachments/assets/b06e984e-3b60-4158-95c8-eb8d80333181" />

<img width="638" height="170" alt="Screenshot 2025-10-22 at 9 51 45 PM" src="https://github.com/user-attachments/assets/44240ac7-1de1-4cbf-a0c6-26063cb1dc98" />

<img width="647" height="198" alt="Screenshot 2025-10-22 at 9 52 10 PM" src="https://github.com/user-attachments/assets/6e7e3b3f-9caf-49b2-9125-d9784614b01d" />

# Queries
pic of query table

1. Query 1 retrieves the movieID and movieTitle from the Movie table for every movie that does not have a corresponding entry in the Merchandise table. It uses a NOT EXISTS subquery to check whether a given movieID appears in the Merchandise table. If no matching row exists, the movie is included in the results.

<img width="565" height="514" alt="Screenshot 2025-10-23 at 5 32 50 PM" src="https://github.com/user-attachments/assets/7259386e-fb31-4456-8af3-745b238e2f1c" />

Query 1 allows managers to identify which movies in the catalog have not yet been leveraged for merchandise opportunities. Since merchandise sales can be a significant revenue stream, spotting movies without merchandise helps decision‑makers recognize untapped potential. These results can guide marketing teams and product developers to prioritize which movies might benefit from new merchandise lines, ensuring that popular or overlooked titles are not missing out on additional revenue. By focusing on movies without merchandise, managers can strategically expand offerings and maximize profitability.



