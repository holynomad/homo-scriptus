
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

## 2024-05-08

네트워크 보안장비 운영 상세 `12:30~13:00`

  - 네트워크 방화벽(Firewall)
    - IP 주소 및 포트번호, 프로토콜을 기반으로 룰셋(필터링 정책)에 따라 패킷 필터링을 수행하는 보안장비
    - 일반적으로 고가용성(HA) 환경구축 (Active-stanby, active-active)
    - 상태검사 (stateful inspection) 기능
  - SSL 오프로드 장비
    - SSL 서버를 대신해서 SSL 트래픽에 대한 모든 암복호화 처리 수행 => SSL 서버 성능 향상
    - SSL-VA (Visibility Appliance), L7 Switch
  - 침입탐지시스템 (IDS)
    - 사전에 등록한 알려진 공격패턴(시그니처), 임계치 등에 따라 공격을 탐지하는 보안장비
    - 탐지목적이기 때문에 NIDS인 경우 일반적으로 미러링 모드(= out-of-path 모드)로 설치
    - 침입탐지 방식에 따라 오용탐지(misuse), 이상탐지(anomaly)
    - 탐지할 데이터 수집원에 따라 호스트 기반 IDS(tripwire), 네트워크 기반 IDS(snort, suricata)
  - 침입방지시스템 (IPS)
    - 탐지하고 차단까지 하는 보안장비
    - 실시간 차단을 위해 인라인 모드로 설치
  - 웹방화벽 (WAF)
    - 웹 트래픽의 웹 콘텐츠를 분석하고 탐지 및 차단

보안솔루션 취약점 `23:00~23:20`

  - 계정관리
  - 접근관리

취약점 점검도구 `23:20~23:50`

  - 네서스 (Nessus) : 테너블 사
  - 닉토 (nikto) : 취약한 cgi 파일 스캔기능

무결성 및 루트킷 점검도구 `23:50~24:30`

  - 트립와이어 (tripwire) : 파일시스템 무결성 점검 => 공격자가 루트킷/백도어 설치 후 tripwire db 갱신하면 탐지 불가
  - chkrootkit
    - 루트킷 hidden process 탐지 원리
      - ls -l exe
      - cat cmdline
    - 대응방법
      - rpm 이용하여 변조된 파일 확인 : rpm -qf /bin/netstat, rpm -V net-tools
      - strace 이용하여 변조된 파일 확인 : strace -e trace=open ps
     
## 2024-05-11

루트킷 침해사고 공격 시나리오 `23:00~23:40`

  - Nessus 통한 웹서버 취약점 스캔 > Tomcat 관리자 페이지 외부노출 및 계쩡 초기 설치 상태 확인
  - Tomcat 관리자 페이지 취약점 이용한 익스플로잇을 통해 백도어 수행하는 쉘 코드를 실행하여 루트 권한의 리버스 쉘 연결
  - 연결한 리버스 쉘 이용하여 추가 공격 행위 은닉위해 루트킷 설치 > 웹서버 지속 접근 위해 리버스 쉘 명령을 cron 테이블(/etc/crontab)에 등록
  - 공격자 웹서버로부터 루트킷 프로그램 다운로드 (wget "리소스 URL")
  - cron 테이블에 명령 등록 (매일 03시 루트 권한으로 리버스 쉘 실행)

DBD (Drive By Download) 침해사고 시나리오 `23:40~24:20`

  - 희생자 PC 취약점을 이용한 공격
  - 해킹한 경유지 사이트를 중계지 -> 유포지로 리다이렉트하는 난독화된 iframe 악성스크립트가 삽입된 응답 페이지 반환
  - 사용자에게 브라우저 취약점을 이용하는 익스플로잇 코드와 악성코드가 삽입된 응답 페이지가 반환된다.
    - 소스 난독화 & 다수의 경유지/중계지를 통해 유포지에 대한 추적 어렵게 함
    - 파밍, 워터링 홀 방식
   
## 2024-05-12

