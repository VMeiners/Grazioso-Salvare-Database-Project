# Grazioso-Salvare-Database-Project

About the Grazioso Salvare Database Project

The Grazioso Salvare Database Project is intended for use in the organization and maintenance of data relating to the client’s rescue animal training organization. Data is provided by the Austin Animal Center and is intended for use by Grazioso Salvare. 

**Motivation**

The motivation behind the Grazioso Salvare Database Project is to meet the client’s requirements for a manageable database in order to organize and manipulate data obtained from the Austin Animal Center in order to accurately and dependably identify and source animals who are prime candidates for rescue training. 

**Required Functionality**

In order to meet the required functionality, the Grazioso Salvare data table dashboard must be capable of the following: 

- Loading an interactive data table dashboard
- Displaying the Grazioso Salvare logo 
- Inclusion of interactive filtering widgets such as radio buttons, dropdown menus, etc. 
- Interactive filtering widgets that allow for filtering of data based on Water Rescue, Mountain or Wilderness Rescue, and Disaster Rescue or Individual Tracking parameters as required by Grazioso Salvara 
- Ability to reset the database to its initial state, displaying all data
- Responsiveness of the data table when filtering and selecting entries
- A responsive geolocation chart which displays the appropriate entry information when selected
- A responsive chart which displays the appropriate information when selected 

**Project Implementation**

To implement the project, the Austin Animal Center dataset, the csv file ‘aac_animal_shelter_outcomes’ was imported into the MongoDB database. The success of the imported document was then verified utilizing ‘show dbs’ in MongoDB. Additional verifications were implemented such as creating indexes and running queries on the AAC database. 

Once the MongoDB portion of the project was verified a success, a CRUD Python Module was created and implemented in order to facilitate interaction between the MongoDB database and the Dash framework. For the CRUD Python Module, connection was established by defining the appropriate host, port, database, and collection. With connection established, methods were implemented in order to allow for creation of entries within the database, reading of existing entries, updating of existing entries, and deletion of existing entries. Each method was tested in order to ensure functionality and can be viewed in the CRUD Functionality section of this document. 

Implementation of the Dash framework took place next wherein the client requirements were established. First, connection was established once again by defining the appropriate host, port, database, and collection. 

With connection established, the layout was updated to include the Grazioso Salvare logo, a unique identifier of significance to the programmer in order to provide a verifiable watermark, and features for the interactive table were added which included, but was not limited to, defining how rows and columns were allowed to be interacted with. Additionally, the interactive filtering options were implemented in the form of a dropdown menu. 

The logic for interactive filtering was added via a method named ‘update_dashboard’. Per the client’s requirements, the options that should be available to users were Water Rescue, Mountain or Wilderness Rescue, and Disaster or Individual Tracking rescue types. Additionally, users needed to be able to reset the values of the data table after filtering was complete.

In order to filter data based on the client’s requirements, the method ‘update_dashboard’ implemented if and elif statements wherein the data was read from the database, searching for animal_type “Dog”. Additional parameters were put into place depending on the rescue type selected. For example, if a user selected Water Rescue, the query would first search for animal_type “Dog”, the sex_upon_outcome of “Intact Female”, and the age_upon_outcome between 26 weeks and 156 weeks. Once those requirements were satisfied, the query looked for breeds meeting the requirements by cycling through the list of acceptable breeds for Water Rescue; “Labrador Retriever Mix”, “Chesapeake Bay Retriever”, and “Newfoundand”. 

Additionally, the methods for ‘update_map’ and ‘update_graph’ were implemented and updated. In terms of a chart to display data, a pie graph was chosen and implemented to provide a visual representation of the breed preference in relation to the selected rescue type while ‘update_map’ would display the appropriate location of an animal selected from the data table. 

**Challenges**

The challenges faced while implementing the Grazioso Salvare database project were the limitations of the virtual desktop Apporto as occasionally connection was lost, resulting in an inability to continue working on the project further. 

##**Dash Functionality** 

Dash was utilized in the Grazioso Salvare database project in order to provide an interactive web application dashboard for users. As Dash is an “open-source Python framework” (Dash framework, n.d., para. 2), it paired well with the use of MongoDB and Python in order to meet client requirements. Additionally, since Dash does not require additional language such as HTML or CSS, creating a functional and polished dashboard. 

The Dash framework consists of the front-end view and back-end controller. With the front-end view, users are presented with an interactive dashboard wherein data can be read and manipulated via widgets such as the dropdown menu for selecting rescue types in terms of dogs. The back-end controller is inaccessible to users, but responsible for implementing code and logic in order to allow for use of the front end widgets. For example, when a user selects the rescue type “Water Rescue”, the data table filters the results for the user on the front-end. In the back-end, the logic is implemented with the requirements set by Grazioso Salvare so that dogs in the preferred breeds for water rescue, such as Labrador Retriever Mixes, that meet the sex upon outcome and age upon outcome requirements are selected from the data. 

**Dash Functionality Screenshots**

The expected result of front-end functionality for the Grazioso Salvare data table dashboard is illustrated in the following series of screenshots. 

