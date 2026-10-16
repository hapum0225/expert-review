# 개발 설계 점검표 근거 (2026-10-15 조사)

> 조사: 조사 전용 보조 AI 1명(파일 수정 불가)이 웹에서 직접 열어 확인. 확인 날짜는 모두 2026-10-15. Next.js · Vercel 페이지는 원문이 거의 그대로 왔고, PostgreSQL · Supabase · Fowler · Stripe 등의 인용은 요약 모델을 거쳤다 — 판정 전 원문 대조 권장.

## 항목별 근거 (요지)

| 항목 | 근거 요지 | 출처 |
|---|---|---|
| D1 | Next.js는 데이터 가져오기 방식을 하나로 정하고 섞지 말라 · 서버 전용 모듈에 모으면 권한 버그가 준다 | R26 |
| D2 | 서버 액션은 화면을 거치지 않고 POST로 직접 호출될 수 있다 · 페이지의 로그인 검사가 액션에 이어지지 않는다 · 입력과 소유권은 서버에서 확인 | R26 |
| D3 | 트랜잭션은 전부 되거나 전부 안 된다 · PL/pgSQL의 BEGIN/END는 트랜잭션이 아니다 · EXCEPTION 블록 밖 앞부분 변경은 남는다 | R1 · R7 · R8 · R12 |
| D4 | 기본 격리 수준의 동작 · FOR UPDATE · ON CONFLICT DO UPDATE의 원자성 · 부분 고유 인덱스 · CHECK는 다른 행을 못 본다 · SKIP LOCKED | R2~R6 · R9 |
| D5 | supabase-js는 던지지 않고 `{ data, error }`를 돌려준다 · 예상된 오류는 반환값, 예상 못 한 오류는 오류 경계 | R19 · R27 |
| D6 | 모든 변경은 마이그레이션 파일로 · 적용 이력 표 · 원격 직접 수정 금지 · 스테이징 분리 · 브랜치 | R11 · R13~R16 |
| D7 | 외래 키 기본 동작 NO ACTION · CASCADE · DB 백업에 Storage 파일 없음 · 개인정보 보호법 제21조(파기 · 분리 보관 — 원문 미열람, 2차 요약) | R5 · R18 · R20 |
| D8 | 테스트 피라미드 · 관찰 가능한 동작 시험 · pgTAP로 DB 함수 · RLS 시험 · CI에서 실행 · 부정 사례 시험 | R23 · R37 · R38 |
| D9a | 개발 · 운영 차이 줄이기 · Vercel 되돌리기는 환경 변수를 되돌리지 않음 | R14 · R16 · R32 · R34 |
| D9b | Vercel 크론은 재시도 없음 · 가끔 두 번 오거나 안 옴 · 겹쳐 돌 수 있음 · 시간대 UTC · Stripe 웹훅 중복 · 순서 비보장 · 토스 웹훅 재전송 최대 7회 | R30 · R31 · R43 · R44 |
| D10 | `NEXT_PUBLIC_`는 빌드 때 박힌다 · `.env*`는 저장소에 올리지 말 것 · service_role은 RLS를 우회하므로 브라우저 · 소스 관리 금지 | R21 · R28 · R33 |
| D11 | 조회 패턴에 맞춘 인덱스 · 실행 계획 · range()는 정렬 지정 필요 · N+1 공식 근거 없음 · 기본 1,000행 상한 공식 원문 미확인 | R16 · R17 · R24 · R25 |
| D12 | 증상 중심 알림 · 이메일 알림은 묻힌다 · 로그는 이벤트 스트림 · 비밀번호 · 토큰은 기록 금지 · error 전체 기록 | R19 · R30 · R35 · R36 · R41 |
| D13 | 기술 부채는 원금과 이자 · 자주 바뀌는 코드부터 | R39 |
| D14 | 결정 기록은 저장소에 · 뒤집힌 결정은 '대체됨' 표시 | R40 |
| D15 | 멱등 키로 재시도 안전 · 웹훅 중복 · 순서 · 원격 호출마다 시간 제한 · 겹겹 재시도는 부하를 키운다 | R30 · R42~R45 |
| D16 | 요금제별 백업 보존(Pro 7일 · Team 14일 · Enterprise 최대 30일) · 시점 복구는 별도 · Free는 백업 내려받기 불가 · Storage는 DB 백업에 없음 | R16 · R18 |
| D17 | timestamptz는 UTC로 저장하고 세션 시간대로 보여 준다 · Vercel 크론은 항상 UTC | R10 · R31 |
| D18 | 변경 뒤 revalidatePath · revalidateTag · 라우트의 dynamic · revalidate 설정(이전 캐시 모델 문서 — 버전 확인) | R29 |

## 출처

