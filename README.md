Download Link: https://assignmentchef.com/product/solved-eecs484-project-2-querying-the-fakebook-database-with-jdbc
<br>
While Project 1 focused primarily on database design, in this project you will focus on writing SQL queries. In addition, you will embed your SQL queries into Java source code (using JDBC) to implement “Fakebook Oracle”, a standalone program that answers several queries about the Fakebook database. For this project, you will use a standardized schema that we provide to you, rather than the schema that you designed in Project 1. You will also have access to our public Fakebook dataset for testing.

1) TestFakebookOracle.java

This file provides the main function for running the program. You can use it to run and test your program, but you don’t need to turn it in.

Please only modify the ​oracleUserName​ and ​password​ static variables, replacing them with your own information.

2) FakebookOracle.java

DO NOT modify this file, although you are welcome to look at the contents if you are curious.

This class defines the query functions (discussed below in Section 3) as abstract functions, which you must implement for Project 2. It also defines some useful data structures and provides formatted print functions for you to make use of.

<h3>3) MyFakebookOracle.java</h3>

This is a subclass of ​FakebookOracle, in which you must implement the query functions. You​      should ONLY fill in the body for each of the query functions.  DO NOT make any other changes.

In this project, you only need to store the results of the queries in our predefined data structures (which we have provided as member variables in the class). You don’t need to worry about output formatting. In the base class ​FakebookOracle.java,​ a set of print functions have been provided for you to view the query results.

The ​MyFakebookOracle class contains parameterized names for the tables you will need to use in your queries, and they are constructed in the class constructor as shown in the following lines of code. You should always use the corresponding variable when you are referring to a table in the SQL statement to be executed through JDBC. For example, you should use the variable cityTableName instead of using a constant value such as ‘PUBLIC_CITIES’ in your Java code.​

For creating and managing the database connection, you should use the predefined object oracleConnection.

<h3>4) solution-public.txt</h3>

This file contains the output query results from running our official solution implementation on the public dataset provided to you. You can make use of this to check whether or not your queries are generating the same results from the same input dataset.

Note that ​<strong>your submission will be graded using a different input dataset, so producing correct results on the public dataset is not a guarantee that your solution is entirely correct.</strong> Make sure that your queries are designed to work more generally on any valid input dataset, not just the sample data we provide. Also, think carefully about the semantics of your queries since it may not be always possible to test them in all scenarios and you often will not have the benefit of knowing the correct answers in practice.

<h2>2. Tables</h2>

For this project, your schema will consist of the following tables:

<ol>

 <li>&lt;prefix&gt;.&lt;DataType&gt;​_USERS</li>

 <li>&lt;prefix&gt;.&lt;DataType&gt;​_FRIENDS</li>

 <li>&lt;prefix&gt;.&lt;DataType&gt;​_CITIES</li>

 <li>&lt;prefix&gt;.&lt;DataType&gt;​_PROGRAMS</li>

 <li>&lt;prefix&gt;.&lt;DataType&gt;​_USER_CURRENT_CITY</li>

 <li>&lt;prefix&gt;.&lt;DataType&gt;​_USER_HOMETOWN_CITY</li>

 <li>&lt;prefix&gt;.&lt;DataType&gt;​_EDUCATION</li>

 <li>&lt;prefix&gt;.&lt;DataType&gt;​_USER_EVENTS</li>

 <li>&lt;prefix&gt;.&lt;DataType&gt;​_PHOTOS</li>

 <li>&lt;prefix&gt;.&lt;DataType&gt;​_ALBUMS</li>

 <li>&lt;prefix&gt;.&lt;DataType&gt;​_TAGS</li>

</ol>

<strong> </strong>

<strong>To Access Public Fakebook Data: </strong>

&lt;DataType&gt; should be replaced with “​PUBLIC​” to access the public Fakebook data tables.

The public data tables are stored in the GSI’s account name (​syzhao​). Therefore, you should use the GSI’s account name as &lt;prefix&gt; in order to access the public tables directly within SQL*Plus for testing your queries. For example, to access the public ​USERS table, you should refer to the table name as ​syzhao.PUBLIC_USERS​. In the Java files provided to you, the above table names are already pre-configured in the given code.

