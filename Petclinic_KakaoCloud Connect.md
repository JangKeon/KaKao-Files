# PetClinic 프로젝트 Kakao Cloud와 연동


1. Local Spring Suite에서 Petclinic Project Clone. 

2. Petclinic Project의 데이터베이스 형태를 h2가 아닌 Mysql로 바꿔줘야 함. (변환 방법은 application.properties 파일의 h2 부분을 application-mysql.properties로 바꾸고 url / username /password를 사용자에 맞게 설정해주면 됨. Kakao I Cloud 내에 있는 Mysql 인스턴스 사용 추천.)

3. Mysql로 변환 이후 Local에서 프로젝트를 실행시켜보고 localhost:8080에서 Petclinic이 잘 보이면 그 상태에서 DockerFile 작성 후 Image 생성. 

4. 생성된 Image를 Docker hub로 푸쉬. (Docker hub에 자기 ID 검색해서 올라갔는지 확인)

5. 카카오 Cloud VM으로 접속 후 생성해놨던 Image Pull, 해당 Image로 Container 생성.

6. 생성된 Container Start(docker start 이미지이름) / Run (docker run -p 8080:8080 도커허브ID/이미지이름)

7. Cloud의 VM 보안 정책에 ALL, 0.0.0.0/0 , ALL 인바운드 정책 추가. (어떤 경로로 접근해도 접속할 수 있게 만들어 주는 것이기에 보안에 취약해짐. 이번 프로젝트의 연결 확인만을 위한 추가)

8. Cloud의 VM 공인IP:8080 포트로 접속해 Petclinic 화면 확인.

참고 자료 : 
https://limjunho.github.io/2021/08/11/spring-mysql.html , (mybatis 부분 필요 없음) 
https://velog.io/@dhk22/Docker-spring-boot-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EB%8F%84%EC%BB%A4-%EC%9D%B4%EB%AF%B8%EC%A7%80%EB%A1%9C-%EB%B9%8C%EB%93%9C ,
수업자료 springboot1 등등..
