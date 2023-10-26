# 빅데이터 플랫폼 실습


# 목차


# Lec01.


## 빅데이터

빅데이터 : 정형, 비정형 데이터를 포함하여 기록, 관리, 해석이 필요한 **거대 데이터**

빅데이터 분석 : 기존 데이터 처리 응용 SW로는 수집, 저장, 분석, 처리가 어려울 정도의 거대한 데이터로부터 가치를 추출하고 결과를 분석하는 기술

- 특징
    - 초기 3대 특징 3V : Volume(규모) + Variety(다양성) + Velocity(속도)
    - 최근 **5대 특징 5V** : **V**olume(규모) + **V**ariety(다양성) + **V**elocity(속도) + **V**eracity(정확성) + **V**alue(가치)

- 필요성
    - 빠른 의사 결정
    - 새로운 서비스 판매 전략 구축
    - 사용자를 포함한 다수 고객에 대한 이해 향상
    - 과거 데이터 분석을 통해 트렌드 변화를 파악
    - 미래를 예측하여 새로운 시장 전개

## 빅데이터 플랫폼

**빅데이터 플랫폼** : 기업 내의 많은 사용자들이 데이터를 처리하고 분석을 쉽게 할 수 있는 환경을 제공해주는 시스템

- 데이터의 수집, 처리, 저장의 역할
- 정보(Knowledge)의 발견, 검색, 보안 제공
- 데이터 분석 및 머신 러닝 지원
- Source → Ingestion & Transformation → Storage → Analytics

## 빅데이터 플랫폼 - Hadoop

**Hadoop** : 대용량의 데이터를 적은 비용으로 더 빠르게 분석할 수 있는 소프트웨어

- 개요
    - 상용 하드웨어를 함께 클러스터링하여 대량의 데이터 세트를 **병렬로 분석**함
    - 한번에 여러 디스크로부터 데이터 읽기 가능
- 특징
    - Distributed : 수십만대 컴퓨터에 자료 분산 저장 및 처리
    - Scalable : 용량이 증대되는 대로 컴퓨터 추가 가능
    - **Fault-Tolerant** : 하나 이상의 컴퓨터가 고장나도 동작 가능
    - Open Source : 오픈 소프트웨어 (무료)
    - Distributed-save : HDFS 이용해 노드 클러스터에 저장 → 데이터 접근 시 각 블록의 복사본 생성
    
- 장점
    - 오픈소스로 비용 부담↓
    - Scale Out 방식
    - Fault Tolerance
    - 저렴한 구축 비용 & 비용 대비 빠른 데이터 처리
    - 오프라인 배치 프로세싱에 최적화
    
- 단점
    - HDFS에 저장된 데이터 변경 불가
    - 신속하게 처리해야 하는 작업에는 부적합
    - 너무 많은 버전과 부실한 서포트
    - 설정의 어려움

## 빅데이터 처리 흐름

### 데이터의 종류

- 정형 데이터 :  RDBMS, 스프레드 시트
- 비정형 데이터 : 텍스트, 이미지, 음성, 영상
- 반정형 데이터 : JSON, XML, 웹로그, 센서데이터 등

### Source (원천 데이터)

- 데이터베이스 : 관계형 RDBMS 데이터 (OLTP / OLAP)
- 이벤트 컬렉터 및 로그 : 사용자 정의형 이벤트 데이터
- API : 공개 제공 데이터 및 정보 전달 규약 데이터
- 파일 및 오브젝트 스토리지 : 우리가 아는 일반적인 파일

### Ingestion and Processing

- 배치형 데이터 : 데이터베이스 및 파일
    - MapReduce : Java 기반 빅데이터 세트
    - Spark : 데이터 분석 , 기계학습 알고리즘 등 컴퓨팅을 위한 오픈 소스 프레임워크
    - Hive : Java 기반 데이터 웨어하우스 도구, 하둡의 복잡한 MapReduce 코드를 적절하게 처리하여 데이터 구조화
