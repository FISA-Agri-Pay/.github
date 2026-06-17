# [우리FISA 6기] 클라우드 엔지니어링 과정 3팀

## 1. 프로젝트 개요

* **주제** : 농업 데이터 기반 BNPL 플랫폼 - 시계열 예측 기반 Kubernetes 오토스케일링 및 Observability 통합 시스템 구축

* **프로젝트 기획 배경** :

  농업인은 영농 주기(파종·생육·수확)에 따라 소득 시점이 달라, 비용은 영농 초기에 먼저 나가지만 수익은 수확 이후 발생하는 **현금흐름 불일치**를 겪습니다. 하지만 기존 금융권은 급여·금융거래 이력 중심으로 평가해 이런 계절성 소득 구조를 반영하기 어렵습니다.

  또한 파종기·수확기·상환일에는 신청·결제·상환 요청이 한 시점에 몰려 **트래픽이 급증**합니다. Reactive 오토스케일링은 트래픽이 늘어난 뒤 Pod를 추가하므로, HPA가 반응하기 전 구간에서 지연·장애가 발생할 수 있습니다.

  이에 본 프로젝트는 두 가지를 함께 해결합니다.

  * **농업 데이터 기반 대안신용평가 BNPL 서비스** — 농지·작물·보험·상환 이력으로 농업인 맞춤 한도 산정
  * **Predictive 오토스케일링** — 트래픽을 사전 예측해 Pod를 미리 확보하고, Reactive 방식과 비교 검증

  즉, 단순 서비스 배포가 아니라 **하이브리드 클라우드 환경에서의 예측 기반 운영 구조 검증**이 본 프로젝트의 핵심입니다.

