# Two-Tier Architecture: Nextcloud + MariaDB

## Definition

A **two-tier architecture** divides an application into two layers, each handling a different responsibility:

1. The **web/application tier**, which users talk to
2. The **database tier**, which keeps the data safe

Think of a restaurant: the waiter takes your order and brings your food (web tier), while the kitchen storeroom keeps all the ingredients (database tier). Customers deal with the waiter, never directly with the storeroom.

## The Web/Application Tier

- **Role:** the "front door" of the system
- Serves the user interface in the browser
- Receives and answers HTTP requests
- Runs the logic: logging in, uploading, sharing, and syncing files
- Asks the database for information whenever it needs it
- **In this lab:** the Nextcloud container, reachable on port 8080

## The Database Tier

- **Role:** the "memory" of the system
- Stores persistent data that must survive restarts, such as user accounts, passwords, and file records
- Answers queries from the application tier
- Is not meant to be opened by end users
- **In this lab:** the MariaDB container, reachable only by Nextcloud

## Why Separate Them?

Keeping the web server and database in different containers means each one can be upgraded, restarted, fixed, or scaled without disturbing the other. It is also safer, because the database can stay hidden from the outside world while only the web tier is exposed. Lastly, it keeps every container focused on a single job, which is the standard way to design containerized systems.
