# Wordpress kubernetes with RDS
### Setup the master slave configurations same as I mentioned in the https://github.com/devops-team-poc/Setup-kubernetes-cluster , but in this, I used the mysql Database for the storage and in this task we will use RDS in place of the MySql database

Steps

- Then, will create the RDS Databse , Go to the AWS console -> RDS -> Create Database -> apply the Public access and Password for the same and other essential details mentions there, I have setup for the t2 micro size and taken the Mysql for the Database 

![image](https://user-images.githubusercontent.com/67600604/179456120-af28c657-dee8-4872-8715-54a76b3eada2.png)

After that, 

![image](https://user-images.githubusercontent.com/67600604/179456367-6f89c10a-8465-4b36-9a38-6fdc054a79bd.png)

Copy the endpoint URL , because it will be neede in the wordpress.yml file 

after that run the command ```kubectl get svc ``` and check the port at which the wordpress website is exposed and after hitting the website with the ``` IP-Adress:Port``` setup the user and dashboard for the further process

Check the file attach in the repository , I have mentioned the username, password and the endpoint url in the file , you can use it as reference that how to mention

Then, create the file using 

``` kubectl create -f wordpress.yml ```
``` mysql -h wordpress-database.cj7cggiwxyqn.ap-south-1.rds.amazonaws.com -P 3306 -u admin -p ```

After that, to check the ``` show databases ```

![image](https://user-images.githubusercontent.com/67600604/179459255-9b85c171-b654-4814-bbba-0952fa87e143.png)

Here, we have created the database named as wordpress , now to check the tables in it, we will use the command ``` show tables ```

![image](https://user-images.githubusercontent.com/67600604/179459527-1a586025-9fb4-4be1-99d2-9caca951c1a3.png)

now go into the tables of user to check if the user is create dor not , that we have created at the time of wordpress setup 

use the command ``` select * from wp_users ; ```

![image](https://user-images.githubusercontent.com/67600604/179460008-8bf5365d-c1ac-4283-a6c4-dc5b65b6b17e.png)

All the users are mentions here , that we creted at the time of wordpress setup.

![image](https://user-images.githubusercontent.com/67600604/179460860-7edc6acd-624e-42a0-b1d2-cc43127156ec.png)
