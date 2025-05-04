# **Library Management System – Coursework Report**

## 1. Introduction

##### Goal of the Coursework :
The goal of this coursework is to design and implement a **Library Management System** that effectively models the core processes of a real-world library.  The system must allow users to manage books, members, and librarians.
##### Application :
The application developed for this system is to simulate the core functionalities of a library, managing it's daily activities. It focuses on managing the library catalog: Librarians can add new books, and the system ensures all books are stored centrally. User management (members and librarians), borrowing and returning operations, reservation handling, fine management for late returns, and persistent storage through JSON files.

##### How to run the program :
**Requirements:**

Python 3.8 or later

**Steps to run** :

* Save the provided code into a Python file, for example, library_system.py.
* Open a terminal or command prompt.
* Navigate to the directory containing library_system.py.
* Execute the following command:
* python library_system.py

##### How to use the program :
Currently, the program is structured to demonstrate its functionality through:


Creating users, example: Two users (Alice as a Librarian, Bob as a Member) are created.
![Ekrano kopija 2025-04-29 090118.png](https://www.dropbox.com/scl/fi/qvuq2621t6qodoob59ssv/Ekrano-kopija-2025-04-29-090118.png?rlkey=uhpmkg93ugamchjf5on268hck&dl=0&raw=1)

Having a library branch: 
![Ekrano kopija 2025-04-29 093034.png](https://www.dropbox.com/scl/fi/1ztosu5zzhk8mqgzsafzq/Ekrano-kopija-2025-04-29-093034.png?rlkey=exrg3wi9pfeffhkrat6f5pvvq&dl=0&raw=1)


Adding Books to the Catalog:
Only librarians can add books
![Ekrano kopija 2025-04-29 090807.png](https://www.dropbox.com/scl/fi/be0q14ikjmsb7gxjtrbhq/Ekrano-kopija-2025-04-29-090807.png?rlkey=uvdfoq627w90uewb0nzslzxxx&dl=0&raw=1) 

Members can borrow, return or reserve books and extend the borrow period:
![Ekrano kopija 2025-04-29 091428.png](https://www.dropbox.com/scl/fi/mo9dyl7xwq54cggbaqc36/Ekrano-kopija-2025-04-29-091428.png?rlkey=oogiyi53c1t4u2c4vtht9apkz&dl=0&raw=1)


## 2. Body / Analysis
### **Functional requirements and implementation**

#### 4 OOP pillars :
###### **Polymorhism :**
* **Concept** that lets a method perform different tasks depending on the object it's working with, even if the objects are of different types.
* Enables you to call the same method (e.g., get_role()) on different objects, and each object will respond in its own way depending on its class.
* Class Person has a polymorphic method get_role(), which is implemented differently in its subclasses Member and Librarian.

![Ekrano kopija 2025-04-29 094651.png](https://www.dropbox.com/scl/fi/fydoebcm8zcwys9l1h19o/Ekrano-kopija-2025-04-29-094651.png?rlkey=otv4gp8v4bo1l8lfb1gbegrzt&dl=0&raw=1)

###### **Abstraction:**
* **Abstract class** is a class that contains one or more abstract methods. Abstract class cannot be instantiated.
* You can define a contract for other classes to follow, without worrying about how they do it internally.
* The Person class is declared abstract using the ABC module, and defines the get_role() method, which must be implemented by subclasses

![Ekrano kopija 2025-04-29 095829.png](https://www.dropbox.com/scl/fi/pwki7ptnh63mc7qd5icrd/Ekrano-kopija-2025-04-29-095829.png?rlkey=io7lxwejdf9h67lwbqtnfrjy3&dl=0&raw=1)


###### **Inheritance :**
* **A mechanism** that allows you to reuse existing classes and extend their functionality. 
* A child class inherits from a parent class and can either use or override its methods and properties.
* Member and Librarian both inherit from the abstract base class Person. Here, Librarian inherits the name property and the structure from Person.

![Ekrano kopija 2025-04-29 100042.png](https://www.dropbox.com/scl/fi/pyhjswkckia7zehhbgip9/Ekrano-kopija-2025-04-29-100042.png?rlkey=eellk5kol6d58hau9maeotscs&dl=0&raw=1)

###### **Encapsulation:**
* **A bundling** of data and methods that operate on that data, while restricting direct access to some components.
* By using private (__variable) or protected (_variable), you **restrict outside access** and enforce controlled interaction.
* These id's are encapsulated and cannot be accessed directly from outside the class.

![Ekrano kopija 2025-04-29 102034.png](https://www.dropbox.com/scl/fi/gf6tubpyl310oemj8eb5j/Ekrano-kopija-2025-04-29-102034.png?rlkey=l0iupw1kspwevptnnaw26q4rt&dl=0&raw=1)
![Ekrano kopija 2025-04-29 102023.png](https://www.dropbox.com/scl/fi/4u3gdt2ke9nweut0erbnm/Ekrano-kopija-2025-04-29-102023.png?rlkey=jcnzitfvuzxzubrxlxjhbfret&dl=0&raw=1)

#### Design Patterns:
###### **Singleton**:
* This design pattern is used for the library catalog.
* The pattern ensures that a class has **only one instance**.
* In a library system, the catalog of books should be centralized. Having multiple instances of the catalog could cause inconsistency in book availability, data duplication, or data loss. 


###### **Factory**:
* It is used for person creation.
* A creational design pattern that **provides an interface** for creating objects.
* This pattern is ideal when the system needs to create objects based on runtime conditions, for example, whether a new user is a "member" or a "librarian".

#### Use of composition and aggregation principles :    
**Composition**  is a relationship where one object completely owns another. If the container object is destroyed, the composed objects usually are too.

* Class Book has an Author. The Author object is created and passed when the Book is initialized. If the Book is deleted, the Author associated with that instance is no longer used by the book.

![Ekrano kopija 2025-04-29 103723.png](https://www.dropbox.com/scl/fi/8gjvkg57joslarnfp33ju/Ekrano-kopija-2025-04-29-103723.png?rlkey=b6zg1z8z3x6vnzff2g0qa54br&dl=0&raw=1)

**Aggregation** is a weaker relationship, where one object contains or references others—but they can exist independently.

* A LibraryBranch has a list of Members and Librarians. But Member and Librarian objects can exist outside of the branch. If a branch is deleted, the people are not deleted they just aren’t part of that branch anymore.

![Ekrano kopija 2025-04-29 104039.png](https://www.dropbox.com/scl/fi/uy4xyad2kwowd3oumam1w/Ekrano-kopija-2025-04-29-104039.png?rlkey=zf3kewtey48uup0j12we33uik&dl=0&raw=1)

#### Reading from file & writing to file :

File I/O (input/output) is used to persist data, such as books, members, and librarians, between sessions. This is handled through the LibraryStorage class.
![Ekrano kopija 2025-04-29 091717.png](https://www.dropbox.com/scl/fi/sksewjdoe6kjff5g7x44u/Ekrano-kopija-2025-04-29-091717.png?rlkey=zytodru21txq4kaskqdpb0lud&dl=0&raw=1)

![Ekrano kopija 2025-04-29 092031.png](https://www.dropbox.com/scl/fi/d5dcbxgi55et341wwotzc/Ekrano-kopija-2025-04-29-092031.png?rlkey=tg7u3gf33q7nqo319mcawferr&dl=0&raw=1)

The save_members method writes the list of Members objects to a JSON file (members.json). Each members' name and id is converted into a dictionary format suitable for JSON serialization. This allows the data to be stored on disk and reused in future sessions.

The load_members method reads from the members.json file. It loads the JSON content into Python dictionaries, then reconstructs the Member objects by passing the data. This allows the application to restore its state from previous runs.

## 3. Results and Summary
###### Results:
* Successfully implemented borrowing, returning, reserving, and fine calculation features.
* Library catalog behaves as a singleton, ensuring centralized management.
* Data is successfully saved to and loaded from JSON files.
* Unit tests validate all major operations.
* Design patterns enhance code readability and maintainability.

###### Challenges Faced:

*  Using singleton, maintaining a single instance without external libraries 
*  Designing JSON to read from & write to file
*  Unit Testing to make sure the system works

###### Conclusions: 
The development of the Library Management System achieved the key objectives outlined in the coursework guidelines, structured object-oriented design, incorporated object-oriented principles like inheritance, encapsulation, and polymorphism. Tried to use all of the good practices listed.

###### Future Prospects:
* Database Integration: Replace JSON storage with an SQL database for better scalability and performance.
* Books recommendations to members using collaborative filtering
*  Add support for notifications, multi-copy book management, and inter-branch book transfers.

