# Future Sages

### **Authentication Table**
**Description**: Stores authentication information for users, including user ID and encrypted password.

- **Columns**:
    - `User_ID`: Unique user ID (INT) `Primary key`
    - `Password_Hash`: Encrypted password hash (VARCHAR)
    - `Password_Salt`: Password salt used in hashing (VARCHAR)
    - `Status`: User status (INT), such as 1 for "Active", 0 for "Inactive"

- **Operations**:
    - **Add** new authentication data
    - **Edit** encrypted password
    - **Delete** authentication data
    - **View** authentication data for users

### **User Table**
**Description**: Contains data of users registered in the system.

- **Columns**:
    - `User_ID`: Unique user ID (INT) `Primary key & Foreign key`
    - `User_Name`: Full name of the user (VARCHAR)
    - `User_Image`: Link to the user's image (VARCHAR)
    - `User_Phone`: Mobile number (VARCHAR)
    - `User_Email`: Email address (VARCHAR)
    - `User_Gender`: Gender (VARCHAR)
    - `User_Birthdate`: Birthdate (DATE)
    - `User_Rank`: User rank or type (VARCHAR), such as "Admin", "Student", "Supervisor"
    - `Status`: User status (INT), such as 1 for "Active", 0 for "Inactive"
    - `Created_Date`: Record creation date (DATE)
    - `Updated_Date`: Last record update date (DATE)

- **Operations**:
    - **Add** a new user
    - **Edit** user data
    - **Delete** a user
    - **View** the list of users

### **Entities Table**
**Description**: Stores information about various entities, such as schools or departments, including managers and contact information.

- **Columns**:
    - `Entity_ID`: Unique entity ID (INT) `Primary key`
    - `Entity_Name`: Name of the entity (VARCHAR)
    - `Manager_ID`: Manager's ID (VARCHAR) `Foreign key`
    - `Entity_Phone`: Entity's mobile number (VARCHAR)
    - `Entity_Email`: Entity's email address (VARCHAR)
    - `Entity_Image`: Link to the entity's image (VARCHAR)
    - `Status`: Entity status (INT), such as 1 for "Active", 0 for "Inactive"
    - `Created_Date`: Record creation date (DATE)
    - `Updated_Date`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new entity
    - **Edit** entity data
    - **Delete** an entity
    - **View** the list of entities

### **Students Table**
**Description**: Contains data of registered students, including basic contact information.

- **Columns**:
    - `Student_ID`: Unique student ID (INT) `Primary key & Foreign key`
    - `Student_Name`: Full name of the student (VARCHAR)
    - `Student_Phone`: Mobile number (VARCHAR)
    - `Student_Email`: Email address (VARCHAR)
    - `Status`: Student status (INT), such as 1 for "Active", 0 for "Inactive"
    - `Created_Date`: Record creation date (DATE)
    - `Updated_Date`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new student
    - **Edit** student data
    - **Delete** a student
    - **View** the list of students based on the group

### **Entity_Students Table**
**Description**: Stores information about the association of students with entities, allowing assignment of students to specific entities.

- **Columns**:
    - `Entity_ID`: Entity ID (INT) `Primary key`
    - `Student_ID`: Student ID (INT)
    - `Status`: Association status (INT), 1 for "Active", 0 for "Inactive"
    - `Created_Date`: Record creation date (DATE)
    - `Updated_Date`: Last record update date (DATE)

- **Operations**:
    - **Add** a new association between a student and an entity
    - **Edit** the status of the association
    - **Delete** an existing association
    - **View** the list of students associated with a particular entity
    - **View** the entities associated with a particular student

### **Groups Table**
**Description**: Stores information about groups within entities and allows assignment of managers to the group.

- **Columns**:
    - `Entity_ID`: Entity ID to which the group belongs (INT) `Composite primary key & Foreign key`
    - `Group_ID`: Unique group ID (INT) `Composite primary key`
    - `Group_Name`: Name of the group (VARCHAR)
    - `Group_Image`: Link to the group's image (VARCHAR)
    - `Status`: Group status (INT), such as 1 for "Active", 0 for "Inactive"
    - `Created_Date`: Record creation date (DATE)
    - `Updated_Date`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new group
    - **Edit** group data
    - **Delete** a group
    - **View** the list of groups based on the entity

### **Student_Groups Table**
**Summary**: This table stores the relationships between students and groups to which they belong, allowing a student to belong to multiple groups.