- 스트리밍형 데이터 : 어플리케이션 이벤트, 센서 데이터
    - Flink : 데이터 분석 및 기계학습을 위한 오픈/크로스/분산 처리 프레임워크
    - Kafka : 실시간 메시지 핸들링(기록 스트림 게시, 구독, 저장 및 처리) 프레임워크
    - Spark : 대규모 데이터 처리용 분산 처리 엔진

### Storage

- 데이터 **마트** : 회사의 금융, 마케팅, 영업부서와 **같은 특정사업부의 요구사항 지원** → 데이터의 중요 정보만 모아서
- 데이터 **웨어하우스** : 데이터를 **구조화된 형식으로 저장**, 사전처리된 데이터 저장 → 많은 데이터 저장(평균, 통계 등)
- 데이터 **레이크** : **원시 데이터** 및 비정형 데이터 저장

# Lec03.


## Hadoop Ecosystem

### 분산 환경 관리자 : Zookeeper

**Zookeeper** : 하나의 서버에만 서비스가 집중되지 않도록 **서비스를 알맞게 분산하여 동시 처리**

- 하나의 서버에서 처리한 결과들을 다른 서버들과 **동기화**
- 오픈소스 from Yahoo!
- 운영 서버에 문제가 생기면 대기 중인 서버를 운영으로 바꿔줌
- 서버들의 환경 설정을 통합적으로 관리해 줌
- 서버 여러대를 앙상블로 구성 → 분산app들이 각각 클라이언트가 됨
- 각각 커넥션을 맺으면 z-node에 key-value 형태로 정보 공유
- Z-node = 파일 or 폴더
- client의 요청 처리 → 요청에 대한 트랜잭션 생성 → 모든 서버로 전파

### 워크플로우 및 코디네이터 시스템 : Oozie

**Oozie** : **하둡의 MapReduce 작업 흐름을 관리**해주는 서버 기반 워크플로우 스케쥴러

- JAVA 기반
- 반복적이고 복잡한 후처리 해결
- Directed Acyclic Graphs (**DAGs**)로 정의, job의 시작, 처리, 분기, 종료 등 액션 구성
- 수집/적재된 데이터셋을 대상으로 다양한 후처리 job 데이터들 간 **의존성&무결성** 이슈로 등장

- 제공기능
    1. Scheduling : 특정 시간 / 주기적 간격 / 이벤트에 의한 정기적 액션 수행
    2. Coordinating : 이전 액션이 끝나면 다음 액션 시작
    3. Managing : 액션 성공 / 실패 시 알림 발송하며 저장
- 용어
    1. Action : Oozie에서 실행하는 하나의 작업 단위
    2. Workflow : 액션들의 제어와 의존관계를 DAGs로 표현
    3. Coordinator : 데이터와 워크플로우를 실행하는 스케쥴 정의

### Hadoop 클러스터 프로비저닝, 모니터링 : Ambari

**Ambari** : 하둡에 누가 들어왔는 지, 뭘 하고 있는 지 등등을 감시해줌

- 클러스터에 설치된 여러 서비스의 관리페이지에서 상태 확인
- 각 컴포넌트의 동작 제어 가능 (ex. 재시작, 네임노드 컨트롤)
- 호스트 정보 확인
- 주기적, 이상 상태 알람 가능
- 설치된 서비스, 계정 정보 확인

### Hadoop 분산 리소스 관리 : YARN

**YARN** : 자원 관리 및 job 스케쥴링

- 필요성
    - 자원 스케쥴링 → 전체 클러스터 성능 향상
    - 메모리, CPU를 필요에 따라 공유
    - CPU, 메모리의 가용치보다 많은 자원 할당 가능
    - 초과 사용 호스트 방지, Trade-off가 높은 작업 우선 지원
- 구성 요소 : **Master-Slave** 구조
    - Resource Manager : YARN Master 서버, 모든 시스템의 지원 관리, job 분배
    - Node Manager : YARN slave 서버, 슬레이브당 하나의 데몬 실행
    - Container : 시스템 자원
    - App Master : 하나의 App을 관리하는 Master 서버
    
    

### 분산 파일 시스템 : HDFS

**HDFS(Hadoop Distributed File System)** : 하둡의 저장소 역할