DBD 침해사고 공격/분석 시나리오 `21:40~23:00`

  공격 시나리오
  - 파일 업로드 취약점 있는 사이트 게시판에 파일 첨부 기능을 이용하여 웹쉘(webshell.php)과 악성 자바스크립트(ma1.js, ma2.js) 파일 업로드
    - ma1.js는 iframe 태그를 통해 중계지인 쇼핑몰 사이트로 이동시키는 난독화된 자바스크립트 코드
    - ma2.js는 사용자 쿠키 정보 탈취 후 공격자 웹서버로 전달하는 코드
  - 웹쉘을 통해 유포지 페이지로 이동시키는 iframe 태그 삽입
  - 취약 웹서버에 '운영체제 명령실행' 취약점이 존재한다는 사실 확인 후, 자신의 접근흔적 삭제 위해 웹서버 엑세스 로그 삭제 시도
    - 127.0.0.1 ; rm -rf /var/log/httpd/access_log
  - 유포지 접속한 사용자의 IE 브라우저 취약점을 이용하여 익스플로잇 수행하여 리버스 쉘 획득
    - 백도어 기능 수행하는 쉘 코드 실행하여 root 권한의 리버스 쉘 연결
  - ma2.js 스크립트 파일을 통해 사용자 쿠키 정보 탈취하여 공격자 웹 서버에 저장

  분석 시나리오
  - 웹서버 점검 시 엑세스로그 흔적 확인
    - 파일 업로드 성공(200) 후, 웹쉘로 의심되는 PHP 파일 호출성공(200)
    - 개발자 통한 보안조치
      - 업로드 파일 확장자에 대한 적절한 필터링 (화이트리스트) 정책 적용
      - 업로드 파일 저장위한 전용 디렉토리 별도 생성 후, 웹서버 설정을 통해 실행 설정 제거
    - 낯선 JS 파일 호출 성공(200) 엑세스로그 확인
    - 엑세스로그 삭제 시도 명령어 로그 확인
    - 개발자 통한 보안조치
      - 사용자 입력값에 운영체제 명령어 실행할 수 있는 문자(세미콜론 등) 포함되어 있는지 적절히 필터링 및 차단
      - 허용 가능한 명령어 리스트를 화이트리스트 정책으로 제한적 허용
    - ma1.js 파일 난독화 디코딩 확인 시 다른 사이트로 이동시키는 iframe 태그 확인
    - ma2.js 파일 분석 시 사용자 쿠키정보 탈취 및 공격자 웹서버 전달 코드 포함 확인
    - 변조의심 파일 MAC time 확인 및 동적분석 진행
    - IE 브라우저 로그 확인 (임시 인터넷 객체, 임시 인터넷 파일(캐시), 열어본 페이지, 임시 쿠키 파일)
    - TCP view, Process Explorer 등을 통해 현재 상태정보 확인

악성코드 행위분석 시나리오 `23:00~23:40`

  - 악성코드 지속성 유지
  - 방화벽 우회 및 은닉
  - 파밍용 호스트 파일 변조
  - 악성코드 분류 : 다운로더, 드롭퍼, 인젝터, 키로거, 랜섬웨어 등
  - 패킹 & 언패킹
  - 정적분석 (아이다, 올리디버거 OllyDbg) & 동적분석
  - 윈도우 PE(Portable Executable) 파일

## 2024-05-13

윈도우 레지스트리 분석 시나리오 `19:30~20:30`

  - HKLM > ... > Current Version > Run > 윈도우 시작 시 동작하는 시작 프로그램에 악성코드 등록
  - HKCU > ... > Current Version > Run > 현재 사용자 로그인 시 동작하는 시작 프로그램에 악성코드 등록
  - HKLM > ... > Current Version > Winlogon : "Userinit" > 윈도우 로그인 시 (모든 사용자) 동작하는 시작 프로그램에 악성코드 등록
  - HKLM > ... > Services : "Start"=dword:00000002 > 서비스 자동 실행에 악성코드 등록
  - HKCR > ... > Directory > shell > ... > command > 윈도우 탐색기 디렉터리의 context menu에 commandPrompt 메뉴명 추가하고 악성코드 등록
  - HKLM > ... > batfile > shell > ... > command > 배치파일 실행 시 악성코드가 먼저 동작하도록 등록
  - HKLM > ... > FirewallPolicy : "EnableFirewall"=dword:00000000 > 윈도우 방화벽 기능 비활성화
  - HKLM > ... > FirewallPolicy > ... > AuthorizedApplicationList > 윈도우 방화벽에 악성코드를 예외 허용 프로그램으로 등록
  - HKLM > ... > OpenPorts > List : "4321:TCP:*:Enabled" > 윈도우 방화벽에 4321/tcp 포트 오픈 허용
  - HKCU > ... : "Hidden"=dword:00000002 > 현재 사용자의 숨김 파일 및 폴더를 표시 안 함으로 설정
  - HKLM > ... > Folder > Hidden> SHOWALL : "CheckedValue"=dword:00000000 > 모든 사용자에 대해 숨김 파일 및 폴더를 표시함으로 변경하지 못하도록 설정
  - HKCU > ... : "ShowSuperHidden"=dword:00000000 > 현재 사용자에 대해 보호된 운영체제 파일 숨기기 설정
  - HKLM > ... > Folder > SuperHidden : "UncheckedValue"=dword:00000000 > 모든 사용자에 대해 보호된 운영체제 파일 숨기기를 해제하지 못하도록 설정

워터링 홀 침해사고 시나리오 `23:00~23:30`

APT `23:30~24:00`

  - 초기 정찰
  - 초기 침입
  - 거점 마련
  - 권한 상승
  - 내부 정찰
  - 내부 침투
  - 지속성 유지
  - 목표 달성
  - 주요 침투 기법 : 스피어 피싱, 워터링 홀, USB 메모리 스틱

사이버 킬 체인 `24:00~24:15`

SSH 포트포워딩 `24:15~24:40`

  - SSH 클라이언트가 SSH 서버에 접속하여 ㅁ나든 연결을 다른 애플리케이션에서 이용하여 통신할 수 있는 기술
  - 포트포워딩 또는 터널링이라고 표현
  - 애플리케이션이 SSH 포트 포워딩을 사용하는 이유는 암호화, 인증 등의 SSH의 보안 기능을 그대로 이용할 수 있는 장점 > 이를 악용하여 의도적으로 방화벽 우회 후 내부 시스템 침투하는 등 공격에도 활용될 수 있는 위험 있음

## 2024-05-14

`공부한 거 정리 필요`