- **Columns**:
    - `Entity_ID`: Entity ID to which the group belongs (INT) `Composite Foreign key`
    - `Group_ID`: Group ID (INT) `Composite Foreign key`
    - `Student_ID`: Student ID (INT) `Foreign key`
    - `Link_ID`: Unique link ID (INT) `Primary key`
    - `Rank`: User rank or type (VARCHAR), such as "Admin", "Student", "Supervisor"
    - `Status`: Association status (INT), such as 1 for "Active", 0 for "Inactive"
    - `Created_Date`: Record creation date (DATE)
    - `Updated_Date`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new association between a student and a group
    - **Edit** the association
    - **Delete** an association
    - **View** the list of groups associated with each student
    - **View** the list of students associated with each group
        
### **Domains Table**
**Description**: Includes main domains or categories (e.g., Family, Education).

- **Columns**:
    - `Entity_ID`: Entity ID to which the group belongs (INT) `Composite primary key & Foreign key`
    - `Domain_ID`: Unique domain ID (INT) `Composite primary key`
    - `Domain_Name`: Name of the domain (VARCHAR)
    - `Domain_Image`: Link to the domain's image (VARCHAR)
    - `Domain_Order`: Order of the domain (INT)
    - `Status`: Domain status (INT), such as 1 for "Active", 0 for "Inactive"
    - `Created_Date`: Record creation date (DATE)
    - `Updated_Date`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new domain
    - **Edit** domain data
    - **Delete** a domain
    - **View** the list of domains in a specific order
        
### **Sections Table**
**Description**: Contains subsections belonging to the main domains.

- **Columns**:
    - `Entity_ID`: Entity ID to which the group belongs (INT) `Composite primary key & Composite Foreign key`
    - `Domain_ID`: Unique domain ID (INT) `Composite primary key & Composite Foreign key`
    - `Section_ID`: Unique section ID (INT) `Composite primary key`
    - `Section_Serial_Number`: Unique serial Number (UniqueIdentifier) `Secondray primary key`
    - `Section_Name`: Name of the section (VARCHAR)
    - `Section_Image`: Link to the section's image (VARCHAR)
    - `Section_Order`: Order of the section within the domain (INT)
    - `Status`: Section status (INT), such as 1 for "Active", 0 for "Inactive"
    - `Created_Date`: Record creation date (DATE)
    - `Updated_Date`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new section
    - **Edit** section data
    - **Delete** a section
    - **View** the list of sections based on the domain
        
### **Topics Table**
**Description**: Contains topics within each section.

- **Columns**:
    - `Entity_ID`: Entity ID to which the group belongs (INT) `Composite primary key & Composite Foreign key`
    - `Domain_ID`: Unique domain ID (INT) `Composite primary key & Composite Foreign key`
    - `Section_ID`: Unique section ID (INT) `Composite primary key & Composite Foreign key`
    - `Topic_ID`: Unique topic ID (INT) `Composite primary key`
    - `Topic_Serial_Number`: Unique serial Number (UniqueIdentifier) `Secondray primary key`
    - `Topic_Name`: Name of the topic (VARCHAR)
    - `Topic_Image`: Link to the topic's image (VARCHAR)
    - `Topic_Order`: Order of the topic within the section of domain (INT)
    - `Status`: Topic status (INT), such as 1 for "Active", 0 for "Inactive"
    - `Created_Date`: Record creation date (DATE)
    - `Updated_Date`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new topic
    - **Edit** topic data
    - **Delete** a topic
    - **View** the list of topics based on the section
        
        
### **Competitions Table**
**Description**: Contains competition data, including questions, time, and stages.

- **Columns**:
    - `Entity_ID`: Entity ID to which the group belongs (INT) `Composite primary key & Composite Foreign key`
    - `Domain_ID`: Unique domain ID (INT) `Composite primary key & Composite Foreign key`
    - `Section_ID`: Unique section ID (INT) `Composite primary key & Composite Foreign key`
    - `Topic_ID`: Unique topic ID (INT) `Composite primary key & Composite Foreign key`
    - `Competition_ID`: Unique competition ID (INT) `Composite primary key`
    - `Competition_Serial_Number`: Unique serial Number (UniqueIdentifier) `Secondray primary key`
    - `Competition_Name`: Name of the competition (VARCHAR)
    - `Competition_Time_Limit`: Time limit (INT)
    - `Competition_Questions_Count`: Number of questions (INT)
    - `Competition_Stages_Count`: Number of stages (INT)
    - `Competition_Stages`: stages with there info and questions (Json) 
    - `Competition_Image`: Link to the competition's image (VARCHAR)
    - `Competition_Enrichment_Text`: Link to enrichment text (VARCHAR)
    - `Competition_Is_With_Sound`: is Competition With Sound or Not (Bit)
    - `Status`: Competition status (INT), such as 1 for "Active", 0 for "Inactive"
    - `Created_Date`: Record creation date (DATE)
    - `Updated_Date`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new competition
    - **Edit** competition data
    - **Delete** a competition
    - **View** the list of competitions
        