- 큰 사이즈 파일들을 작은 단위로 나누어서 저장함
- 빠른 배치 처리 O
- 빠른 데이터 응답 시간 X
- 데이터 복사 / 보존 / 공유하는 저비용 저장 시스템
- **여러번 Read**
- 파일 수정 X

- 특징
    - Block 기반 저장(128MB)
    - Block 복제를 이용한 Fault Tolerance : 장애 복구 대비
    - 복제 시 같은 Rack 서버에 하나, 다른 Rack 서버에 하나 저장
    - 문제가 생기면 다른 블록으로 복구
    - **Master-Slave** 구조
    
- **Master : NameNode**
    - MetaData 관리 : 사용자가 설정한 위치에 보관하고 실행 시 파일 읽기
    - DataNode 관리 : 살아있는 지 **heartbeat(3s)** & 업데이트 잘 되는 지 **BlockReport(6H)** 보내서 동작 상태와 Block 상태 관리
    - NameNode 통해 데이터 READ/WRITE
- **MetaData**
    - Fsimage : namespace, 블록 정보, 메모리 정보 등
    - Edits : 파일 생성, 로그, 메모리 저장 중 주기적으로 생성
- **Slave : DataNode**
    - Active : DataNode 가 살아있는 지 죽어있는 지 체크
    - Standby : DataNode의 업그레이드, 패치 등 작업을 위해 Block 보관
- **Secondary NameNode : Back-up**
    - FSimage와 Edits.new 일정시간마다 merge
    - NameNode가 가동을 멈춰도 대신하지는 않음

### 대용량 데이터 분산 처리 모델 : MapReduce

**MapReduce** : 대용량 데이터를 분산.병렬 컴퓨팅 환경에서 처리하기 위해 제작된 처리 모델

- 요즘은 잘 쓰지는 않음 : 느림(디스크 I/O 빈번 발생, 실시간성 X ) → Spark(In-memory 방식), MR(상대적으로 저렴)
- Map : 데이터를 작은 단위로 나누어서(Chunk) 로직 수행
- Reduce : 분산 처리된 결과를 다시 하나로 합쳐주는 병렬적 수행 방식

# Lec05.


## Hadoop Ecosystem(2)

### 비정형 데이터 수집 : Flume

**Flume** : 로그데이터를 수집하는 기술

- 오픈소스 프로젝트 by Apache
- 여러 서버에서 생산된 대용량 로그 데이터를 수집 → HDFS와 같은 목적지에 데이터를 전송하는 기능
- 구조가 단순하고 유연함
- 다양한 유형의 스트리밍 데이터 플로우
- 개요
    - 시스템 사용 · 원천 데이터 수집
    - 클러스터 장치로부터 로그 파일 수집 → HDFS에 적재
- 주요 특징
    - **Source** : 수집한 데이터를 channel로 전달
    - **Channel** : Source와 Sink를 연결, 데이터 버퍼링
    - **Sink** : Channel로부터 데이터를 받아와 최종 목적지인 HDFS, Hive에 제공
    - **Interceptor** : Source와 Channel 사이에서 데이터 필터링 및 전처리
    - **Agent** : Source → Interceptor → Channel → Sink → Component 순서의 작업 단위

### Flume : Multi-Agent Flow


- 데이터가 여러개의 Flume Agent로 흐르도록 하는 구조
- 직전 Sink가 무조건 Avro 통신이어야 하고, hop의 Source 역시 Avro 유형이어야 함

### Flume : Consolidation


- 가장 일반적인 구조
- 여러 웹서버에서 정보를 수집하는 경우
- Agent가 수집을 돕고, 하나의 Agent가 통합
- 무조건 Avro 유형이어야 하는 것은 아님

### Flume : Multiplexing Flow


- 하나 이상의 목적지에 데이터 저장
- 다중 이벤트 지원 Flow

### Flume : Flafka (= Flume + Kafka)


- Flume의 취약점(**데이터 안정성**)을 보완
    - Flume : 시스템 장애 발생 시 데이터 유실 위험성↑
    - Channel 정보 소실 → Channel을 메모리로 사용하는 경우 유실↑, 성능↓
    - Kafka의 장점(**데이터 안전 관리**)과 혼합하여 사용

### 직렬화/역직렬화 : Avro

