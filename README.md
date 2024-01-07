```
# docker image 빌드
docker build -t (태그이름) (Dockerfile 위치)

# docker image 확인
docker images

# docker image 실행
docker run (태그이름)

# docker image를 실행한 이후 terminal 사용하기
docker -it run (태그이름) sh

# docker port 매핑
docker run -p (호스트포트):(container포트)

# docker volume 지정하기
docker run -v "$(pwd):(WORKDIR)"
```
