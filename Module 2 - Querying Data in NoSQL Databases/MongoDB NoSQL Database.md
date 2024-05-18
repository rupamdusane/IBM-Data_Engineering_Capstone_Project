<img width="940" alt="SN_web_lightmode" src="https://github.com/rupamdusane/IBM-Data_Engineering_Capstone_Project/assets/92736419/3c5603a3-6721-4d9d-8cd2-bf9a9195b098">

# Querying data in NoSQL databases

> All of SoftCart's catalog data will be stored on a MongoDB NoSQL server. Create the database `catalog` and import our electronics products from `catalog.json` into a collection named `electronics`. Run test queries against the data and export the collection into a file named `electronics.csv` using only the `_id`, `type`, and `model` fields.

> It is highly recommened that you finish the Setup and Practice Assignment Lab before you proceed with this Assignment.

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


**Task 2 - List out all the databases**


**Task 3 - List out all the collections in the database catalog.**


**Task 4 - Create an index on the field “type”**


**Task 5 - Write a query to find the count of laptops**


**Task 6 - Write a query to find the number of smart phones with screen size of 6 inches.**


**Task 7. Write a query to find out the average screen size of smart phones.**


**Task 8 - Export the fields _id, “type”, “model”, from the ‘electronics’ collection into a file named electronics.csv**


End of assignment.
