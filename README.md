# Avtaar Assignment 2

## SQL DB Queries for User-Events

### Write DB Queries for the following : 

1. Query to create the user table

    ```sql
    create table User (
    uid int AUTO_INCREMENT,
    name varchar(255) NOT NULL,
    gender ENUM('Male', 'Female'),
    email varchar(255) UNIQUE NOT NULL,
    PRIMARY KEY (uid));
    ```
    
2. Query to create the events table

    ```sql
    create table events (
    id int AUTO_INCREMENT,
    uid int NOT NULL,
    name varchar(255),
    occurrence ENUM('YEARLY', 'ONETIME') NOT NULL,
    startDate date NOT NULL,
    endDate date,
    PRIMARY KEY (id),
    FOREIGN KEY (uid) REFERENCES user(uid));
    ```
    
3. Query to insert into User table

    ```sql
    insert into user(name, gender, email) values('abhay', 'Male', 'abc@gmail.com');
    ```
    
4. Query to insert into Events table

    ```sql
    insert into events(uid, name, occurrence, startDate, endDate)
    values(1, 'New year party', 'ONETIME', '2021-12-31', '2022-01-01');
    ```
    
5. Query to get all events for today -> Both Yearly and OneTime (For one time, ongoing events sholud come)

    ```sql
    select * from events
    where date(startDate) = curdate()
    or startDate <= curdate() and endDate >= curdate();
    ```
    
6. Query to get all users for a list of uid 
    Eg. get users whose uid is one of (1, 2, 6, 8, 9)

    ```sql
    select * from user
    where uid in (1, 2, 6, 8, 9);
    ```
    
7. Query to get all events for a uid
    Eg. get all events for uid=1

    ```sql
    select * from events
    where uid = 1;
    ```
    
8. Query to get all events for the next 7 days.

    ```sql
    select * from events
    where startDate >= curdate() and startDate <= curDate() + 7;
    ```
    
    
### Screenshot of Database

1. User

![Output](https://github.com/AJ-Walker/Avtaar-Assignment-2/blob/main/userdata.PNG)

2. Events

![Output](https://github.com/AJ-Walker/Avtaar-Assignment-2/blob/main/eventsdata.PNG)


