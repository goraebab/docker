

#### 1. spring petclinic 다운로드 및 빌드 

##### 1) 소스코드 다운로드

```sh
# git clone https://github.com/spring-projects/spring-petclinic.git
```



##### 2) spring-petclinic/src/main/resources/application-mysql.properties 파일 수정

```ini
spring.datasource.username=petclinic
spring.datasource.url=jdbc:mysql://127.0.0.1/petclinic?characterEncoding=UTF-8&serverTimezone=UTC
```



##### 3) 빌드

```sh
# cd spring-petclinic
# mvn clean package
```



#### 2. spring petclinic mysql 설정

##### 1) mysql petclinic 사용자 추가

```sql
CREATE USER 'petclinic'@'%' IDENTIFIED BY 'petclinic';
GRANT ALL PRIVILEGES ON *.* TO petclinic@'%' IDENTIFIED BY 'petclinic';
```



##### 2) mysql petclinic 사용자 제거

```sql
DROP USER 'petclinic'@'%';
```



#### 3. spring petclinic 실행

##### 1) mysql을 main db로 사용하는 경우

```sh
# java -jar -Dspring.profiles.active=mysql target\spring-petclinic-2.1.0.BUILD-SNAPSHOT.jar 
```



##### 2) mysql을 main db로 사용하고, datasource url을 변경해서 실행하는 경우

```sh
# java -jar -Dspring.profiles.active=mysql -Dspring.datasource.url=jdbc:mysql://192.168.56.123/petclinic target\spring-petclinic-2.1.0.BUILD-SNAPSHOT.jar
```



