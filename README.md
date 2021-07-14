# Sapient Freshers-2021-jun-asde

Batch POC: Kanhav Ghai 
*** 

Aarsh Verdan - DTU, Joined in pJP, likes to play online games, guitar, and likes to learn technology 

Akhil tomar - DTU, likes : Backing Trecking, Travelling 

Akshit Kumar - IIT Karagpur, playing video games, graphic designing, PS, 

Aneesha Kota - IIT bhubaneshwar, play badminton, sports, singing 

Bitan - IIT Bhubanesh, sudoku, likes reading a lot, watching web series one 

Deepanjan  - IIT Patna, CS, like to sing, swimming 

Harshit singal - IIT Delhi, part of PJP, optimistic, likes to play soccer, and like playing chess 

Hemanth Umanshanar - NIT Suratkat, plygin video games, watigin movies, playing guitar 

Kanav Ghai - IIT Patna, likes youtube with sports, and likes eating 

Karmanya Sharma - likes to learn, play football, badminton, started blogging, 

Krishna - IIT Bhubaneshwar, CS, watching cricket, likes cooking 

Lakshya - IIT Gandhinagar, CS, playing badminton,  likes listening to music, 

Prateek - IIT Kharagpur, watining movies, does cooking 

Priyadarshan - DTU, CS, likes to play guitar, likes to play with dog, reads blogs 

Raj Shekar - does painting, drawing , and likes to watch TV Series 

Rizwan Khan - from Delhi, IIT Patna, playing cricket 

Rohit - IIT Gandhinagar, ply online games, cricket watch TV Series, 

Sailaja - IIT bhubaneshwar, plays badminton, mobile games 

sanjana - NITK surajkal, digital art work, 

Shushrut - NITK suratkal, CS, motor sport 

Sioddharth - IIT Roorkey, plays any sports, watch movies, TV series, etc 

pradyuman - IIT patna, plays chess, watch movies, in free time 

Suhas - IIT suratkal, PC games, watch F1, football

Veena - NITK suratkal, playing basket ball, likes eating street food. 



***


# DAY 1 
CONFLUENCE(Wiki) - JIRA - BITBUCKET 

Git +  GitHub / BitBucket  
Jenkins (CI/CD)

LEFT -> RIGHT ( collges, they teach technologys then solve the problem)
RIGHT -> LEFT (first identify the problem then the technology comes)


Work Approach
1. Tech stack 
2. 4-5 Week of training - in that we have a small project 
3. 7 Weeks a full fledged project work 
   
TDD Style - Technology 
BDD Style - Semi Technology
     GIVEN, WHEN, THEN (AND, BUT)
DDD Style - Pure Business 

DOR - Defination of Release  
DOD - Defination of Done 


## _Working Method_

<img src="./images/work-method.png" alt="work image">


List Of Softwares : 

* Git Bash : https://git-scm.com/downloads
* Java 8 : https://www.oracle.com/in/java/technologies/javase/javase-jdk8-downloads.html
* Jenkins : https://www.jenkins.io/download/
* Docker : https://docs.docker.com/docker-for-windows/install/
    
    > docker run hello-world 

* Eclipse : https://www.eclipse.org/downloads/
* VS Code : https://code.visualstudio.com/download
* NodeJS : https://nodejs.org/en/



Either go with "master", "main" 

### Git Commands 
> git init 

> git branch <branchName> -- create a branch 

> git checkout <branchName> - checkout / switch branch 

> git branch --merged  - to show if the current branch is merged from other branch 

> git branch --no-merged - to show if the current branch is not merged from other branch 

> git checkout main 

> git merge new_branch 

> git checkout -b dev1  (create and switch the branch)

### Git Reset 
* soft reset - will keep the file in stagin area but not commit 
* mixed reset (defult) - this will take the file to untracked area 
* hard reset - the content is also take off 

In any case if you want to get back your code, have the commit id and you can checkout from there 

> The git reset command is a complex and versatile tool for undoing changes. It has three primary forms of invocation. These forms correspond to command line arguments --soft, --mixed, --hard. 

> git stash temporarily shelves (or stashes) changes you've made to your working copy so you can work on something else, and then come back and re-apply them later on.


In Git we have 4 area 
1. Untracked files 
2. Tracked (add)
3. committed files (commit)
4. stash

### working with stash
> git stash save "message"

> git stash list 

> git stash pop - it applied and removes

> git stash apply stash@{<NUMBER>} - applies and doesnot remove 

> git stash drop stash@{<NUMBER>} - to remove the stash 

> git stash clear - to clear all the stash 

> git stash show stash@{<NUMBER>} - to show the stash 

> git shash show -p  stash@{<NUMBER>} - to show the actual code 

> git fetch + git merge = git pull 

to delete the branch on remote 
> git push origin --delete branch_name

> git push origin :branch_name



### Branching Stratergy 

<img src="./images/branching-stratergy.png" alt="branching stratergy" width="350" height="200">



# Jenkins 

1. Freestyle project 
   1. scripted fashion (.sh / .bat)
2. Pipe line project * 
   1. you can have groovy code  in Jenkins 
   2. You can have groovy code in "Jenkinsfile" on remote SCM 



```
pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        
    }
}

```


```
    pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }

    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/jglick/simple-maven-project-with-tests.git'

                // Run Maven on a Unix agent.
                sh "mvn -Dmaven.test.failure.ignore=true clean package"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}

```


### Create Maven Project 

> mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 -DinteractiveMode=false


****



# DAY 2 

Run with PR from Master -> Dev -> branches 
<img src="./images/branching-assignment.drawio.png" alt="branching straergy in sapient">

1. Maven 

Maven has 3 Stages 
* clean (clean)
* work (various stages like compile, deploy, install, provided etc)
* report (site) - this will help you to generate the report 


> mvn compile

> mvn clean compile

> mvn package

> mvn clean package

> mvn test

> mvn clean test

> mvn site – to generate documentation

> mvn clean

> mvn eclipse:eclipse – compatible to eclipse

*** 
simple to program to show usage of slf4j 


1. Docker

> Tightly Couples Loosely Cohisive -> Highly Cohisive Loosely Coupled systems 

Docker allows tha orchestration with 
* Docker Swarm 
* Rancher 
* ECS 
* Kubernetees 
  
*** 
## Docker Introduction Commands 

> docker info 

> docker images - will get all the images which are in current system 

> docker pull image-name - will search for the image in hub.docker.com 

> docker ps - active containers which are running 

> docker ps -a [ - active containers which are running  + which are stopped]

> docker rm container-id [to remove the container which is stopped]

> docker rmi imageif [ to remove the images]

> docker system prune [ to remove images which are not in use ]

> docker stop container-id [to stop the container which is running ]

> docker start container-id [to start the container ]
Note: you cannot delete running container to do so first stop / force delete 

> docker pull mongo 

> docker run -name sapient-mongodb1 -d mongo 

to get into the mongo instance 

> docker exec -it [ containerid/name ] sh 

**to push image to hub.docker.com**

> Syntax: docker push username/imageid:tag
> Example: docker push adithnaveen/java-image:1

### _Hosting Jenkins With Docker_

> docker pull jenkins 

> docker run --name sapient-jenkins-instance -d -p 8080:8080 -p  50000:50000  jenkins:2.7.4

> docker logs [ container-id ] - to get the logs of the running container 

> docker inspect [container -id ] - to get the details of the container 