**Starting State of Dashboard**
![StartingStateDashboard](https://github.com/user-attachments/assets/502e7a98-39ee-46e0-a983-af5b0717f7cb)
![StartingStateDashboard2](https://github.com/user-attachments/assets/58f17620-3524-4e9e-ab53-0fa303f96c90)

**Dropdown Menu Functionality - Water Rescue**
![WaterRescueFunctionality](https://github.com/user-attachments/assets/9109141b-1eea-4723-b487-6613a05dc41a)

**Dropdown Menu Functionality - Mountain or Wilderness Rescue**
![MountainRescueFunctionality](https://github.com/user-attachments/assets/a6ed91f6-b2c6-46a8-8797-1a0a120a6cc0)

**Dropdown Menu Functionality - Disaster or Individual Tracking**
![DisasterFunctionality](https://github.com/user-attachments/assets/0ac25005-7e86-462d-ba46-5d8c3a056708)

**Dropdown Menu Functionality - Reset State**
![ResetState](https://github.com/user-attachments/assets/ded71a09-1f53-43e6-8d20-2ba7d01047f1)


##**MongoDB Use and Functionality** 

As the client required a database for ingesting data from various animal shelters, as provided by the Austin Animal Center, the application needed to allow for effective data integration of siloed data which is a key feature with MongoDB in terms of schema flexibility (Giamas, 2022). Additionally, Grazioso Salvare intends to allow their program to remain open source. The popularity and accessibility of MongoDB would extend the handling of siloed data to other organizations utilizing the same application in that unknown data types would be accounted for and handled appropriately. 

MongoDB was selected to host Grazioso Salvare’s database platform due to its overall scalability and accessibility (Giamas, 2022) as well. In its current iteration, Grazioso Salvare’s database application consists of one csv file from the Austin Animal Center. In future iterations, the addition of more data will not become a burden on the system due to MongoDB’s ability to vertically and horizontally (Giamas, 2022), allowing for ease of growth. This meets the client’s requirements of leaving the application open source for use by other organizations in that the amount of data for other organizations cannot be accounted for, but must still be planned for. 

The decision to interface MongoDB with Python was due to the ease of integration between the two as PyMongo is the official driver for MongoDB (Giamas, 2022). PyMongo’s integration abilities allow for compatibility in terms of handling lists and dictionaries as well as the ability to work with both JSON and BSON documents (Build a python database with mongodb, n.d.), making data manipulation of the Grazioso Salvare database accessible for users. 

**MongoDB Functionality Screenshots** 

The expected results of MongoDB functionality are illustrated in the following screenshots. 

Importing and Inserting aac_shelter_outcomes.csv Into MongoDB

Verification of CSV Import and Insert Into MongoDB: 

Secondary Verification of CSV Import and Insert Into MongoDB Using Indexing & Query: 

Creating New User in MongoDB: 

Verification of New User in MongoDB: 

Secondary Verification of New User in MongoDB Using RunCommand: 


##**CRUD Functionality Screenshots**

**Testing CRUD Implementation:** 
(The instance of test_insert is unique due to dog instance’s data, programmer’s dog)
![TestingCRUD1](https://github.com/user-attachments/assets/d7a8a128-2a2d-46bc-8360-2af6e12b475c)

**Results of CRUD Testing Implementation:**
![TestingCRUD2](https://github.com/user-attachments/assets/f60a56c0-993c-4fbc-9c83-03e50dcabf53)

**CREATING New Animal Instance:** 
(instance of new_animal unique as database primarily handles dogs and cats, new_animal_type = Primate)
![CreatingNewAnimal](https://github.com/user-attachments/assets/c6356dd2-4629-46d3-b573-9da580fa47a6)

**READING New Animal Instance:**
![ReadingNewAnimal](https://github.com/user-attachments/assets/f9108c8a-d6d2-421d-af37-6f81bff2c05a)

**UPDATING New Animal Instance:** 
![UpdatingNewAnimal](https://github.com/user-attachments/assets/bfc20954-7f35-4879-b5b6-f47cf3291335)

**Verifying UPDATING New Animal Instance:** 
![VerifyingNewAnimalUpdate](https://github.com/user-attachments/assets/20e772ce-0f5d-45a0-bb95-0fb79df809e1)

**DELETING New Animal Instance:** 
![DeletingNewAnimal](https://github.com/user-attachments/assets/67d36ea4-df6f-4914-963b-8fcc59ca746d)


##**Roadmap/Features**

Features which could be implemented in future iterations of the Grazioso Salvare program could include web-accessibility and an interactive dashboard. Additionally, obtaining data from various animal rescue organizations nationwide, rather than only from the Austin Animal Center, could be implemented via web scraping animal rescue websites or by entering partnerships with said rescues.  

**Foreseeable Issues with Proposed Features:**

- Inability to scale the program due to budgetary or technical restraints
- Legality of web scraping animal shelter websites
- Additional time commitment of facilitating a partnership in order to obtain the necessary data

**Contact**
Valerie Meiners

**Resources:** 
Build a python database with mongodb. (n.d.). MongoDB. https://www.mongodb.com/resources/languages/python

Dash framework. (n.d.). Tutorialspoint. https://www.tutorialspoint.com/python_web_development_libraries/python_web_development_libraries_dash_framework.htm

Giamas, A. (2022). Mastering MongoDB 6.x : Expert techniques to run high-volume and fault-tolerant database solutions using MongoDB 6.x: Vol. Third edition. Packt Publishing.
