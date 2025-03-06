<br><b>Task_1 Backend (Java Spring Boot Framework)</b>

I navigated to the https://start.spring.io/ and designed new project for my backend.

![alt text](image.png)

I downloaded generated Java Spring Boot project compressed file and moved it via scp from my host PC to the oracle linux machine

<i>scp backend.zip username@192.x.x.128:/home/username/</i>

After unziping the project I navigated to the backend/src/main/resources/application.properties and configured the connection to the postgresql instance.
```
spring.datasource.url=jdbc:postgresql://localhost:5432/main_db
spring.datasource.username=test
spring.datasource.password=test
spring.jpa.show-sql=true
```
<i> ./mvnw spring-boot:run </i> was executed and backend>postgres db connection established

In the next step I needed to create Java entity class, which represents table in database. This class is annotated with @Entity, so Hibernate can map it to SQL table.
The first java file: Users.java in /src/main/java/com/kubo27/backend/ path. 
#username as a primary key
```
package com.kubo27.backend.model;

import lombok.*;
import jakarta.persistence.*;

@Data
@Entity
@Table(name = "users")
public class Users{

        @Id
        private String username;
        @Column(nullable = false)
        private String password_hash;
        @Column(nullable = false)
        private String email;
        @Column (nullable = false)
        private String status;

}
```


The next file : UsersRepository.java is a JPA repository as an interface that communicates witg SQL db without using sql query. JPA automatically provides a CRUD operations (create,read,update,delete).


```
package com.kubo27.backend.repository;

import com.kubo27.backend.model.Users;
import org.springframework.data.jpa.repository.JpaRepository;

public interface UsersRepository extends JpaRepository<Users, String>{
}
```


And the last UserController.java. This file contains all the logic for the user registration via REST API.
I created only one mapping for testing purposes


```
package com.kubo27.backend.controller;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;
import com.kubo27.backend.repository.*;
import com.kubo27.backend.model.*;


@RestController
@RequestMapping("/api/user")
public class UserController {

    @Autowired
    UsersRepository usersRepository;

    @PostMapping
    public String create(@RequestBody Users users) {
        usersRepository.save(users);
        return "User is created";
    }


}
```


```
curl -X POST "http://localhost:8080/api/user" -H "Content-Type: application/json" -d '{"username": "testuser","password_hash":"124faasf21","email":"test@user.com","status":"verified"}'
```