<h2>3. Queries</h2>

There are 10 total queries (Query 0 to Query 9). Query 0 is provided to you as an example, and you are left to implement the remaining nine. The points are as shown. The queries vary tremendously in terms of difficulty. If you get stuck on a harder query, try an easier one first and come back to the tough one later. For all of these queries, sample answers on the given data are available in the attached zip file. If the English description is ambiguous, please look at the sample answers.

Also, for all of these queries, when feasible, you should try to do ​<strong>most of heavy-lifting to answer the query within SQL</strong>​. For example, if a query requires you to present the data in sorted order, use ​ORDER BY ​in your query rather than retrieving the result and then sorting it within Java.

Also, the grading program we use does impose a ​<strong>time limit</strong> on the time it waits for a query. If a query appears to be taking too much time, you should consider rewriting it in a different way to make it faster. As mentioned in class, nested queries are usually more expensive to run since most DBMSs do not handle them efficiently.

<h2>Query 0: Find information about month of birth</h2>

This function has been implemented for you in ​MyFakebookOracle.java​, so that you can use it as an example. The function computes the month in which the most users were born and the month in which the fewest users were born. The names of these users are also retrieved.

The sample function uses the ​Connection​ object, ​oracleConnection​, to build a

Statement​ object.  Using the ​Statement​ object, it issues a SQL query, and retrieves a ResultSet​. It iterates over the ​ResultSet​ object, and stores the necessary results in a Java object.  Finally, it closes both the ​Statement​ and the ​ResultSet​ objects.

<h2>Query 1: Find information about names</h2>

The next query asks you to find information about users’ names, including (1) the longest first name, (2) the shortest first name, and (3) the most common first name. If there are ties, you should include all of the matches in your result, alphabetically ordered.

The following code snippet illustrates the data structures that should be constructed. However, it is up to you to add your own JDBC query to answer the question correctly.




<h2>Query 2: Find “lonely” users<sub> </sub></h2>

The next query asks you to find information about all users who have no friends in the network (ordered by their ID). Again, you will place your results into the provided data structures. The sample code in ​MyFakebookOracle.java​ illustrates how to do this.

<h2>Query 3: Find “world travelers”</h2>

The next query asks you to find information about all users who no longer live in their hometowns. In other words, the ​current_city associated with these users should NOT be the same as their ​hometown_city (neither should be ​null).​ You will place your result (ordered by ​user_id​) into the provided data structures.​

<h2>Query 4: Find information about photo tags</h2>

For this query, you should find the top ​n photos that have the most tagged users. You will also need to retrieve information about each of the tagged users. If there are ties (i.e. photos with the same number of tagged users), then choose the photo with smaller id first. This will be string lexicographic ordering since the data types are ​VARCHAR​s (for instance, “10” will be less than “2”).

<h2>Query 5: Suggest friends based on photo tags</h2>

For this task, you will suggest potential friends to a user. Specifically, you will find the top n pairs of users according to the following criteria:

<ul>

 <li>Both users should be of the same gender</li>

 <li>They should be tagged together in at least one photo (They do not have to be friends of the same person)</li>

 <li>Their age difference is ​&lt;= yearDiff​ (just compare the years of birth for this)</li>

 <li>They are not friends with one another</li>

</ul>

You should return up to ​n recommended friend pairs. Your output will consist of a set of pairs (​user1_id​, ​user2_id​). No pair should appear in the result set twice. You should always order the pairs so that ​user1_id &lt; ​user2_id​. If there are more than ​n top pairs, you should break ties as follows:

<ul>

 <li>First choose the pairs with the largest number of shared photos</li>

 <li>If there are still ties, choose the pair with the smaller ​user1_id</li>

 <li>If there are still ties, choose the pair with the smaller ​user2_id</li>

</ul>




<h2>Query 6: Suggest friends based on mutual friends</h2>

