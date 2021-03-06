# <img src="./doc/thenx.png" width="80" height="80"> Thenx Generator

------
English | [简体中文](./README-zh_CN.md)

The Thenx Generator is a more convenient general-purpose data interface generation platform based on the [MyBatis Generator (MBG) ](https://github.com/mybatis/generator). Compared with the traditional MyBatis Generator project, it is more than three times more efficient, and the portability, maintainability and decoupling of the platform project are improved by the way of extensions, so that the developers can write business code more focused.

You can directly introduce the Thenx Generator dependency to complete the data interface generation by simply configuring the database- related information, classpath, and Mapper path that you use.

Our main objectives are:

- Provide more efficient data interface generation for all Java ecological developers. 
- By shielding the implementation of non-business code to improve the efficiency of business developers focused development. 
- Avoid unannotated arbitrary interface classes, methods, and XML.

------

## Deployment and use

Thenx Generator dependencies can be introduced in the form of standalone Jar packages, but we recommend that you introduce Thenx Generator dependencies through Maven or Gradle.

The following are the Maven -based dependencies:

```xml
           <dependency>
                <groupId>org.thenx</groupId>
                <artifactId>thenx-generator-boot</artifactId>
                <version>0.0.1-SNAPSHOT</version>
            </dependency>
```

Dependencies can be introduced to create **generator.properties** profiles in the **resources directory** to get the Thenx Generator running:

```properties
# 1. db info
thenx.driver= com.mysql.cj.jdbc.Driver
thenx.url= jdbc:mysql://localhost:63306/generator_db?useUnicode=true&characterEncoding=utf8
thenx.username= generator_user
thenx.password= 123456789

# 2. jdbc -connector libs/*.jar
thenx.target.connector= libs/mysql-connector-java-8.0.15.jar

# 3. table name
thenx.target.table= generator_tests

# 4. entity
thenx.entity.package= org.thenx.entity
thenx.entity.project= thenx-generator-tests/src/main/java

# 5. dao
thenx.dao.package= org.thenx.dao
thenx.dao.project= thenx-generator-tests/src/main/java

# 6. mapper
thenx.mapper.package= mapper
thenx.mapper.project= thenx-generator-tests/src/main/resources
```

------

## Seek help

If you run into any problems using the Thenx Generator, we're always ready to help!

- Tell us about the problems you have by asking [questions](https://github.com/thenx-projects/thenx-generator/issues). 
- Let us know by email what problems you have (opensource@thenx.org)

## Feedback problem

If you find any bugs or new feature suggestions in the course of using the Thenx Generator, let us know directly by [submitting ISSUES](https://github.com/thenx-projects/thenx-generator/issues)!

## Building projects from source

You can extend your secondary development based on the Thenx Generator project or if you don't want to use the current stable version of the Thenx Generator, you can use Maven to build the latest project for the current main branch. It is worth noting that this project is based on OpenJDK 11, which we are using with the **Amazon corretto-11** version, which in theory can be run and compiled as long as it is JDK 11.

We just need to execute the following instructions to clone the latest code from the main branch:

```shell
$ git clone --depth=1 https://github.com/thenx-projects/thenx-generator.git
```

------

## Module description

The Thenx Generator has several important modules, and here is a quick overview:

### sql
This module simply stores the SQL fragments needed for contributors and developers to test the project, and imports them directly into your MySQL database.
### thenx-generator-boot
The thenx-generator-boot module is the startup entry for the entire Thenx Generator project, where the **GeneratorBoot** class is the primary startup class and the method (generator method) that needs to be called after the Thenx Generator dependency is introduced.

### thenx-generator-config
Thenx-generator-config module is used to configure code generation rules, generation path, and implementation of **CommentGenerator** method to improve the simple Entity, DAO layer generation rules.

### thenx-generator-plugins
The thenx-generator-plugins module is designed to improve the overall functionality and performance of MBG by extending the **PluginAdapter** interface to enhance and improve the Entity, DAO, Mapper, and annotate information based on reflection.

### thenx-generator-tests
The thenx-generator-tests module is mainly used for the test module of the whole project, including the path of Entity, DAO and Mapper, and can also prove the feasibility of the Thenx Generator in the multi-module project.

------

## License

Thenx Generator is Open Source software released under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0.html).
