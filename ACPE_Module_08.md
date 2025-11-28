
---

## Module 8

---

```
[1]
한 보안 담당자는 특정 EC2 인스턴스의 보안 그룹 설정이  
**지난 3개월 동안 어떻게 변경되었는지 타임라인으로 보고** 싶습니다.  
어떤 AWS 서비스를 사용하는 것이 가장 적절합니까?

A. Amazon CloudWatch ✅
B. AWS CloudTrail  
C. AWS Config  
D. AWS Trusted Advisor  

---

[2]
운영 팀은 프로덕션 EC2 인스턴스의 **CPU 사용률이 80%를 초과하는 상태가 5분 이상 지속되면 이메일 알림**을 받고 싶습니다.  
이 요구사항을 충족하기 위한 구성 조합으로 가장 적절한 것은 무엇입니까?

A. CloudWatch 메트릭 + CloudWatch 알람 + SNS 토픽 + 이메일 구독  ✅
B. CloudTrail 이벤트 + SNS 토픽 + 이메일 구독  
C. AWS Config 규칙 + CloudWatch 대시보드  
D. AWS Artifact 보고서 + SNS 토픽  

---

[3]
다음 중 **Amazon CloudWatch**와 **AWS CloudTrail**을 올바르게 구분한 설명은 무엇입니까?

A. CloudWatch는 API 호출 이력을 기록하고, CloudTrail은 메트릭을 수집한다.  
B. CloudWatch는 리소스 상태와 성능 지표를 모니터링하고, CloudTrail은 사용자 활동과 API 호출을 기록한다.   ✅
C. 둘 다 메트릭 수집만 담당하며, 로그 기능은 제공하지 않는다.  
D. 둘 다 요금 청구서(Invoice)를 다운로드하는 데 사용된다.  

---

[4]
어느 날 아침, 한 S3 버킷이 삭제되어 있는 것을 발견했습니다.  
**누가, 언제, 어떤 방법으로 해당 버킷을 삭제했는지** 추적하고 싶을 때 가장 먼저 확인해야 할 서비스는 무엇입니까?

A. Amazon CloudWatch Logs  
B. AWS CloudTrail  ✅
C. AWS Config  
D. AWS Artifact  

---

[5]
규제 준수 팀에서 “AWS가 어떤 국제 규격(예: ISO, SOC 등)에 대해 
어떤 **감사/규정 준수 보고서**를 가지고 있는지”를 보고 싶어 합니다.  
이 팀이 가장 먼저 확인해야 할 서비스는 무엇입니까?

A. AWS Artifact ✅
B. AWS Trusted Advisor  
C. AWS Organizations  
D. AWS Config 

---

[6]
한 회사는 여러 AWS 계정을 AWS Organizations로 묶어 사용하고 있습니다.  
보안 정책상, **개발 조직(OU)** 에 속한 모든 계정에서는 
**프로덕션 리전에 EC2를 생성하지 못하도록** 제한하고 싶습니다.  
이를 위해 사용해야 할 기능은 무엇입니까?

A. 각 계정의 IAM 사용자에게 직접 정책을 붙인다.  
B. AWS Config 규칙을 생성한다.  
C. 서비스 제어 정책(SCP)을 개발 OU에 적용한다.  ✅
D. AWS Artifact에서 제한 규칙을 설정한다.  

---

[7]
다음 중 **AWS Trusted Advisor가 제공하는 5가지 평가 범주**에 
실제로 포함되는 항목만을 모두 고른 것은 어느 것입니까? (정답 2개)

A. 비용 최적화(Cost Optimization)  ✅
B. 애플리케이션 코드 품질(Code Quality)  
C. 내결함성(Fault Tolerance)  ✅
D. 마케팅 성과(Marketing Performance)  

---

[8]
보안 담당자가 최근 계정에서 **API 오류 비율이 갑자기 비정상적으로 증가하는 패턴**을 자동으로 감지하고 싶어 합니다.  
어떤 기능을 활용해야 합니까?

A. CloudWatch 대시보드 ✅
B. AWS CloudTrail Insights
C. AWS Config Aggregator
D. AWS Trusted Advisor 서비스 제한(Service Limits) 체크  

---

[9]
다음 중 **서비스와 주요 용도를 올바르게 매칭한 조합**은 어느 것입니까? (정답 2개)

A. AWS Config – 리소스 구성 변경 이력 및 관계 추적  ✅
B. Amazon CloudWatch – 규정 준수 보고서 다운로드  
C. AWS CloudTrail – 사용자 활동 및 API 호출 이력 기록  ✅
D. AWS Artifact – 리소스 성능 메트릭과 알람 설정  

---

[10]
한 운영 팀은 현재 AWS 계정에서  
- 사용률이 낮은 리소스를 찾아 비용을 절감하고,  
- 과도하게 허용된 보안 그룹 규칙을 점검하며,  
- 서비스 한도(예: EC2 인스턴스 수 제한)에 근접했는지도 확인  
하고 싶습니다.  

가장 적절한 AWS 서비스는 무엇입니까?

A. AWS Trusted Advisor  
B. AWS Artifact  
C. AWS Config  
D. Amazon CloudWatch  ✅

---

```
```
1. A
2. A
3. B
4. B
5. A
6. C
7. AC
8. A
9. AC
10. D
```

