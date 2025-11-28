
---

## Module 9

---

#### 요금 및 지원

```
AWS 요금 및 지원 모델을 설명할 수 있습니다.
AWS 프리 티어를 설명할 수 있습니다.
AWS Organizations 및 통합 결제의 주요 이점을 설명할 수 있습니다.
AWS Budgets의 이점을 설명할 수 있습니다.
AWS Cost Explorer의 이점을 설명할 수 있습니다.
AWS 요금 계산기의 주요 이점을 설명할 수 있습니다.
다양한 AWS Support 플랜을 구별할 수 있습니다.
AWS Marketplace의 이점을 설명할 수 있습니다.
```

---

> ### 📄 요금 예시

##### ③ Amazon S3

* 스토리지 : 객체 크기, 스토리지 클래스, 저장한 기간에 따라 요금 청구
* 요청 및 데이터 검색 : 웹 사이트에서 사진 파일을 서버에 요청할때마다 비용을 지불해야 함.
  1. 객체를 버킷에 추가 혹은 복사 : `PUT`, `COPY`, `POST` 또는 `LIST` 요청
  2. 버킷에서 객체를 검색하라는 요청 : `GET
* Data Transfer Out :  S3 -> CloudFront로 전송되는 데이터 버킷이나, 동일한 리전 내라면, 드는 비용은 없다.
* 관리 및 복제  : 관리 기능에 대한 비용을 지불해야 한다.

##### ④ Amazon DynamoDB

* 요청당 과금과, 프로비저닝 시간당 과금, 예약 용량(1–3년) 로 절감.
* 테이블 클래스 – Standard vs Standard-IA(비정기 접근, 저장비↓/요청비↑).
* 스토리지/전송 – GB-월 저장, 인터넷 Data Transfer Out 별도 과금.
* 프리 티어(Always Free)
  리전별 매월 25GB 저장 + 25 RCU + 25 WCU(Standard 테이블 클래스 기준). 
  Streams 250만 읽기 무료.
* **지역별 가격 상이**: 콘솔/가격 페이지에서 리전 선택 필수.


---

> ### 📄 통합 결제(Consolidated Billing / Organizations)

<div align=center>
    <img src="image/2025-10-08-00-44-34.png" width="80%">
    <h5></h5>
</div>

#### AWS Organizations의 통합 결제 기능을 사용하면<br> 조직의 모든 AWS 계정에 대한 단일 청구서를 받을 수 있다.
* 

##### ① 장점

1. **단일 청구서**
2. **볼륨 할인 공유**
3. **RI/Savings Plans 공유**
4. 계정별 비용 분리 가시화.

##### ② Consolidated billing

* 주요 이점
    * Organization과 연계하여 multiple AWS accounts의 영수증을 확인, 
    사용량을 합산하여 관리 및 모니터링 가능
    * 볼륨(사용량) 대량 구매 할인을 적용받기 위해 계정 간 사용량을 결합

---

> ### 📄 AWS Budgets

#### 예산을 생성하여 서비스 사용, 서비스 비용 및 인스턴스 예약을 계획할 수 있다.
* 예상 AWS 사용량을 기준으로 월말 비용을 검토
* AWS 배포를 확장하는 과정에서 예산을 초과한 금액을 지출하지 않기를 원할 것입니다.

#### 1). 예산/사용량/RI SP 커버리지/활용

* 목표 설정 → **임계 초과 전** 이메일/SNS/Chatbot 알림.

#### 2). Budgets Actions

* 자동 태그 IAM 정책 전환 등 **완화 조치**(선택).

---


> ### 📄 AWS Cost Explorer

<div align=center>
    <img src="image/2025-10-08-00-47-09.png" width="80%">
    <h5>시간 경과에 따라 AWS 비용 및 사용량을 시각화 및 관리</h5>
</div>

#### 비용 사용량 **시각화/분석**(서비스 계정 태그 리전별) 

* 발생 비용 기준 상위 5개 AWS 서비스의 비용 및 사용량에 대한 기본 보고서가 포함되어 있습니다.
* Rightsizing 권장 
* **Cost Anomaly Detection** 연계.

---

> ### 📄 TCO Calculator

#### 온프레미스 데이터 센터를 사용하는 것과 AWS를 사용하는 것의 비용을 비교·추정

---

> ### 📄 AWS Support Plans(지원 플랜)

#### 문제를 해결하고 비용을 절감하며, <br> AWS 서비스를 효율적으로 사용하는데 도움이 되는 4가지 Support 플랜

* `Basic` , `Developer` , `Business` , `Enterprise`
  * 비 프로덕션(실험용/테스트용)이든, 프로덕션(실제 서비스) 계정이든 모두 사용가능하다.

##### ① **Basic**(무료)

* 계정 청구
* 개발자 포럼
* **Trusted Advisor검사에 액세스할 수 있다.**. 

##### ② **Developer**

* 모범 사례 지침 클라이언트 측 진단 도구
* AWS에서 실험 중이거나 테스트하는 경우 권장됩니다.
* **Trusted Advisor검사에 액세스할 수 있다.**. 
* 12시간 긴급하지는 않지만 시기적절한 지원을 원하는 고객의 요구 사항

##### ③ **Business**

* 최저 비용으로 모든 AWS Trusted Advisor 검사를 포함하는 Support 플랜
* 24×7, 전화/채팅
* **Trusted Advisor 전체 체크**
* **API 지원**

##### ④ **Enterprise On-Ramp/Enterprise**

* 24×7, **TAM/Concierge**, 운영 아키텍처 리뷰, 미션 크리티컬. 
  * **TAM** : 빠르고 효율적인 기술 지원
    * 애플리케이션 계획, 배포, 최적화, 아키텍쳐 검토를 지속적인 커뮤니케이션
  * **Concierge** : 요금·계정 관련 도움

---

> ### 📄 AWS Marketplace

![](image/2025-10-08-00-54-01.png)

* 서드파티 SW를 **AWS 청구로 통합 결제**, 
* 시간 월 연 구독/AMI SaaS 등. **Private Offers/조직 구매** 가능.
* 산업 및 사용 사례별로 소프트웨어 솔루션을 탐색할 수도 있습니다.

---
