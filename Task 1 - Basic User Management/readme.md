
So today our task is to,
         - Create a new user in the server and add them in Home.
         - After Creation, When the user tries to login, They Must to Change their password.
         - And assigning root access to this user manually.

1. Creating a new user in server.
     To create a user in a server, we have two commands.
               -useradd <username> (DO NOT USE THIS! As it just creates a user. And then we manually have to add them to the server's home! it will be difficult later.)
               -adduser <username>  (But this will do you more than that by not only add the user to the home, but we can create a password at the creation itself! And also, We can add details of the user like their name and contact details for future references.)

     And in the Screenshots, I have created a user called Developer. by using this command
        > adduser Developer

2. Giving access for the user to Change their own password.
     for this, we use
        > chage -d 0 Developer

     (The above command means that,
          chage - changeage
          -d 0  - date to zero
          Developer - The Username) this means, the password is going to get deleted in zero days, so it asks us to change the password immediately right after the login!

3. Giving sudo access to a user.
   [CAUTION: Should be given only to authorised persons.]
       There are multiple ways to give sudo access to a user. (sudo access means, giving root level access like they can install new things to the server and they can delete or view root level files)
     - We can add the user into a group, and then give access to them. (Useful when we have to give the same access to multiple users)
     - We can manually write a single line script for a specific user. by using the command below.
          > sudo visudo
            (inside this,
                > Developer ALL=(ALL:ALL)ALL
              Which means, we are giving all the sudo access to this user called Developer.)
  

<img width="3691" height="2248" alt="1000261679" src="https://github.com/user-attachments/assets/0442cf46-ef51-4412-8ce2-94f1d2d6d2be" />

<img width="3710" height="2322" alt="1000261681" src="https://github.com/user-attachments/assets/9d420d64-7162-4cf8-a201-42037588efc5" />
