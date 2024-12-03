# UFC-Database-2
## Team Name: 
  We're Using Chat
## Team Members:
* Benjamin Brown - https://github.com/bdb12838
* Matthew Burt - https://github.com/matthewburt915
* Jared Eidson - https://github.com/jke99240
* Harrison Mcclure - https://github.com/Harrison-mcclure
* John Overstreet - https://github.com/joo11882
## Scenario Description (Why does this data matter?):
This database models the fighters, events, customers, and employees of the UFC so that the upper level management, like Dana White, can make decisions to drive profit and popularity. It will allow management to schedule marquee fights, improve advertising, and decide fighter bonus pay. By capturing detailed information about fighters’ performance, event scheduling, customer engagement and employee responsibilities, the database that our group has created will support decision making in several areas. In conclusion, this database will be an invaluable tool for UFC management, enabling data-driven decisions that not only optimize operations but also enhance the fan experience, boost fighter performance, and ultimately drive the organization's success.
## Original Data Model
![image](https://github.com/user-attachments/assets/36c9f16b-d590-48f3-a13f-ec1a2c9d441c)

The two main entities in our model are the Events and Fighters entities with the rest of of the model revolving around them in some way or another. Fighters contains information about the atheletes who are contracted by the UFC while Events has data on where the fights take place and how they are viewed. Fighters can fight in many Events and Events have many Fighters. Since this is a many to many relationship we created a weak entity Event Statistics which contains information about a fighter at an event. This entity also holds attributes like payment and fight statistics that are vary depending on the fighter and event.

Another entity that relates to both Fighters and Events is Country which has a one to many relationship with both entities. A country can have many fighters but a fighter can only be from one Country. Along the same lines, a country can host many events but a given event can only happen in one Country. Country stores a country's code (USA), which is the primary key, and a country's name (Canada).

Two entities that have relationships with Fighters is WeightClasses and Belts. WeightClasses stores data on the name of the weightclass and the maximum weight at which fighters can compete at said weightclass. It has a one to many relationship with Fighters as a weightclass has many fighters competing in it but a fighter can only belong to one weightclass at a given time. Belts contains information on the current champions of each weightclass and when they won their belts. Belts has a one to many relationship with Fighters because a Fighter can have multiple belts (if they won the belt of one weightclass and then changed weightclasses and won another one) but a belt can only be held by one fighter. Belts and WeightClasses has a one to one relationship as each weightclass has one belt and each belt belongs to one weightclass.

Another entity in our data model is Employees which stores information on the people who work for the UFC. This data includes their full name, job title, the date they were hired, and the ID of their boss. Employees has a many to many relationship with Events as an event can be worked by many employees and an employee can work many events. Since this is a many to many relationship we created a weak entity called EmployeesWorkingEvent. This new entity shows us which employees are working which events. Employees also has a one to many recursive relationship which is where a boss (who is stored in Employees) has many workers reporting to them but a worker only reports to one boss.

Customers is the last entity in our model and it contains the names, emails, and ages of people who purchase tickets to a UFC event. Customers has a many to many relationship with Events as an event is viewed by many customers and a customer can view many events. Because this is a many to many relationship we created a weak entity that shows which customers are viewing which event, called CustomersViewingEvent. This entity also stores data on the ticket price and the ticket type (PayPerView or inPerson).
## Updated Data Model
![Last_Data_Model](https://github.com/user-attachments/assets/1fcb6cf4-03be-4f66-ae32-2bb06d151936)

There were a few changes made to the data model which are worth pointing out. A Many to Many recursive relationship was added to the Fighters entity which now displays the fighter ID of the oppenent opposite of a fighter in a given match. A fighter can have many openents and an openent will be oposite of many fighters throughout their career. The modality between Fighters and Belts was also altered to further distingiush their relationship. A fighter can have 0 to many belts but a belt can only have one fighter. Another change to the data model was the addition of the currentRankings attribute to the fighter entity, which stores each fighter's current ranking information. Finally, the database was populated with many more entries to enhance visualizations and query results.
## Data Dictionary
![Screenshot 2024-12-03 at 11 33 55 AM](https://github.com/user-attachments/assets/936882a9-3835-4f21-af58-fb42e71dfcfe)

![image](https://github.com/user-attachments/assets/0374d34a-905e-4367-89c4-29a0982a9ff9)

![image](https://github.com/user-attachments/assets/be826c1a-40a3-4485-8778-efd2c31ec947)

![Screenshot 2024-12-03 at 11 33 36 AM](https://github.com/user-attachments/assets/0f509482-11cb-49fc-9d40-c73b8735d75d)

![image](https://github.com/user-attachments/assets/c0b39a22-0258-47ed-a675-e2845ad1f1ee)

![image](https://github.com/user-attachments/assets/b6e97d83-03ee-4091-a464-f096eefa91bc)

![image](https://github.com/user-attachments/assets/ecdbb8c0-5b3e-41f4-af5d-6c5918ffec9a)

![image](https://github.com/user-attachments/assets/6fc86ebe-d405-4be6-bae0-3e87a288142e)

![image](https://github.com/user-attachments/assets/b2e7457c-c5fa-483b-b95f-c3a7b5c4fe13)

![image](https://github.com/user-attachments/assets/0146862a-6ec4-4548-9b5f-ef6d7bb9f91d)

## Five Complex Queries 
1. Query 1 returns the fighters name , ranking , weight class, and the average win ratio of their opponents. The Fighters table is duplicated (one for main, one for the opponent) and both are joined to EventStatistics. This query is useful so management can easily view the overall quality of opponents that a fighter has faced, which they can use to factor into the rankings. A fighter may be overrated if they have been beating opponents with bad records and vice versa. 

![Screenshot 2024-11-21 at 11 30 45 AM](https://github.com/user-attachments/assets/0ad211b9-2e9f-42f3-82d1-305764644a05)

2. Query 2 shows the month and the corresponding average ticket price by joining the Events table and CustomersViewingEvents table and year is limited to 2024. With this query management can see the average ticket price for each month, which can be useful in scheduling future events. For 2025 the UFC might try and host multiple events in June and October since they had the highest average ticket prices in 2024.

![Screenshot 2024-11-21 at 11 31 38 AM](https://github.com/user-attachments/assets/2c95787c-9a13-4dc0-a0f0-936434991ac6)

3. Query 3 returns the ids, names, job titles, and number of employees managed for all UFC employees. The results are sorted by number of employees managed and then by employee id. This query can be used to see the management structure of the UFC and if some bosses are managing too many or too few employees.

![Screenshot 2024-12-03 at 1 28 58 PM](https://github.com/user-attachments/assets/c597eb3c-afbd-4b80-9c39-53a7988438d9)
  
4. Query 4


5. Query 5

   
## Three Visualizations
1. Visualization 1  shows the average ticket price and attendance by venue. Management can use this visualisation to focus on specific venues. Venues that have high ticket prices and high attendance would draw in more revenue. For example, the Tokyo Dome.

![image](https://github.com/user-attachments/assets/7a6e4e93-fa43-49cd-8cae-c179f07f220f)

2. Visualization 2 shows the average height and wingspan of each weight class. This can help managers of fighters to pick which weight class they want to get into based on their height and wingspan. Since weight is something that a fighter can more or less change, this will help them see which weight class they have a clear height and reach advantage. 

![image](https://github.com/user-attachments/assets/8c238e23-ce6b-4fcf-8aa3-fff943f0419c)

3. Visualization 3
Shows the average payment per fighter. This can help managers by finding out who brings in the most revenue so they can sell more tickets. Can also help the UFC understand what a fighter expects to get paid from each and fight and help them budget their fights in order to maximize profit.

<img width="1094" alt="Screenshot 2024-12-03 at 1 45 04 PM" src="https://github.com/user-attachments/assets/16b4d355-b3de-4faf-94f4-c2d1634933f4">

   
## Database Information
Name of the database: cs_meb61924

Additional information: Each query listed above is marked in the database using stored procedures which can be called using the following format: CALL TP_Q1();
