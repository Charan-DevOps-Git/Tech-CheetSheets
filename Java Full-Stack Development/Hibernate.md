# Introduction

Hibernate is an object-relational mapping (ORM) framework for Java. It provides a framework for mapping an object-oriented domain model to a relational database.

# Basic Setup

1.Add Hibernate Dependencies:

Maven:
```
<dependencies>
    <dependency>
        <groupId>org.hibernate</groupId>
        <artifactId>hibernate-core</artifactId>
        <version>5.4.32.Final</version>
    </dependency>
    <dependency>
        <groupId>org.hibernate</groupId>
        <artifactId>hibernate-entitymanager</artifactId>
        <version>5.4.32.Final</version>
    </dependency>
    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
        <version>8.0.23</version>
    </dependency>
</dependencies>
```

Gradle:
```
dependencies {
    implementation 'org.hibernate:hibernate-core:5.4.32.Final'
    implementation 'org.hibernate:hibernate-entitymanager:5.4.32.Final'
    implementation 'mysql:mysql-connector-java:8.0.23'
}
```

2. Hibernate Configuration File (hibernate.cfg.xml):

```
<!DOCTYPE hibernate-configuration PUBLIC "-//Hibernate/Hibernate Configuration DTD 3.0//EN" "http://hibernate.sourceforge.net/hibernate-configuration-3.0.dtd">
<hibernate-configuration>
    <session-factory>
        <property name="hibernate.dialect">org.hibernate.dialect.MySQL8Dialect</property>
        <property name="hibernate.connection.driver_class">com.mysql.cj.jdbc.Driver</property>
        <property name="hibernate.connection.url">jdbc:mysql://localhost:3306/yourdatabase</property>
        <property name="hibernate.connection.username">yourusername</property>
        <property name="hibernate.connection.password">yourpassword</property>
        <property name="hibernate.hbm2ddl.auto">update</property>
        <property name="hibernate.show_sql">true</property>
        <property name="hibernate.format_sql">true</property>
        <mapping class="com.example.YourEntityClass"/>
    </session-factory>
</hibernate-configuration>
```

# Entity Mapping

- Basic Entity Class:
```
import javax.persistence.Entity;
import javax.persistence.Id;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;

@Entity
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String username;
    private String password;

    // Getters and setters
}
```

# Annotations:

- @Entity: Marks the class as a persistent entity.
- @Table: Specifies the table name (optional if the table name is the same as the class name).
- @Id: Marks the field as a primary key.
- @GeneratedValue: Specifies the primary key generation strategy.
- @Column: Specifies the column details (optional if the column name is the same as the field name).

# Hibernate Session

- Creating a Session Factory:
```
import org.hibernate.SessionFactory;
import org.hibernate.cfg.Configuration;

public class HibernateUtil {
    private static SessionFactory sessionFactory;

    static {
        try {
            sessionFactory = new Configuration().configure().buildSessionFactory();
        } catch (Throwable ex) {
            throw new ExceptionInInitializerError(ex);
        }
    }

    public static SessionFactory getSessionFactory() {
        return sessionFactory;
    }
}
```

- Opening a Session and Transaction:
```
import org.hibernate.Session;
import org.hibernate.Transaction;

public class Main {
    public static void main(String[] args) {
        SessionFactory sessionFactory = HibernateUtil.getSessionFactory();
        Session session = sessionFactory.openSession();
        Transaction transaction = null;

        try {
            transaction = session.beginTransaction();

            // Perform operations

            transaction.commit();
        } catch (Exception e) {
            if (transaction != null) {
                transaction.rollback();
            }
            e.printStackTrace();
        } finally {
            session.close();
        }
    }
}
```

# CRUD Operations

- Create:
```
public void createUser(User user) {
    Session session = HibernateUtil.getSessionFactory().openSession();
    Transaction transaction = session.beginTransaction();
    session.save(user);
    transaction.commit();
    session.close();
}
```

- Read:
```
public User getUser(Long id) {
    Session session = HibernateUtil.getSessionFactory().openSession();
    User user = session.get(User.class, id);
    session.close();
    return user;
}
```

- Update:
```
public void updateUser(User user) {
    Session session = HibernateUtil.getSessionFactory().openSession();
    Transaction transaction = session.beginTransaction();
    session.update(user);
    transaction.commit();
    session.close();
}
```

- Delete:
```
public void deleteUser(Long id) {
    Session session = HibernateUtil.getSessionFactory().openSession();
    Transaction transaction = session.beginTransaction();
    User user = session.get(User.class, id);
    if (user != null) {
        session.delete(user);
    }
    transaction.commit();
    session.close();
}
```

# Queries

- HQL (Hibernate Query Language):
```
import org.hibernate.query.Query;

public List<User> getAllUsers() {
    Session session = HibernateUtil.getSessionFactory().openSession();
    Query<User> query = session.createQuery("FROM User", User.class);
    List<User> users = query.list();
    session.close();
    return users;
}
```

- Criteria API:
```
import org.hibernate.Criteria;
import org.hibernate.criterion.Restrictions;

public User getUserByUsername(String username) {
    Session session = HibernateUtil.getSessionFactory().openSession();
    Criteria criteria = session.createCriteria(User.class);
    criteria.add(Restrictions.eq("username", username));
    User user = (User) criteria.uniqueResult();
    session.close();
    return user;
}
```

# Relationships

- One-to-One:
```
@Entity
public class UserProfile {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @OneToOne(mappedBy = "userProfile")
    private User user;

    // Getters and setters
}
```
```
@Entity
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @OneToOne
    @JoinColumn(name = "user_profile_id")
    private UserProfile userProfile;

    // Getters and setters
}
```

- One-to-Many:
```
@Entity
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @OneToMany(mappedBy = "user", cascade = CascadeType.ALL, orphanRemoval = true)
    private Set<Post> posts = new HashSet<>();

    // Getters and setters
}
```
```

@Entity
public class Post {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @ManyToOne
    @JoinColumn(name = "user_id")
    private User user;

    // Getters and setters
}
```

- Many-to-Many:
```
@Entity
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @ManyToMany(cascade = { CascadeType.PERSIST, CascadeType.MERGE })
    @JoinTable(
        name = "user_role",
        joinColumns = @JoinColumn(name = "user_id"),
        inverseJoinColumns = @JoinColumn(name = "role_id")
    )
    private Set<Role> roles = new HashSet<>();

    // Getters and setters
}
```
```
@Entity
public class Role {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @ManyToMany(mappedBy = "roles")
    private Set<User> users = new HashSet<>();

    // Getters and setters
}
```

# Caching

- First-Level Cache: Session-level cache (enabled by default).
- Second-Level Cache: Configure in hibernate.cfg.xml:
```
<property name="hibernate.cache.use_second_level_cache">true</property>
<property name="hibernate.cache.region.factory_class">org.hibernate.cache.ehcache.EhCacheRegionFactory</property>
<property name="net.sf.ehcache.configurationResourceName">/ehcache.xml</property>
```

# Resources

- [Hibernate Tutorials](https://www.javatpoint.com/hibernate-tutorial)
- [Java Persistence API (JPA) Documentation](https://www.javatpoint.com/jpa-introduction)

This cheat sheet covers the fundamental aspects of Hibernate, including setup, basic entity mapping, CRUD operations, relationships, caching, and more. Expand with specific use cases and examples as needed for your projects.
