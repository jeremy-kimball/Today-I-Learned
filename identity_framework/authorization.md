## Authorization (Roles/Claims) With Identity Framework
Roles can be added through SQL Inserts to the table "AspNetRoles" with an Id and Name. As roles are fairly static it is commonplace to adjust users roles inside of the database directly. We will start with a template database structure provided by Identity framework. It looks like this minus the messages table in the bottom right of the screenshot, as that is part of what we will be using to test users access. 
![image](https://github.com/jeremy-kimball/Today-I-Learned/assets/130601077/d19ad8df-8a30-45d7-9bc3-de0d7a93c5d0)
Example
```
INSERT INTO "AspNetRoles" (id, name)
VALUES (1, 'Admin');
```
Afterwards inside the join table between  "AspNetUsers" and "AspNetRoles" called "AspNetUserRoles" we can insert to assign a specific user to a role.
```
INSERT INTO "AspNetUserRoles" (user_id, role_id)
VALUES ('USER_ID_HERE',1)
```
We now have created a role called admin and assigned it to a user via their ID.

## Usage
Above our controller actions we can now choose to allow or deny users based on the role that they are assigned
![image](https://github.com/jeremy-kimball/Today-I-Learned/assets/130601077/b039ec9c-4a03-47f3-a6f3-306489f9112a)



