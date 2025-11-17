
---

## Module 1 : AWS Cloud Benifits

---

> ### 시험 대비

| 영역     | 핵심 키워드                              | 요약 포인트              |
| ------ | ----------------------------------- | ------------------- |
| 서비스 모델 | IaaS / PaaS / SaaS                  | 서비스 제공 범위와 관리 책임 구분 |
| 비용 모델  | CapEx → OpEx / Pay-as-you-go        | 초기 투자 ↓, 운영 효율 ↑    |
| 확장성    | Elastic Provisioning / Auto-scaling | 수요 변화 대응            |
| 인프라 구조 | Region / AZ / Multi-AZ              | 재해복구 및 가용성 확보       |
| 운영     | HA / FT / DR                        | 중단 없는 서비스 제공        |
| 책임 모델  | Shared Responsibility               | 공급자 vs 고객의 역할       |
| 데이터 기술 | IoT / Big Data (3V·4V)              | 클라우드와 결합된 데이터 활용    |
| 보안     | Data Privacy / Trust Overlay        | 데이터 무결성 및 신뢰 확보     |

> ### 📄 용어 정리.

#### 1). DynamoDB RCU/WCU 

##### ① Read Capacity Unit : 테이블에서 데이터를 읽는 각 API 호출이 읽기 요청입니다. 
##### ② Write Capacity Unit : 테이블에 데이터를 쓰는 각 API 호출이 쓰기 요청입니다. 

---

#### 2). Provisioning VS On-Demand
* **필요할 리소스(서버, 네트워크, 스토리지, 계정, 용량) 등을 <br> 사전에 생성/할당/설정해 사용 준비 상태로 만드는 일.**
* **반면에 온디맨드는 필요할 때 즉시 자동 확보.**
    ```
    예).
    DynamoDB 용량 프로비저닝: 
        초당 읽기/쓰기 단위를 미리 설정(RCU/WCU). 
        비용은 설정 용량 기준으로 시간당 청구.
    EC2 프로비저닝: 
        인스턴스 타입/디스크/보안그룹을 미리 만들어 띄움.
    RDS Provisioned IOPS: 
        DB에 필요한 IOPS를 사전 예약.
    Lambda Provisioned Concurrency: 
        함수 실행 환경을 상시 예열해 두기.
    휴대폰 요금제
        프로비저닝(정해진 용량을 확보) : "데이터 10GB 정액제"
        온디맨드(종량제) : "쓴 만큼만 과금"
    ```

---

#### 3). Computer Cluster (CC)

* **서로 격리된** 데이터센터를 논리적 그룹으로 묶은 것
    *물리적이 아니라, 논리적으로 묶었다는 것은 실제 구현된 하드웨어는 격리된 게 맞는데* 
    **마치 하나의 컴퓨팅 자원처럼 '착각'하며 사용, 동작한다는 것이다"**
* 이렇게 구성된 컴퓨팅 자원을 "클러스터가 여러 개 있어요"라고 말한다.
* 컴퓨터끼리 **협력적인 작업과 막대한 병렬성** 이는, 다음 두 가지 작업을 동시에 수행
    1. **고가용성(HA)/내결함성(FA)**
    2. **Load Balancing** : 클라이언트 요청을 여러 서버에 분산하여 트래픽 부하를 줄이는 방식
* `Kubernetes`, `Hadoop`

---

#### 4). Cloud Platform Architecture
```
Cloud Platform Architecture
  │
  ├── Cloud Models
  │   ├─ Public : AWS | Google Cloud | MS Azure | Salesforce | IBM Blue
  │   ├─ Private : 내부 구축형, 독립 인프라, 보안↑ ✅
  │   └─ Hybrid : 혼합 구조, 양자 결합, 유연성↑ ✅
  │
  ├── Cloud Services
  │   ├─ IaaS → EC2, S3 & EBS, VPC
  │   ├─ PaaS → AWS Elastic Beanstalk, Amazon RDS & DynamoDB
  │   └─ SaaS → Gmail, Google Docs
  │
  ├── Cloud Management ACPR
  │   └─ Autonomic (Capacity, Power, Reliability)
  │
  └── Cloud Security
      ├─ Data Privacy
      ├─ Trust Overlay : 데이터 무결성 보호, 
      └─ Watermarking Protection : 신뢰 기반 인증
```

---

> ### 📄 1. 개념 & 비용/운영 포인트

#### 1). 서비스 3 요소 XaaS (Infra–Platform–Software) 

##### Hardware / Internet Infrastructure (called a Platform) / Software(Application)

##### ① IaaS (Infrastructure as a Service)

* 가상화된 **인프라 (컴퓨팅, 스토리지, 네트워크) 를 서비스 형태**로 제공
  * Amazon EC2
  * Amazon S3 & EBS
  * Amazon VPC

##### ② PaaS (Platform as a Service)

