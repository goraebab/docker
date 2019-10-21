
### 1. MySQL docker image 가져오기 

```sh
# docker search mysql
# docker pull mysql
# docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
mysql               latest              c8ee894bd2bd        4 days ago          456MB
```



### 2. MySQL 실행하기.

```sh
# docker run --name mysql -e MYSQL_ROOT_PASSWORD=1234 -d -p 3306:3306 mysql
```