For this part, you will suggest potential friends to a user based on mutual friends. In particular, you will find the top ​n pairs of users in the database who have the most common friends, but are not friends themselves. Your output will consist of a set of pairs (​user1_id​, ​user2_id​). No pair should appear in the result set twice; you should always order the pairs so that ​user1_id &lt; ​user2_id​.

If there are ties, you should give priority to the pair with the smaller ​user1_id​. If there are still ties, then give priority to the pair with the smaller ​user2_id​.

Finally, please note that the ​_FRIENDS table only records binary friend relationships once, where ​user1_id is always smaller than ​user2_id​. That is, if users 11 and 12 are friends, the pair (11,12) will appear in the ​_FRIENDS​ table, but the pair (12,11) will not appear.

<strong>Specs clarification</strong>​: The dataset we will test on will have sufficient qualifying pairs to be n or higher on our test inputs. You will not have to consider situations where the pair of users in the top n have 0 common friends.

<h2>Query 7: Find the most popular states to hold events</h2>

Find the name of the state with the most events, as well as the number of events in that state. If there is a tie, return the names of all the tied states. Again, you will place your result in the provided data structures, as demonstrated in ​MyFakebookOracle.java​.

<h2>Query 8: Find oldest and youngest friends</h2>

Given the ​user_id of a user, your task is to find the oldest and youngest friends of that user. If two friends are exactly the same age, meaning that they were born on the same day, month, and year, then you should assume that the friend with the larger ​user_id​ is older.

<h2>Query 9: Find the pairs of potential siblings</h2>

A pair of users are potential siblings if they have the same last name and hometown, if they are friends, and if they are less than 10 years apart in age. While doing this, you should compute the year-wise difference and not worry about months or days. Pairs of siblings are returned with the lower ​user_id user first. They are ordered based on the first ​user_id and, in the event of a tie, the second ​user_id​.

<h2>4. Compiling and running your code</h2>

You are provided with an Oracle JDBC Driver (ojdbc6.jar). This driver has been tested with Java JDK 1.7 and JDK 1.8.

If you are unsure which Java development environment you prefer to use, we suggest that you develop your code in Eclipse. You can do this by creating a Java Project called ‘project2’ inside Eclipse, and then Importing the 3 Java source files to the project.

You should also add your JDBC driver’s JAR to Eclipse’s classpath. To do this in Eclipse, go to ‘Project Settings’ then ‘Java Build Path’, and then click on the ‘Libraries’ tab, then ‘Add External JAR’.

If you prefer, you can just use an editor (e.g., ​vi or ​emacs​) to develop your code. In this case, you should create a directory called ‘project2’ and put the three Java source files provided to you in this directory.

To compile your code you should change to the directory that contains ‘project2’. In other words, suppose you created the directory ‘project2’ in ​/your/home/Private/EECS484​.

cd /your/home/Private/EECS484

Then, you can compile the Java source files as follows:

javac project2/FakebookOracle.java project2/MyFakebookOracle.java project2/TestFakebookOracle.java




You can run your program as follows (note that you should set the class path (-cp) for your copy of ojdbc6.jar):

java -Xmx64M -cp “project2/ojdbc6.jar:” project2/TestFakebookOracle

Note  the colon (:) after ojdbc6.jar.

<h3>Connect from Campus or over a VPN</h3>

If you get a timeout error from Oracle, make sure you connect from campus or use the University VPN to connect (see this page for information: <u>​</u><u>http://www.itcom.itd.umich.edu/vpn/</u><u>​</u>). It is possible that the guest wireless network may not work for remote access to the database without being on the VPN. Alternatively, use UM Wireless or a CAEN machine directly for your development.

<h2>5. Testing</h2>

A good strategy to write embedded SQL is to first test your SQL statements in a more interactive database client such as SQL*Plus before writing them inside Java code, especially for very complex SQL queries. You have the public dataset available to test your application.

We provide you with the output from our official solution querying against the public data (available in ​solution-public.txt​). You can compare your output with ours to debug.

During grading, we will run your code on a second (hidden) dataset.