> docker history i-hello-world-3


To deploy a java application 

Steps 
```
    1. docker pull openjdk 
    2. mvn clean install 
    3. copy jar file to docker container 
    4. java -cp target/app-snapshot.jar com.mycompany.app.App
```

_**Docker can build images automatically by reading the instructions from a Dockerfile**_

to build image 
> docker image build -t i-hello-world-4 .


to run 
>  docker run i-hello-world-5:latest


Assignment Image 

To build a pipe line for using jenkins / docker 
<img src="./images/jenkins-docker.drawio.png">


## Docker Volumes 

> docker volume ls 

> docker volume create vol-name

> docker volume inspect vol-name 

start jenkins instance attached to volume(default)

> docker run --name jenkins-container-1 -v [ vol-name ]:/var/jenkins_home -p 8080:8080 jenkins:2.7.4 

start jenkins instance attached to volume - bind a folder 

> docker run --name jenkins-container-1 -v /users/naveenkumar/Desktop/folder-name:/var/jenkins_home -p 9000:8080 jenkins:2.7.4 

*** 
<img src="./images/mono-micro.drawio.png" width="300" alt="micro & monolithic discussion">


> Team 1 - Prateek, rajshekar, akshit, harshit

> Team 2 - Deepanjan, kanav, rizwan, praduman 

> Team 3 - karmanya, priyadarshan, aarsh verdhan, akhil 

> Team 4 - krishna, aneesha, bitan, sailaja 

> Team 5 - rohit, laksay, shushut, siddharth 

> Team 6 - sanjana, suhas, hemanth, veena 





****

# DAY 3 

****

- WORM (Write Once Read Many)

* Docker Volumes 
* install sonar lint + object aid 
* understand java program 

```
    int main() {} - you have control 
    void main() {} - 0 
```


_HelloWorld.java_
```
package com.naveen; 

    public class HelloWorld {
        static void hi()  {}
        void bye()  {}
        int x=100; - heap  
        static int yy=100;
        boolean flag = true; 
        public static void main(String [] args) {
            int y; 
            HelloWorld h = new HelloWorld();
            h.bye();
            hi();
            System.out.println(h.x);
            System.out.println("hi);
        }
    }



```
> javac -d . HelloWorld.java  - syntax and semantic .class - compiler / JITC
> java com.naveen.HelloWorld hi[0] bye[1] cya[2] - interpreter 


### Diagram 
<img src="./images/java-hello-world-arch1.drawio.png" width="450">


_stack calls_

```
version 1 
int main(){
    hi();
}

hi(){
    bye()
}
bye() {
    cya()
}
cya(){}    

```


```
version 1 
int main(){
    hi();
}

hi(){
    ....
}
```


String can hold - "10" , "true", .png 
.exe - mac / lin (does not work)
.so / a.out - win / max (does not work)
.dmg - win / lin 

> access specifiers 
1. public 
2. private 
3. protected 
4. default(package)



***
Folder Structure 
Training (Repo)
    aneesha-llid
        w1-d1-git-jenkins
        w1-d2-maven-docker
        w1-d3-java
        w1-d4-java-dp

    bitan-llid
    Participant 3
    ..
    Participant n
***


- Differnt UML diagrams (26) types of diagram 
  - class diagram 
  - use case diagram 
  - activity diagram 
  - sequence 
  - profile diagram 
  - flow chart 
  - data flow diagram 
  - component diagram 
  - objecet diagram 
  - state diagram 
  - context diagram 

* HLD - High Level Diagram 
  * use case diagram 
  * flow chart 
  * component diagram
  * context diagram 


* LLD - Low Level Diagram 
  * class diagram 
  * use case diagram 
  * flow chart 


plantuml (explore)
abstract class  "abstract class"
annotation      annotation
circle          circle
()              circle_short_form
class           class
diamond         diamond
<>              diamond_short_form
entity          entity
enum            enum
interface       interface


OOPS - anti pattern  
* compositon - has-a
  
  ```
    class Employee {
        private int empId; 
        private Name name;
        private double salary; 

    // getters / setters 
    }

    class Customer {
        private Name name; 
        private int custId;
        private double income; 
    }
    class Trainer {
        private int tId; 
        private Name name; 
        private double level;

    }

    class Name {
        private String firstName; 
        private String middleName; 
        private String lastName; 
    }


  ```



* aggregation 
* association -is-a (generalization - speciliazation)
  ```
    class Vehicle {} - generic class 
    class Car extends Vehicle {}  generic class  - specific class 
    class Maruti extends Car {} - specific class 
  ```





* S - Single-responsibility principle
* O - open close - should be open for extension, but closed for modification
* L - Functions that use pointers or references to base classes must
             be able to use objects of derived classes without knowing it

```
    
    interface Vehilcle {
        public void move();
    }
    class Car extends Vehicle {
        public void driveStreering() {}
         public void move(){} 
    }
    class TwoWheeler extends Vehilce {
        public void handle(){}
         public void move(){} 
    }

    class VehilcleBL {
      

        public static void show(Vehicle v) {
            v.move();
            if(v instanceof Car) {
                v.driveSteering();
            }else if(v instanceof TwoWheeler) {
                v.handle()
            }
        }

    }

    class App {
        public static void main(String [] args) {
            Vehicle v; 
            v = getMe("car");
            VehicleBL.show(v);        

            v = new getMe("twoWheeler");
           VehicleBL.show(v); 
        }
    }

```


in C 
```
    int main() {
        int *p; 
        p  = (int *) malloc(100); 
        ... your business logic 

        free(p); 
    }
```

* I -  Interface segregation principle: 
    "Many client-specific interfaces are better than one general-purpose interface" 
* D - Dependency Injection (DI)/ IOC 


*** 
* KISS 
* DRY 
* YAGNI 




### Vehicle management system 
Below are the asks 

* The company (XYZ) who manufacures chasis / nuts/ enginee etc 
* they have a problem to integrate various cars which they are catering 
* the want a unifed system where can build "nut/bolt" for differnet cars / two / trucks 
*  the code is exposed to the client but they have comeback saying its complicated to 
  understand what is available 
  Ex:  class Vehicle {} 
  class Car extends Vehicle{}
  class Maruti extends Car {}
  
    class Breeza extends Maruti {}
    class Swift extends Maruti{}
  
  class BMW extends Car {}
    class X1 extends BMW {}
    class X2 extends BMW {}

  class Volve extends Car{}
    class VSixty extends Volvo {}

X1 x1  = new X1(); 
x1.showNutBolt() (wrong)

* they want a common interface where they can see size / dimention / weight of nut/ bolts 
* they would like to have the data kept in matrix format 
  * maruti -> Breeza / Swift ...
  * BMW -> X1, X2...
  * Volvo - VSixty, CSixty ...
```
> way 1
class Brands {
    private String branchName; 
    private List< Car > cars; 
}


List<Brands> brandedCars = new List<Brands>(); 
Brands marutiBrands = new Brands(); 
marutiBrands.setBrandName("Maruti"); 
marutiBrands.setCars()
brandedCars.add(List.of(new Car("Breeza", 4), new Car("Swift", 5)); 

> way 2 

HashMap<String, List<Car>> brandedCars = new HashMap<>(); 
brandedCars.put("maruti", List.of(new Breeza(), new Swift())
brandedCars.put("maruti", List.of(new Car("Breeza", 4), new Car("Swift", 5)); 

```




