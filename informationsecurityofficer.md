
## 2024-05-04 
`22:45~24:30`

이메일 인증 기술

  - SPF (Sender Policy Framework) : 발송자 메일서버 인증
  - DKIM (DomainKeys Identified Mail) : 메시지 헤더&바디 디지털 서명 통한 수신자 검증
  - DMARC (Domain-based Message Authentication, Reporting and Conformance) : SPF + DKIM + 인증결과 리포팅

DB 보안

  - 위협 2가지
  - 집성 (aggregation)
  - 추론 (inference)

  - 보안통제 3가지
  - 접근통제
  - 추론통제
  - 흐름통제

  - DBMS 보안 통제
  - DML / DDL / DCL / TCL
  - 뷰(view) 기반 접근 통제
  - SQL (DCL) 기반 접근 통제

DB 암호화 기술

  - 컬럼 암호화 방식 : API 방식 (응용프로그램 자체 암호화 방식), Plug-in 방식 (DB서버 암호화 방식), Hybrid 방식
  - 블록 암호화 방식 : TDE (Transparent Data Encryption) 방식 (DBMS 자체 암호화 방식), 파일 암호화 방식 (운영체제 암호화 방식)

## 2024-05-05
`17:25~18:00, 22:00~22:33, 23:00~23:40`

MySQL 취약점 점검

  - default 관리자 (root) 패스워드 및 계정명 변경 : update 후 flush privileges;
  - MySQL 설치 시 자동생성된 mysql 계정의 로그인 차단 : /etc/passwd > /bin/false or /sbin/nologin
  - MySQL 서버에 대한 원격접속 차단 : my.cnf > skip-networking
  - 데이터베이스 사용자별 접속/권한 설정 확인 : select host, user, password, file_priv, process_priv, shutdown_priv from user
  - 버전확인 및 보안패치
  - MySQL 데이터 디렉토리 보호여부 점검 : chmod 750 /var/lib/mysql

클라우드 컴퓨팅 보안

  - 가상화 : 데스크톱 가상화, 애플리케이션 가상화, 서버 가상화, 스토리지 가상화, 네트워크 가상화
  - 서비스 모델
  -   IaaS
  -   PaaS
  -   SaaS
  - 배치 모델
  -   퍼블릭 클라우드 모델
  -   프라이빗 클라우드 모델
  -   하이브리드 클라우드 모델
  - SECaaS : 안랩의 WAF 관제서비스 'WebGuard' 참조

보안장비 운용 - SNORT

  - 룰 헤더 설정
  -   action 유형 및 일반옵션
  - 룰 바디 설정
  -   내가 탐지할 payload의 범위를 지정하는 옵션들
  -   정규표현식
