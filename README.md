# jOOQ-gradle

### 1. Create Tables using DDL
Create the necessary tables in your database using DDL statements.

### 2. Configure Database Connection

`src/main/resources/application.yml`

```
spring:
  application:
    name: demo

  datasource:
    url: jdbc:mariadb://localhost:3306/DB
    username: DB_USER
    password: DB_PASSWORD
```

`/build.gradle`
```gradle
...

jooq {
	configuration {
		jdbc {
			driver = 'org.mariadb.jdbc.Driver'
			url = 'jdbc:mariadb://localhost:3306/DB'
			user = 'DB_USER'
			password = 'DB_PASSWORD'
		}

		generator {
			database {
				// https://www.jooq.org/doc/latest/manual/code-generation/codegen-advanced/codegen-config-database/codegen-database-name/
				name = 'org.jooq.meta.mariadb.MariaDBDatabase'
				inputSchema = 'DB_SCHEMA'
			}
			
...
```
### 3. Run jOOQ Code Generation
```
./gradlew jooqCodegen
```

After the code generation process completes, navigate to the build/generated-sources/jooq/main directory. Inside this directory, check the generated jOOQ classes with the J prefix.