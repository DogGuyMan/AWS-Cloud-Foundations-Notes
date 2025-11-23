
---

## Moduel 3 : Global Infrastducture

---

#### 글로벌 인프라 구조의 핵심 장점은 2가지
##### ① High availability and fault tolerance
##### ② 에지 로케이션 : Low latency for end users

#### 이 모듈의 학습 목표는 다음과 같습니다.
```
AWS 글로벌 인프라의 이점을 요약할 수 있습니다.
    AWS 리전 및 가용 영역
    가용 영역의 기본 개념을 설명할 수 있습니다.

에지 로케이션 및 Amazon CloudFront
    AWS CloudFront 이점을 설명할 수 있습니다.

Amazon 서비스를 프로비저닝 할 수 있는 다양한 방법을 비교할 수 있습니다.
    AWS Management Console, AWS CLI 및 SDK
    AWS Elastic Beanstalk
    AWS CloudFormation
```

#### 문제
```
Region의 정의로 가장 적절한 것은?
C. AWS 리소스가 위치한 지리적 영역 ✅

**Availability Zone(AZ)**를 올바르게 설명한 것은?
B. 리전 내 독립 전원/네트워크를 가진 DC 그룹 ✅

고가용성(HA)을 위해 권장되는 기본 패턴은?
B. 한 리전 내 2개 이상 AZ 분산 ✅

멀티-AZ ≠ 멀티-리전인 이유는?
B. AZ 장애 대비 vs. 리전 재해 대비 ✅

리전 선택 기준으로 가장 거리가 먼 것은? ❌
A. 데이터 주권/규제
B. 인스턴스 스토어 사용 여부 🤔
    "인스턴스 스토어 사용 여부"는 인스턴스 타입 특성이지
    일반적인 리전 선택의 1차 기준이 아닙니다.
C. 고객과의 지리적 근접성
D. 서비스/기능 가용성

에지 로케이션의 주된 역할은?
B. CloudFront 캐시로 지연 감소 ✅

Amazon CloudFront의 이점은?
B. 전 세계 캐싱·TLS·오리진 보호(OAC/OAI) ✅

Route 53의 주된 기능은?
B. DNS 및 트래픽 라우팅 정책(지연/가중/헬스체크/페일오버) ✅

CloudFront와 Route 53의 관계로 옳은 것은?
B. 서로 독립이지만 Alias로 커스텀 도메인 매핑에 자주 함께 사용 ✅

CloudFront 커스텀 도메인 구성 필수 요소는?
B. CloudFront에 CNAME 등록 + ACM 인증서(버지니아 북부) + DNS 레코드 ✅

AWS Management Console의 특징은?
B. GUI로 API 호출 수행 ✅

AWS CLI의 장점은?
B. 자동화/스크립팅·일괄 작업 용이 ✅

AWS SDK를 사용하는 이유는?
B. 애플리케이션 코드에서 직접 AWS API 호출 ✅

API를 가장 정확히 설명한 것은?
B. 요청/응답 규약(인터페이스)으로 서비스 제어 ✅

Elastic Beanstalk의 핵심 가치는?
B. 애플리케이션 배포/운영 자동화(프로비저닝·ALB·오토스케일·모니터링) ✅

CloudFormation을 올바로 설명한 것은? ❌
A. 수동 배포 위주 ❌
    수동 배포 도구가 아님(자동화/IaC). ✅
B. 인프라를 코드(IaC)로 정의·반복 가능하게 프로비저닝 ✅
C. 로그 수집 서비스 ❌
    로그 수집 아님(CloudWatch Logs). ✅
D. 비용 추정 도구 ❌
    비용 추정 도구 아님(프라이싱 계산기/Cost Explorer 등). ✅

콘솔/CLI/SDK/CFn 중 재현성과 형상관리에 최적화된 것은? ❌
A. 콘솔 : 수동 클릭 → 기록/재현 어려움, 드리프트 유발.
B. CLI : 스크립트화는 가능하지만 명령형이라 상태관리/롤백/의존성 처리 수동 부담 큼.
C. SDK : 애플리케이션 코드로 API 호출(명령형). 재현성과 형상관리는 개발자가 별도 구현해야 함.
D. CloudFormation ✅

프로비저닝의 의미로 맞는 것은?
A. 배포 코드 작성
B. 필요 자원을 미리 준비/할당하여 사용 가능 상태로 만드는 것 ✅

글로벌 사용자 지연을 최소화하려면 가장 먼저 고려할 것?
A. 더 큰 인스턴스
B. 가까운 리전 선택 + CloudFront 엣지 캐시 ✅

재해복구 요구가 리전 단위인 경우 기본 전략은?
A. 단일 AZ 증설
B. 멀티-리전 아키텍처(Active/Active 또는 Active/Passive) ✅
```
---