* **애플리케이션 개발 및 테스트** **"플랫폼"** 제공
    * AWS Elastic Beanstalk : 로드밸런싱
    * Amazon RDS & DynamoDB

##### ③ SaaS (Software as a Service)
* 설치 불필요, 웹 브라우저를 통한 소프트웨어 서비스 제공
* 예시: Gmail, Salesforce CRM, MS SharePoint

---

#### 2). 클라우드 컴퓨팅 3요소

1. **Computing** : Amazon EC2(**가상화**된 서버), Google Compute Engine
2. **Storage** : Amazon S3, Google Cloud Storage
3. **Networking** : CDN(Content Delivery Network), VPC(Virtual Private Cloud)

---

#### 3). AWS 클라우드 장점

1. **Economical (경제성)**
    * **Utility Computing** : **CapEx $\rightarrow$ OpEx** 서버 구축의 초기 비용 감소 대신 사용량 기반으로 시작
    * **Pay-as-you-go** : 사용량 기반(Pay-as-you-go). 필요만큼 시작·중지.
    * **규모의 경제** : 이용량 집계로 각자의 종량제 단가$\downarrow$ 효과
2. **Elastic 확장/축소** 
   * 용량 추정 불필요
   * 탄력성/오토스케일링으로 수요에 따라 신속 즉시 Elastic 하게 Provision/Deprovision
3. **속도/민첩성**(빠른 배포·실험)
   * 리소스 분 단위 프로비저닝, 빠른 실험/실패 비용↓ → 시장 출시 가속.
4. **HA(High Access), FT(Fault Tolerance), DR(Disaster Recovery)**
      * AZ : **고가용성·내결함성**을 설계
      * Region : 재해 복구 설계
5. **자원의 투명성** : Illusion of infinite resources
6.  **platform provides On-demand(인터넷) service**:
    * 클라이언트-서버 기본 모델로 언제 어디서든, 유저는 리소스를 요청할 수 있고, 서버는 리소스를 제공할 수 있다.

---

#### 4). 설계 지침

* **서비스 신뢰성 SLA(Service Level Agreement)** 
  SLA 기반 99.95% 이상 가용성 보장 필요
* **경제성 Pay-per-use**

---

> ### 📄 2. 배포 유형 한눈에

* **클라우드 기반**: 확장성$\uparrow$, 속도$\uparrow$, 초기비용$\downarrow$, 규제·주권 이슈는 검토.
* **온프레미스**: 통제력·지연시간 유리, 초기/운영비$\uparrow$, 확장성$\downarrow$.
* **하이브리드**: 유연하지만 **통합/운영 복잡도$\uparrow$**. 점진적 이전에 적합.
  (*참고*) **멀티클라우드**: 공급자 다변화(하이브리드와 별개로도 봄).

> **시험 포인트**
> 소유·관리 주체(온프레=기업 / 클라우드=공급자 / 하이브리드=혼합),
> 확장성(클라우드 ≫ 하이브리드 > 온프레),
> 초기비용(온프레$\uparrow$ / 클라우드$\downarrow$).

---

> ### 📄 3. 글로벌 인프라 구조

* **멀티-AZ(Availability Zone 가용 영역)** 
  * 고가용성(HA) & 내결함성(FT)
  * 컴퓨터 클러스터링이 기본으로 보장되어야지 가능하다.

* **멀티-리전** 
  * 지리적 단위(규제·지연·데이터 주권 고려).
  * 재해복구/주권·초저지연 요구.

* **멀티-AZ ≠ 멀티-리전**. AZ 중단 대비는 되지만 리전 재해 대비는 별도.

---

> ### 📄 4. 고가용성(HA) & 내결함성(FT) 요약


* **HA(High Availability)**: 장애 시 **중단 최소화** (예: 웹/앱 서버를 다중 AZ로 배치).
* **FT(Fault Tolerance)**: **부분 실패에도 정상 동작**(자동 복구, 중복, 헬스체크+오토스케일).
* **실무 권장**: 최소 2+ AZ, RDS **Multi-AZ**, 로드밸런서(ELB/ALB)+헬스체크,
  백업/복구 테스트, 모니터링/알람, 비용 경보.

---

> ### 📄 5. 공유 책임 모델

<div align=center>
    <img src="image/2025-11-03-15-00-16.png" width="80%">
    <h5></h5>
</div>

1. 고객 책임 Security IN the Cloud
   * AWS에 저장하는 데이터와 해당 데이터에 대한 접근 권한과 클라이언트 암호화 책임이 있다.
2. 공유 책임 : Varies by service
   * 사용 서비스에 따라 달라지는데
     네트워크의 "방화벽 구성" 서버측 "암호화", "트래픽 보호",
     OS(귀하의 회사는 OS에 보안 패치를 적용할 책임이 있습니다.)
3. AWS 책임 : 
   * 인프라 보호, 의외로 OS는 인프라는 아니긴 함
     하드웨어, 소프트웨어, 네트워킹 및 시설

---
