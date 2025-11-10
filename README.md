## 4.3 Exercises Q2

You are tasked with designing a database to manage the administration of the "Database Fiesta" contest, where students from higher learning institutions or secondary schools can register in groups of three to four members, with a mentor advising each group. Each student is identified by a unique ID and has relevant details such as name, telephone number, and email. Mentors, who can advise up to three groups, are associated with their name, telephone number, and institution or school. Institutions or schools, each identified by an ID, name, and address (street, city, postcode, state), may have one or more student groups registered. The database will track group registrations, which include the registration date, category and group members' details. Each student group creates one poster for the contest, which is assigned an ID, title, and description. The posters are evaluated by two judges, each with an ID, name, affiliation (organization), and email, with their organization details stored as well (including organization ID, name, and address). Each judge can evaluate up to ten posters, assessing them based on six aspects: Coverage of the Topic, Use of Graphics, Organization, Layout and Design, Mechanics, and Comprehension. The database will store the total marks and results for each poster, allowing for the selection of first, second, and third place winners in each category based on the combined scores from both judges.


## ERD

<img width="927" height="599" alt="Untitled Diagram drawio" src="https://github.com/user-attachments/assets/0e8966bc-da6f-4371-9e01-29b441b980aa" />


# Business Rules

The entity STUDENT has attributes STUDENTID as primary key, NAME, TELNUM, EMAIL, and GROUPID as foreign key.

The entity GROUP has attributes GROUPID as primary key, REGISTRATIONDATE, CATEGORY, MENTORID as foreign key, and INSTITUTEID as foreign key.

The entity INSTITUTE has attributes INSTITUTEID as primary key, NAME, and ADDRESSID as foreign key.

The entity MENTOR has attributes MENTORID as primary key, NAME, TELNUM.

The entity POSTER has attributes POSTERID as primary key, TITLE, DESCRIPTION, and GROUPID as foreign key.

The entity JUDGE has attributes JUDGEID as primary key, NAME, EMAIL, and ORGID as foreign key.

The entity ORGANIZATION has attributes ORGID as primary key, NAME, and ADDRESSID as foreign key.

The entity ADDRESS has attributes ADDRESSID as primary key, STREET, CITY, POSTCODE, and STATE.

The entity RESULT has attributes RESULTID as primary key, FIRSTPLACE, SECONDPLACE, THIRDPLACE, and DEFAULT.

The composite entity CONTEST has attributes POSTERID and JUDGEID as both primary and foreign keys. It also has attributes TOPICCOVERAGE, GRAPHICSUSE, ORGANIZATION, LAYOUTANDDESIGN, MECHANICS, TOTALMARKS and RESULTID as foreign key.

Each GROUP must have between three and four STUDENT members (Cardinality: 3,4). Each STUDENT belongs to exactly one GROUP (Cardinality: 1,1).

Each MENTOR can advise zero to three GROUPs (Cardinality: 0,3). Each GROUP is advised by exactly one MENTOR (Cardinality: 1,1).

Each GROUP must create exactly one POSTER (Cardinality: 1,1). Each POSTER is created by exactly one GROUP (Cardinality: 1,1).

Each POSTER is evaluated by exactly two JUDGEs (Cardinality: 2,2). Each JUDGE can evaluate one to ten POSTERs (Cardinality: 1,10).

The overall RESULT for a poster is determined by the combined scores from the two judges on the CONTEST entity.

Each INSTITUTE can have one or more GROUPs registered (Cardinality: 1,N). Each GROUP is registered under exactly one INSTITUTE (Cardinality: 1,1).

Each INSTITUTE is located at exactly one ADDRESS (Cardinality: 1,1). Each ADDRESS can be associated with one INSTITUTEs.

Each ORGANIZATION is located at exactly one ADDRESS (Cardinality: 1,1). Each ADDRESS can be associated with one ORGANIZATIONs.

Each JUDGE belongs to exactly one ORGANIZATION. Each ORGANIZATION has one to many JUDGEs.

The foreign key INSTITUTEID that's supposed to be an attribute of both entity STUDENT and MENTOR was omitted because of redundancy. The INSTITUTEID of both the STUDENTs and the MENTORs can refer to the entity GROUP, which already has the foreign key INSTITUTEID.