> ### 📄 1. 고가용성 & 내결함성

> 모든 리소스를 보관하는 거대한 데이터 센터 하나를 보유하는 것은 바람직한 방법이 아니죠.
> 데이터 센터의 정전이나 자연재해 같은 일이 발생한다면 이 데이터 센터를 사용하는 모든 사용자의 애플리케이션이 동시에 중단되게 됩니다
> 홍수가 나든, 퍼레이드가 나든 이유가 무엇이든 간에 우리는 고객에게 높은 가용성을 제공을 해야 합니다.
> #### 이런 상황을 방지하기 위해서 우리는 고가용성과 내결함성이 필요해요. 

##### 세계 다양한 지역에서 운영되고 있는 지리적 위치를 사용하고 있습니다. 

---

> ### 📄 2. 글로벌 인프라

<div align=center>
    <img src="image/2025-09-21-20-04-47.png" width="80%">
    <h5></h5>
</div>

* AWS가 권장하는 모범 사례는 **한 리전에서 두 개 이상의 가용 영역을 사용하는 것**입니다. 
* 이것은 서로 다른 두 AZ에 인프라를 중복해서 배포한다는 뜻이죠. 

#### 1). 리전 선택 (Region) : 리전은 AWS 리소스가 있는 지리적 영역입니다.

* 지진, 홍수, 화재와 같은 대규모 재난에서의 HA 제공

##### ① 데이터 타 국가 법적 요구 사항
##### ② 고객과의 근접성(!!) : 가까운 리전을 선택하면 더 빠르게 제공하는데 도움이 된다.
##### ③ 기능 가용성(예를 들어 양자 컴퓨팅 플랫폼은 아직 모든 리전에서 못사용함)
##### ④ 요금 (서비스 비용이 리전마다 다를 수 있다.)

```
리전 선택의 고려사항
1. 컴플라이언스(규정준수) 요구사항 : 지역별 엄격한 현지 법률 규정(GDPR) 확인
2. 프록시미티(근접성) : 지역과 가까운 정도, 지연시간
3. 피쳐 가용성 : AWS는 어떤 지역에 따라서 서비스를 제공 안할수도 있다.
4. 프라이싱 : 리전별로 가격이 다를수도, 비용 최적화 적인 곳이 있다.
```

---

#### 2). 가용 영역 (AZ) : 리전 내의 단일 데이터 센터 또는 데이터 센터 그룹

* 소프트웨어적인 장애에 비즈니스를 중단 없이 계속 운영할 수 있게 됩니다.
* 단일 데이터 센터로 가용 영역을 복수로 지정할 수는 없다.
  1. FT를 위해 사용되고
  2. Privete Link를 통해 매우빠른 연결을 하고 있다.

<div align=center>
    <img src="image/2025-09-21-20-05-36.png" width="80%">
    <h5> 리전 내의 단일 데이터 센터 또는 데이터 센터 그룹입니다. </h5>
</div>

---

> ### 📄 3. 에지 로케이션 (Region 바깥과 소통)

<div align=center>
    <img src="image/2025-09-21-22-41-25.png" width="80%">
    <h5> ‼️Edge Location Host AWS Service‼️ <br> 에지 로케이션은 다른 여러 AWS 서비스를 호스팅 한다. </h5>
</div>

#### Edge locations are located outside of AWS Regions 
#### 에지 로케이션이 호스팅하는 서비스들 중 <br> 대표 글로벌 인프라 서비스 일부는 다음과 같다.

##### ① CloudFront
##### ② Amazon Global Accelerator
##### ③ Amazon Route 53

#### 1). Amazon CloudFront : CloudFront is 컨텐츠 전달 "네트워크"

##### CDN : 전 세계 고객과 더 가까운 곳에 콘텐츠 복사본을 제공하는 네트워크

* ‼️**여기서 말하는 "콘텐츠"란**‼️
  * ‼️이미지, 데이터, 클라이언트 애플리케이션, **API**들을 말한다.‼️
* Amazon CloudFront는 전 세계에 있는 에지 로케이션을 이용해 사용자가 어떤 위치에 있든 통신 속도를 높입니다. 
* 반드시 같은 리전에서 위치할 필요는 없다.

```
Which component of the AWS Global Infrastructure does Amazon CloudFront use to ensure low-latency delivery? (Select the best answer.)

* AWS Edge Location
  Amazon CloudFront uses AWS edge locations to ensure low-latency delivery.
```

##### ‼️또 다른 말로는 CDN 즉 네트워크 시스템을 <br> 콘텐츠 캐싱 시스템(저장하고 접근)이라고도 한다.‼️

* Edge locations cache content to deliver data
   improve the delivery of content by caching it closer to end users
   
