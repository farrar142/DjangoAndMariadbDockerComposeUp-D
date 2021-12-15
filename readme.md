# 도커 위에 django프로젝트와 db를 컴포즈 하여 올리는 파일입니다.
- manage.py가 있는 최상위 디렉토리에서
- docker-compose up

### ${app_name}/setting.py 
-   상단에 from secured.py import _database
-   DATABASE = _databases로 바꿔주세요
-   ALLOWED_HOSTS = ["*"]로 바꿔주세요
### 데이타베이스 유저 세팅.
-   secure.py의 _database를 환경에 맞게 바꿔주세요.
-   docker-compose.yml 파일의 db: environment:항목도
-   알맞게 바꿔주세요.
### 시퀀스
1. db가 먼저 빌드 된 뒤 web이 빌드됩니다.
2. 하지만 db의 초기화 속도가 느려서 web이 먼저 서버를 실행합니다.
3. 본래라면 서버가 db를 찾지 못하고 종료되지만
4. netcat을 사용하여 db가 준비가 된 뒤
5. 웹 서버를 실행하게 됩니다.
6. 실행 하고 싶은 명령어는 wait.sh에서 커스터마이징 가능합니다.