### **User_Round Table**
**Description**: Rounds user Round in domains, sections, and topics.

- **Columns**:
    - `Entity_ID`: Entity ID to which the group belongs (INT) `Composite primary key & Composite Foreign key`
    - `Domain_ID`: Unique domain ID (INT) `Composite primary key & Composite Foreign key`
    - `Section_ID`: Unique section ID (INT) `Composite primary key & Composite Foreign key`
    - `Topic_ID`: Unique topic ID (INT) `Composite primary key & Composite Foreign key`
    - `Competition_ID`: Unique competition ID (INT)  `Composite primary key & Composite Foreign key`
    - `User_ID`: User ID (INT) `Composite primary key & Foreign key`
    - `Round_Serial_Number`: Unique serial Number (UniqueIdentifier) `Secondray primary key`
    - `Score`: Earned score (FLOAT)
    - `Status`: Record status (INT), such as 1 for "Active", 0 for "Inactive"
    - `Created_Date`: Record creation date (DATE)
    - `Updated_Date`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new Round record
    - **Edit** user Round
    - **Delete** a Round record
    - **View** user Round in specific domains
        

### **Plans Table**
**Description**: Stores information about available subscription plans, including the number of allowed groups and students, and validity duration.

- **Columns**:
    - `Plan_ID`: Unique plan ID (INT)
    - `Plan_Name`: Name of the plan (VARCHAR), such as "Basic Plan", "Premium Plan"
    - `Allowed_Groups`: Maximum allowed number of groups (INT)
    - `Allowed_Students`: Maximum allowed number of students (INT)
    - `Duration`: Validity duration (VARCHAR), such as "Month", "Year"
    - `Price`: Subscription price (DECIMAL)
    - `Description`: Brief description about the plan (TEXT)
    - `Status`: Plan status (INT), such as 1 for "Available", 0 for "Unavailable"
    - `Created_Date`: Record creation date (DATE)
    - `Updated_Date`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new plan
    - **Edit** plan data
    - **Delete** a plan
    - **View** the list of available plans
        
### **Subscriptions Table**
**Description**: Stores subscription information for entities, including the package of available features such as the number of groups and students.

- **Columns**:
    - `Subscription_ID`: Unique subscription ID (INT)
    - `Plan_ID`: Plan ID (INT)
    - `Entity_ID`: Entity ID (INT)
    - `Start_Date`: Subscription start date (DATE)
    - `End_Date`: Subscription end date (DATE)
    - `Subscription_Status`: Subscription status (VARCHAR), such as "Active", "Expired"
    - `Status`: Record status (INT), such as 1 for "Active", 0 for "Inactive"
    - `Created_Date`: Record creation date (DATE)
    - `Updated_Date`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new subscription
    - **Edit** subscription data
    - **Cancel** a subscription
    - **View** the list of subscriptions for entities
        
- **Use Cases**:
    - When **adding a new entity**, a default subscription should be created for it.
    - When **editing an entity**, its subscription information can be modified.
    - When **deleting an entity**, the associated subscription should be deleted.
    - Ensure that the number of groups and students does not exceed the allowed limits in the subscription.
        
### **Subscription_Payments Table**
**Description**: Stores information about payments related to subscriptions, including payment date, amount, and payment status.

- **Columns**:
    - `Payment_ID`: Unique payment ID (INT)
    - `Subscription_ID`: Associated subscription ID (INT)
    - `Payment_Date`: Date of payment (DATE)
    - `Amount`: Amount paid (DECIMAL)
    - `Payment_Method`: Payment method (VARCHAR), such as "Credit Card", "Bank Transfer"
    - `Payment_Status`: Payment status (VARCHAR), such as "Paid", "Pending", "Canceled"
    - `Transaction_ID`: Transaction number from the payment system (VARCHAR)
    - `Status`: Payment status (INT), such as 1 for "Active", 0 for "Inactive"
    - `Created_Date`: Record creation date (DATE)
    - `Updated_Date`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new payment
    - **Edit** payment data
    - **Delete** a payment
    - **View** the list of payments related to subscriptions
