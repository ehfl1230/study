1. auto-repair
테이블이 손상되었을 시, 자동 복구하는 기능  
**[사용법]**  
특정 테이블 검사하고 싶을 경우:
mysqlcheck -u [계정정보] -p[패스워드] --auto-repair [DB명] [테이블명]
특정 DB를 검사하고 싶을 경우:
mysqlcheck -u [계정정보] -p[패스워드] --auto-repair [DB명]  
전체 DB 검사하고 싶을 경우:
mysqlcheck -u [계정정보] -p[패스워드] --auto-repair --all-databases  

2. optimize
데이터베이스 최적화
**[사용법]**  
특정 DB를 최적화하고 싶을 경우:
mysqlcheck -u [계정정보] -p[패스워드] --auto-repair [DB명]  
전체 DB 최적화하고 싶을 경우:
mysqlcheck -u [계정정보] -p[패스워드] --auto-repair --all-databases  



