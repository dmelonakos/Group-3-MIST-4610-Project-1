# Group-3-MIST-4610-Project-1
 
## Team Members
Cooper Waters [@coopw07](https://github.com/coopw07)

David Melonakos [@dmelonakos](https://github.com/dmelonakos)

Noah Hirschfield [@nbh14975](https://github.com/nbh14975)

Jacob Weiszer [@JacobWeisz](https://github.com/JacobWeisz)

Coleman Willis [@Chipolman10](https://github.com/Chipolman10)

## Problem Description
The task is to model the general workings of a gym franchise, MaxFitness. The model is centered on the Gym entity which represents each physical gym location that the company owns and operates. Each gym includes equipment, classes, and personal training sessions for its members. For this project, we have to modeled the various relationships between these and other entities and have populated them with sample data for demonstration purposes. Through the use of the data model, our gym can now be more efficient in identifying consumer trends, keeping track of importance pieces of information, and displaying relationships between the different entities of the gym. This project contains an overview of the data model, a data dictionary, and a list of sample queries that would be valuable for our franchise in the decision making process.

## Data Model and Explanation
Explanation of the Data Model:

Our Data Model is based on our concept of the MaxFitness franchise and the data they would likely want to store. To begin, the Gym entity is the central entity in our data model from which all other entities originate. The Gym has a primary key (gymID), attributes (gymName, gymAddress, gymPhoneNumber), and a foreign key (managerID). In this example, a gym has only one manager, which is represented by a 1-to-1 relationship with the Employee Entity. Additionally, each gym will employ many employees, but an employee will only work for one gym, which is represented by a 1-to-many relationship between the Gym and Employee entities. Regarding the Employee entity itself, it contains information about each employee including their name, position type, address, and phone number.

The Employee entity is then connected to the Classes entity on a 1-to-many relationship because, in this example, an employee may teach many classes, but a class may only be taught by one employee. Regarding the Classes entity, it contains information on specific instances of a class and contains information on the class type (Cycling, Yoga, Kickboxing, etc.), the class capacity, and the scheduled class date. Then, the Classes entity is connected to the Members entity through a many-to-many relationship because a class can have many members and a member can register for many classes. This is represented by an associative entity named ClassRegistration which contains the registration date, along with both the memberID and classID as foreign keys. 

Backtracking a little bit now, the Employee entity is also connected to the PTSessions (PT = Personal Training) entity on a 1-to-many relationship because an employee can teach many personal training sessions, but a personal training session can only be taught by one employee. Similar to the Classes entity, the PTSessions entity contains information on the PT Type, PT description, and session scheduled date, and it records individual instances of a PT Session. Then, the PTSessions entity is connected to the PTRegistration entity on a 1-to-1 relationship because a PT session can only be registered for 1 time. The PTRegistration entity is then connected to the Members entity on a 1-to-many relationship because a member may register for multiple PTSessions, but a registration can only apply to one member. Additionally, regarding the PTRegistration entity, it contains the registration date, along with the member ID and PT session ID as foreign keys.

Next, the Member entity contains information on each of our members including their names, phone numbers, and addresses. The Member entity is connected to the Gym entity on a 1-to-many relationship because a gym can have many members, but a member can belong to only one gym (in this hypothetical). Additionally, the Member entity is connected to the Membership entity on a 1-to-many relationship because a specific membership can apply to many members, but a member can only have one membership. To clarify, the Membership entity contains information about our different membership types (gold, silver, bronze, etc.) along with their prices and benefits included. 

All members also make payments. This is represented by a 1-to-many relationship between the Member and Payment entities because a member can make multiple payments, but a payment can only apply to one member. The Payment entity contains information on the payment amount, date, and method.

Circling back to the Gym entity, every gym has pieces of equipment. This fact is represented by a 1-to-many relationship between the Gym and Equipment entities because a gym can have many pieces of equipment, but a piece of equipment can only belong to one gym. The Equipment entity itself contains information about each individual piece of equipment (identified by their PKs) including its name (treadmill, bench press, etc.), type (cardio, weight-training), date it was bought, and condition. 

Finally, the Equipment entity is connected to the MaintenanceRequest entity on a 1-to-many relationship because a piece of equipment can have many maintenance requests associated with it, but a maintenance request can only apply to one piece of equipment. We also decided to make this an identifying relationship because a maintenance request should not exist if a piece of equipment is not associated with it.


![ssGymDMFinal](https://github.com/user-attachments/assets/09d25c73-b1ee-492c-a994-9e7c49037c6f)

## Data Dictionary
![image](https://github.com/user-attachments/assets/d54f827f-ad2b-4667-b70b-dcc96f20db97)
![image](https://github.com/user-attachments/assets/ecefc316-700f-4f86-8937-420f7ed9facc)
![image](https://github.com/user-attachments/assets/a298120c-fd9c-4d42-b2ae-24fdf8be6a99)
![image](https://github.com/user-attachments/assets/d6b707b2-9424-465d-811f-d08792d81634)
![image](https://github.com/user-attachments/assets/e98d24bd-3f28-499a-8377-5403799fd74d)
![image](https://github.com/user-attachments/assets/044574c5-bc76-4427-afbc-b63f5c3fc540)
![image](https://github.com/user-attachments/assets/e873da4f-9298-409d-b049-f1825b31370b)
![image](https://github.com/user-attachments/assets/4ae141dd-8409-4850-80b0-d55142dceae8)
![image](https://github.com/user-attachments/assets/72049e84-360c-4dc3-9da5-41f4dd73bc3c)
![image](https://github.com/user-attachments/assets/cc0715a5-051a-4b11-ae36-1bdee8f59284)
![image](https://github.com/user-attachments/assets/a5d07371-08e1-4cb7-8dc4-d95728ccf5d5)


## Queries
### Query 1
Query 1 lists the names of gyms that have less than four employees
![image](https://github.com/user-attachments/assets/5e908fc7-2c75-4af6-afbd-29773d11c438)
Description: In order for gyms to be able to meet the demand of its members, we need each gym to have at least four employees. This query lists the number of gyms that don't so that we know which gyms need to hire more employees so that no gym is overwhlemed.
### Query 2
Query 2 lists the Total Members and Total Equipment at each Gym that has more members than pieces of equipment
![image](https://github.com/user-attachments/assets/11db0695-14ec-4375-807c-9df70e80e7ad)
Description: It's important for a gym to have more pieces of equipment than members so that members are not having to stand around and wait for equipment to become available. This query outputs the gyms that we need to add more pieces of equipment to so that we accommodate the number of members there.
### Query 3
Query 3 lists the employee first name, employee last name and count of classIDs for the Employees at our gyms that are teaching three or more classes
![image](https://github.com/user-attachments/assets/e2d84bfe-7579-40dc-bcfe-d794448c7852)
Description: Our company wants to award any employees that go above and beyond their duties by teaching three or more classes. These employees will be recognized and recieve a raise. It's important to recognize our employees hard work to minimize employee turnover.
### Query 4
Query 4 lists the first name and last name of members not currently enrolled in any classes
![image](https://github.com/user-attachments/assets/773a4ed5-fc43-4066-b196-01d69b78f041)
Description: A gym wants to promote it's classes to maximize revenue and member satisfaction. We would like to promote our classes to members not currently enrolled in any classes so this query will help give us a list of members we can market our advertising towards.

### Query 5
Query 5 lists the average payment amount for each gym
![image](https://github.com/user-attachments/assets/e0d15219-49e5-4c7a-9278-3c95def424e5)                                                                         
Description: A gym wants to keep track of how much members are spending of memberships at each gym on average. This query gives us that result so that we can advertise at gyms with lower averages to maximize profits. It can also tell us which gyms members perfer to pay a premium at and which ones members choose the basic membership.
### Query 6
Query 6 lists the day of the week and the total number of members regsistered for the class where the class category is "yoga"
![image](https://github.com/user-attachments/assets/f20d0cb8-bcf7-4d94-90e3-f95cfe286950)
Description: A gym wants see what day of the week it should add another yoga class for based on how many members are already registered for yoga class. A gym doesn't need to add another class on a Tuesday if Tuesdays are not popular among yoga class enrollees. This query gives us the total number of members registered by day of the week so that we can make an informed decesion about what day of the week the next yoga class should be taught on.
### Query 7
Query 7 counts the number of PT sessions each trainer is teaching
![image](https://github.com/user-attachments/assets/b43bee18-0977-426a-a568-c1b22572b73f)
Description: We don't want to overwhelm our trainers, so using this query we can find which trainers are teaching the most classes and make adjustments to help them balance their schedules.
### Query 8
Query 8 lists the count of each membership type
![image](https://github.com/user-attachments/assets/9b88a85b-5c66-464b-9c47-2cbaf1cf8bac)
Description: This query helps our gym find which memberships are most popular and from there they can investigate why a membership is so popular whether that be the price of the membership or the amenities associated with the membership.
### Query 9
Query 9 lists the member first and last name and their total payments, but only if those members have a total payment value greater than the average total payment value by member
![image](https://github.com/user-attachments/assets/2fc87119-b767-47fa-b3a2-36fbf3e55758)
Description: We are interested in providing a discount to our most loyal members and want to know which members have spent the most money with us so we can apply that discount properly.

### Query 10
Query 10 lists the gym name, equipment number, equipment name, and the date the equipment was bought if the that piece of equipment has never had routine maintenance conducted on it
![image](https://github.com/user-attachments/assets/22267cd6-211a-4669-a9f3-57d477508a78)
Description: Our company wants to stay up to date on the quality of our gym equipment so this query gives us a list of the pieces of equipment that have not had any routine maintenance done on it. By looking at the date the equipment was bought, we can send maintenance people to check older pieces of equipment to make sure they are still in good condition for use. 

## Database Information
Database Name: ns_4610Fa24Group3

Each query listed is bookmarked through stored procedures according to the format CREATE PROCEDURE TP_Qx() and can be called using CALL TP_Qx(), where x represents the query number