| 번호 | 내용 | 주소 |
|---|---|---|
| R1 | PostgreSQL 18 Transactions | https://www.postgresql.org/docs/current/tutorial-transactions.html |
| R2 | PostgreSQL 18 Transaction Isolation | https://www.postgresql.org/docs/current/transaction-iso.html |
| R3 | PostgreSQL 18 Explicit Locking | https://www.postgresql.org/docs/current/explicit-locking.html |
| R4 | PostgreSQL 18 INSERT (ON CONFLICT) | https://www.postgresql.org/docs/current/sql-insert.html |
| R5 | PostgreSQL 18 Constraints | https://www.postgresql.org/docs/current/ddl-constraints.html |
| R6 | PostgreSQL 18 Partial Indexes | https://www.postgresql.org/docs/current/indexes-partial.html |
| R7 | PostgreSQL 18 PL/pgSQL 구조 | https://www.postgresql.org/docs/current/plpgsql-structure.html |
| R8 | PostgreSQL 18 PL/pgSQL 제어 구조 | https://www.postgresql.org/docs/current/plpgsql-control-structures.html |
| R9 | PostgreSQL 18 SELECT 잠금 절 | https://www.postgresql.org/docs/current/sql-select.html |
| R10 | PostgreSQL 18 날짜/시간 타입 | https://www.postgresql.org/docs/current/datatype-datetime.html |
| R11 | PostgreSQL 위키 Transactional DDL(공식 문서 아님) | https://wiki.postgresql.org/wiki/Transactional_DDL_in_PostgreSQL:_A_Competitive_Analysis |
| R12 | Supabase Database Functions | https://supabase.com/docs/guides/database/functions |
| R13 | Supabase Database Migrations | https://supabase.com/docs/guides/deployment/database-migrations |
| R14 | Supabase Managing Environments | https://supabase.com/docs/guides/deployment/managing-environments |
| R15 | Supabase Branching | https://supabase.com/docs/guides/deployment/branching |
| R16 | Supabase Going into Prod | https://supabase.com/docs/guides/deployment/going-into-prod |
| R17 | Supabase Query Optimization | https://supabase.com/docs/guides/database/query-optimization |
| R18 | Supabase Backups | https://supabase.com/docs/guides/platform/backups |
| R19 | Supabase supabase-js 오류 다루기 | https://supabase.com/docs/guides/api/handling-errors-in-supabase-js |
| R20 | Supabase Cascade Deletes | https://supabase.com/docs/guides/database/postgres/cascade-deletes |
| R21 | Supabase API Keys | https://supabase.com/docs/guides/api/api-keys |
| R23 | Supabase Testing Overview (pgTAP) | https://supabase.com/docs/guides/local-development/testing/overview |
| R24 | Supabase Joins and Nesting | https://supabase.com/docs/guides/database/joins-and-nesting |
| R25 | Supabase JS range() | https://supabase.com/docs/reference/javascript/range |
| R26 | Next.js Data Security (2026-10-06 갱신) | https://nextjs.org/docs/app/guides/data-security |
| R27 | Next.js Error Handling (2026-10-06) | https://nextjs.org/docs/app/getting-started/error-handling |
| R28 | Next.js Environment Variables (2026-08-25) | https://nextjs.org/docs/app/guides/environment-variables |
| R29 | Next.js Caching(이전 모델 · 2026-08-18) | https://nextjs.org/docs/app/guides/caching |
| R30 | Vercel Managing Cron Jobs (2026-08-11) | https://vercel.com/docs/cron-jobs/manage-cron-jobs |
| R31 | Vercel Cron Jobs (2026-09-16) | https://vercel.com/docs/cron-jobs |
| R32 | Vercel Instant Rollback (2026-07-07) | https://vercel.com/docs/instant-rollback |
| R33 | 12-Factor Config | https://12factor.net/config |
| R34 | 12-Factor Dev/prod parity | https://12factor.net/dev-prod-parity |
| R35 | 12-Factor Logs | https://12factor.net/logs |
| R36 | Google SRE Book Ch.6 | https://sre.google/sre-book/monitoring-distributed-systems/ |
| R37 | Fowler/Vocke Practical Test Pyramid (2018) | https://martinfowler.com/articles/practical-test-pyramid.html |
| R38 | Fowler Test Pyramid (2012) | https://martinfowler.com/bliki/TestPyramid.html |
| R39 | Fowler Technical Debt (2019) | https://martinfowler.com/bliki/TechnicalDebt.html |
| R40 | Nygard Documenting Architecture Decisions (2011) | https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions |
| R41 | OWASP Logging Cheat Sheet | https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html |
| R42 | Stripe Idempotent requests | https://docs.stripe.com/api/idempotent_requests |
| R43 | Stripe Webhooks | https://docs.stripe.com/webhooks |
| R44 | 토스페이먼츠 웹훅 연결하기 | https://docs.tosspayments.com/guides/v2/webhook |
| R45 | AWS Timeouts, retries, and backoff with jitter (2019) | https://builder.aws.com/content/3EumjoZascWd1oZiEgL8ORlv3qE/timeouts-retries-and-backoff-with-jitter |

못 연 것 · 근거를 못 찾은 것: PostgREST 공식 문서(429 — "호출 하나 = 트랜잭션 하나"는 2차 자료뿐), 개인정보 보호법 제21조 원문, Supabase 기본 1,000행 상한 원문, N+1 · "기대값을 대상 코드로 만들기"의 1차 근거, 토스 웹훅 중복 · 서명 · 순서 규정.
