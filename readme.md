#REQUIREMENTS I NEEDED TO INSTALL TO WORK ON MY LINUX MINT:

sudo apt install openjdk-11-jdk
export JAVA_HOME=/usr/lib/jvm/java-1.11.0-openjdk-amd64
sudo apt install maven
mvn clean install
mvn clean install jetty:run

#SELECT WITH

sudo update-alternatives --config java


## Containerising Pet Clinic app using Docker

This is a [dockerized version of the original app](https://github.com/spring-projects/spring-petclinic) published by Spring Boot community. 


## Running PetClinic app locally

Petclinic is a [Spring Boot](https://spring.io/guides/gs/spring-boot) application built using Maven. It is an application designed to show how the Spring stack can be used to build simple, but powerful database-oriented applications. The official version of PetClinic demonstrates the use of Spring Boot with Spring MVC and Spring Data JPA.

## How it works?

Spring boot works with MVC (Model-View-Controller) is a pattern in software design commonly used to implement user interfaces, data and control logic. It emphasizes a separation between business logic and its visualization. This "separation of concerns" provides a better division of labor and improved maintenance.We can work with the persistence or data access layer with [spring-data](https://spring.io/projects/spring-data) in a simple and very fast way, without the need to create so many classes manually. Spring data comes with built-in methods below or by default that allow you to save, delete, update and/or create.


## Getting Started


```
git clone https://github.com/dockersamples/spring-petclinic.git
cd spring-petclinic
./mvnw package
java -jar target/*.jar
```

You can then access petclinic here: http://localhost:8080/

<img width="625" alt="image" src="https://user-images.githubusercontent.com/313480/179161406-54a28200-d52e-411f-bfbe-463cf64b64b3.png">

The applications allows you to perform the following set of functions:

- Add Pets
- Add Owners
- Finding Owners
- Finding Veterinarians
- Exceptional handling


Or you can run it from Maven directly using the Spring Boot Maven plugin. If you do this it will pick up changes that you make in the project immediately (changes to Java source files require a compile as well - most people use an IDE for this):

```
./mvnw spring-boot:run
```

> NOTE: Windows users should set `git config core.autocrlf true` to avoid format assertions failing the build (use `--global` to set that flag globally).

> NOTE: If you prefer to use Gradle, you can build the app using `./gradlew build` and look for the jar file in `build/libs`.

## Building a Container

```
 docker build --tag petclinic-app .
```

## Multi-Stage Build

```
 DOCKER_BUILDKIT=0 docker build -t petclinic-app --target development .
```

## Using Docker Compose

```
docker compose up -d --build
```

#Next, let’s test our API endpoint. Run the following curl commands:

``` 
curl --request GET \ --url http://localhost:8080/vets \ --header 'content-type: application/json'
```


## References

- [Building PetClinic app using Dockerfile](https://docs.docker.com/language/java/build-images/)