write 1 method which should show all the cars (nuts/bolts)



****
# DAY 4 

Convention 
> package - has to be in lower case & cannot be in default package 
    * com.company.something 
    * org.company.something 

> variable / methods - camelcase - start with lower case then every words first char is in upper chse 

  * empId, empName, debitSalary, creditSalary, getEmployeeSalaryFromDB() 
  
> class name - pascal casing 
  * start with upper case then every next work first char in upper case 
    Employee, EmployeeProcessor, EmployeeDAO, IEmployeeDAO 
> constants 
    * to be in upper case 
    * COMPANY_NAME, TAX 


class - contracting Abastract Class (only abstract, you can have concrete methods) 
    / Interface (100%, concrete methods but has to be default prefixed) 


Noun - Entity / Bean 
Employee - DB 

EmployeeDAO 


> access-specifer access-modifier returntype methodname(param)

>access-specifer  - public, private, protected, default 
> access-modifier - static, final, sychronized, abstract 
> void or type (int, flotat, Employee, Vehicle) 



```
    class Company {}
    @Data 
    class Employee {
        private Company company; 
        private int empId; 
        private String name;

        public void setCompany(Company company) {
            this.company = company; 
        }
    }

// BLR 
    Company company = Company.getInstance();

    Employee e = new Employee(); 
    e.setCompany(company); 
    e.blah() 

// CHN
 Company company = Company.getInstance();

    Employee e = new Employee(); 
    e.setCompany(company); 
    e.blah() 


    Vehicle
        Car 
            BMW 
                X1
                X2
                X3
                X4
                ..
            Maruti  
                Swift 
                Kizashi
                Scross.. 
        TwoWheeler 
    Color 
        BLUE
        GREEN
        BLACK
        WHITE

```


chain of rsponsitibliy 

```
    fetch(url)
        .then()
        .then()
        .then()
        .catch()
```

Class.forName("com.mysql.jdbc.Driver"); 

Project Work : StackTooFlow 

User Stories: 

1. The application should have option to login to system 
2. the application should allow to register 
3. The application shoul allow to reset the passwor if user forgets 
4. The application should allow to ask a question 
5. There should be UP / DOWN down vote the question 
6. UP/DOWN on comment for the question 
7. the Application should allow to have comments for the question 
8. The application shall allow suggest similar problem 
9. Should allow answer the question 
10. Option to Delete / Edit option only for owner of questionn 
11. Option to Delete / Edit option only for owner of commenter 
12. List Trending questions 
13. show user dashboard which contains 
    1.  his/ her question 
    2.  his/her comments 
    3.  View his/her grade / points - rating 
    4.  System should store user profile like name,email, gender, social links etc 
14. application shall allow to search a question / answer - without login 
15. application shall allow to search on user 
16. view other people profile 
17. sort the answer based on relevence 
18. assign tag for the question 
19. user shall have the notification 
20. User can close the question 
21. spam a question / use could report the comment 
22. spam a user 
23. owner of the question can mark the answer by other user is best answer 
24. One use should be able to follow other users 

****

# DAY 5 

> TDD/BDD/DDD/ATD 

* TDD - Test Driven Development 
* BDD - Behaviour Driven Developement 
* DDD - Domain Driven Development 
* ADTD - Acceptance Driven testing / Development 

Next 5 Years - LowCode / NoCode 

> TDD (FOSS - Free & Open Source)
* jUnit 4 
* jUnit 5 - Jupiter - 



BL - 500 ms               -----
TEST - 500ms (370XX)ms    -.--






### BDD 
```

<img src="./images/tdd-bdd.drawio.png" width="350">


Given - Pre Condition 
When - Actual Work 
Then - Post Condition 

And - Multiple 
But - Clause 

**To run We will user JUNI**

Featue - registration module 

Scenario: 
    Given the application is loaded
    When the user clicks on "Registration Button" 
    And Enter valid pattern email address 
    And Proper pattern Password 
    Then show a message called "User Registered Successfully"   

```

Sprint Ceremony - User Strories 
Sprint Groomming - Stake Holder / Product Owner will come and talk to developer 
    and explain the feature file 
    give a closure 
Sprint Retrospective 


Cucumber 
    Gherkin (Small Cucumber) - Ruby (on top of Java)

Ruby / Kotlin / Scala / Groovy / R - written on top of Java 


types of tests 
* Sanity - check everything once 
* Stress - increment the count for the BL 
* Functional Test - Dont test everything but specifed 
* Spike Test - Give Too much load to the system 


Plugin Called Lombok - 
getters and setters 
parametric / default contstructors 
toString 

@Data 
@Getters
@Setters 
@ToString 

TDD in a BDD way


```
Scenario:  Title 

Given  the site is loaded 
When username is "" 
And password is peter
Then take him to home page 

And 
But 

-- the step is created 
@Given("^the site is loaded$)
public void the_site_is_loaded() {
    business logic 
}

@When("^username is \"([a-zA-Z0-9]{1,})\"")
public void username_is_passed(String userName) {
    String expected="harry";     
    assertEquals(expected, userName)
    
    assertNotNull(userName); 

    // statement will not execute 
    <!-- selenium  -->
}


```
****

# DAY 6 

Data model
Types: Conceptual/logical/physical
ER modeling - Entity/Attribute/Relationship
ER diagrams/normalization
RDBMS using MySQL/Postgres
DDL/DML/Queries
Basic examples of JDBC (connect/insert/select)
Problems with JDBC and why we need ORM
What is JPA?
Setting up environment
Entity classes
Configuration
CRUD operations
Queries


## 3 Schema arch 

SQL - ACID 
> Conceptual - User / Develer 
> logical - mysql / db2/ dbderby / postgres/ oracle (Primary key/ foreign key, not null, uniqe)
> physical - system (memory allocation) - talking to system, fragmentation 


1945 - ENIAC / EDSAC / EDVAC 
> 1st generatation - Mechanical  ( 2+2)

> 2nd generation - semiconductor 

> 3rd generation - chips 
    > programming C / C++ / Microcontroller (8086/8085)
    - Michine Level Langage 
    - Assembly Language 
    - Programming Language - C / C++ (How To Do Langauge ) - int *p = int*  malloc(100;), read the file content file *fptr; 
    - Java / SQL - (What to do language) - Select * from emp; 

> 1st Normalform  - dont have null values 

> 2nd Normalform - every thing to be dependen on primary key 

> 3rd Normalform - dont have your attribute dependen on another attribute (transivive dependency) - if they are dependent then they should be dependent on primary key only 

> BCNF - 4th Normal Form - linking table when you multiple attributes 


unnormalized 

Emp - 10,000

Dept - 1,000

Project - 300

Location = 250 

select e.empid, d.deptname from emp e , dept d, project p , location l 
    where e.deptid = d.deptid 
    and e.projectid = p.projectid
    and e.locationid = l.locationid
    and d.deptiid = 1000; 


### NO SQL Databases 
> MongoDB 

> Redis 

> Cassandra 

> Memcache 

> Spanner 

> Dynamodb 


> 1972 DB2 (IBM) - SQL - Postgres 
> docker pull postgres 

> Connecting to DB

### Drivers 

> Type1 Driver  - JDBC-ODBC Bridge, plus ODBC driver
    where had few hundred transactions per day - to OS - has to talk to DB - get an act - give it to programming lanague 

