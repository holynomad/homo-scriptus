
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
    - IaaS
    - PaaS
    - SaaS
  - 배치 모델
    - 퍼블릭 클라우드 모델
    - 프라이빗 클라우드 모델
    - 하이브리드 클라우드 모델
  - SECaaS : 안랩의 WAF 관제서비스 'WebGuard' 참조

보안장비 운용 - SNORT

  - 룰 헤더 설정
    - action 유형(alert, log, drop, reject 등) 및 일반옵션 (msg, sid, rev 등)
  - 룰 바디 설정
    - 내가 탐지할 payload의 범위를 지정하는 옵션들 (content, offset, depth, distance, within, nocase 등)
    - 정규표현식

## 2024-05-06

snort를 이용한 침입탐지시스템 운영 `15:50~17:15`

  - alert tcp $EXTERMAL_NET any -> $HOME_NET any (msg:"[TEST] offset_depth"; content:"test"; offset:2; depth:4; nocase; sid:1000012;
  - pcre (Perl Compatible Regular Expression) 옵션 
    - pcre:"/^(GET|POST)/"
  - event threshold 관련 옵션
    - threshold:type limit, track by_dst, count 1, seconds 5;
    - threshold:type threshold, track by_dst, count 5, seconds 30;
    - threshold:type both, track by_dst, count 3, seconds 60;

iptables를 이용한 침입차단시스템 운영 `22:00~22:40`

  - 상태추적 (connection tracking 또는 stateful inspection) 기능
    - 방화벽 통과하는 모든 패킷 연결 상태 추적해서 메모리 기억 & 비교해서 통과/거부 판단
  - iptables -A INPUT -p tcp ! --syn -m state --state NEW -j DROP
  - iptables -A INPUT -p tcp --tcp-flags ALL NONE -m limit --limit 1/second -j LOG --log-prefix "[NULL scan LOG limit]"

보안솔루션 (I) `22:50~23:30`

  - 무선침입방지시스템 (WIPS : Wireless Intrusion Prevention System)
  - 네트워크접근제어 (NAC : Network Access Control)
  - 통합보안시스템 (UTM : Unified Threat Management)
  - 엔드포인트 탐지 및 대응 솔루션 (EDR : Endpoint Detection and Response)
  - 스팸차단솔루션 (Anti-Spam Solution)
  - 보안운영체제 (Secure OS)

## 2024-05-07

콘텐츠/정보유출방지 보안솔루션 `22:30~22:50`

  - 보안 USB
  - 디지털저작권관리 (DRM)
  - 네트워크/단말 정보유출방지 (DLP)

보안관제 솔루션 `22:50~23:15`

  - 전사적 보안관리 시스템 (ESM) : 다양한 보안장비 발생하는 로그,이벤트 등을 통합적으로 수집 및 관리
    - 구성요소 : ESM 에이전트, ESM 매니저, ESM 콘솔
  - 보안정보 및 이벤트관리 시스템 (SIEM) : 다양한 장비 및 범위에서 발생하는 로그,이벤트를 수집하여 빅데이터 기반의 상관관계분석을 통해 위협 차단하는 통합보안관제 솔루션
    - 데이터 통합, 상관관계 분석, 알림, 대시보드
  - 보안 오케스트레이션, 자동화 및 대응 시스템 (SOAR) : 자동화된 분석/대응 환경을 통한 보안인력 효율적 운영 및 분석 정확도 향상 솔루션
    - 주요기능 : SIRP, SOA, TIP
  - 패치관리시스템 (PMS)

인증 및 암호 솔루션 `23:15~23:30`

  - 하드웨어보안모듈 (HSM)
  - 싱글사인온 (SSO)
  - 통합접근관리 (EAM)
  - 통합계정관리 (IAM)

네트워크 보안장비 운영 `23:30~24:30`

  - 네트워크 방화벽
  - SSL 오프로드 장비 : SSL-VA (visibility appliance), L7-switch
  - 물리적 네트워크 구간 : 외부망 - DMZ - 내부망
  - 네트워크 보안장비 설치모드 : 인라인 모드, 미러링 모드


