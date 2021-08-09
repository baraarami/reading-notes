#  Web App Security
## [Many to many relationships](https://www.baeldung.com/hibernate-many-to-many)
- **Example :** many-to-many association
- ![](https://www.baeldung.com/wp-content/uploads/2017/09/New.png)
  - employee can be assigned to `multiple` projects
  - project may have `multiple` employees working for it
  -  `many-to-many` association between the two.
- How to join table employee_project? 
  -connect both sides ,of( employee table with employee_id )as its `primary key` `+` a project table with project_id as its `primary key`
  ## Code it :
  - ***Database Setup***
 ######
```
CREATE TABLE `employee` (
  `employee_id` int(11) NOT NULL AUTO_INCREMENT,
  `first_name` varchar(50) DEFAULT NULL,
  `last_name` varchar(50) DEFAULT NULL,
  PRIMARY KEY (`employee_id`)
) ENGINE=InnoDB AUTO_INCREMENT=17 DEFAULT CHARSET=utf8;

CREATE TABLE `project` (
  `project_id` int(11) NOT NULL AUTO_INCREMENT,
  `title` varchar(50) DEFAULT NULL,
  PRIMARY KEY (`project_id`)
) ENGINE=InnoDB AUTO_INCREMENT=18 DEFAULT CHARSET=utf8;

CREATE TABLE `employee_project` (
  `employee_id` int(11) NOT NULL,
  `project_id` int(11) NOT NULL,
  PRIMARY KEY (`employee_id`,`project_id`),
  KEY `project_id` (`project_id`),
  CONSTRAINT `employee_project_ibfk_1` 
   FOREIGN KEY (`employee_id`) REFERENCES `employee` (`employee_id`),
  CONSTRAINT `employee_project_ibfk_2` 
   FOREIGN KEY (`project_id`) REFERENCES `project` (`project_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```
- ***The Model Classes***
```
@Entity
@Table(name = "Employee")
public class Employee { 
    // ...
 
    @ManyToMany(cascade = { CascadeType.ALL })
    @JoinTable(
        name = "Employee_Project", 
        joinColumns = { @JoinColumn(name = "employee_id") }, 
        inverseJoinColumns = { @JoinColumn(name = "project_id") }
    )
    Set<Project> projects = new HashSet<>();
   
    // standard constructor/getters/setters
}
```
```
@Entity
@Table(name = "Project")
public class Project {    
    // ...  
 
    @ManyToMany(mappedBy = "projects")
    private Set<Employee> employees = new HashSet<>();
    
    // standard constructors/getters/setters   
}
```
#
## What to use In order to map a many-to-many association?
- `@ManyToMany`
- `@JoinTable`
- `@JoinColumn annotations`
# [Security: a humorous overview](https://scholar.harvard.edu/files/mickens/files/thisworldofours.pdf)
- How can I set a password based on potential threats ??
-  From the writer's point of view , here is some examples !!!...
 
  * Database Setup:
      - created database with the name spring_hibernate_many_to_many
      - create the employee and project tables along with the employee_project join table with employee_id and project_id as foreign keys
      - Once that is setup, preparation of the Maven dependencies and Hibernate configuration needs to be done.
      - Create model classes with JPA annotations. When both classes refer to one another, the association between them is bidirectional. 
      - In order to map a many-to-many association, we use the @ManyToMany, @JoinTable and @JoinColumn annotations.
      - @ManyToMany annotation - is used in both classes to create the many-to-many relationship between the entities. This association has two sides i.e. the owning side and the inverse side.
      - @JoinTable - is used to define the join/link table. 
      - @JoinColumn annotation - is used to specify the join/linking column with the main table. 
      - Execution: write the a JUnit test

**This World of Ours by James Mickens**
  * Its like security researchers have problems with public relations because they make it so you can't just do whatever you want on a website.
  * Security researchers are always trying to combate security issues, and make a better system for people to create passwords that are more secure. No matter what password you use, it can be breached. Its not a good idea to use the same password for everything.
  * The threat model is what security researchers use to combat security breaches by telling people how to make passwords and where the security threats come from, but those security breaches aren't always from obvious places.
  * There is no perfect security system out there, and no matter how strong of a security system it will be eventually broken in to. 
  * Information flow control and security labels are used to make things more secure.
  * Most people don't want to spend a bunch of money just to make there system more secure. So, security researchers should not focus on what would happen, but on what will happen when I properly compile my program.


######
|Threat|Solution|
|------|--------|
|Ex-girlfriend/boyfriend breaking into your email account and publicly releasing your correspondence with the My Little Pony fan club|Strong passwords|
|Organized criminals breaking into your email account and sending spam using your identity|Strong passwords + common sense (don’t click on unsolicited herbal Viagra ads that result in keyloggers and sorrow)|
|The Mossad doing Mossad things with your email account| Magical amulets?,  Fake your own death, move into a submarine?, YOU’RE STILL GONNA BE MOSSAD’ED UPON|

