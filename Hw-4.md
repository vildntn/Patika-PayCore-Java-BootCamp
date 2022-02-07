# Homework 4

### 1 – What is JPA ?
JPA(Java Persistence API) is a technology that associates objects with relational database tables and does not forget these relationships, which we can continue to use later.
* With JPA, developers can work directly on objects instead of SQL commands, and JPA contains SQL queries.
* JPA creates the interface point between the application and the database.
* JPA is concerned with how the data will be mapped on the database, the security and performance of the data.
* JPA is a technology available for both Java SE and Java EE.
* Hibernate, TopLink, EclipseLink and OpenJPA are the main tools that implement JPA.
* With JPQL, we can provide database communication with classes and objects, thanks to the Java Persistence API.
### 2 - What is the naming convention for finder methods in the Spring data repository interface ?
The finder method should use a special keyword like "find", followed by the name of the variable.The query is prepared by Spring Data JPA according to the defined method names and parameter value.In this way, it is sufficient to define and use a method in the repository according to the desired result.
*For example:*
```
List<Cat> findByName(String name);
```
This method will return a list of cat by a name which taken from parameter.

### 3 - What is PagingAndSortingRepository?
PagingAndSortingRepository is the interface that extends from CrudRepository to provide additional methods to retrieve entities using pagination and sorting.
It provides two method:
* Page findAll(Pageable pageable): returns a Page of entities meeting the paging restriction provided in the Pageable object.
* Iterable findAll(Sort sort) :returns all entities sorted by the given options.
### 4 - Differentiate between findById() and getOne()?
*The getOne() method* returns the reference of the object of the given id. This method always returns a proxy without going to the database (lazy fetch). Throws EntityNotFoundException if the requested entity is not found in the database.
Each time the *findById method* is called, it goes to the database and retrieves the object from there. This is the EAGER loaded transaction, so if the object we are trying to fetch is not in the DB, it will return null.
* The getOne method offers better performance, while the findById method requires an additional database query.
* Since the object is retrieved completely with the findById method, all its properties can be accessed, while it cannot be accessed with the getOne method.
### 5 - What is @Query used for?
Query annotation is used to create queries over objects created from classes called Entities that are mapped to database tables.Spring Data JPA @Query annotation is used on Repository interface.The @Query annotation contains the custom JPQL querty.For our methods, we can write sql-like queries in query annotation with Jpql.
*For Example:*
```
@Query("From JobExperience j Inner join j.curriculumVitae c Where c.jobSeeker.id=:id Order By j.endDate desc")
	List<JobExperience> getAllJobExperienceByJobSeekerIdByDate(int id);
```
This method returns a list of previous job experiences sorted by descending date by a job seeker's id which is taken from parameter.
### 6 - What is lazy loading in hibernate?
In Hibernate, the relation between objects differs in pulling the data in the database.These are called Lazy loading and Eager loading.
*Lazy loading* is known as the concept of delaying the loading of an object until it is needed.With Lazy loading, we shorten the initial processing time by pulling the data you won't need right away, later when needed.Lazy loading in hibernate improves the performance. It loads the child objects on demand.If we are not sure to use the associated object, we should use lazy loading.
### 7 – What is SQL injection attack? Is Hibernate open to SQL injection attack?
SQL injection is the unauthorized access to the data in the database by interfering with the SQL query made by the web application.Thanks to SQL injection, attackers can steal user information on the website, access hidden information, interfere with existing data, change some operations, increase its authority and completely delete the database.Hibernate provides many ways we should use to protect ourselves from SQL Injection attacks. But sql or jpql queries that wrongly written are always open to sql injection attacks.
### 8 - What is criteria API in hibernate?
The Criteria API is used to define queries for entities and their persistent state by creating query-defined objects.The Criteria API allows us to build up a criteria query object programmaticaly, where we can apply different kinds of filtration and logical conditions.
### 9 - What Is Erlang? Why Is It Required For Rabbitmq?
Erlang is a general-purpose, concurrent, dynamic, functional programming language that also has garbage collection feature.RabbitMQ is written using Erlang programming language and Erlang language must be installed on the system for it to work in our environment.RabbitMQ runs in Erlang virtual runtime.
### 10 – What is the JPQL?
JPQL (Java Persistence Query Language) is a query language used to query SQL-like JPA Entity objects.The main difference between SQL and JPQL is that SQL works with relational database tables, whereas JPQL works with Java classes and objects.
*Example of JPQL*
```
@Query("From Product where productName=:productName and category.categoryId=:categoryId")
List<Product> getByNameAndCategory(String productName, int categoryId);
```
This method will return a list of suitable products according to the product name and category id taken from the parameter.

### 11 – What are the steps to persist an entity object?
1. Creating an entity manager factory object.
2. Obtaining an entity manager from factory.
3. Initializing an entity manager.
4. Persisting a data into relational database.
5. closing the transaction.
6. Releasing the factory resources.
### 12 – What are the different types of entity mapping?
There are three types of entity mapping and each relationship can be one-way or two-way.In entities using a one-way relationship, the unrelated entity can not reach the other entitiy (undirectional), while the entities using two-way relationship can reach each other(bidirectional).
* one-to-one
* one-to-many or many-to-one.
* many-to-many
### 13 - What are the properties of an entity?
Properties that an entity must have:
* Persistability: This is how the entity stored in database is called.
* Persistant Identity: This identity is equavalent to primary key in database
* Transactionality: An entity can perform crud operations like create,delete.
* Granuality: Entities should not be primitive.
### 14 - Difference between CrudRepository and JpaRepository in Spring Data JPA?
CrudRepository and JPA repository both are the interface of the spring data. 
* JpaRepository extends the PagingAndSorting repository which is extended from CrudRepository.
* CrudRepository is the base interface.
* While CrudRepository provides only crud methods like findOne
* JpaRepository extends the PagingAndSorting repository that provides the pagination and sorting for us.
* CrudRepository doesn't provide pagination and sorting methods.
* While JPA also provides some extra methods like flush(),saveAndFlush(),but CrudRepository provides only crud functions.
