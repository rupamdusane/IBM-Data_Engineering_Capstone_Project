<img width="940" alt="SN_web_lightmode" src="https://github.com/rupamdusane/IBM-Data_Engineering_Capstone_Project/assets/92736419/3c5603a3-6721-4d9d-8cd2-bf9a9195b098">

# Querying data in NoSQL databases

### Assignment Overview
In this assignment, you will perform a series of tasks in a single exercise. But before proceeding with the assignment, you will install the ‘mongoimport’ and ‘mongoexport’ in the lab environment and then download the JavaScript Object Notation (JSON) file. The exercise requires you to first import the JSON file to the MongoDB server into a database and a collection (electronics), then list out all the databases and the collections in the database catalog. Next, you will list the first five documents in the collection, and then you will write a query to find the count of laptops, the number of mobile phones with a screen size of 6 inches, and the average screen size of smartphones. Finally, you will export the ID, type, and model fields from the collection into a Comma Separated Values (CSV) file. After performing each task, you will take a screenshot of the command used, and the output obtained and give a name to the screenshot.

> All of SoftCart's catalog data will be stored on a MongoDB NoSQL server. Create the database `catalog` and import our electronics products from `catalog.json` into a collection named `electronics`. Run test queries against the data and export the collection into a file named `electronics.csv` using only the `_id`, `type`, and `model` fields.


# Scenario
You are a data engineer at an e-commerce company. Your company needs you to design a data platform that uses MongoDB as a NoSQL database. You will be using MongoDB to store the e-commerce catalog data.

# Objectives
In this assignment you will:
- import data into a MongoDB database.
- query data in a MongoDB database.
- export data from MongoDB.
# Tools / Software
- MongoDB Server
- MongoDB Command Line Backup Tools

# Exercise 1 - Install Dependencies
Before you proceed with the assignment :

This assignment will be using `mongoimport` and `mongoexport` commands from the MongoDB CLI Database Tools library. First I will check to see if the library is installed by running one of these commands.
```

mongoimport

```
> bash: mongoimport: command not found
Since the command is not recognized, I will need to manually install the library. First I will determine the Linux Platform and Architecture using the `lsb_release -a` command.

```

lsb_release -a

```
```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.6 LTS
Release:        18.04
Codename:       bionic
```
The processor type can be found using `uname -p`

```

uname -p

```
> x86_64

Now I can select the appropriate package for MongoDB Database Tools from the following link: https://www.mongodb.com/try/download/database-tools

The package I will be installing is `Ubuntu 18.04 x86_64` with the `.deb` extension.
```

sudo wget https://fastdl.mongodb.org/tools/db/mongodb-database-tools-ubuntu1804-x86_64-100.6.1.deb

```
I will use `apt install` to install the package.

```

sudo apt install ./mongodb-database-tools-ubuntu1804-x86_64-100.6.1.deb

```
Now I will verify the installation by running the `mongoimport` command again.
```

mongoimport

```
```
> 2023-02-05T15:11:01.000-0500    no collection specified
> 2023-02-05T15:11:01.000-0500    using filename '' as collection
> 2023-02-05T15:11:01.000-0500    error validating settings: invalid collection name: collection name cannot be an empty string
```
The command is now recognized, meaning the package has successfully been installed.

### OR

To install these tools run the below commands on the terminal.
```
wget https://fastdl.mongodb.org/tools/db/mongodb-database-tools-ubuntu1804-x86_64-100.3.1.tgz
tar -xf mongodb-database-tools-ubuntu1804-x86_64-100.3.1.tgz
export PATH=$PATH:/home/project/mongodb-database-tools-ubuntu1804-x86_64-100.3.1/bin
echo "done"
```
Verify that the tools got installed, by running the below command on the terminal.
```
mongoimport --version
```
If you do not get an error and get a version number, you are good to go ahead.

Download the catalog.json file from https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0321EN-SkillsNetwork/nosql/catalog.json.

# Exercise 2 - Working with MongoDB
**Task 1 - Import ‘catalog.json’ into mongodb server into a database named ‘catalog’ and a collection named ‘electronics’**

![mongoimport](https://github.com/rupamdusane/IBM-Data_Engineering_Capstone_Project/assets/92736419/dc9e6430-cbc7-4806-8986-1a8b62d65afa)


**Task 2 - List out all the databases**

![list-dbs](https://github.com/rupamdusane/IBM-Data_Engineering_Capstone_Project/assets/92736419/80339340-ece4-4c27-be61-f42ba0280e5c)


**Task 3 - List out all the collections in the database catalog.**

![list-collections](https://github.com/rupamdusane/IBM-Data_Engineering_Capstone_Project/assets/92736419/405110d6-d53f-40ac-9b47-5d4b4cb94a92)


**Task 4 - Create an index on the field “type”**

![create-index](https://github.com/rupamdusane/IBM-Data_Engineering_Capstone_Project/assets/92736419/d88727cd-adf0-4eb6-ac09-51754e365124)


**Task 5 - Write a query to find the count of laptops**

![mongo-query-laptops](https://github.com/rupamdusane/IBM-Data_Engineering_Capstone_Project/assets/92736419/7ea73ea4-c163-469c-bcf0-1451242879e2)


**Task 6 - Write a query to find the number of smart phones with screen size of 6 inches.**

![mongo-query-mobiles1](https://github.com/rupamdusane/IBM-Data_Engineering_Capstone_Project/assets/92736419/14a1e329-3641-4075-b259-6a3aa4d63e9a)


**Task 7. Write a query to find out the average screen size of smart phones.**

![mongo-query-mobiles2](https://github.com/rupamdusane/IBM-Data_Engineering_Capstone_Project/assets/92736419/77191ffc-605c-4846-8029-ca90f4f4b1b2)


**Task 8 - Export the fields _id, “type”, “model”, from the ‘electronics’ collection into a file named electronics.csv**

![mongoexport](https://github.com/rupamdusane/IBM-Data_Engineering_Capstone_Project/assets/92736419/24207fe2-75bb-4b87-ac93-1e2803df7e5a)


End of assignment.