- **직렬화** : 객체를 전송 가능한 형태로 만드는 것 (데이터를 연속적인 형태로 변환)
- **역직렬화** : 저장된 데이터나 네트워크 전송 데이터를 받아 메모리 상에서 재구축하여 다시 객체 형태로 만듬

- JSON직렬화와 다른 점?
    - Avro = Schema의 존재
    - 데이터 타입을 알 수 있음
    - 데이터 압축 → 효율적
    - Schema에 설명 O
    - 여러 언어로 액세스 가능
    - Hadoop과 천생연분
    - Binary(2진법) 형태로 직렬화…구조 파악 어려움

### 정형 데이터 수집 : Sqoop

**Sqoop** : 구조화된 관계형 데이터베이스(RDBMS)와 Hadoop 간의 대용량 데이터들을 효율적으로 변환해주는 어플리케이션

- by Apache
- Oracle, MySQL과 같은 RDBMS도 HDFS로 적재 가능
- MapReduce를 사용하여 면환된 데이터를 다시 RDBMS로 내보내기도 가능
- 가져오기/내보내기를 MapReduce로 사용하기 때문에, 병렬 처리 가능
- Reduce 작업은 일어나지 않음!!

### 분산 데이터 베이스 : HBase

**HBase** : 오픈소스 분산형 데이터베이스 관리 시스템, RDBMS와는 다른 구조의 NoSQL 시스템 중 하나

- by Apache
- 분산되고 확장되면서 큰 데이터를 저장하기 위한 비관계형 DB
- HBase 내의 테이블들은 MapReduce를 사용하여 입출력 가능
- 빠른 READ / WRITE 지원
- **Master-Slave** 구조

- NoSQL 제시 배경
    1. 기존 데이터 저장 시스템 : DBMS 기준
    2. 파일 오픈, 내용 검색 등 작업 수행 시 중복多 → 정규화 작업
    3. Key-Column 관계를 기반으로 연결 → 데이터 중복 감소 . . . Join, Filter 등 사용
    4. 데이터 양 폭증 → RDBMS 문제↑ . . . Scale-out 이 어려움
    5. Row기반 순차 검색 = 시간↑
    6. 대규모 분산 시스템에서 확장성, 유연성 X . . . 새로운 방식의 도입 시작

- Hbase의 구성 요소
    - Region Server : 데이터의 READ/WRITE 담당
    - HBase Master : Meta Data변경 사항에 대해 모든 Region 모니터링 (create&delete)
    - Zookeeper : 중앙 관리 (상태 유지)
    - NameNode : HDFS meta data 관리하는 프로세스 담당
    - DataNode : HDFS 블록을 저장하는 데몬 프로세스 담당 (데이터 저장)

- 데이터 읽기 연산↑
- **Master-slave 구조** = Scale-out 용이
- 빠른 연산 작업
- Row-key 기반 정렬, 순차 데이터 처리↑
- Row-key가 하나만 존재하므로 설계에 대한 많은 고민 필요

### NoSQL vs RDBMS

- RDBMS
    - 저장 및 검색 : 테이블의 관계가 기준
    - 행(recode, tuple) & field, item
    - 관계성을 나타내는 Key 존재
    - MySQL, Oracle, MS-SQL, PostgreSQL
    - 분류, 정렬, 탐색 속도 빠름
    - 구조화된 질의 → 데이터 핸들링
    - 완전성↑
    - 데이터 확인 쉬움
    - 부하 발생 시 처리 어려움
    - 엄격한 규정
    

- NoSQL
    - 기존 테이블 구조를 탈피 → 다양한 저장 방식 (관계지향 X)
    - 간편한 복제, API → 검색 용이
    - 빅데이터 및 실시간 시스템에 최적화
    - HBase, Cassandra, MongoDB 등
    - 관계에 대한 정의 X
    - 복잡도↓ = 대용량 데이터 저장 관리
    - 자유로운 저장
    - 많은 양의 데이터 저장 처리
    - Key에 대한 입출력만 지원
    - 데이터 규격화 X
    - 비교적 느림