---

> ### 📄 1. AWS Config

* 리소스의 구성 변경 이력과 관계를 타임라인으로 추적하는 서비스.
  리소스 간에 어떤 관계가 있는지
* 개발자의 AWS 리소스 구성을 측정, 감사, 평가 지원  

---

> ### 📄 2. Amazon CloudWatch

#### AWS 리소스와 AWS에서 실행되는 애플리케이션을 실시간으로 모니터링

#### 1). 구성

1. **메트릭** : CPU 사용률, 디스크 I/O, 요금 데이터 수집
2. **경보** : 메트릭에 대한 임곗값을 정의하고 알림을 보내거나, 리소스를 자동으로 변경
3. **대시보드** : 지표, 경보, 데이터를 통합된 보기로 시각화
4. **Logs** : AWS 서비스의 로그를 중앙 집중화

#### 2). 사용 예제

* CloudWatch 알람 → SNS 토픽 → 이메일 알림 
* 요금 알림 (billing alarm), 요금의 임계값 설정
* 장기간 너무 높아질 경우 이를 경보로 알림 
* 자원 사용량 알림 CPU 자원 사용량 임계값 설정

---

> ### 📄 3. AWS CloudTrail

#### 사용자 활동과 API 호출을 이벤트로 기록 & 추적 

#### 1). CloudTrail 구성
1. **이벤트** : AWS 계정내 작업 추적 중요한 활동에 대한 세부 정보
2. **로그** : 이벤트(세부 정보)의 로그파일 S3 (저장 기간이 90일로 제한)
3. **AWS CloudTrail Insights** : 이상 패턴을 자동 감지
   * API 호출 패턴/오류 비율의 비정상적인 변화를 자동으로 분석

#### 2). 사용 예제
  * API 호출 예 : ( 콘솔, CLI, SDK, 기타 서비스 호출 포함)
  * 보안 분석, 감사, 변경 이력 추적 등에 사용

---

> ### 📄 4. AWS Artifact

#### 보고서와 계약을 온디맨드로 액세스하여 시간을 절약

1. 보고서 : AWS 규정 준수 보고서에 액세스
2. 계약 : AWS와의 계약을 검토, 수락, 관리

---

> ### 📄 5. AWS Organizations

#### 1). 사용 이점 

1. **AWS 계정 생성/관리를 자동화**
   * 새 계정 자동 생성(API/콘솔 통해)
2. 여러 AWS **계정**에 걸친 **액세스 정책을 중앙에서 관리**
   * Service Control Policy(SCP)를 OU/계정 단위로 적용해서  
   **여러 계정에 대한 서비스 접근 정책을 중앙에서 관리 & 자동화**
3. 청구서, 결제를 통합
   Organizations는 **통합 청구**를 묶어 주지만,
   **여러 계정의 비용을 분석하지는 않는다**
   실제 분석(그래프/리포트) 기능은 **Cost Explorer**가 담당.  

#### 2). 서비스 제어 정책 (SCP)

##### 사용자가 액세스할 수 있는 AWS 서비스, 리소스, 개별 API 작업에 대한 규칙이나 제한을 설정
*IAM 정책을 적용할 수 없습니다.*

**SCP가 적용할 수 있는 자격 증명과 리소스**
  1. 개별 멤버 계정
  2. 조직 단위(OU)

---

> ### 📄 6. AWS Trusted Advisor

#### 베스트 프랙티스 점검/추천

* 계정을 분석하고 모범 사례에 대한 권장 사항도 제공
    1. 비용 최적화(저사용 리소스)
    2. 보안(보안 그룹 과도 허용)
    3. 서비스 제한(Service Limits)

#### 1. 다섯 가지 범주 평가 항목
1. 성능
2. 비용 최적화
3. 보안
4. 내결함성
5. 서비스 제한

---
