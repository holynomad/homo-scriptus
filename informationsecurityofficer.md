
`2024-05-04 22:45~24:30`

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