>  Type2 Driver - Native-API, partly Java Driver
    - 1000's 1998 - java was popular - DB vendor came (Oracle / MySQL / DB2..... ) - it did not stay for even 1 year 

>  Type3 Driver 
    - EJB - Entripise Java Beans -Glassfish(Sun Microsystem) / JBoss(JBoss/ RedHat) / Weblogic (Oracle)/ websphere (IBM)

> Type4 Driver - Native-protocol, Pure Java Driver
    - Java -Interface - (Oracle / Mysql/ db2, .... ) - .jar 

*** 
# JDBC - JPA 

> JPA is implemented - ORM - Hibernate / iBatis / TopLink / Castor etc 

### DB's have default port 
> MySQL - 3306 

> Oracle-  1521 

> Postgres - 5432

> MongoDB 27017 


### creating docker container for postgress

> docker pull postgres

> docker run --name postgres-sapient1 -p 5432:5432 -v /Users/naveenkumar/Desktop/postgres-db:/var/lib/postgresql/data -e POSTGRES_PASSWORD=kanchan -d postgres

> docker exec -it < containerid > psql -U postgres 



###  Postgress commands 

> \l - list dbs 

> \c  dbname - to connect to db 

> create table emp(empid int primary key, empname varchar(30), empsal decimal); 

> \dt - to list the tables 

> \d < tablename > - to desc table 


### to install lombok 
> https://projectlombok.org/download - download the jar 
>  java -jar lombok-1.18.20.jar

> in pom.xml 
```
    <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
        <version>1.18.20</version>
	</dependency>
```


> @Data -> Generates getters for all fields, a useful toString method, and hashCode and equals implementations that check all non-transient fields. Will also generate setters for all non-final fields, as well as a constructor.
Equivalent to @Getter @Setter @RequiredArgsConstructor @ToString @EqualsAndHashCode.


### working with JPA 
- JPA is a standarad , implentor is Hibernate (it could be other people also like ibatis, toplik etc )
````
// is transient class 
class Emp{}

// persitence class 
@Entity
class Emp{}
````
*** 

# DAY 7 

### Retro - Day 6 
```
public void insert(Emp e) {

    Sql ="insert into emp values(?,?,?)"; 
    gc.ps = GC.getPostgresConn.preapredStatement(sql); 
    gc.ps.setInt(1, e.getEmpId()); 
}
```



> Inheritenace 

```
@Entity
@Inheritance( strategy = InheritanceType.SINGLE_TABLE )
@Inheritance( strategy = InheritanceType.JOINED )
@Inheritance( strategy = InheritanceType.TABLE_PER_CLASS )

class Vehicle {}


@Entity 
class Car extends Vehicle {}

Car c = new Car(); 

```

> composition 

```
    @Embedded 
    class Emp {
        private Name name; 
        .... 
    }
    @Embdeble 
    class Name {

    }

```


Lombok - we added lombock in pom.xml + java -jar lombok.jar (installeer for eclipse)



> What is Java/.net/python...  - OOPS 
> ORM - Hibernate 
> DB - RDBMS 

*** 
> Overview of NOSQL and Mongodb
> Setup a local server
> Mongodb Atlas
> Basic operations on collections
> Using Mongodb drivers in Java 
> Examples of Save+Retrieve docs from Java


<img src="./image/../images/mongo.drawio.png" width="400">

> DB (Mongo) 
    -  they are not normalized 

    - embdded document 

    - json 

    - can store objects directly with some converters (jackson/gson)

    - Java Object ->  Json (with Jackson / Gson )

    - generally fast 

    - no concept of ACID 

    - Horizontal Scalability 

    - Words to understand 
        > DB, Collection, Record, field (key: value)
    


> DBMS (Oracle / Postgress)
    - they are normalized 

    - refrential integrity 

    - atomic 

    - Object - Atomic - JAXB

    - that does not mean this is slow 

    - storong ACID 

    - Vertical  Scalability 

    - Words to understand 

        - DB, Table, Row/Tuple / Attirbute 


> Processor - 2.4 Ghz (1,000,000,000) - small - 64 bit 

> Cache - 2-3 mb  (Ghz)

> RAM - 2.4 MHZ - 16GB 

> HDD - 10,000 RPM (1 TB )


> by default mongodb will look in windows (c:\data\db) in unix flavour os (/data/db)

Folder where fils are kept  /Users/naveenkumar/Desktop/mongodb .wt  
```
> mongod --dbpath .   - to start the server 

> monog - will connect to server, it is client shell, by default will connect to 27017

> show dbs 

> db.emps.insert({empid:101, empname:"Rizwan"}); 

> db.emps.insert({empid:102, empname:"Hemanth"});  

> show collections 
```
### Query 
Syntax 
> db.emps.find({selection} , {projection}); 

> db.emps.find({empname:"Rizwan"}, {_id:0, empname:1})

> db.emps.insert({empid:103, name:"Prateek", address: {hno:123, street:"American Dream Way", state:"VA"}})

> db.emps.find({"address.hno":123})


#### Mongo Jaa 
```<!-- https://mvnrepository.com/artifact/org.mongodb/mongo-java-driver -->
<dependency>
    <groupId>org.mongodb</groupId>
    <artifactId>mongo-java-driver</artifactId>
    <version>3.9.1</version>
</dependency>

```

### We have written the methods for 

> insert one / insert many 

> update 

> delete 

> select 

> select all 

> select condition 

To explore - TODO 

> upsert 
```
 class Employee {
     private Name name; 
     ... 
 }

class Name {
    private String empName; 
    .... 
 }
 ```

> Refractor use proper interfaces / dao classes 

> try with validators 



> sonar checks 
> Add a nested comment explaining why this method is empty, 
    throw an UnsupportedOperationException or complete the implementation.



### Project Structure 

<img src="./images/project-structure.drawio.png" width="400">

**** 

# Day 8 

Overview of HTTP
Request/Response model: RFC-2616
Examples: access public APIs
Server side coding in Java
Servlets and HTTP
Handling client requests
Parameters/headers/cookies
Filters + Listeners 


- early 90's 
- GUI - Applets, swing, d2k 
- you got to have a piece software to run (STUB) - Floppy(1.44MD, 512KB) / CD / DVD / USB (386, 486, pentimum 1, 2, 3)
- in the server side we have skeleton (Interface + BL + DB)
- RMI - Remote Method Invocation, COM, DCOM, EDI, CORBA etc. 
- W3C > ICANN Internet Corporation for Assigned Names and Numbers (~1994)
- HTTP (1.0 - Stateful Prototocl), (1.1 - stateless prototocol), (2.0 - two way protocol-gRPC)
- CGI -> (Sun Microsystems / Microsoft)
- Threads which developer can manage 
- 1.1 - stateless prototocol - (Sun Microsystems / Microsoft), PHP, Python 



#### Servlets 

- Servlets is a class which extends HttpServlet
- you can make an entry of the servlet for container(Tomcat) - either in web.xml or annotate @WebServlet 

Cookie v/s storage(local / Session)
- Cookie the end user has to ack , to store only text data 
- storage is for developers to store large data 

<img src="./images/http-request.drawio.png" width="400">

**** 

# Day 9

- HTML response using JSP
- MVC for building a web application using servlets/jsp
- understanding sessions,  context, page, request 


<img src="./images/mvc.drawio.png" width="400>

- working of session or other containers 
<img src="./images/session.drawio.png">


> req.getSession() - Returns the current session associated with this request, or if the request does not have a session, creates one.

