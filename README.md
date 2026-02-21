# Transportation Management App

This project is about a logistics web application, allowing cutomers to make bookings to transport goods from one place to another. See the [presentation.pdf](./presentation.pdf) for more details and screenshots.

---		

## Getting started

### Starting tha app

Run the app with Docker Compose:

```sh
docker compose up --build
```
and navigate to http://localhost:3000/

### Using the MySQL CLI inside the container

Open a shell to the MySQL container and connect with the CLI:

```sh
docker exec -it mysql_db mysql -u root -p
```

Enter `root` as a password when prompted.

Useful SQL commands once inside:

```sql
SHOW DATABASES;
USE app_db;
SHOW TABLES;
SELECT * FROM user;
```

---

## Demo of the app

The file `./back-end/Transportation-Service-back-end/src/main/resources/data.sql` is executed to insert a manager in the User table after Hibernate schema creation is performed, as well as insert some drivers and vehicles in some places of Austria.

Use the following credentials to log in as Manager and be able to add new drivers and vehicles:

- Manager's email: `m.m@gmail.com`
- Manager's password: `m`

To make a booking, sign up as a customer and then login. You provide the pickup and destination address, weight and size of the good to be transported. After this an offer will be generated and you as a customer can accept it or not. If accepted, the shipment will start when the corresponding driver clicks the button "Start" at his webpage when he is ready to start the shipment.

Login with the driver's email provided in the offer generated for the booking (the password is `d2` for `driver2.d@gmail.com`, `d3` for `driver3.d@gmail.com` and so on) and start the shipment.

After that login as a customer and check the status of your shipment. You can see the estimated time of arrival, the current location of the driver and the route on a map. The shipment ends when the average road transportation time ends, or when the driver has arrived before that time in the destination and has pressed the "End" button.

---

## Rebuilding the app after code changes

```sh
docker-compose up --build -d
```
