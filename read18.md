# Web App Security
### Hibernate Many to Many Annotation Tutorial

#### how the `@ManyToMany` annotation can be used for specifying this type of relationships in Hibernate
#### A Typical Example

![Entity Relationship Diagram](./images/relation.jpg)

* the picture shows the many-to-many association between two entities employee and project:
    * any given employee can be assigned to multiple projects and a project may have multiple employees working for it, leading to a many-to-many association between the two
    * We have an employee table with employee_id as its primary key and a project table with project_id as its primary key.
    * A join table employee_project is required here to connect both sides.

#### Database Setup
* creating database is needed
* creating tables are needed and define a `primary-Key` and `forign-key`
* preparation of the dependencies and Hibernate configuration

#### The Model Classes
* classes need to be created with JPA annotations
* refer to one another, which means that the association between them is bidirectional.
* many-to-many association mapped by the `@ManyToMany`, `@JoinTable` and `@JoinColumn` annotations
* `@ManyToMany` annotation is used in both classes to create the many-to-many relationship between the entities.
* This association has two sides i.e. the owning side and the inverse side
* `@JoinTable` is used to define the join/link table
* The `@JoinColumn` annotation is used to specify the join/linking column with the main table
* in the example provided: the `mappedBy` attribute is used in the `@ManyToMany` annotation to indicate that the employees collection is mapped by the projects collection of the owner side.

#### Execution
* to see the many-to-many annotation in action, we can write JUnit test
* We can see the many-to-many relationship between the two entities created in the database

## Security: a humorous overview
![Searching a BST](./images/humoroussecure.jpg)
