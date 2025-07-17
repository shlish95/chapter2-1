# 콘서트 예약 서비스 - 시스템 요구사항 및 설계 문서

## 1. 개요 (Overview)

- 본 문서는 콘서트 좌석 예약 시스템의 시나리오 흐름, 기능 요구사항, 설계 요소(시퀀스 다이어그램 및 ERD)를 문서화한 자료입니다.
- 주요 기능: 대기열 토큰 발급, 좌석 예약, 잔액 충전/조회, 결제 처리
- 시스템은 동시성 제어 및 다수 인스턴스 환경에서도 안정적으로 동작해야 합니다.

---

## 2. 시스템 요구사항 (Requirements)

### ✅ 기능 요약

| 구분 | 기능 | 설명 | API                                                                  |
|------|------|------|----------------------------------------------------------------------|
| 1️⃣ | 유저 대기열 토큰 API | 유저별 대기열 토큰을 발급하고 검증 | POST /queue-token                                                    |
| 2️⃣ | 잔액 충전 / 조회 API | 유저가 사전에 잔액을 충전하고 조회 가능 | POST /balance/charge <br> GET /balance/{userId}                      |
| 3️⃣ | 예약 가능 날짜 / 좌석 조회 API | 콘서트 예약 가능 날짜 및 좌석 리스트 제공 | GET /reservations/dates <br> GET /reservations/seats?date=YYYY-MM-DD |
| 4️⃣ | 좌석 예약 요청 API | 특정 좌석을 임시 배정 (5분간 점유) | POST /reservations                                                   |
| 5️⃣ | 결제 API | 임시 예약된 좌석을 결제 및 소유권 확정, 토큰 만료 처리 | POST /payments |

---

## 3. 시퀀스 다이어그램 (Sequence Diagram)

<details>
<summary>유저 토큰 발급 API</summary>

![시퀀스 다이어그램](/images/UserTokenIssue.png)

</details>

<details>
<summary>유저 토큰 검증 API</summary>

![시퀀스 다이어그램](/images/UserTokenVerification.png)

</details>

<details>
<summary>잔액 충전 및 조회 API</summary>

![시퀀스 다이어그램](/images/BalanceChargeAndCheck.png)

</details>

<details>
<summary>예약 가능 날짜 및 좌석 조회 API</summary>

![시퀀스 다이어그램](/images/AvailableDatesAndSeats.png)

</details>

<details>
<summary>좌석 예약 요청 API</summary>

![시퀀스 다이어그램](/images/SeatReservation.png)

</details>

<details>
<summary>결제 API</summary>

![시퀀스 다이어그램](/images/Payment.png)

</details>

---

## 4. ERD (Entity - Relationship Diagram)

![ERD](/images/ERD.png)