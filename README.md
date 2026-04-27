🎯 # Exercise 6:
Database Foundations
-----------------------------------

🧩 Question 1: Dynamic Schema Generation 

    "When you executed the POST request in Step 4A, you did not have to write a complex SQL 
    CREATE TABLE query beforehand to define columns for "temperature" or "humidity". Explain 
    the concept of a "Schema-less" database. Why is this specific feature highly beneficial during 
    the early prototyping phases of an IoT network where sensor data formats might frequently 
    change?"

Explanation: A "Schema-less" database means we don't have to follow a strict set of rules or set up a fixed "table" structure before start saving data. In traditional databases, we had to write complex SQL commands to define exactly what every "column" (like temperature or humidity).

It is good for IoT because during the early stages of building an IoT network, things change constantly. One day you might just be tracking temperature, but the next day you might decide to add humidity or battery status. Because MongoDB is schema-less, you can just start sending that new data and the database will accept it instantly. You don't have to stop your system or go back and "rebuild" the database every time you add a new sensor, which saves a lot of time while prototyping.

------------------------------------------

🛡️ Question 2: Middleware Abstraction 

      "In this architecture, your ESP32 (simulated by Postman) never talks directly to the MongoDB 
      database. It only talks to Node-RED via HTTP endpoints, and Node-RED handles the database 
      queries. Defend this architecture. Why is it a massive security risk to expose port 27017 directly 
      to the public internet so that edge sensors can write directly to the database?"

Explanation: In this setup, the sensor (simulated by Postman) never talks to the database directly; it only talks to Node-RED  because Node-RED acts as a "buffer" or middleware. It takes the simple HTTP requests from the sensors and handles the more complicated task of talking to the database for us.

The Security Risk: If we opened port 27017 (the database's "front door") directly to the public internet so that every sensor could write to it, it would be a massive security risk. Anyone on the internet could find that open port and try to break in to steal or delete our data. By using Node-RED in the middle, we can keep our database "hidden" in a private network
