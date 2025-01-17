
# Jaeger: 마이크로서비스 추적의 강력한 도구 

## Jaeger란 무엇인가?

Jaeger는 복잡한 마이크로서비스 환경을 모니터링하고 문제를 해결하는 데 사용되는 오픈소스 소프트웨어입니다. 주로 **분산 서비스 간 트랜잭션을 추적**하는 데 도움을 줍니다.

## 분산 추적의 의미

### 왜 필요한가?

현대의 클라우드 네이티브 소프트웨어는 다양한 기능을 제공하는 여러 개의 개별 서비스(마이크로서비스)로 구성됩니다. 사용자의 단 한 번의 요청이 수십 개의 서비스를 거칠 수 있죠.

### 문제 발생 시

- 어떤 서비스에서 문제가 발생했는지
- 요청 처리 속도가 느려진 원인
- 전체 요청 흐름 추적

이러한 복잡한 상황에서 **분산 추적**이 해결책을 제공합니다.

## Jaeger의 핵심 작동 방식

### 추적(Trace)과 스팬(Span)

- **추적**: 시스템 전체를 통과하는 데이터/실행 경로
- **스팬**: 작업의 논리적 단위 (예: 데이터베이스 쿼리, HTTP 요청)
  - 각 스팬은 작업 이름, 시작 시간, 지속 시간 포함

### 작동 프로세스

1. **애플리케이션 계측**: 코드에 추적 생성 로직 추가
2. **추적 생성**: 마이크로서비스 전체의 작업 경로 추적
3. **데이터 수집**: Jaeger Agent를 통해 스팬 수집
4. **저장**: Jaeger Collector가 데이터를 백엔드 데이터베이스에 저장
5. **시각화**: Jaeger Query 서비스에서 UI로 추적 정보 제공

## Jaeger의 주요 활용 사례

1. **성능 최적화**
   - 지연이 발생하는 서비스 정확히 파악
   - 서비스 간 상호작용 시각화

2. **문제 해결**
   - 서비스 장애의 근본 원인 추적
   - 비정상적인 패턴 감지

3. **보안 및 컴플라이언스**
   - 데이터 흐름 추적
   - 감사 추적 제공

4. **개발 및 테스트**
   - 로컬 환경에서 애플리케이션 문제 사전 감지

## Jaeger의 역사

- **2015년**: 우버(Uber)에서 오픈소스 프로젝트로 시작
- **2017년**: CNCF Incubation 프로젝트 채택
- **2019년**: CNCF 정식 프로젝트 승인

## 최근 Red Hat의 변화 (2024년)

Red Hat은 Jaeger에서 Tempo와 OpenTelemetry로 전환 중입니다:

- Jaeger와 Elasticsearch 사용 중단
- OpenTelemetry의 Red Hat 빌드 채택
- Prometheus 스택 통합
- 자동 메트릭 생성 및 경고 기능 추가

Ref_01 : https://www.redhat.com/ko/topics/microservices/what-is-jaeger


---

## Grafana 기반 MSA 서버 모니터링 시스템 구축 포스팅 요약

### 왜 Grafana를 선택했나?
* **단일 대시보드:** 시스템 모니터링, 로그 모니터링, 경고 알람, 분산 트레이싱 등 모든 기능을 한 곳에서 확인 가능
* **높은 자유도:** 다양한 플랫폼과의 연동, 커스터마이징 가능
* **LGTM Stack:** Loki, Grafana, Tempo, Mimir를 활용한 강력한 연동성

### 각 도구의 역할
* **Grafana:** 시각화 도구, 다양한 데이터 소스 연동
* **Loki:** 로그 모니터링, 높은 확장성
* **Prometheus:** 메트릭 정보 수집, 시계열 데이터베이스
* **Tempo:** 분산 추적 시스템, 로그와의 연동

### Docker를 활용한 시스템 구축
* 각 도구를 Docker 이미지로 구성하여 관리 용이
* Docker Compose를 이용한 간편한 배포

### 구축 과정
1. **Grafana 설치:** 대시보드 생성 및 관리
2. **Prometheus 설치:** 메트릭 데이터 수집, node-exporter 연동
3. **Loki 설치:** 로그 수집, Promtail 연동
4. **Tempo 설치:** 분산 추적, Grafana와 연동
5. **Spring Boot trace 설정:** Micrometer Tracing 라이브러리 활용

### 결론
Grafana 기반 모니터링 시스템 구축을 통해 운영 효율성을 향상시켰으며, 추가적인 기능 확장 가능성이 높음. 그리고 가격이 싼것 같음

엔터프라이즈 Advanced의 경우 월 299달러.

### 주요 장점
* **통합 대시보드:** 운영 편의성 증대
* **비용 절감:** 오픈소스 활용
* **높은 자유도:** 커스터마이징 가능




Ref_02 : [Grafana를 사용해 MSA 서버 모니터링 구축하기](https://velog.io/@dudgns0507/Grafana%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%B4-MSA-%EC%84%9C%EB%B2%84-%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81-%EA%B5%AC%EC%B6%95%ED%95%98%EA%B8%B0-Loki-Tempo-Prometheus)
