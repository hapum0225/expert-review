# 보안 점검표 근거 (2026-10-15 조사)

> 조사: 조사 전용 보조 AI 1명이 웹에서 직접 열어 확인(약 45쪽). 확인 날짜 2026-10-15. Next.js · Vercel 문서는 원문, 나머지는 요약 모델 경유. 작성자 쪽 세션이 표본 1건(Supabase Next.js 서버 쪽 인증 — "서버 코드에서 getSession()을 믿지 말고 getClaims()를 쓰라")을 직접 대조해 일치 확인.

## 항목별 근거 요지

| 항목 | 근거 요지 | 출처 |
|---|---|---|
| S1 | RLS 없는 테이블은 grant가 있는 모든 롤이 읽고 쓴다 · SQL Editor 등으로 만든 테이블은 RLS가 자동으로 켜지지 않는다 · 뷰는 RLS를 우회 | R1 R9 R12 R14 R25 |
| S2 | using = 기존 행 · with check = 쓰기 후 행 · update는 둘 다 · user_metadata는 사용자가 고칠 수 있어 정책 근거 금지 | R1 R9 R10 |
| S3 | secret 키는 RLS 우회 · 브라우저 · 저장소 · URL · 로그 금지 · `NEXT_PUBLIC_`은 번들에 박힘 · 구키 이름은 2026년 말 폐기 예정, 신키 `sb_secret_` | R2 R19 R18 |
| S4 | 서버 액션은 직접 POST로 호출 가능 · 페이지 인증이 액션에 이어지지 않음 · getSession()을 믿지 말고 getClaims() | R6 R18 R20 R25 R26 R27 |
| S5 | search_path 고정 · pg_temp 마지막 · 기본으로 PUBLIC 실행 가능 → revoke · 본문에서 소유 확인 | R3 R9 R10 R24 |
| S6 | 액션 안에서 관리자 재확인(ASVS 8.3.1 L1) · 다층 방어(8.4.2 L3) | R10 R18 R27 |
| S7 | 매개변수화 · 이름은 허용 목록 · 서버 검증 · dangerouslySetInnerHTML은 신뢰 데이터만 · `.or()` 공식 경고는 못 찾음 | R18 R20 R25 R27 R29 |
| S8 | 운영은 정확한 리디렉트 경로(`**`는 개발용) · 외부 리디렉트 허용 목록 · 세션 쿠키 응답 캐시 경고 | R5 R6 R27 R28 |
| S9 | 비공개 버킷 보호는 storage.objects 정책 · 공개 버킷 넓은 SELECT = 목록 노출 · 크기 · 형식 제한 · 서버가 만든 파일명 | R4 R10 R11 R17 R27 R28 |
| S10 | 필요한 필드만 담은 DTO · 서버 액션도 행 통째 반환 금지 · 객체 · 필드 단위 접근 제한 | R1 R13 R18 R26 R27 |
| S11 | `.env`는 `.gitignore` · 키 유출 시 교체 순서 · 비밀을 소스 · 빌드 산출물에 넣지 않음(ASVS 13.3.1) | R2 R19 R27 |
| S12 | Supabase 기본 한도(가입 · 로그인 IP당 5분 30회 등 · 요약값) · CAPTCHA · ASVS 6.3.1(L1) | R7 R8 R14 R18 R25 R27 |
| S13 | Vercel CRON_SECRET → Authorization 헤더 비교 · Edge Function은 JWT 검증 기본, 웹훅은 서명 직접 검증 | R16 R23 |
| S14 | OWASP A03:2025 공급망 · npm audit은 네트워크 필요 · Next.js RSC 취약점 실례(CVE-2025-66478) · 2026-10 긴급 업데이트 예고(수정 버전 미확인) | R21 R22 R25 R30 |
| S15 | Next.js 서버 액션은 Origin/Host 비교로 보호, route.ts는 직접 · ASVS 3.5.x(L1) · 상태 변경 GET 금지 | R18 R20 R25 R27 R28 |
| S16 | OWASP A01 · API7:2023 · ASVS 1.3.6(L2) · 허용 목록 · 리디렉트 끔 · DNS 재바인딩 | R25 R26 R27 R28 |
| S17 | OWASP A05 · ASVS 1.2.5 · 1.3.2 · 5.3.2(L1) | R25 R27 |
| S18 | OWASP A02 · A10 · ASVS 16.5.1(L2) · 운영 모드에선 오류 메시지가 해시로 바뀌지만 개발 모드는 평문 | R20 R25 R27 R28 |
| S19 | 갱신된 세션의 Set-Cookie 응답이 캐시되면 다른 사람으로 로그인됨 · 요청 값은 매번 재확인 | R6 R20 |
| S20 | ASVS 13.4.2 · 13.4.5(L2) · OWASP A02 | R25 R27 |

## 행안부 49항 대조 (요약 — 번호는 2차 자료 나열 순서로 붙인 것)

