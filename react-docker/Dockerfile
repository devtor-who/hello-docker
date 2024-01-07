# Base Image
FROM node:20-alpine

# pnpm 설치
RUN npm install -g pnpm

# 시스템 사용자를 생성하고 권한부여
#   -S -> 사용자 생성
#   -G -> 사용자에 그룹 지정
#
# root사용자로 app을 실행하지 않기위한 작업
# 만약 root사용자로 app을 실행할 경우 host시스템이 노출될 가능성이 있음
RUN addgroup app && adduser -S runner -G app

# 시스템 사용자 변경
USER runner

# Docker 내의 directory
WORKDIR /app

# 의존성 파일 복사
COPY package.json pnpm-lock.yaml ./

USER root

# 위에서 생성한 사용자에게 현재 directory 읽기권한 부여
RUN chown -R runner:app .

## 시스템 사용자 변경
## volume을 사용하는 경우 volume 호스트의 권한과 docker container USER 권한이 
## 서로달라서 문제가 발생함
# USER runner

# 의존성 설치
RUN pnpm install

# 애플리케이션 파일 복사
COPY . .

# 포트 노출
EXPOSE 5173

# 실행 명령어
CMD ["npm", "run", "dev"]