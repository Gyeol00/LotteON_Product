# 롯데온 클론 팀 프로젝트

## 시연 동영상 링크
<p align="left">
  <a href="https://youtu.be/gVVp2Rey7m4?si=Eac93dnpeyJEuUuo" target="_blank">
    <img alt="Watch Demo Video" src="https://img.shields.io/badge/YouTube-Demo%20Video-red?style=for-the-badge&logo=youtube&logoColor=white" height="28"/>
  </a>
</p>

# 아키텍처
![슬라이드1 JPG](https://github.com/user-attachments/assets/5ac367b3-e47c-44de-9337-653d1b920985)

# ERD
![image](https://github.com/user-attachments/assets/4d6dfaa7-49f6-484d-a287-c2b79c438ba6)


# ✅ 담당 역할 및 주요 기여
자세한 코드 리뷰 - https://meadow-thorium-fd0.notion.site/20d1c83ebcd980fe8e88febc0d827c76?source=copy_link

- **배포 책임자 역할**
  - AWS EC2 서버 배포 및 운영 자동화 (GitHub Actions CI/CD 파이프라인 구축)
  - 배포 과정 문제 해결 및 안정적인 서비스 운영 책임

- **프로젝트 일정 및 관리**
  - 노션(Notion)을 활용한 WBS(Work Breakdown Structure) 작성
  - 간트차트 기반 프로젝트 일정 관리 및 팀원 업무 분배 조율
  - 주간 회의 및 진행 상황 공유를 통한 일정 준수 및 리스크 관리


<br>

## 1️⃣ 상품 목록 페이지 - Redis를 이용한 캐싱처리, Ajax 비동기처리로 SPA 구현
![452882317-d38636c9-7f40-4905-a302-a50d83dfb258](https://github.com/user-attachments/assets/f5a3ad96-5419-4a11-832a-75d0409277f7)


롯데ON의 상품 목록 페이지는  
**카테고리별 베스트 상품(최근 3개월 판매량 TOP10)** 과  
**정렬 / 필터 / 토글 기능**을 최적화해 사용자 경험을 극대화했습니다.

-  **QueryDSL**로 복잡한 데이터를 제외하고 필요한 필드만 조회  
-  **Redis 캐시**로 초기 페이지 및 TOP10 인기 상품을 빠르게 응답  
-  **AJAX 비동기 처리**로 정렬/필터/페이지 전환을 새로고침 없이 자연스럽게 구현  
-  **URL 파라미터 관리**로 사용자가 선택한 뷰 상태를 일관되게 유지


###  사용 기술

| 기술 | 설명 |
|------|------|
| **QueryDSL** | 필요한 필드만 조회하여 **불필요한 데이터 전송 최소화** |
| **Redis 캐시** | 카테고리별 TOP10 상품을 캐싱해 **첫 페이지 응답 속도 향상** |
| **AJAX** | 정렬, 필터, 토글, 페이지 이동을 **비동기 처리로 자연스럽게 구현** |
| **URL 파라미터 관리** | 사용자가 선택한 뷰 상태(리스트/그리드)를 **다음 페이지에서도 유지** |


### ✅ 성과

- 정렬, 토글, 페이지 이동을 새로고침 없이 처리해 **몰입도 높은 UX 제공**
- Redis 캐시 + QueryDSL 최소 조회로 **초기 로딩 속도 향상**
- **선택한 뷰 상태와 정렬 방식이 유지**되어 **일관된 사용자 경험** 보장
- DB 조회 횟수 감소 및 통신 데이터 절감으로 **서버 부하 최적화**

<br><br>

## 2️⃣ 상품 상세 페이지  – AJAX 통합 UX, 쿠폰·장바구니 기능, Mixed Content 보안 대응
![상품상세보기-롯데On](https://github.com/user-attachments/assets/1294f908-3d68-4c3f-8600-b8acf88f3804)


롯데ON의 상품 상세 페이지는  
**상품 정보, 리뷰·문의·교환/반품, 쿠폰, 장바구니, 광고 기능을**  
**AJAX 기반 통합 UX**로 구성해, 새로고침 없는 몰입형 사용자 경험을 제공합니다.  
또한 `Spring Security` 인가 처리 및 `CSP 정책` 적용으로 **보안 이슈까지 선제 대응**했습니다.


###  사용 기술

| 기술 | 설명 |
|------|------|
| **QueryDSL** | 상품/리뷰/문의 등 통합 조회 시 필요한 필드만 선택해 DB 부하 절감 |
| **AJAX** | 리뷰·문의 정렬/페이징, 쿠폰 발급, 장바구니 담기 등 전체 기능 비동기 처리 |
| **Spring Security + Redirect** | `credentials: 'include'`로 인증 판단 후 비회원 리다이렉트 처리 |
| **CSP (`upgrade-insecure-requests`)** | HTTPS AJAX 차단 문제 해결 (Mixed Content 대응) |


### ✅ 성과 요약

- 하나의 페이지에서 **상품, 리뷰, 문의, 쿠폰, 장바구니 기능을 통합 제공**
- 모든 전환이 **AJAX 비동기 처리**로 UX 이탈 최소화 (정렬, 페이징, 모달)
- **로그인 후 원위치 복귀**로 비회원 이탈 방지
- **HTTPS 환경에서의 AJAX 문제(CSP)** 해결로 보안 신뢰성 확보
- 쿠폰 발급은 **유효기간, 중복 발급 여부 등 실제 커머스 상황에 맞춰 정교화**

<br><br>

## 3️⃣ 장바구니 기능 – 옵션 중복 방지, DTO 기반 구조화, 수량 조정/삭제 API 분리
![화면 캡처 2025-06-05 140635](https://github.com/user-attachments/assets/edf1a6e4-6ff4-48db-a5c5-8238a89314d0)


롯데ON의 장바구니 기능은  
**DTO 기반 옵션 구조화**와 **중복 옵션 확인 후 수량 증가 처리**를 통해  
사용자 경험과 유지보수성을 동시에 확보했습니다.  
Controller → Service → Repository 구조에서 **6개 옵션 필드 완전 일치 비교**로 중복을 방지하고,  
**수량 변경/삭제 API를 분리**해 일관된 기능 흐름을 제공합니다.


### 사용 기술

| 기술 | 설명 |
|------|------|
| **ItemRequestDTO** | 옵션 정보를 포함한 상품 요청 구조화 (최대 6개 옵션 Map 전달) |
| **Service 중복 체크 로직** | 동일 상품·옵션 조합은 수량만 증가 |
| **Repository 커스텀 쿼리** | `findByUserAndProductAndOptions()`로 옵션 6개 완전 일치 비교 |
| **Spring Security 인증** | `UserDetails` 기반 사용자 인증으로 비회원 접근 차단 |


### ✅ 성과 요약

- **동일 옵션 조합 중복 저장 방지** → UX 혼란 제거
- **DTO 기반 구조화**로 복잡한 옵션 처리에 유연하게 대응
- **수량 변경/삭제 API 분리** → 책임 분리 및 유지보수성 향상
- **인증 기반 접근 제어** → 보안 강화 및 개인화된 장바구니 UX 구현

<br><br>

## 4️⃣ 주문하기 – CartDTO 기반 통합 주문 흐름 (장바구니 & 바로 주문)
![452868523-fee4ac1b-5ce1-453e-833a-b574221baf8f](https://github.com/user-attachments/assets/f59cbc4e-8066-474b-83ff-58c80eb320f4)



롯데ON의 주문 기능은  
**CartDTO 하나로 장바구니 기반 주문과 바로 주문을 통합**해 처리하며,  
DB와 세션을 상황에 맞게 활용하여 유연한 주문 흐름을 제공합니다.  
장바구니 주문은 DB에서 Cart Entity를 조회하고,  
바로 주문은 ItemRequestDTO 기반으로 즉시 CartDTO를 생성하여 **세션에 저장**합니다.  
이를 통해 코드 중복을 줄이고, **이탈 후 복귀 시 주문 상태 복원 UX**를 구현했습니다.


### 사용 기술

| 기술 | 설명 |
|------|------|
| **CartDTO / ItemRequestDTO** | 주문 요청 구조 통일: 상품번호, 수량, 옵션 정보를 구조화 |
| **Controller 분리** | `/product/order` (장바구니), `/product/order/direct` (바로 주문) |
| **SRP 기반 Service 구조** | `ProductService`, `UserService`, `CouponIssueRepository` 분리 설계 |
| **DB vs Session 기반 처리** | 주문 방식에 따라 DB or 세션으로 주문 정보 저장 방식 구분 |


### ✅ 성과 요약

- `CartDTO` 기반 통합 구조로 **주문 흐름 일관성 및 재사용성 확보**
- 장바구니/바로 주문 간 **UX 분리 및 코드 통합 처리**
- 주문 도중 이탈해도 **세션 복원 처리로 사용자 편의성 향상**
- DTO 중심 설계로 **상품/쿠폰/유저 데이터의 관리 효율 증가**
- 기능별 서비스 책임 분리로 **확장성과 유지보수성 향상**
- DB/세션 이원화로 **서버 부하 분산 및 UX 안정성 확보**

<br><br>

## 5️⃣ 결제하기 – 카카오페이 연동, 트랜잭션 기반 주문 처리
![카카오페이 (1)](https://github.com/user-attachments/assets/a4615ad1-c551-4087-a7a7-a074830e590c)


롯데ON의 카카오페이 결제 기능은  
**장바구니 주문과 바로 주문을 하나의 흐름으로 통합**하고,  
`@Transactional` 기반 트랜잭션 처리로 **데이터 정합성을 보장**합니다.  
또한 `HttpSession`을 활용해 결제 중 이탈 상황에도 상태를 복원하며,  
외부 API 연동은 `RestTemplate` 기반의 **Service 레이어로 분리**하여 확장성과 안정성을 확보했습니다.



| 기술 | 설명 |
|------|------|
| **@Transactional** | 주문~결제 전 과정을 하나의 트랜잭션으로 처리하여 데이터 정합성 확보 |
| **HttpSession** | 주문번호, 결제금액, 장바구니 번호 등 핵심 데이터를 세션에 저장 |
| **RestTemplate** | 카카오페이 API 연동 – 결제 준비, 승인 요청 처리 |
| **서비스 분리 구조** | `OrderTransactionService`, `ProductOrderSubmitService`, `KakaoPayService` 로 기능 분리 |
| **ModelMapper** | Entity → DTO 변환으로 계층 간 의존성 최소화 |


### ✅ 성과

- **장바구니 주문과 바로 주문을 통합**하여 코드 일관성 및 재사용성 확보
- 트랜잭션 처리로 **재고 부족, 포인트/쿠폰 처리 실패 시 자동 롤백**
- **결제 이탈 후 복귀 시에도 상태 유지**, 사용자 경험(UX) 개선
- **외부 결제 API 호출 시점 명확화**, 결제 승인 성공 시에만 주문 상태 변경
- 포인트, 쿠폰, 재고, 상태 변경 등을 **단일 책임 메서드로 분리**하여 유지보수성 향상