- **S1~S14가 이미 다룸**: 1-1 SQL 삽입(S7) · 1-4 XSS(S7) · 1-6 위험한 파일 업로드(S9) · 1-7 신뢰되지 않는 URL 자동 연결(S8) · 1-15 보안 결정에 쓰이는 부적절한 입력값(S4 · S6) · 2-1 인증 없는 중요 기능(S4 · S6 · S13) · 2-2 부적절한 인가(S1 · S2 · S4 · S6) · 2-3 잘못된 권한 설정(S1 · S2 · S5 · S9) · 2-6 하드코드된 중요정보(S11) · 2-16 인증 시도 제한(S12) · 5-5 역직렬화(S14) · 7-2 취약한 API(S14).
- **이번에 추가(S15~S20)**: 1-11 CSRF · 1-12 SSRF · 1-2 · 1-3 · 1-5 코드 · 경로 · 명령 삽입 · 4-1~4-3 오류 처리 · 6-1 세션 데이터 노출 · 6-2 · 2-13 디버그 코드 · 주석 속 정보.
- **해당 기능이 있을 때만**: 2-5 · 2-8 · 2-9 · 3-1.
- **이 규모에 해당 없음 · 낮음**: XML 계열(1-8 · 1-9) · LDAP(1-10) · HTTP 응답분할(1-13) · 정수 오버플로(1-14) · 메모리(1-16 · 1-17 · 5-1~5-4) · 약한 암호 · 키 길이 · 해시 직접 구현(2-4 · 2-7 · 2-14) · 인증서 검증(2-11) · 코드 다운로드 무결성(2-15) · 무한 반복(3-2) · Java류 배열(6-3 · 6-4) · DNS 기반 결정(7-1).
- iron-laws 저장소의 공개 오탐률은 범주별 0.0%~65.1%(SQL 삽입 41.8% · 경로 조작 50.4%) — 판정 근거로 쓰지 않음.

## 출처

| 번호 | 내용 | 주소 |
|---|---|---|
| R1 | Supabase Row Level Security | https://supabase.com/docs/guides/database/postgres/row-level-security |
| R2 | Supabase API keys | https://supabase.com/docs/guides/api/api-keys |
| R3 | Supabase Database Functions | https://supabase.com/docs/guides/database/functions |
| R4 | Supabase Storage access control | https://supabase.com/docs/guides/storage/security/access-control |
| R5 | Supabase Redirect URLs | https://supabase.com/docs/guides/auth/redirect-urls |
| R6 | Supabase Auth Next.js server-side | https://supabase.com/docs/guides/auth/server-side/nextjs |
| R7 | Supabase Auth rate limits | https://supabase.com/docs/guides/auth/rate-limits |
| R8 | Supabase Auth CAPTCHA | https://supabase.com/docs/guides/auth/auth-captcha |
| R9 | Supabase Database advisors(린트) | https://supabase.com/docs/guides/database/database-advisors |
| R10 | Supabase 린트 0015 · 0011 · 0025 | https://supabase.com/docs/guides/database/database-linter?lint=0015_rls_references_user_metadata |
| R11 | Supabase Storage buckets | https://supabase.com/docs/guides/storage/buckets/fundamentals |
| R12 | Supabase Securing your Data API | https://supabase.com/docs/guides/api/securing-your-api |
| R13 | Supabase Column level security | https://supabase.com/docs/guides/database/postgres/column-level-security |
| R14 | Supabase Production checklist | https://supabase.com/docs/guides/deployment/going-into-prod |
| R15 | Supabase Password security | https://supabase.com/docs/guides/auth/password-security |
| R16 | Supabase Edge Functions auth | https://supabase.com/docs/guides/functions/auth |
| R17 | Supabase JS createBucket | https://supabase.com/docs/reference/javascript/storage-createbucket |
| R18 | Next.js Data Security (2026-10-06) | https://nextjs.org/docs/app/guides/data-security |
| R19 | Next.js Environment Variables (2026-08-25) | https://nextjs.org/docs/app/guides/environment-variables |
| R20 | Next.js 블로그 How to Think About Security (2023) | https://nextjs.org/blog/security-nextjs-server-components-actions |
| R21 | Next.js 보안 공지 CVE-2025-66478 (2025-12-03) | https://nextjs.org/blog/CVE-2025-66478 |
| R22 | Next.js 보안 업데이트 예고 2건 (2026-09-22 · 2026-10-08) | https://nextjs.org/blog/upcoming-nextjs-security-update-october-2026 |
| R23 | Vercel Managing Cron Jobs | https://vercel.com/docs/cron-jobs/manage-cron-jobs |
| R24 | PostgreSQL CREATE FUNCTION | https://www.postgresql.org/docs/current/sql-createfunction.html |
| R25 | OWASP Top 10:2025 | https://top10.owasp.org/2025/ |
| R26 | OWASP API Security Top 10 2023 | https://api-security.owasp.org/editions/2023/en/0x11-t10 |
| R27 | OWASP ASVS 5.0.0 | https://github.com/OWASP/ASVS/tree/v5.0.0/5.0/en |
| R28 | OWASP 치트시트(리디렉트 · 업로드 · SSRF · CSRF · 오류 처리) | https://cheatsheetseries.owasp.org/ |
| R29 | React dangerouslySetInnerHTML | https://react.dev/reference/react-dom/components/common |
| R30 | npm audit | https://docs.npmjs.com/cli/v10/commands/npm-audit |
| R31 | 행정안전부 「소프트웨어 개발보안 가이드」 게시글(2021.11.30) | https://www.mois.go.kr/frt/bbs/type001/commonSelectBoardArticle.do?bbsId=BBSMSTR_000000000015&nttId=88956 |
| R32 | 49항 목록(2차 자료 · 개인 블로그) | https://sisw.com/entry/KISA-%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4-%EB%B3%B4%EC%95%88%EC%95%BD%EC%A0%90-%EA%B8%B0%EC%A4%80 |
| R33 | itwiki Secure SDLC(유형별 개수) | https://itwiki.kr/w/Secure_SDLC |
| R34 | 보안클라우드 2021.11 개정 통폐합 · 신규 | https://boancloud.co.kr/secure-coding/2/ |
| R35 | iron-laws README · ACCURACY(이름 · 분류만) | https://github.com/JinHo-von-Choi/iron-laws |

못 연 것: 행안부 가이드 PDF · hwp 원문(열람 도구 오류 — 49항 이름은 2차 자료) · KISA 자료실(인증서 오류) · Next.js 2026-10 긴급 업데이트 본문(수정 버전) · Supabase `.or()` 필터 경고 · PostgREST 문서.
