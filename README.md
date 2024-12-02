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
## Updated Data Model
![Last_Data_Model](https://github.com/user-attachments/assets/1fcb6cf4-03be-4f66-ae32-2bb06d151936)

There were a few changes made to the data model which are worth pointing out. A Many to Many recursive relationship was added to the Fighters entity which now displays the fighter ID of the oppenent opposite of a fighter in a given match. A fighter can have many openents and an openent will be oposite of many fighters throughout their career. The modality between Fighters and Belts was also altered to further distingiush their relationship. A fighter can have 0 to many belts but a belt can only have one fighter. Another change to the data model was the addition of the currentRankings attribute to the fighter entity, which stores each fighter's current ranking information. Finally, the database was populated with many more entries to enhance visualizations and query results.
## Data Dictionary 
![image](https://github.com/user-attachments/assets/0374d34a-905e-4367-89c4-29a0982a9ff9)
<img width="710" alt="Screenshot 2024-12-02 at 2 36 38 PM" src="https://github.com/user-attachments/assets/8212111c-e8be-4a21-81d4-2ce4085e9f17">
<img width="716" alt="Screenshot 2024-12-02 at 2 35 40 PM" src="https://github.com/user-attachments/assets/689483d5-839f-493f-824e-de897447044c">

## Five Complex Queries 

## Three Visualizations
