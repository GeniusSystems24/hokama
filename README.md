# Future Sages
[اللغة العربية](/arabic/README.md)
## Database
![database diagram](/image/digram-ERD.svg)
### List of Tables
1. [Authentication Table](#authentication-table): Stores authentication information for users, including user ID and encrypted password.
2. [User Table](#user-table): Contains data of users registered in the system.
3. [Entity Table](#entity-table): Stores information about various entities, such as schools or departments, including managers and contact information.
4. [Student Table](#student-table): Contains data of registered students, including basic contact information.
5. [EntityStudent Table](#entitystudent-table): Stores information about the association of students with entities, allowing assignment of students to specific entities.
6. [Group Table](#group-table): Stores information about groups within entities and allows assignment of managers to the group.
7. [GroupMember Table](#groupmember-table): Stores the relationships between students and groups to which they belong, allowing a student to belong to multiple groups.
8. [Domain Table](#domain-table): Includes main domains or categories (e.g., Family, Education).
9. [Section Table](#section-table): Contains subsections belonging to the main domains.
10. [Topic Table](#topic-table): Contains topics within each section.
11. [Competition Table](#competition-table): Contains competition data, including questions, time, and stages.
12. [UserRound Table](#userround-table): Rounds user Round in domains, sections, and topics.
13. [Plan Table](#plan-table): Stores information about available subscription plans, including the number of allowed groups and students, and validity duration.
14. [Subscription Table](#subscription-table): Stores subscription information for entities, including the package of available features such as the number of groups and students.
15. [SubscriptionPayment Table](#subscriptionpayment-table): Stores information about payments related to subscriptions, including payment date, amount, and payment status.

### Table Structures

#### **Authentication Table**
- **Description**: Stores authentication information for users, including user ID and encrypted password.

![alt text](/image/Authentication.svg)
- **Columns**:
    - `UserID`: Unique user ID (INT) `Primary key`
    - `PasswordHash`: Encrypted password hash (VARCHAR)
    - `PasswordSalt`: Password salt used in hashing (VARCHAR)
    - `Status`: User status (INT), such as 1 for "Active", 0 for "Inactive"

- **Operations**:
    - **Add** new authentication data
    - **Edit** encrypted password
    - **Delete** authentication data
    - **View** authentication data for users

#### **User Table**
- **Description**: Contains data of users registered in the system.

![alt text](/image/user.svg)
- **Columns**:
    - `UserID`: Unique user ID (INT) `Primary key & Foreign key`
    - `UserName`: Full name of the user (VARCHAR)
    - `UserImage`: Link to the user's image (VARCHAR)
    - `UserPhone`: Mobile number (VARCHAR)
    - `UserEmail`: Email address (VARCHAR)
    - `UserGender`: Gender (VARCHAR)
    - `UserBirthdate`: Birthdate (DATE)
    - `UserRank`: User rank or type (VARCHAR), such as "Admin", "Student", "Supervisor"
    - `Status`: User status (INT), such as 1 for "Active", 0 for "Inactive"
    - `CreatedDate`: Record creation date (DATE)
    - `UpdatedDate`: Last record update date (DATE)

- **Operations**:
    - **Add** a new user
    - **Edit** user data
    - **Delete** a user
    - **View** the list of users

#### **Entity Table**
- **Description**: Stores information about various entities, such as schools or departments, including managers and contact information.

![alt text](/image/Entity.svg)
- **Columns**:
    - `EntityID`: Unique entity ID (INT) `Primary key`
    - `EntityName`: Name of the entity (VARCHAR)
    - `ManagerID`: Manager's ID (VARCHAR) `Foreign key`
    - `EntityPhone`: Entity's mobile number (VARCHAR)
    - `EntityEmail`: Entity's email address (VARCHAR)
    - `EntityImage`: Link to the entity's image (VARCHAR)
    - `Status`: Entity status (INT), such as 1 for "Active", 0 for "Inactive"
    - `CreatedDate`: Record creation date (DATE)
    - `UpdatedDate`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new entity
    - **Edit** entity data
    - **Delete** an entity
    - **View** the list of entities

#### **Student Table**
- **Description**: Contains data of registered students, including basic contact information.

![alt text](/image/Student.svg)
- **Columns**:
    - `StudentID`: Unique student ID (INT) `Primary key & Foreign key`
    - `StudentName`: Full name of the student (VARCHAR)
    - `StudentPhone`: Mobile number (VARCHAR)
    - `StudentEmail`: Email address (VARCHAR)
    - `Status`: Student status (INT), such as 1 for "Active", 0 for "Inactive"
    - `CreatedDate`: Record creation date (DATE)
    - `UpdatedDate`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new student
    - **Edit** student data
    - **Delete** a student
    - **View** the list of students based on the group

#### **EntityStudent Table**
- **Description**: Stores information about the association of students with entities, allowing assignment of students to specific entities.

![alt text](/image/EntityStudent.svg)
- **Columns**:
    - `EntityID`: Entity ID (INT) `Primary key`
    - `StudentID`: Student ID (INT)
    - `Status`: Association status (INT), 1 for "Active", 0 for "Inactive"
    - `CreatedDate`: Record creation date (DATE)
    - `UpdatedDate`: Last record update date (DATE)

- **Operations**:
    - **Add** a new association between a student and an entity
    - **Edit** the status of the association
    - **Delete** an existing association
    - **View** the list of students associated with a particular entity
    - **View** the entities associated with a particular student

#### **Group Table**
- **Description**: Stores information about groups within entities and allows assignment of managers to the group.

![alt text](/image/Group.svg)
- **Columns**:
    - `EntityID`: Entity ID to which the group belongs (INT) `Composite primary key & Foreign key`
    - `GroupID`: Unique group ID (INT) `Composite primary key`
    - `GroupName`: Name of the group (VARCHAR)
    - `GroupImage`: Link to the group's image (VARCHAR)
    - `Status`: Group status (INT), such as 1 for "Active", 0 for "Inactive"
    - `CreatedDate`: Record creation date (DATE)
    - `UpdatedDate`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new group
    - **Edit** group data
    - **Delete** a group
    - **View** the list of groups based on the entity

#### **GroupMember Table**
**Summary**: This table stores the relationships between students and groups to which they belong, allowing a student to belong to multiple groups.

![alt text](/image/GroupMember.svg)
- **Columns**:
    - `EntityID`: Entity ID to which the group belongs (INT) `Composite Foreign key`
    - `GroupID`: Group ID (INT) `Composite Foreign key`
    - `MemberID`: Member ID `User` (INT) `Foreign key`
    - `LinkID`: Unique link ID (INT) `Primary key`
    - `Rank`: User rank or type (VARCHAR), such as "Admin", "Student", "Supervisor"
    - `Status`: Association status (INT), such as 1 for "Active", 0 for "Inactive"
    - `CreatedDate`: Record creation date (DATE)
    - `UpdatedDate`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new association between a member and a group
    - **Edit** the association
    - **Delete** an association
    - **View** the list of groups associated with each member
    - **View** the list of members associated with each group
        
#### **Domain Table**
- **Description**: Includes main domains or categories (e.g., Family, Education).

![alt text](/image/Domain.svg)
- **Columns**:
    - `EntityID`: Entity ID to which the group belongs (INT) `Composite primary key & Foreign key`
    - `DomainID`: Unique domain ID (INT) `Composite primary key`
    - `DomainName`: Name of the domain (VARCHAR)
    - `DomainImage`: Link to the domain's image (VARCHAR)
    - `DomainOrder`: Order of the domain (INT)
    - `Status`: Domain status (INT), such as 1 for "Active", 0 for "Inactive"
    - `CreatedDate`: Record creation date (DATE)
    - `UpdatedDate`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new domain
    - **Edit** domain data
    - **Delete** a domain
    - **View** the list of domains in a specific order
        
#### **Section Table**
- **Description**: Contains subsections belonging to the main domains.

![alt text](/image/Section.svg)
- **Columns**:
    - `EntityID`: Entity ID to which the group belongs (INT) `Composite primary key & Composite Foreign key`
    - `DomainID`: Unique domain ID (INT) `Composite primary key & Composite Foreign key`
    - `SectionID`: Unique section ID (INT) `Composite primary key`
    - `SectionSerialNumber`: Unique serial Number (UniqueIdentifier) `Secondray primary key`
    - `SectionName`: Name of the section (VARCHAR)
    - `SectionImage`: Link to the section's image (VARCHAR)
    - `SectionOrder`: Order of the section within the domain (INT)
    - `Status`: Section status (INT), such as 1 for "Active", 0 for "Inactive"
    - `CreatedDate`: Record creation date (DATE)
    - `UpdatedDate`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new section
    - **Edit** section data
    - **Delete** a section
    - **View** the list of sections based on the domain
        
#### **Topic Table**
- **Description**: Contains topics within each section.

![alt text](/image/Topic.svg)
- **Columns**:
    - `EntityID`: Entity ID to which the group belongs (INT) `Composite primary key & Composite Foreign key`
    - `DomainID`: Unique domain ID (INT) `Composite primary key & Composite Foreign key`
    - `SectionID`: Unique section ID (INT) `Composite primary key & Composite Foreign key`
    - `TopicID`: Unique topic ID (INT) `Composite primary key`
    - `TopicSerialNumber`: Unique serial Number (UniqueIdentifier) `Secondray primary key`
    - `TopicName`: Name of the topic (VARCHAR)
    - `TopicImage`: Link to the topic's image (VARCHAR)
    - `TopicOrder`: Order of the topic within the section of domain (INT)
    - `Status`: Topic status (INT), such as 1 for "Active", 0 for "Inactive"
    - `CreatedDate`: Record creation date (DATE)
    - `UpdatedDate`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new topic
    - **Edit** topic data
    - **Delete** a topic
    - **View** the list of topics based on the section
        
        
#### **Competition Table**
- **Description**: Contains competition data, including questions, time, and stages.

![alt text](/image/Competition.svg)
- **Columns**:
    - `EntityID`: Entity ID to which the group belongs (INT) `Composite primary key & Composite Foreign key`
    - `DomainID`: Unique domain ID (INT) `Composite primary key & Composite Foreign key`
    - `SectionID`: Unique section ID (INT) `Composite primary key & Composite Foreign key`
    - `TopicID`: Unique topic ID (INT) `Composite primary key & Composite Foreign key`
    - `CompetitionID`: Unique competition ID (INT) `Composite primary key`
    - `CompetitionSerialNumber`: Unique serial Number (UniqueIdentifier) `Secondray primary key`
    - `CompetitionName`: Name of the competition (VARCHAR)
    - `CompetitionTimeLimit`: Time limit (INT)
    - `CompetitionQuestionsCount`: Number of questions (INT)
    - `CompetitionStagesCount`: Number of stages (INT)
    - `CompetitionStages`: stages with there info and questions (Json) 
    - `CompetitionImage`: Link to the competition's image (VARCHAR)
    - `CompetitionEnrichmentText`: Link to enrichment text (VARCHAR)
    - `CompetitionIsWithSound`: is Competition With Sound or Not (Bit)
    - `Status`: Competition status (INT), such as 1 for "Active", 0 for "Inactive"
    - `CreatedDate`: Record creation date (DATE)
    - `UpdatedDate`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new competition
    - **Edit** competition data
    - **Delete** a competition
    - **View** the list of competitions
        
#### **UserRound Table**
- **Description**: Rounds user Round in competitions.

![alt text](/image/UserRound.svg)
- **Columns**:
    - `EntityID`: Entity ID to which the group belongs (INT) `Composite primary key & Composite Foreign key`
    - `DomainID`: Unique domain ID (INT) `Composite primary key & Composite Foreign key`
    - `SectionID`: Unique section ID (INT) `Composite primary key & Composite Foreign key`
    - `TopicID`: Unique topic ID (INT) `Composite primary key & Composite Foreign key`
    - `CompetitionID`: Unique competition ID (INT)  `Composite primary key & Composite Foreign key`
    - `UserID`: User ID (INT) `Composite primary key & Foreign key`
    - `RoundSerialNumber`: Unique serial Number (UniqueIdentifier) `Secondray primary key`
    - `Score`: Earned score (FLOAT)
    - `Status`: Record status (INT), such as 1 for "Active", 0 for "Inactive"
    - `CreatedDate`: Record creation date (DATE)
    - `UpdatedDate`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new Round record
    - **Edit** user Round
    - **Delete** a Round record
    - **View** user Round in specific domains
        

#### **Plan Table**
- **Description**: Stores information about available subscription plans, including the number of allowed groups and students, and validity duration.

![alt text](/image/Plan.svg)
- **Columns**:
    - `PlanID`: Unique plan ID (INT) `primary key`
    - `PlanName`: Name of the plan (VARCHAR), such as "Basic Plan", "Premium Plan"
    - `AllowedGroup`: Maximum allowed number of groups (INT)
    - `AllowedStudent`: Maximum allowed number of students (INT)
    - `Duration`: Validity duration (VARCHAR), such as "Month", "Year"
    - `Price`: Subscription price (DECIMAL)
    - `Description`: Brief description about the plan (TEXT)
    - `Status`: Plan status (INT), such as 1 for "Available", 0 for "Unavailable"
    - `CreatedDate`: Record creation date (DATE)
    - `UpdatedDate`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new plan
    - **Edit** plan data
    - **Delete** a plan
    - **View** the list of available plans
        
#### **Subscription Table**
- **Description**: Stores subscription information for entities, including the package of available features such as the number of groups and students.

![alt text](/image/Subscription.svg)
- **Columns**:
    - `SubscriptionID`: Unique subscription ID (INT) `primary key`
    - `PlanID`: Plan ID (INT) `foreign key`
    - `EntityID`: Entity ID (INT) `foreign key`
    - `StartDate`: Subscription start date (DATE)
    - `EndDate`: Subscription end date (DATE)
    - `SubscriptionStatus`: Subscription status (VARCHAR), such as "Active", "Expired"
    - `Status`: Record status (INT), such as 1 for "Active", 0 for "Inactive"
    - `CreatedDate`: Record creation date (DATE)
    - `UpdatedDate`: Last record update date (DATE)
    
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
        
#### **SubscriptionPayment Table**
- **Description**: Stores information about payments related to subscriptions, including payment date, amount, and payment status.

![alt text](/image/SubscriptionPayment.svg)
- **Columns**:
    - `PaymentID`: Unique payment ID (INT) `primary key`
    - `SubscriptionID`: Associated subscription ID (INT) `foreign key`
    - `PaymentDate`: Date of payment (DATE)
    - `Amount`: Amount paid (DECIMAL)
    - `PaymentMethod`: Payment method (VARCHAR), such as "Credit Card", "Bank Transfer"
    - `PaymentStatus`: Payment status (VARCHAR), such as "Paid", "Pending", "Canceled"
    - `TransactionID`: Transaction number from the payment system (VARCHAR)
    - `Status`: Payment status (INT), such as 1 for "Active", 0 for "Inactive"
    - `CreatedDate`: Record creation date (DATE)
    - `UpdatedDate`: Last record update date (DATE)
    
- **Operations**:
    - **Add** a new payment
    - **Edit** payment data
    - **Delete** a payment
    - **View** the list of payments related to subscriptions

## User Interfaces
### Waterframe diagram
![Waterframe diagram image](/image/31d543109869851.5fdda2da34e98.png)