## Authorization (Roles/Claims) With Identity Framework
Roles can be added through SQL Inserts to the table "AspNetRoles" with an Id and Name.
<br>
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
*photo here*


