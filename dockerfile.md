

##### dockerfile 디렉토리 생성

```dockerfile
> mkdir D:\Temp\dockerfile
```



##### dockerfile 생성

D:\Temp\dockerfile\Dockerfile

```dockerfile
FROM centos:6.10
MAINTAINER aswip78@gmail.com
RUN touch data.txt
RUN echo "hello docker" >> data.txt
CMD ["/bin/bash"]
```



##### dockerfile 빌드

```sh
> docker build --tag centos2:0.1 D:/Temp/dockerfile
```





##### dockerfile 이미지 조회

```sh
> docker images
REPOSITORY        TAG             IMAGE ID            CREATED             SIZE
centos2           0.1             e241846bb6df        4 seconds ago       194MB
```



##### 생성된 이미지 히스토리 조회

```sh
> docker history centos2:0.1
IMAGE           CREATED          CREATED BY                                      SIZE    
e241846bb6df    31 minutes ago   /bin/sh -c #(nop)  CMD ["/bin/bash"]            0B
d82aa6a1442e    31 minutes ago   /bin/sh -c echo "hello docker" >> data.txt      13B
2c8026326801    31 minutes ago   /bin/sh -c touch data.txt                       0B
294c5f6d212c    31 minutes ago   /bin/sh -c #(nop)  MAINTAINER aswip78@gmail.…   0B
48650444e419    3 months ago     /bin/sh -c #(nop)  CMD ["/bin/bash"]            0B
<missing>       3 months ago     /bin/sh -c #(nop)  LABEL org.label-schema.sc…   0B
<missing>       3 months ago     /bin/sh -c #(nop) ADD file:2e9397e387a495d85…   194MB
```







##### dockerfile 이미지 실행 

```sh
> docker run -i -t --name vcentos2 centos2:0.1 /bin/bash
```





##### dockerfile에서 생성된 /data.txt 파일 확인

```sh
# cat /data.txt
hello docker
```





##### 컨테이너로부터 파일 꺼내기

```sh
> docker cp vcentos2:/data.txt ./
```





##### 컨테이너 변경사항 커밋

docker commit <옵션> <컨테이너 이름> <이미지 이름>:<태그> 형식

```sh
> docker commit -a "jinhokwon" -m "add hello.txt" vcentos centos2:0.2
```





##### 컨테이너 변경사항 조회

Usage:  docker history [OPTIONS] IMAGE

```sh
> docker history centos2:0.2
```







##### 컨테이너 세부정보 조회

```sh
> docker inspect vcentos
[
    {
        "Id": "caef16e94ffc68e1b8eebb27f628a233e1fb1bfe78ee9c4e5b59b3e13e8b69f0",
        "Created": "2019-07-02T22:26:57.0012945Z",
        "Path": "/bin/bash",
        "Args": [],
        "State": {
            "Status": "exited",
            "Running": false,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 0,
            "ExitCode": 0,
            ... 이하 생략 ...
]            
```







```dockerfile
FROM centos:6.10
MAINTAINER Foo Bar <foo@bar.com>

RUN echo $'[repo] \n\
name            = nginx repo \n\
baseurl         = http://nginx.org/packages/centos/7/$basearch/ \n\
enabled         = 1 \n\
gpgcheck        = 0' > /etc/yum.repos.d/nginx.repo

RUN yum -y update
RUN yum -y install nginx
RUN echo "\ndaemon off;" >> /etc/nginx/nginx.conf
RUN chown -R www-data:www-data /var/lib/nginx

VOLUME ["/data", "/etc/nginx/site-enabled", "/var/log/nginx"]

WORKDIR /etc/nginx

CMD ["nginx"]

EXPOSE 80
EXPOSE 443
```



##### dockerfile 이미지 빌드

```sh
> docker build --tag hello:0.1 D:/Temp/dockerfile
```



##### docker 이미지 목록 조회

```sh
> docker images
```



##### docker 이미지 실행

```sh
> docker run --name hello-nginx -d -p 80:80 -v D:/Temp:/win hello:0.1
```



##### boot2docker로 IP 확인

```sh
> boot2docker ip
The VM's Host only interface IP address is: 192.168.59.103
```





##### nginx로 접속

```sh

```