* ‼️거듭 말하지만. **여기서 말하는 "콘텐츠"란**‼️
  * ‼️이미지, 데이터, 클라이언트 애플리케이션, **API**들을 말한다.‼️

* ‼️**캐싱은 파일 복사본을**‼️
  1. ‼️캐시 서버에 저장하고
     저장(배포)는 CloudFront로‼️
  2. ‼️캐시서버에 캐시된 콘텐츠에 빠르게 액세스
     접근은 Route 53을 통해 한다?‼️

##### 따로 지리적 배포 제한을 하지 않으면 모든 국가에서 접근이 가능하다.
* 하지만 사용자의 IP주소를 기반으로 Whitelist, Blacklist를 설정해 국가별 접근을 제어할 수 있다.

##### 엣지 네트워킹의 좀더 자세한 원리
* 410개 이상의 글로벌 멀티 서비스 접속 지점(POP)을 두어 네트워크 홉을 제거한다 -> 이것이 더 짧은 지연시간을 제공한다.

* POP의 스펙
  * 캐싱
  * 네트워크 연결
  * 엣지 컴퓨팅

* CloudFront 라는 이름의 CDN
  * 파일 캐싱 말고, API 전송의 역할
  * 애플리케이션 오리진(원본 위치)로 전송된 요청을 통합

* DDoS및, 봇 공격과 같은 보안 이슈는 Cloud WAF에 의존을 한다.

* 트래픽 처리같은 경우 
  * CloudFront 하나가 전세계에 분산된 에지 로케이션에서 나온 트래픽을 처리한다.
  * Route 53을 통해 웹사이트 이름을 IP주소로 변환해 라우팅하거나
  * AWS Global Accelerator을 통해 글로벌 트래픽 라우팅 간소화

---

#### 2).  Amazon Route 53 : Route 53 is a Domain Name System or DNS

* 어떤 도메인이 어느 엔드포인트(클라이언트 입장에서 보이는 URL 진입점)로 갈지 이름 해석/트래픽 정책.
* 즉, "유저 기기"에서 부터 "인터넷 애플리케이션과 같은 서버 기기"로 부터 라우팅 하는 DNS
* Route 53 is a Domain Name System or DNS that routes "end users" to "end application"

---

#### 3). 패턴

* CloudFront는 어떤 DNS든 사용 가능
Route 53도 마찬가지로 어떤 CDN/원서버에도 사용 가능.
* 결론은 서로는 AWS 서비스를 반드시 써야한다가 아니다.
  ```
  1. CloudFront 배포 생성후, 배포 도메인 부여 dxxxx.cloudfront.net
  2. Route 53 Alias A/AAAA 레코드로 www.example.com(또는 루트 도메인) 만들면, 해당 CloudFront 배포에 매핑
  ```

---

> ### 📄 4. AWS와 상호 작용하는 방법

<div align=center>
    <img src="image/2025-11-03-16-48-38.png" width="80%">
    <h5></h5>
</div>

#### 1). API

* 어떻게 요청을 보내면 어떻게 응답을 줄 것인지에 대한 약속이다.
* API를 통해 AWS 리소스를 구성하고 관리할 수 있다.
* API를 요청하고 응답받는 방법은 다음과 같다.

---

#### 2). AWS Management Console

* AWS Lambda나, EC2를 생성하는 행위도 클릭 딸깍 으로 가능하다.
* API 호출은 AWS Management Console에서 GUI를 사용할 수 있다.

---

#### 3). AWS Command Line Interface(AWS CLI)

* AWS Management Console이 하는 행동을 모두 CLI 커맨드로 실행할 수 있다.
* 일명 자동화가 가능하다는 것이다.

---

#### 4).AWS SDK

* 커맨드가 아니라 아예 프로그래밍 언어로 AWS API 행동을 모두 수행할 수 있다.
* C++, Java, .NET 등

---

#### 5). 리소스 프로비저닝 자동화 서비스

##### 사용자가 프로비저닝을 하는 것도 귀찮다면, 바탕으로 알아서 자동으로 환경이 구축 된다.

##### ① AWS Elastic Beanstalk

* Elastic Beanstalk로 서버를 구축하고 프로젝트 배포하기 가능
* 서버 코드를 전부 Zip파일로 만들면 된다. 
  그러면 아래의 작업을 알아서 자동으로 구축해 준다.
    1. 용량 조정
    2. 로드 밸런싱
    3. 자동 조정
    4. 애플리케이션 상태 모니터링

##### ② AWS CloudFormation

* 인프라를 코드로 취급할 수 있습니다. 
* CloudFormation은 IaC(인프라를 코드로) 정의해 템플릿(YAML/JSON)을 버전관리하고, 반복·재현 가능하게 배포합니다. 
* 의존성 해석, 체인지셋, 롤백, 드리프트 감지까지 제공해 형상관리와 재현성에 최적.