|  | RDBMS | NoSQL |
| --- | --- | --- |
| 데이터 저장 | 행&열을 가진 관계형 모델 | 다양한 저장 모델 : Document, Key-Value, Column, graph… |
| 스키마 융통성 | - 고정된 스키마
- 미리 정의된
- Null값 존재
- 변경 어렵고 비쌈 | - 가변적
- 데이터 입력 시 실시간 변경 가능
빈 필드는 저장 공간 할당 X |
| 확장성 | Scale-up | Scale-out |
| 데이터 타입 | Structured | Structured ~ Unstructured |
| example | MySQL, Oracle, MS-SQL | HBase, MongoDB, Cassandra |

# Lec06.


## Everything of Spark

### Spark

**Spark** : 범용적 목적의 분산 고성능 클러스터링 플랫폼

- 특징
    - **분산된 여러대의 노드에서 연산**을 할 수 있게 해 줌
    - Hadoop의 단점을 보완하기 위한 빅데이터 분석 프레임워크 중 하나
    - Hadoop **대체 X**!!! → Hadoop 보완 O
    - 디스크 I/O를 통한 분석 → **데이터를 메모리에 올려서 분석**
    - 배치 분석 & 스트리밍 데이터 분석 지원
    - Hadoop YARN(일반) + Spark(실시간)로 많이 사용하는 추세
- 주요 기능
    - MapReduce : Hadoop
    - Streaming 데이터 핸들링 : Apache Storm
    - SQL 기반 데이터 쿼리 : Hadoop Hive
    - 머신 러닝 라이브러리 : Apache Mahout
- 장점
    - 빠른 속도(100배 빠름)
    - 기존 플랫폼과 유연한 연동 → 빠른 연동 가능
    - 개발자 친화적 : 여러 편의성 제공
    - 미리 정의된 Function으로 복잡한 기능 빠르게 처리
- 단점
    - 비용↑ : 메모리를 사용하기 때문에
    - 클러스터 메모리가 넉넉해야 함

- Hadoop MR 처리 방식 : 저장은 HDFS, 분석은 MR, 자원 관리는 YARN -? 데이터 분산 저장, 복제 등등… 작업의 양이 많아질 수록 성능 영향↑
- SPARK : **RDD(회복력이 있는 분산 데이터셋)**이라는 분산 메모리에 저장
    - 빠른 속도, 내결합성, 고수준의 API 제공
- RDD : 제조리 내부에서 **데이터 손실 시 재연산**하여 복구할 수 있는 메모리
    - Fault-Tolerant 보장 : **DAGs 형태**라 유실 시 다시 돌아가서 재연산
    - **Lineage(혈통)**을 가짐 : 메모리 재연산을 위함
    - Transformation API (map, reduce, join, sort) : 데이터 가공
    - Action(count, collect, loopup, save) : 가공 결과물 생성
    - 처리 속도↑
    - 최적화 어려움

# Lec07.


## Docker

**Docker** : Go언어로 작성된 리눅스 기반 오픈소스 가상화 플랫폼

- VM이라는 가상화 플랫폼이 있지만, 효과적으로 사용하지 못할 때
    - 서버에서 실행하는 가상화 이미지들의 활용도가 낮을 때
    - CPU 및 자원 점유율이 서버 가용량보다 못 미치거나 너무 많을 때

**Container** : 가상화 기술 중 하나, Docker 엔진 위에 Application에 필요한 바이너리만 올려서 사용하는 구조 → **Host의 Kernel을 공유**하므로 I/O처리가 쉬워짐

- 기존 OS를 가상화 시켰음 → OS레벨의 가상화로 프로세스 격리 시켜서 동작
- 기존에는 HostOS에 가상화를 시키기 위해 Hypervisor엔진 위 GuestOS 사용 → **Host와 Guest가 완전히 분리** . . . 무거움!
- 가상 머신 생성 X, HostOS의 자원을 조금 가져와서 여러 환경을 만드는 것
    - 성능 향상
    - OS간 이식성↑
    - Scale-out 용이

**Image** : Container응 실행할 수 있는 실행 파일, 설정 값들을 보유한 파일

- 미리 환경을 적재하여 구축 후, Image 생성해서 배포 (Docker hub에)