JSP Support - EL - to avoid usage of scritlet 
> ${... }


```
class Emp {
    private int empId; 
    public Emp(int empId) {
        this.empId = empId;
    }

}
```


> building a MVC program (full stack with JAVA)

- get you dependencies (https://mvnrepository.com/artifact/javax.servlet/jstl) 


- project branching 

> sanjana, prateek, akshit, hemanth 
. txt file 
- user 1- description user 1 - 2days - sanjana - PJMB-123-building-login-page
- user 2- description user 2 - 2days - prateek - PJMB-124-building-reg-page
- user 3- description user 3 - 2days - akshit - PJMB-125-building-post-question-page
- user 4- description user 4 - 2days - hemanth - PJMB-126-building-post-answer-page

### raise PR for all 
 PJMB-123-building-login-page -> dev 
 PJMB-124-building-reg-page -> dev 
 PJMB-125-building-post-question-page - dev 
 PJMB-126-building-post-answer-page -> dev 

 
- bootstrap 
- html 
- css 
- servlets
- jsp 
- POJO 
- jUnit 


**** 

# Day 10


Performance testing techniques(white box, grey box, black box) 
Load testing
Stress testing
Soak testing
Spike testing
Performance tools
Jmeter/Gatling




- NFR - Non Functional Requirement 
- Sanity Test - everything once 
- Functional Test - testing 1 functions 
- Component / Integration Test 
  - if you test 1 method - Unit Test 
  - if you combile 2 methods - integration 
  - component - cohesive 
- 100000 times - load test / stress test 
- 10:00 (5 Req) -> 10:30 (20 Req) -> 11:00 (5000000 Req)- spike test 
  - Kubernetees 
  - Racher 
  - Docker Swarm 
  - EKS + ECS 
- you are not calling application directly - rather the application calls application for a duration of time 
- jMeter - Java  / Gatling  / Lucust 
- A system may behave normally when used for 2 hours, but when the same system is used continuously for 10 hours or more than that then it may fail or behave abnormally/randomly/it may crash. To predict such failure Soak Testing is performed.

  
> http://localhost:8080/ < Enter >
> http://localhost:8080/blah < Enter >


- A - not good quality - okiesh 
- AA - USA 508 Standard, screen reader enabled, mobile / tablet / desktop compatible 
- AAA  - USA 508 Standard, screen reader enabled, mobile / tablet / desktop compatible + color codes for blind 




https://www.publicissapient.com
https://www.publicissapient.com/industries/energy-commodities/tech-awards


> docker run --name sap-sonar -p 9000:9000 -d sonarqube


*** 

### Sonar 
Project Name : first-project
token : naveen - c18bd838d076195e879ffbf09e7109a5e98403ab


mvn sonar:sonar \
  -Dsonar.projectKey=first-project \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.login=c18bd838d076195e879ffbf09e7109a5e98403ab




Jenkinsfile 
    - the code bitbucket + branch 
    - bundle as war 
    - Dockerfile 
    -   from Tomcat 
    -   copy . /usr/local/tomcat/webapps 
    

> mvn clean install -DskipTests=true 
>
> mvn clean install -DskipTests=true 
 
 


- whitebbox - performance - I'm a developer - develop  (unit testing) - BL 
- grey box - intrim test - we not only 1 method we combine more than 1 - 
- black box - E2E - black box test 
- 


*******

# Day 11 

<img src="./images/spring-arch.drawio.png" width="400">


- POJO (cohesive coding if coupled there is not body to check)
- constroller Servlet 
- view ( JSP) - portlet, JSF 
- full stack (only with java tecchnology)

- container 
  - tomcat 
    - init 
    - service 
    - destory 


- EJB - ran into gb's and you needed middle tier 

- 80, 90, 2000's 
- Corba 

- Struts (1,2) 
- web framework 
- Rod Johson - Spring 

```

    class Employee {

        protected void finalize() {}
    }


    Employee e = new Employee(); 
```
- jdk 1.5 - 2004 
- JVM - GC - when it wants not when you want 
- System.getRuntime().gc(); - super costly 


- Spring - IOC/DI 
- Spring MVC 
- Spring Boot + Netflix (eureka, api-gateway, hystrix, zipkin), swagger(documentation)
- Security - JWT 


- with servlet 

````
    @WebServlet("/*")
    public class DispatcherServlet extends HttpServlet {
        void doGet(HttpServletRequest req, HttpServletResponse res) {}

    }

// will be injected to you POJO 
    class MyServlet {
            HttpServlet httpServlet ; 
    }

````

> mkdir kanav kanav/week3 kanav/week3/d1 kanav/week3/d2 kanav/week3/d3 kanav/week3/d4 kanav/week3/d5
> touch readme.md
> touch kanav/week3/readme.md
> touch kanav/week3/d1/readme.md
> touch kanav/week3/d2/readme.md




> Spring with xml 
````
    <beans>
        <bean id="hi" class="com.naveen.Hi></bean>

        <bean id="one" class="com.naveen.One autowire="byName"/>
        <bean id="two" class="com.naveen.Two></bean>
        <bean id="three" class="com.naveen.Three></bean>

        <bean id="app" class="com.naveen.App autowire="byName" / >
    <beans>


    class One {
        Hi hi; 
    }
    class Two {}
    class Three {}
    class App {
        private One one; 
        private Two two; 
        private Three three; 

    }
````

> @Service 

> @Comonent 

> @Repository 

***

## AOP 
> Before 
> After 
-  AfterReturning 
-  AfterThrowing
> Around


> Aspect: a modularization of a concern that cuts across multiple classes. - method 

> Join point: a point during the execution of a program, such as the execution of a method or the handling of an exception. In Spring AOP, a join point always represents a method execution.

> Advice: action taken by an aspect at a particular join point.

> Pointcut: a predicate that matches join points.
> @Pointcut("execution(* transfer(..))")// the pointcut expression



*** 
Assignment : 
-  List amount of time takes for the method 
-  Get the name of the method 
-  Get method args of the methods
-  Create a couter log which will keep a track of each method which is invoked and number of times 
  
  Hint :
  ``` 
  Map<String, Integer> countingMap = new HashMap();
  
  ```

### protprocessing 

    ```
        @Component 

        class Hi {
            @Bean(id="myid", init ="init", destroy="destory")
            public void getSomeBean() {}
        }

        
        @Component 

        class Bye {
            @Bean(id="myid", init ="init", destroy="destory")
            public void getSomeBean() {}
        }

        
    ```


> aop  - loggers - @Before then 

> aop - loggers @After - you get all the details 

BeanPostProcessr -> | mutate if you need | -> the actual bean is given to developer 



***

# Day 12 

Spring MVC
DispatcherServlet
HandlerMapping
ViewResolver
Controller
RestController
Error handling



> Jackson is a high-performance JSON processor for Java. 


> prefix - /WEB-INF/pages/
> suffic - .jsp 

*** 


# Day 13
> Spring 5.x 
> Sprint boot verstion 2.x 


> 1999 
> W3c - xpath, xml schema, xslt, xsl etc 
> helped to create more languages and standars 
> SOAP - Simple Object Access Protocol 
> JDK1.6 - saop built in JAVA, jaxb is available 
> standard
> header and body 


```
<?xml version="1.0"?>

<questions>
    <question>
        what is your name         
    </question>
      <question>
        what is dad name         
    </question>
      <question>
        what is mom name         
    </question>
</questions>

> DOM(document object model) / SAX(Simple API for XML ) / StAX (Stream API For XML )
> postulate - C, C++, JAVA (JAXB), .NET, PHP, PYTHON, GO, DART... 


> 2003 - jessey james - google - ajax 
> 2005 - json 

{
    questions: [
        question:what is your name , 
        question:what is dad name , 
        question:what is mom name , 
    ]
}
   
```

***** 
```
http://localhost:8080/someapplication/
@RequestParam("/hello")
@RequestParam("/hello1")
@RequestParam("/hello2")
@RequestParam("/hello3")

```
- jackson, gson
> w3c approved - javascript 

> REST 
> RESTFULL

> HATEOAS - Hypermedia as the Engine of Application State is a constraint of the REST application architecture that distinguishes it from other network application architectures.
> RMM (richardson maturity model)
- level 0 - Level zero of maturity does not make use of any of URI, HTTP Methods(GET/POST/PUT/DELETE/PATCH), and HATEOAS capabilities. ( RMI )
- level 1 - Level one of maturity makes use of URIs out of URI, HTTP Methods, and HATEOAS. (RMI-CORBA)
- level 2 - makes use of URIs and HTTP out of URI, HTTP Methods, and HATEOAS
- level 3 - makes use of all three, i.e. URIs and HTTP and HATEOAS, it also gives links to the resources


```
@RestController("/resources")
class MyResource{
    @GetMapping("/{resourceId}")
    public Resource getOneResource(int resourceId) {}
    public List<Resource> getAllResource() {}
    public Resource saveResrouce(Resource resource)
    public Resrouce updateResource(Resource resource)
    public void deleteResource(int resourceId){}
}

GET /
GET /{resourceId}
POST /
PUT / 
DELETE /{resourceId}


```



```
@RestController 
class MyResource{
    
    @GetMapping("/resources/{resourceId}")
    public Resource getOneResource(int resourceId) {}
    
    @GetMapping("/resources")
    public List<Resource> getAllResource() {}
    
    @PostMapping("/resources")
    public Resource saveResrouce(Resource resource)
    
    @PutMapping("/resources")
    public Resrouce updateResource(Resource resource)
    
    @DeleteMapping("/resources/{resourceId}")
    public void deleteResource(int resourceId){}
}

GET /resources/{resourceId} - get one 
GET /resources - get all 
POST /resources - post 1 
PUT /resources - update 1 
DELETE /resources/{resourceId} - delete 1 



    @GetMapping("/get-resources/{resourceId}")
    public Resource getOneResource(int resourceId) {}
    
```


- JAX-WS - SOAP
- JAX-RS - REST 

> jersey 
> resteasy
> restlet 
> spring boot 


> packages in spring boot application 

- com.company.rest.works.config
- com.company.rest.works.exception
- com.company.rest.works.model
- com.company.rest.works.repo
- com.company.rest.works.resources
- com.company.rest.works.services
- com.company.rest.works.swagger



> in mongodb object id is of 12 bytes data 
> 4 - system information 
> 4 - sharded + replication information
> 4 - running serial number 


{
    question: "Your Question Goes Here", 
    status: "open/close"
    answers: [
        {answer: "First Answer"}, 
        {answer: "Second Answer"}, 
        {answer: "Third Answer"} 
    ]
}

*** 

# DAY 14 

Primary Key - Uniq + Not Null + Index 

{
    _id:  info 
    qid:< unique > - yes 
}

> a 4-­‐byte value representing the seconds since the Unix  epoch,
> a 3-­‐byte machine identiﬁer,
> a 2-­‐byte process id, and
> a 3-­‐byte counter, starting with a random value.


we can create a index - to speed up + (sparse index, uniq, text, 2d, 2dsphere)


{
    id:101, 
}

> Micro services overview
> Architecture
> Use cases and implementation
> Do's and Dont's
> Netflix OSS - Eureka/Ribbon/Zipkin/Hystrix
> API gateway



> spring boot always refer to   project 
- application.properties 
  - User 
  - Login 
  - Question 
  - Rank 
  - 


> latency 
> Turn around time 

*** 
> to call - one service to another service we can use rest template 
```
RestTemplate restTemplate = new RestTemplate();
String fooResourceUrl  = "http://localhost:8080/spring-rest/foos";
ResponseEntity<String> response  = restTemplate.getForEntity(fooResourceUrl + "/1", String.class);

```

> OpenFeign instead fo rest template 



>1000000000 ->(zipkin)  User -> api-gateway (101) -> eureka (101) -> message-service (101) -> message-details-service


> spring boot 

> Netflix OSS Tools 

*** 

### Eureka Server
> https://start.spring.io/#!type=maven-project&language=java&platformVersion=2.4.8.RELEASE&packaging=jar&jvmVersion=11&groupId=com.company&artifactId=eureka-server&name=eureka-server&description=Demo%20project%20for%20Spring%20Boot&packageName=com.company.eureka.server&dependencies=web,devtools,cloud-eureka-server 

 ### Gateway
 > https://start.spring.io/#!type=maven-project&language=java&platformVersion=2.4.8.RELEASE&packaging=jar&jvmVersion=11&groupId=com.company&artifactId=api-gateway&name=api-gateway&description=Demo%20project%20for%20Spring%20Boot&packageName=com.company.api.gateway&dependencies=web,devtools,cloud-eureka,cloud-gateway

### Message-Service 
> https://start.spring.io/#!type=maven-project&language=java&platformVersion=2.4.8.RELEASE&packaging=jar&jvmVersion=11&groupId=com.company&artifactId=message-service&name=message-service&description=Demo%20project%20for%20Spring%20Boot&packageName=com.company.message.service&dependencies=web,devtools,cloud-eureka,cloud-feign

### Message-Details-Service
https://start.spring.io/#!type=maven-project&language=java&platformVersion=2.4.8.RELEASE&packaging=jar&jvmVersion=11&groupId=com.company&artifactId=message-details-service&name=message-details-service&description=Demo%20project%20for%20Spring%20Boot&packageName=com.company.message.details.service&dependencies=web,devtools,cloud-eureka

*** 


| Service Name                               | Port Number | Links                                                                      |
| ------------------------------------------ | ----------- | -------------------------------------------------------------------------- |
| Eureka                                     | 8761        | http://localhost:8761                                                      |
| API Gateway                                | 8765        | http://localhost:8765/MESSAGE-SERVICE/message                              |
| Message Service (Eureka Client, OpenFeign) | 9090 - 9095 | http://localhost:9090/message, http://localhost:9090/feign/message-details |
| Message Detail Service                     | 9050 - 9050 | http://localhost:9050/message-details                                      |


#### To invoke end poinsts 
> http://localhost:9090/message 
> http://localhost:9050/message-details
> http://localhost:8765/message-service/message 

> http://localhost:8765/MESSAGE-DETAILS-SERVICE/message-details 
> http://localhost:8765/message-details-service/message-details (after ignoring in case in application.properties )


#### to view swagger documentation 
> http://localhost:9090/swagger-ui.html 

> http://localhost:9090/v3/api-docs





Message 
- getMessage()
- getMyName() 
- saveMessage() 
- updateMessage()
- deleteMessage()
- 
MessageDetails 
- getMessageDetails()
- saveMessageDetails() 
- updateMessageDetails()
- deleteMessageDetails()



http://localhost:8765/message-service/fetchMessage (x) 

http://localhost:8765/promotion/buy-items/10/discount/2
http://localhost:8765/promotion/buy-items/20/discount/5
http://localhost:8765/promotion/buy-items/24/discount/5
http://localhost:8765/promotion/buy-items/10/discount/2
http://localhost:8765/promotion/buy-items/10/discount/2
http://localhost:8765/promotion/buy-items/10/discount/2




@Cconfiguration
@PropertyResource("classpath:application.properties")

server.port=9090
```
public String hi() {

    // i want to see 9090 here from application properties 

}

```

> localhost:9009/actuator/health

### Assignment 
1. in gateway configure in such a way that the service name need not be sent 
2. have your dependies of eureka client, swagger, in mongo service which was written 
3. write 1 method which shall show the port number of the instance running 
4. create 2 instances of any microserivce which you have -Dserver.port=9091 & see the port numbers coming, check to see LB is working 

*** 



<img src="./images/spring-micro-services-drawio.png" width="400">

# Day15 

> Spring security - jwt 
> Testing and mockito
> Spring boot actuator



```

### session validation 


<%
try{
	if(!((LoginBean)session.getAttribute("LOGIN")).getSessionId().equals(request.getSession().getId())){
		request.getRequestDispatcher("LoginError.jsp").forward(request, response);
	}
}catch(NullPointerException npe){
	npe.printStackTrace();
	 %>
	<jsp:forward page="LoginError.jsp"/>
	<%
	
}
%> 

```

> JWT 
> OAUTH 2.0 - inter application authentication 

- claims 

> Authorization - UserType (User/Admin/Manager)
> Authentication - management of session was /JWT 

*** 

> mock(List.class); 


- if i want to mock implementation 
- spy(ArrayList.class)



### To Test application on SpringBoot with Mockito 
> https://github.com/adithnaveen/baxter-fullstack-sep-2020/blob/master/spring-boot-projects/product-service/src/test/java/com/training/productservice/ProductServiceTest.java

> https://github.com/adithnaveen/baxter-fullstack-sep-2020/blob/master/spring-boot-projects/product-service/src/test/java/com/training/productservice/ProductHttpRequestTest.java

> https://github.com/adithnaveen/baxter-fullstack-sep-2020/blob/master/spring-boot-projects/product-service/src/test/java/com/training/productservice/ProductWebLayerTest.java



```


@Repository 
public interface UserRepository extends MongoRepository<User, Integer> {}

@Service
public class HomeService {
    @AutoWirrd
    private UserRepository repo; 

    
    public String sayGreet() {
        return "Hello World"; 
    }

    public User getUser(int id) {
        retrun repo.findUserById(id).get();     
    }

}


@Controller
public class HomeController {

    @AutoWired 
    private HomeService service; 

	@RequestMapping("/")
	public @ResponseBody String greeting() {
		return service.sayGreet();
	}
    @RequestMapping("/{id}")
	public @ResponseBody String getUser(@PathVariable("id") int id) {
		return service.getUser();
	}

}
```
*** 
# Day16 

> UI/UX
> JS, TS 
> React
> React Hooks 
> React Reduxt 



- html structure 


```
    
<html>
    <head>
        all the meta information 
    </head>
    <body>
    <div id="nav>
        // your navigator here 
    </div>
    <div id="header1">
        <h1>MyHeader</h1>
    </div>
    
    <div id="header2">
        <h2>MyHeader</h2>
    </div>

    <nav>
    </nav>
    <header>
        <h1>MyHeader</h1>
    </header>


    </body>
 

</html>
```

- SEO - HTML Semantics - Position 
  - Google / MSN / YAHOO/ BING / REDIFF 
- DOM - Document Object Model 
- BOM - Browser object model 

- table / span / div 



- header 
- nav
- section
- p
- article
- footer 
- summary 
- details 
- aside 
- 

- WIA ARIA 
- AA 
- AAA 
- 508 USA Standard 



Tools 
> lighthouse 
> axw 
> wave 


compliant 
> mobile 
> tablet 
> desktop/laptop 

```
    // desktop first desk.css 

    h1 {
        color:blue;
        font-family:arial;
        column-cont:3; 
        font-weight:36px;
    }

    // if i want for mobile compliant mobile.css 


    h1 {
        color:blue;
        column-cont:none;
        font-wdith:12px;
    }

// mobile first approach 
  h1 {
        color:blue;
        font-family:arial;
        font-wdith:12px;
    }

// on desktop 
h1 {
 font-wdith:36px;
 column-count:4
}

```


> responsive  - not building it 
> adaptive - only here 


Twitter 
> bootstrap 


12 Grids (xsm, sm, md, lg, xlg)
 < 12 (OK) - dont have  > 12 


## Project Discussion 

1. Domain
2. Tech Stack 
   1. Spring Boot 
   2. Micro Service Arch 
   3. Netflix OSS 
   4. mongodb 
   5. postgress 
   6. Selenium 
   7. Cucumber 
   8. ELK 
   9. Docker 
   10. Jenkins 
   11. jUnit
   12. jMeter 
   13. Redis 
   14. Kafka 
   15. ReactJS 
   16. MS Teams 
   17. terraform (PAAS)
   18. Ansible / Chef / Puppet 
   19. SonarQube + Sapinet SonarQube
   20. Cloud AWS 
3. logistics 
   1. 32 Gigs Application server 
   2. 16 Gigs Application server 
   3. S3 For static site 
   4. domain name 
   5. Mongo Repo 
   6. creating POD
   7. DOD, DOR 
   8. hub.docker.com 
   9. 


****
- by 12/July/2021
- Spring Microserivces Multi Module project  
  - with Hello World 
  - connected with mongoDB 
  - Docerize 
  - ++ Build it with Jenkins 

23 Pax/6


*** 

# Day17 

- val =100; this becomes global 
- var val = 100;  -out side the function then it will become global, inside the function its local, but global in the function 
- let - local to the instance block 
- const - local to the instance block  and once assigned you cannot change the value 

1. const 
2. let 
3. var 
4. without any type 

```
class Person {
    private int age; 
    private String name; 

    void display() {
        ///
    }
}
```


### Promise - The Promise object represents the eventual completion (or failure) of an asynchronous operation and its resulting value.



```
    // it can store anything and everything  
    ArrayList list = new ArrayList(); 
    list.add("hi");
    list.add(true);
    list.add(new Object());
    list.add(null);
    list.add(new World());

    let x = ???; 

    ArrayList<String> list = new ArrayList<String>(); 
```

- ducktyping 

#### Who will support 
- JavaScritp Support  (x)
- es6 support (x)
- typescript (yes)


Does Duck Quack 
    - feathers 
    - swim 
    - white in color 


### Images in class 

<img src="./images/17-js-ts.drawio.png" width="400">

*** 
<img src="./images/17-ui-mvc-mvp-mvvm.drawio.png" width="400">
*** 

# Day18

- Form Team 
- TDD -Javascript 
- Introduction to React 


### Project Discussion 

- You payment on line you get points 
  - Rule based enginee 
- product 
- product details 
- reports 
- login 
- registration
- 

- Understnding NODE 
- Node is WebServer 
- Node JS is written in JS 
- runs on V8 enginee - chrome, edge 
- Node runs on single threaded 

T1 - 1000 
T2 - 345 
T3 - 476
T4 - 90

> QT - 50 ms 

> 2/3 of the memory is not effectively used 

> node sample.js 
> 


#### JEST 


```
describe("some story", () => {

    test("your story", ()=> {
        // asserts 
    })
    test("your story", ()=> {
        // asserts 
    })

}) 

describe("some story", () => {

    test("your story", ()=> {
        // asserts library -  chaijs (assert, should, etc) (mocha)
    })
    test("your story", ()=> {
        // asserts 
    })
        describe("some story", () => {

            test("your story", ()=> {
                // asserts 
            })
            test("your story", ()=> {
                // asserts 
            })

        }) 
}) 
```


## working with reactjs 

```

<script>
    document.getElementById("resource1).innerHTML ="something"
</script>

<body> -> index.html 
    <div id="header"></div>  -- critical path 
    <div id="main">
        <div id="resource1">
            /// data, process the data, attach CSS to data, then render - DOM ->  VDOM
        </div>
        <div id="resource2"></div>
        <div id="resource3"></div>
        <div id="resource4"></div>
    </div>
    <div id="footer"></div>
</body>

```

```
    <Btn name="something"/>
```

- in reactJS - Stateful - class based - will have life cycles - overriden mehtods - with hit to end point -
  - From REST 
- in reactJS - Stateless - functions 
  - Hooks 
- 

*** 
> instead of npm -> yarn 

> npx create-react-app react-app 

> npm start
    - Starts the development server.
    - they start node server - 3000 
    - hot server 
    - css 
    - js 
    - webpack 

  yarn build
    Bundles the app into static files for production.

  yarn test
    Starts the test runner.

  yarn eject
    Removes this tool and copies build dependencies, configuration files
    and scripts into the app directory. If you do this, you can’t go back!

We suggest that you begin by typing:

  cd react-app
  yarn start


*** 

# Day 19 

Diffrences 
- Stateless 
  
  ```
    export default function MyApp(props) {
        return(
            <div></div>
        )
    }
  ```

- Statefull 

    ``` 
        -> props, context 
        class MyApp extends Component {
            state:{}
            render(){
                log(props)
                // to fetch and process 
                return (
                    <div>{somedata}</div>
                )
            }
        }
    ```



Form handling 
1. uncontrolled components ( deprecated now)
2. Controlled components - state 

```` 
<form onSubmit={this.handleSubmit}>
        <label>
          Name:
          <input type="text" name={this.state.name} />
        </label>
        <input type="submit" value="Submit" />
      </form>

````

```
<button class="btn btn-primary" onclick={this.somefunction}>Title </button>

<MyComponent class="btn btn-primary" handler={{this.somefunction}} caption="Title">


const Button =() => {}
const InputText =() => {}
const Password =() => {}
const CheckBox =() => {}

const Form = () => {
    return(
        <div>
            <InputText />
            <Password />
            <Button />
        </div>
    )
}

const Form2 = () => {
    return(
        <div>
            <InputText />
            <Password />
            
        </div>
    )
}

const Page = () => {

    return(
        <div>
            <Form />
            <Form2 />
        </div> 
    )

}

```

<img src="./images/19-react-forms.drawio.png" width="400">


*** 

# Day 20 


> React HOC - Higher Order Component 


Redux Reducer - its a function 

const initialState  = [];
action.type, action.data
reducer = (state = initialState, action) => {

    switch(action.type) {
        case 'ADD_NAME':
            return [...state,  action.data  ]
            break; 
        case 'DELETE_NAME':
            break; 
        case 'GET_NAMES':
            break; 
        default: 
            break; 

    }
}

> React-Redux Connect 
````
> function connect(mapStateToProps?, mapDispatchToProps?, mergeProps?, options?)
````

> npm i bootstrap json-server redux react-redux redux-devtools-extension redux-thunk react-router-dom

 

*** 


# Day 21 
- Redux 
- Hooks 
- Suspense - Lazy Loading - routing 
- JWT authentication is done 



> https://github.com/adithnaveen/sapient-freshers-2021-jun-asde/tree/main/images - Browser Routing 
> https://mail.google.com/mail/u/0/#inbox - hashed routing 
> https://mail.google.com/mail/u/0/#starred
> https://mail.google.com/mail/u/0/#drafts



> http://localhost:3000 -> / 
> http://localhost:3000 -> /add-contact
> http://localhost:3000 -> /show-contacts


*** 

```
-- old code 
   <div className="row">
        <div className="col">
          <ContactForm />
        </div>
        <div className="col">
          <ContactList />
        </div>
      </div>

```

> http://localhost:3000/#/show-contacts

> http://localhost:3000/add-contact

> https://in.news.yahoo.com/italy-crush-england-dreams-winning-215421919.html

> http://localhost:3000/contact-details/2
> http://localhost:3000/contact-details/3
> http://localhost:3000/contact-details/4

```
class MyComopnent extends Component{
    state={key:val}
    componentDidMount(){ <- side effect works 
        fetch
    }
    render(){return <></>}

}
```

const MyComponent = () => {
    useState <- will maintain the state 
    useEffect  <- help to get the data (side effect work)
    return(){<></>}
}



> 16.8 hooks 


```
import React, { useState } from 'react';

function Example() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

```
  // Similar to componentDidMount and componentDidUpdate:

useEffect(() => {
    // Update the document title using the browser API
    document.title = `You clicked ${count} times`;
  });

```


> useEffect(()=>{}) // it will be called implicitly everytime 
> useEffect(()=>{}, []) // it will be called implicitly but only once 
> useEffect(()=>{}, [name]) / will be called only for the state "name" 


> useState 
> useEffect 
> useEffect  + useState = useReducer 


> CSR - client side rendering 
> SSR - server side rendering 



*** 

# Day 22 

- Kafka 
- Selenium 

<img  src="./images/22-kafka-selenium.drawio.png">



> ESB - Enterprise Service Bus 
-  Open MQ - IBM 
-  Rabbit MQ - Rabbit 
-  Kafka - LinkedIn -> Apache 
-  Mule Soft 
-  Tibco 

- ZooKeeper Port Number - clientPort=2181

*** 

Working with Kafka 

- Step 1 - start Zookeeper 
  - ./zookeeper-server-start.sh ../config/zookeeper.properties 
- Step 2 - Start Kafka 
  - ./kafka-server-start.sh ../config/server.properties 
- Step 3 - Create Topic 
  -    ./kafka-topics.sh --create --bootstrap-server localhost:9092 --topic first-topic
  -    ./kafka-topics.sh --create --bootstrap-server localhost:9092 --topic second-topic
- Step 4 - List the Tipics Created
  - ./kafka-topics.sh --list --bootstrap-server localhost:9092  
- Step 5  - Host a producer on Kakfa Server 
  - ./kafka-console-producer.sh --broker-list localhost:9092  --topic first-topic
- Step 6 - Host a Kafka Consumer
  - ./kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic first-topic
- Step 7 - Host a Kafka Consumer from beginning 
  - ./kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic first-topic --from-beginning
- Step 8 - to delete a topic 
  - ./kafka-topics.sh --delete --topic second-topic --bootstrap-server localhost:9092  

*** 

SDET -> ASDE 

- junit -> parameterization -> jmeter / gatline / locust 
- rest assured -> API -> jmeter / gatline / locust / soapui 
- e2e -> Selenium ->(protractor, ranorex, browserstack, appium etc)



> Chrome -> every week 
> Firefox -> every week 
> Edge -> every week 
> Safari -> every week 
> opera -> every week 

*** 














