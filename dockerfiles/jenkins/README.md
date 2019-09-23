jenkins 구축

1. docker pull jenkins

2. docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts


jenkins plugin 수동 설치

1. jenkins 수동 파일 download
 -https://updates.jenkins-ci.org/download/plugins/
 
2. docker cp [host 파일경로] [container name]:[container 내부 경로] 사용하여 plugin 폴더에 파일 copy

3. restart
