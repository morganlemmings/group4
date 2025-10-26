# group4 
Group 4 MIST 4610 Project #1

# Team Members
[@morganlemmings](https://github.com/morganlemmings) 
[@melissatran0](https://github.com/melissatran0) 
[@mrb74060](https://github.com/mrb74060) 
[@jasongold3](https://github.com/jasongold3) 
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

<img width="721" height="252" alt="Screenshot 2025-10-26 at 1 15 09 PM" src="https://github.com/user-attachments/assets/e9bf00c8-ee1e-461b-86f7-90cf38474cb0" />

1. Query 1 retrieves the movieID and movieTitle from the Movie table for every movie that does not have a corresponding entry in the Merchandise table. It uses a NOT EXISTS subquery to check whether a given movieID appears in the Merchandise table. If no matching row exists, the movie is included in the results.

<img width="565" height="514" alt="Screenshot 2025-10-23 at 5 32 50 PM" src="https://github.com/user-attachments/assets/7259386e-fb31-4456-8af3-745b238e2f1c" />

Query 1 allows managers to identify which movies in the catalog have not yet been leveraged for merchandise opportunities. Since merchandise sales can be a significant revenue stream, spotting movies without merchandise helps decision‑makers recognize untapped potential. These results can guide marketing teams and product developers to prioritize which movies might benefit from new merchandise lines, ensuring that popular or overlooked titles are not missing out on additional revenue. By focusing on movies without merchandise, managers can strategically expand offerings and maximize profitability.

2. Query 2 retrieves the location and opening date of each Disney park from the Park table. The results are ordered by opening date in descending order, meaning the most recently opened parks appear first and the oldest parks appear last.

<img width="533" height="259" alt="Screenshot 2025-10-26 at 12 37 05 PM" src="https://github.com/user-attachments/assets/3632bb70-ffd6-4ec7-a52a-99a27b1c7469" />

Query 2 allows managers and analysts to quickly see the timeline of Disney park openings, starting with the newest additions. Understanding the order of park openings is useful for evaluating expansion strategies, identifying which parks are relatively new and may still be in growth phases, and comparing performance across parks of different ages. By listing the parks in descending order of opening date, decision‑makers can easily focus on the most recent investments and assess how these newer parks are performing compared to established ones.

3. Query 3 retrieves all columns from the Movie table for movies that were released after January 1, 2020. It applies two filters in the WHERE clause to ensure only movies released after 2020 are included, and only movies whose box office revenue is greater than the overall average box office revenue across all movies are included. The results are then ordered by box office in descending order, so the movies with the highest earnings appear first.

<img width="776" height="338" alt="Screenshot 2025-10-26 at 12 41 36 PM" src="https://github.com/user-attachments/assets/e36b62b2-f88a-48f5-bffa-bdff42d49365" />

Query 3 allows managers and analysts to identify the most financially successful movies released in recent years. By filtering for movies released after 2020, the results focus on current market trends and audience preferences. Comparing each movie’s box office revenue against the overall average ensures that only above‑average performers are highlighted. Ordering the results from greatest to least earnings makes it easy to see which films have been the strongest box office successes. This insight is valuable for decision‑makers who want to understand which recent films are outperforming the market, guiding future investment, marketing strategies, and production planning. It highlights not just which movies are new, but which ones are truly driving revenue growth.

4. Query 4 retrieves the first name, last name, and the park location for all customers whose favorite park is Epcot. It joins the Customer table with the Park table using the foreign key relationship Customer.favPark_parkID = Park.parkID. The WHERE clause filters the results so that only customers whose favorite park matches the location “Epcot” are included.

<img width="577" height="494" alt="Screenshot 2025-10-26 at 12 45 50 PM" src="https://github.com/user-attachments/assets/bc01144b-73fe-4576-8285-dd760aeddc22" />

Query 4 allows managers to identify all customers who have designated Epcot as their favorite park. Knowing which customers prefer a specific park is valuable for targeted marketing campaigns, personalized promotions, and loyalty programs. For example, managers could send Epcot‑themed offers, event invitations, or merchandise promotions directly to these customers. This helps strengthen customer engagement by aligning outreach with individual preferences, ultimately improving satisfaction and increasing the likelihood of repeat visits.

5. Query 5 calculates merchandise revenue per Disney park. It joins four tables: Purchase, Merchandise, Store, and Park. The query filters for purchases made on or after January 1, 2023, and only includes merchandise priced at $25 or more. For each park, it computes the total revenue from merchandise sales and the number of units sold. The results are grouped by park location and ordered by total revenue in descending order, so the parks generating the most merchandise revenue appear first.

<img width="967" height="328" alt="Screenshot 2025-10-26 at 12 49 59 PM" src="https://github.com/user-attachments/assets/25678af3-090a-4081-a3f3-27984992674d" />

Query 5 provides managers with a clear view of merchandise performance across parks. By focusing on recent sales (2023 onward) and filtering for higher‑value items ($25+), it highlights meaningful revenue drivers rather than low‑value transactions. The results show which parks are generating the most merchandise revenue and how many units are being sold. This insight helps managers do a large number of things, some of which include identifying which parks are most profitable in terms of merchandise sales and allocating inventory and marketing resources more effectively.

6. Query 6 calculates the total merchandise revenue generated by Disney movies, grouped by the year each movie was released. It joins three tables: Movie, Merchandise, and Purchase. The query uses YEAR(Movie.releaseDate) to extract the release year of each movie. It then sums the prices of all merchandise items sold to calculate the total revenue associated with movies released in that year. The results are grouped by release year and ordered in ascending order, so the earliest years appear first.

<img width="565" height="371" alt="Screenshot 2025-10-26 at 12 55 26 PM" src="https://github.com/user-attachments/assets/ccdc1667-a942-4ce6-8cdb-f9fb3e4df347" />

Query 6 provides managers with a year‑by‑year breakdown of merchandise revenue tied to Disney movie releases. Grouping merchandise sales by the release year of the associated films highlights how different movie cohorts have performed in generating merchandise revenue. This information is valuable for: Trend analysis (Understanding which years, and therefore which movie releases, drove the most merchandise sales), Strategic planning (Identifying whether newer releases are outperforming or underperforming older ones in merchandise revenue), and Resource allocation (Guiding marketing and production teams on which types of movies or release years to emphasize in future merchandise campaigns).

7. Query 7 identifies customers who have not made any purchases since January 1, 2008. It joins the Customer table with the Purchase table on the customer ID. The WHERE NOT EXISTS subquery checks whether a given customer has any purchase records dated on or after January 1, 2008. If no such record exists, that customer is included in the results.

<img width="544" height="460" alt="Screenshot 2025-10-26 at 12 59 41 PM" src="https://github.com/user-attachments/assets/bfbf923f-8df4-4f11-a88d-8c908bb672a4" />

Query 7 allows managers to identify customers who have been inactive for a long period of time (no purchases since 2008). These customers represent a segment that may require re‑engagement strategies, such as targeted marketing campaigns, loyalty incentives, or personalized outreach to encourage them to return. By listing their names and email addresses, managers can directly contact these customers with tailored offers. This insight helps the business: reconnect with lapsed customers, understand long‑term churn patterns, and design campaigns to win back inactive segments. Ultimately, this query supports customer relationship management by highlighting opportunities to revive dormant customer accounts and increase revenue through reactivation.

8. Query 8 retrieves customer information alongside details about family rides at their favorite park. It joins four tables: Customer, Visit, Park, and Attraction. The query calculates each customer’s visit duration and filters results to only include customers whose visit duration is longer than the average visit duration across all visits. It further restricts results to customers whose favorite park is either Magic Kingdom or Hollywood Studios, and only lists attractions of type Family Ride at those parks. Results are ordered by visit duration in descending order, so the longest visits appear first.

<img width="527" height="409" alt="Screenshot 2025-10-26 at 1 04 59 PM" src="https://github.com/user-attachments/assets/8d596468-1fa2-4c90-a31a-31c82fc0508b" />

Query 8 helps managers identify customers who spend more time than average at Disney parks, specifically those who favor Magic Kingdom or Hollywood Studios. By also listing the family rides available at their favorite park, managers can see which attractions are most relevant to these high‑engagement customers. This information is valuable because knowing their favorite parks and the family rides available there helps managers design targeted promotions, and personalized experiences and insights can guide resource allocation (e.g., staffing, ride maintenance, or marketing) toward attractions that appeal to long‑stay visitors. Ordering by visit duration makes it easy to prioritize the most loyal and engaged customers for outreach or rewards programs.

9. Query 9 calculates each genre’s average, highest, and lowest, and count of movies (total) while focusing on recent, relevant genres (action, adventure, fantasy) released after 2010. It then uses a subquery to keep only the genres whose average box office exceeds the overall average across all movies.

<img width="1164" height="320" alt="Screenshot 2025-10-26 at 1 09 37 PM" src="https://github.com/user-attachments/assets/94bcbde3-9121-4a50-b804-effadc8d77b0" />

Query 9 highlights which modern genres (Action, Adventure, Fantasy) have been the strongest performers since 2010. By calculating the average, maximum, minimum, and total number of movies per genre, it provides a comprehensive performance snapshot. This insight helps executives and analysts identify which genres consistently deliver strong box office returns, spot blockbuster‑heavy genres, understand the risk floor, and gauge how much output each genre contributes. Ordering by average box office makes it easy to prioritize the genres that are most profitable overall.

10. Query 10 joins the Movie, Casting, and Actor tables to link actors with the films they have appeared in. It groups results by each actor’s details and calculates two aggregates: the total number of movies and the highest box office revenue among those movies. The HAVING clause filters the results to only include actors who have appeared in at least three movies and who have starred in at least one film with box office earnings above the overall average across all movies. The final output lists each qualifying actor along with their personal details, movie count, and best box office performance.

<img width="1192" height="257" alt="Screenshot 2025-10-26 at 1 13 20 PM" src="https://github.com/user-attachments/assets/d171e8af-0267-4d6b-bd21-2807a068f00f" />

Query 10 highlights actors who combine both experience and commercial success. By requiring at least three movie appearances, it ensures that only actors with a consistent track record are considered, filtering out one‑hit wonders. The additional condition, that they must have been in a movie performing above the industry’s average box office, identifies actors who have proven their ability to contribute to financially successful projects. This information is valuable for casting directors, producers, and executives who want to minimize risk when selecting talent for future films. It pinpoints actors who not only bring reliability through multiple appearances but also have demonstrated appeal to audiences, making them strong candidates for roles in upcoming high‑budget or strategically important productions.

# Database Information
Name of the database: ns_Group4
Procedures are labeled TP_Qx, x being the query number