* **기술 스택** :

  | 영역 | 기술 스택 |
  | --- | --- |
  | Frontend | ![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB) ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white) ![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white) ![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white) ![Zustand](https://img.shields.io/badge/Zustand-764ABC?style=flat-square) |
  | Backend | ![Java 21](https://img.shields.io/badge/Java%2021-007396?style=flat-square&logo=openjdk&logoColor=white) ![Spring Boot 3.5](https://img.shields.io/badge/Spring%20Boot%203.5-6DB33F?style=flat-square&logo=springboot&logoColor=white) ![Spring Security](https://img.shields.io/badge/Spring%20Security-6DB33F?style=flat-square&logo=springsecurity&logoColor=white) ![Spring Data JPA](https://img.shields.io/badge/Spring%20Data%20JPA-6DB33F?style=flat-square&logo=spring&logoColor=white) ![Spring Batch](https://img.shields.io/badge/Spring%20Batch-6DB33F?style=flat-square&logo=spring&logoColor=white) ![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white) ![FastMCP](https://img.shields.io/badge/FastMCP-111827?style=flat-square) |
  | Data / Event | ![PostgreSQL 16](https://img.shields.io/badge/PostgreSQL%2016-4169E1?style=flat-square&logo=postgresql&logoColor=white) ![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white) ![AWS SQS](https://img.shields.io/badge/AWS%20SQS-FF4F8B?style=flat-square&logo=amazonsqs&logoColor=white) |
  | AI / AIOps | ![Python 3.11](https://img.shields.io/badge/Python%203.11-3776AB?style=flat-square&logo=python&logoColor=white) ![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white) ![GRU](https://img.shields.io/badge/GRU-7C3AED?style=flat-square) ![vLLM](https://img.shields.io/badge/vLLM-111827?style=flat-square) ![Qwen3-32B](https://img.shields.io/badge/Qwen3--32B-615CED?style=flat-square) ![MCP](https://img.shields.io/badge/MCP-111827?style=flat-square) |
  | Infrastructure | ![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white) ![VMware ESXi](https://img.shields.io/badge/VMware%20ESXi-607078?style=flat-square&logo=vmware&logoColor=white) ![pfSense](https://img.shields.io/badge/pfSense-212121?style=flat-square&logo=pfsense&logoColor=white) ![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white) ![MetalLB](https://img.shields.io/badge/MetalLB-0B7FAB?style=flat-square) ![NGINX Ingress](https://img.shields.io/badge/NGINX%20Ingress-009639?style=flat-square&logo=nginx&logoColor=white) |
  | DevOps | ![GitLab](https://img.shields.io/badge/GitLab-FC6D26?style=flat-square&logo=gitlab&logoColor=white) ![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=flat-square&logo=jenkins&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white) ![Harbor](https://img.shields.io/badge/Harbor-60B932?style=flat-square&logo=harbor&logoColor=white) ![ArgoCD](https://img.shields.io/badge/ArgoCD-EF7B4D?style=flat-square&logo=argo&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![Trivy](https://img.shields.io/badge/Trivy-1904DA?style=flat-square&logo=trivy&logoColor=white) |
  | Observability | ![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white) ![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white) ![Loki](https://img.shields.io/badge/Loki-F46800?style=flat-square&logo=grafana&logoColor=white) ![Tempo](https://img.shields.io/badge/Tempo-F46800?style=flat-square&logo=grafana&logoColor=white) ![Alertmanager](https://img.shields.io/badge/Alertmanager-E6522C?style=flat-square&logo=prometheus&logoColor=white) ![OpenTelemetry](https://img.shields.io/badge/OpenTelemetry-000000?style=flat-square&logo=opentelemetry&logoColor=white) ![Fluent Bit](https://img.shields.io/badge/Fluent%20Bit-49BDA5?style=flat-square&logo=fluentbit&logoColor=white) ![Cilium](https://img.shields.io/badge/Cilium-F8C517?style=flat-square&logo=cilium&logoColor=white) ![Hubble](https://img.shields.io/badge/Hubble-F8C517?style=flat-square) |

---

## 2. 아키텍쳐

### 2-1. 시스템 아키텍쳐

![시스템 아키텍처](../images/system-architecture.png)

### 설명

AWS · On-Prem · VESSL AI를 연계한 하이브리드 클라우드 구조입니다.

* **AWS (사용자 접점 · 채널계 · DR)** — 요청은 Route 53 → WAF(Shield·ACM) → CloudFront로 유입되며, 정적 콘텐츠는 S3, 동적 요청은 ALB를 거쳐 EKS로 전달됩니다. EKS는 ap-northeast-2의 두 AZ(A/B) private subnet에 Worker node를 두고 Auto Scaling으로 운영하며, public subnet에는 Bastion host·NAT Gateway를 배치했습니다. RDS는 AZ 간 복제로 이중화하고, 별도 DR Standby(DR RDS)는 KMS로 암호화합니다. DB 자격증명은 Secrets Manager(ASM)로 관리하며 ECR(이미지)·SQS(메시징)를 사용하고, 운영 알림은 CloudWatch → Lambda → SNS로 처리합니다.
* **On-Prem (핵심 금융 서비스 · 데이터 · 운영, 192.168.0.0/24·10.30.0.0/16)** — VPN Gateway 뒤 pfSense Active/Standby로 경계와 이중화를 구성합니다. Kubernetes 클러스터는 네임스페이스로 Service(백엔드·Cronjob), Observability(Prometheus·kube-state-metrics·AlertManager·OTel Collector), AiOps(KEDA·MCP·예측 모델), CI/CD(ArgoCD 기반 GitOps 배포 · Harbor·Trivy 이미지 스캔)를 분리 배치하고, DaemonSet으로 Fluent-bit·Cilium Agent·Node-exporter를 전 노드에 띄웠습니다. PostgreSQL은 Patroni 물리 복제로 Write/Read를 이중화하고, TrueNAS가 PV 스토리지를, GitLab·Jenkins가 소스·빌드를 담당합니다.
* **VESSL AI (kr-west)** — vLLM 기반 Qwen3-32B를 서빙해 AIOps의 LLM 추론을 담당합니다.

AWS VPN Gateway와 On-Prem pfSense를 Site-to-Site VPN으로 연결하고, On-Prem PostgreSQL(Read)을 AWS DMS의 Full-load + CDC로 DR RDS에 복제합니다. 예측 모델이 산출한 트래픽 값은 PostgreSQL에 저장되어 prediction-exporter → Prometheus → KEDA 경로로 예측형 오토스케일링에 활용됩니다.

---

### 2-2. 소프트웨어 아키텍처

![소프트웨어 아키텍처](../images/software-architecture.png)

### 설명

프론트엔드 · API · 백엔드 · 데이터 · AI/오토스케일링 · Observability 계층으로 분리했습니다. 백엔드는 인증·신용·상품/결제·관리·배치로 책임을 나누고, 금융 도메인은 Spring Boot(Java), AIOps·예측 모델은 FastAPI/FastMCP(Python)로 구성한 폴리글랏 구조입니다. 핵심 금융 데이터와 예측 메트릭은 PostgreSQL, 세션·임시 저장·캐시는 Redis에 둡니다.

결제는 SQS 이벤트로 비동기 처리하며, 이벤트 ID 기준 멱등 처리로 한도 차감·주문·원장 기록의 중복 반영을 막고, 배치가 이자·자동 상환·연체를 담당합니다. 예측 모델이 산출한 트래픽 값은 PostgreSQL에 저장되고, prediction-exporter가 이를 메트릭으로 노출하면 Prometheus가 수집해 KEDA가 예측 기반 Scale-out을 수행합니다.

인증/인가(Spring Security·JWT), 검증·예외 처리, OpenTelemetry 분산 트레이싱은 공통 관심사로 분리했고, Prometheus·Loki·Tempo·Alertmanager·Grafana로 메트릭·로그·트레이스·알림을 통합 관측하며, MCP 기반 AIOps가 이를 조회해 장애 원인 후보와 운영 리포트를 생성합니다.

---

## 3. 주요 기능 소개

### 3-1. 핵심 기술 구성

| 핵심 기술 | 설명 |
| --- | --- |
| 하이브리드 클라우드 MSA | AWS 채널계(`service-catalog`)와 On-Prem 핵심계(인증·신용·결제) 마이크로서비스를 Site-to-Site VPN으로 연결하고, 금융 데이터 민감도를 기준으로 서비스를 분산 배치. |
| 고가용성 & 재해복구(DR) | VLAN 망분리와 pfSense Active/Standby(CARP)로 네트워크 경계·이중화를 구성하고, PostgreSQL Patroni HA에 더해 AWS DMS CDC로 On-Prem DB를 RDS에 실시간 복제해 DR 환경을 구성. |
| 예측형 오토스케일링 | Reactive 방식의 반응 지연을 보완하기 위해, 예측 모델이 미래 트래픽을 PostgreSQL에 저장하면 prediction-exporter → Prometheus를 거쳐 KEDA가 External Metric으로 읽어 Pod를 사전 Scale-out. |
| 통합 Observability | 하이브리드(AWS·On-Prem)의 메트릭·로그·트레이스·알림을 통합 수집. Cilium(eBPF) CNI로 별도 계측 없이 HTTP 요청량·응답시간을 관측. |
| FastMCP 기반 AIOps | 메트릭·로그·알림·Kubernetes 조회 등 운영 도구를 MCP Tool로 표준화하고, 장애 발생 시 LLM 기반으로 원인 후보(RCA)와 운영 리포트를 자동 생성. |

---

### 3-2. 통합 워크플로우 다이어그램
![통합 워크플로우](../images/workflow.png)

---

### 3-3. 세부 기능 소개

#### [이벤트 기반 BNPL 결제]
 
* 기능 설명 :
  체크아웃 시 결제 요청을 저장한 뒤 SQS로 결제 이벤트를 발행하고, 결제 서비스가 이를 소비해 한도 차감·주문 생성·이용 원장 기록을 수행합니다. SQS는 at-least-once 전달이므로, 처리 이력 테이블(paymentEventProcessLog)에 이벤트 ID와 결제 요청 Public ID를 기록해 동일 결제의 중복 반영을 방지합니다(애플리케이션 레벨 멱등 처리).
  또한 SQS 메시지 attribute에 OpenTelemetry trace context를 함께 전달하고, 결제 서비스 소비 시 이를 복원해 체크아웃 → SQS → 결제 소비로 이어지는 결제 흐름을 end-to-end 추적할 수 있도록 구성했습니다.
  
* 핵심 코드(스크립트) :
```java
// 결제 요청 저장 후 SQS 이벤트 발행
BnplPaymentRequest paymentRequest = bnplPaymentRequestRepository.saveAndFlush(BnplPaymentRequest.create(
        paymentRequestPublicId,
        userPublicId,
        totalAmount,
        cartItems
));

UUID orderPublicId = orderPublicId(paymentRequest.getPublicId());

creditPaymentEventProducer.publish(
        toEvent(paymentRequest, orderPublicId, cartItems, request.deliveryAddress(), request.idempotencyKey())
);
```
 
```java
// SQS 메시지 발행 및 trace context 전파
SendMessageRequest request = SendMessageRequest.builder()
        .queueUrl(paymentRequestQueueUrl)
        .messageBody(payload)
        .messageGroupId(event.userPublicId().toString())
        .messageDeduplicationId(event.paymentRequestPublicId().toString())
        .messageAttributes(SqsTraceContext.currentMessageAttributes())
        .build();
```

```java
// 이벤트 소비 시 멱등 처리 + 주문 생성 + 한도 차감 + 이용 원장 기록
if (paymentEventProcessLogRepository.existsByEventIdOrPaymentRequestPublicId(eventId, paymentRequestPublicId)) {
    return;
}

order = orderRepository.save(Order.confirmed(
        orderPublicId,
        userPublicId,
        paymentRequestPublicId,
        message.totalAmount(),
        message.deliveryAddress(),
        message.items(),
        Objects.requireNonNullElse(message.occurredAt(), LocalDateTime.now())
));

creditLimit.use(message.totalAmount());

creditUsageLedgerRepository.save(CreditUsageLedger.purchase(
        creditLimit.getPublicId(),
        order.getPublicId(),
        paymentRequestPublicId,
        message.totalAmount(),
        usedAt
));

paymentEventProcessLogRepository.save(PaymentEventProcessLog.processed(
        eventId,
        paymentRequestPublicId,
        message.idempotencyKey()
));
```

* 코드 링크(스크립트 링크) :
  * `back-end/service-catalog/src/main/java/com/kkpp/catalog/checkout/service/CheckoutService.java`
  * `back-end/service-catalog/src/main/java/com/kkpp/catalog/checkout/event/SqsCreditPaymentEventProducer.java`
  * `back-end/service-payment/src/main/java/com/kkpp/payment/event/SqsCreditPaymentRequestedConsumer.java`
  * `back-end/service-payment/src/main/java/com/kkpp/payment/service/CreditPaymentProcessingService.java`
  * `back-end/service-payment/src/main/java/com/kkpp/payment/domain/PaymentEventProcessLog.java`
---
 
#### [예측형 오토스케일링]
 
* 기능 설명 :
  예측 모델이 미래 요청량을 산출하면 서비스별 처리 용량을 기준으로 필요한 Pod 수를 계산해 PostgreSQL(`prediction_metrics`)에 저장합니다. prediction-exporter가 이를 메트릭으로 노출하면 Prometheus가 수집하고, KEDA가 해당 메트릭을 External Metric으로 읽어 백엔드 replica를 사전 조정합니다. 모델은 Prophet·SARIMA·GRU·LSTM을 동일 조건에서 비교했고, Pod 부족이 곧 장애로 이어지는 특성상 Under-provisioning rate를 기준으로 GRU를 선정했습니다.
* 핵심 코드(스크립트) :
```python
def required_pods(request_rate, policy=DEFAULT_POD_POLICY):
    values = np.asarray(request_rate, dtype=float)
    pods = np.ceil(np.maximum(values, 0) / policy.effective_capacity).astype(int)
    pods = np.clip(pods, policy.min_pods, policy.max_pods)
 
    if values.ndim == 0:
        return int(pods)
 
    return pods
```
 
```yaml
# TODO: 실제 KEDA ScaledObject 매니페스트로 교체 (Prometheus trigger 기준)
# apiVersion: keda.sh/v1alpha1
# kind: ScaledObject ...
```
 
* 코드 링크(스크립트 링크) :
  * `ai-prediction-model/src/models/gru/`
  * `ai-prediction-model/src/evaluation/pod_policy.py`
  * `ai-prediction-model/src/evaluation/service_pod_policy.py`
  * `prophet-autoscaler/`
---
 
#### [FastMCP 기반 AIOps Agent]
 
* 기능 설명 :
  FastAPI/FastMCP 기반 MCP 서버로 Prometheus·Loki·Alertmanager·Kubernetes 조회 도구를 표준화했습니다. Alertmanager 알림 발생 시 관련 메트릭·로그를 모아 장애 원인 후보(RCA)와 운영 리포트 초안을 생성하며, LLM 추론은 VESSL AI의 vLLM(Qwen3-32B)을 사용합니다.
* 핵심 코드(스크립트) :
```python
for tool_plan in plan_result.planned_tools:
    if not is_read_tool_plan(tool_plan):
        continue
 
    enriched_plan = enrich_tool_plan(
        tool_plan,
        incident_key=incident.incident_key
    )
 
    tool_results.append(self._dispatcher.execute(enriched_plan))
```
 
```python
tool = resolve_registered_tool(
    server_name=plan.server_name,
    tool_name=plan.tool_name,
)
 
permission = McpToolPermission(tool.tool_permission)
policy = resolve_tool_policy(permission)
operation = self._resolve_operation(plan.server_name, plan.tool_name)
```
 
* 코드 링크(스크립트 링크) :
  * `mcp-aiops-backend/src/aiops_platform/main.py`
  * `mcp-aiops-backend/src/aiops_platform/mcp/server.py`
  * `mcp-aiops-backend/src/aiops_platform/agent/dispatcher.py`
  * `mcp-aiops-backend/src/aiops_platform/alertmanager_agent/service.py`
---
 
#### [CQRS 기반 읽기/쓰기 분리 (성능 개선)]
 
* 기능 설명 :
  데이터 변경(쓰기)과 조회(읽기)의 모델·책임을 분리하는 CQRS 패턴을 적용하고, DB도 PostgreSQL Primary(쓰기)/Replica(읽기)로 분리해 조회 부하를 Replica로 분산했습니다. K6 부하 테스트(100 RPS, 10분) 결과, 응답 시간과 요청 처리 안정성이 모두 개선됐습니다.
  | 지표 | 적용 전 | 적용 후 | 차이 |
  | --- | --- | --- | --- |
  | 평균 응답 시간 | 50.48ms | 35.60ms | 29.5% 감소 |
  | p95 응답 시간 | 68.05ms | 51.28ms | 24.6% 감소 |
  | 최대 응답 시간 | 4.01s | 1.38s | 65.6% 감소 |
  | 실패율 | 0% | 0% | - |
  | Dropped Iterations | 304건 | 21건 | 93.1% 감소 |
* 핵심 코드(스크립트) :
```java
// core DB용 Repository / EntityManager / TransactionManager 분리
@EnableJpaRepositories(
    basePackages = {
        "com.kkpp.admin.adminauth.repository",
        "com.kkpp.admin.bnpl.repository",
        "com.kkpp.admin.order.repository",
        "com.kkpp.admin.credit.repository"
    },
    entityManagerFactoryRef = "coreEntityManagerFactory",
    transactionManagerRef = "coreTransactionManager"
)
```
```java
// 조회 모델: readOnly 트랜잭션 + DTO Projection 조회
@Transactional(readOnly = true)
public CreditReviewPageResponse getReviews(CreditReviewStatus status, int page, int size) {
    Page<CreditReviewSummaryResponse> result =
            applicationRepository.findReviewSummaries(status, pageable);

    return new CreditReviewPageResponse(
            result.getContent(),
            result.getNumber(),
            result.getSize(),
            result.getTotalElements(),
            result.getTotalPages(),
            result.isFirst(),
            result.isLast()
    );
}
```
```java
// 쓰기 모델: 별도 쓰기 트랜잭션 + 비관적 락
@Transactional
public CreditReviewDecisionResponse approve(UUID publicId, ApproveCreditReviewRequest request) {
    CreditReviewApplication application = getApplicationForUpdate(publicId);

    application.approve(request.reviewedBy(), request.approvedAmount(), decidedAt);

    CreditReviewLimit savedLimit = limitRepository.save(limit);
}

@Lock(LockModeType.PESSIMISTIC_WRITE)
@Query("select application from CreditReviewApplication application join fetch application.user where application.publicId = :publicId")
Optional<CreditReviewApplication> findByPublicIdForUpdate(@Param("publicId") UUID publicId);
```
 
* 코드 링크(스크립트 링크) :
  * `service-admin/src/main/java/com/kkpp/admin/global/config/CoreDataSourceConfig.java`
  * `service-admin/src/main/java/com/kkpp/admin/global/config/CatalogDataSourceConfig.java`
  * `service-admin/src/main/java/com/kkpp/admin/credit/service/CreditReviewService.java`
  * `service-admin/src/main/java/com/kkpp/admin/credit/repository/CreditReviewApplicationRepository.java`
  * `service-admin/src/main/java/com/kkpp/admin/bnpl/service/BnplAdminService.java`
---
 
#### [CI/CD 빌드 최적화 (성능 개선)]
 
* 기능 설명 :
  이미지 최적화와 빌드 파이프라인 최적화를 함께 수행했습니다. 멀티스테이지 빌드와 경량 런타임 베이스를 적용하고 취약 베이스·불필요 패키지를 제거해 이미지 크기와 보안 취약점을 줄였습니다(Trivy 스캔 기준 취약점 0). 멀티스테이지로 늘어난 빌드 시간은, Docker 내부의 중복 Gradle 빌드를 제거(Jenkins가 생성한 JAR만 패키징)하고 Spring Boot Layered JAR로 의존성 레이어를 Harbor에 캐싱하여 단축했습니다.
  | 이미지 | 적용 전 | 적용 후 | 비교 |
  | --- | --- | --- | --- |
  | 이미지 크기 | 842MB | 694MB | 17.5% 감소 |
  | 취약점 개수 | 128 | 0 | 100% 감소 |
  | 레이어 개수 | 48 | 32 | 33.3% 감소 |
  | 파이프라인 | 적용 전 | 적용 후 | 비교 |
  | --- | --- | --- | --- |
  | Docker Build & Push | 2분 5초 | 45초 | 약 64% 단축 |
  | 전체 파이프라인 | 5분 27초 | 3분 10초 | 약 42% 단축 |
* 핵심 코드(스크립트) :
```dockerfile
# TODO: 실제 Dockerfile로 교체
# 멀티스테이지 + 경량 런타임 베이스 + Spring Boot Layered JAR (의존성/애플리케이션 레이어 분리)
```
 
```groovy
// TODO: 실제 Jenkinsfile 핵심 stage로 교체
// Docker 내부 중복 Gradle 빌드 제거 + Layered JAR 패키징 부분 발췌
```
 
* 코드 링크(스크립트 링크) :
  * `TODO: Dockerfile 경로`
  * `TODO: Jenkinsfile 경로`
 