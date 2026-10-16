# SEO · AEO · GEO 점검표 근거 (2026-10-15 조사)

> 조사: 조사 전용 보조 AI 1명이 웹에서 직접 열어 확인(59건 열람 · 58건 사용). 확인 날짜 2026-10-15. Next.js 문서 · GitHub 파일은 원문 마크다운, 나머지는 요약 모델 경유. 작성자 쪽 세션이 표본 1건(Google 변경 이력 — FAQ 리치 결과 2026-05-07 중단 · llms.txt 불필요 2026-06-15)을 직접 대조해 일치 확인.

## 항목별 근거 요지

| 항목 | 공식이 말하는 것 | 출처 |
|---|---|---|
| E1 | robots는 숨기는 수단이 아님 — 숨기려면 noindex나 로그인 · robots로 막으면 noindex를 못 읽음 · 막힌 JS는 렌더링 안 됨 · Next.js 페이지의 robots는 레이아웃 값을 통째로 대체 | G1 G2 G3 G8 N1 N3 |
| E2 | 사이트맵은 발견을 도울 뿐 색인 보장 아님 · 약 500쪽 이하 · 내부 링크 충분하면 필수 아님 · priority · changefreq 무시 · lastmod는 검증 가능할 때만(Bing도 실제 수정 시각) · Next.js 예시는 `new Date()` | G4 G5 B1 N2 |
| E3 | 렌더링은 자원 여유가 있을 때 · 서버 측 렌더링은 여전히 좋은 방법 · metadata는 서버 컴포넌트에서만 · HTML만 읽는 봇에는 head에 블로킹 제공(네이버 Yeti 포함 — 원문 대조 필요) | G8 G9 N1 N4 N10 N11 |
| E4 | title은 페이지마다 고유 · 간결 · description은 고유가 도움 · keywords 메타 미사용 · template에는 default 필수 · metadata와 generateMetadata 동시 금지 | G24 G25 G27 N1 |
| E5 | canonical은 강한 신호 · 사이트맵은 약한 신호 · 절대 주소 · 서버 영구 리디렉션 | G6 G7 G13 N1 |
| E6 | JSON-LD 권장 · 보이는 내용과 일치 · 필수 속성 없으면 리치 결과 자격 없음 · 지원 유형 목록에 FAQ 없음(2026-05-07 중단 · 2026-06-15 문서 삭제) · `<` 이스케이프 | G17~G22 G35 N5 X1 |
| E7 | OG 필수 4개 · Google 대표 이미지 지정 절(2026-03) · og:image는 절대 주소 · openGraph는 통째로 대체 | X5 G23 N1 N4 |
| E8 | alt가 이미지 메타데이터 중 가장 중요 · "h1 하나" 규칙 없음 · Google은 lang 속성을 언어 판단에 안 씀 · WCAG 3.1.1은 html lang 요구 | G23 G10 G27 X3 G16 X4 G29 |
| E9 | href 있는 `<a>`만 안정적으로 링크 인식 · 중요한 페이지는 링크 1개 이상 · 설명형 앵커 · Next.js Link는 `<a href>` 출력 | G10 G8 G13 N9 |
| E10 | LCP 2.5초 · INP 200ms · CLS 0.1(75번째 백분위) · next/image · next/font | G26 X2 N7 N8 |
| E11 | 읽을 수 있는 단어 · 하이픈 · 세션 ID 금지 · 불필요한 파라미터 줄이기 · 한글 주소 가능(퍼센트 인코딩) | G11 |
| E12 | 공식 원문 못 엶 · IndexNow 참여 검색엔진에 Naver 포함 · Next.js verification은 google · yandex · yahoo · other | B5 N1 N11 |
| E13 · E14 | AI 개요 · AI 모드에 추가 요건 없음 · 생성형 검색 최적화 = 여전히 SEO · llms.txt 불필요 · 청킹 · AI 전용 문체 불필요 · 대량 생성은 스팸 소지 · GEO 논문(KDD 2024)은 실험 환경 한정 · llms.txt 채택과 인용 빈도 상관 없음(벤더 연구 · 추정) | G28~G31 G35 X6 X7 B2 B3 |
| E15 | 4xx는 색인 안 됨 · 200으로 빈 화면이면 소프트 404 · 서버 리디렉션 권장 · Next.js 스트리밍 시작 뒤 404는 200으로 남음 | G12 G9 G7 N6 |
| E16 | 페이지마다 고유 주소 · `<a href>` · rel=prev/next 미사용 · 첫 페이지를 canonical로 쓰지 말 것 | G13 N1 |
| E17 | `<img src>`만 찾음 · CSS 이미지는 색인 안 함 · 파일명 설명형 | G23 N2 |
| E18 | 서로 가리켜야 함 · x-default · 언어별 별도 주소 | G15 G16 N1 N2 |

## 출처 (Google 검색 센터 = `https://developers.google.com/search/docs/` 뒤 경로)

| ID | 내용 | 주소 | 갱신 표기 |
|---|---|---|---|
| G1 | robots.txt 소개 | `crawling-indexing/robots/intro` | 2025-12-10 |
| G2 | noindex | `crawling-indexing/block-indexing` | 2025-12-10 |
| G3 | robots meta · X-Robots-Tag | `crawling-indexing/robots-meta-tag` | 2026-03-24 |
| G4 | 사이트맵 개요 | `crawling-indexing/sitemaps/overview` | 2025-12-10 |
| G5 | 사이트맵 만들기 | `crawling-indexing/sitemaps/build-sitemap` | 2026-07-08 |
| G6 | 중복 URL · canonical | `crawling-indexing/consolidate-duplicate-urls` | 2026-07-10 |
| G7 | 리디렉션 | `crawling-indexing/301-redirects` | 2026-04-14 |
| G8 | JavaScript SEO 기본 | `crawling-indexing/javascript/javascript-seo-basics` | 2026-03-04 |
| G9 | JavaScript 검색 문제 해결 | `crawling-indexing/javascript/fix-search-javascript` | 2025-12-18 |
| G10 | 크롤링 가능한 링크 | `crawling-indexing/links-crawlable` | 2025-12-10 |
| G11 | URL 구조 | `crawling-indexing/url-structure` | 2025-12-10 |
| G12 | HTTP 상태 · 소프트 404 | `crawling-indexing/http-network-errors` | 2026-02-04 |
| G13 | 페이지네이션 | `specialty/ecommerce/pagination-and-incremental-page-loading` | 2025-12-10 |
| G15 | hreflang | `specialty/international/localized-versions` | 2026-09-21 |
| G16 | 다지역 사이트(lang 속성) | `specialty/international/managing-multi-regional-sites` | 2025-12-10 |
| G17 | 구조화 데이터 소개 | `appearance/structured-data/intro-structured-data` | 2025-12-10 |
| G18 | 지원 유형 목록 | `appearance/structured-data/search-gallery` | 2026-06-15 |
| G19 | 구조화 데이터 일반 지침 | `appearance/structured-data/sd-policies` | 2026-07-10 |
| G20 | Organization | `appearance/structured-data/organization` | 2026-09-08 |
| G21 | Event | `appearance/structured-data/event` | 2026-09-08 |
| G22 | LocalBusiness | `appearance/structured-data/local-business` | 2026-09-08 |
| G23 | 이미지 SEO(대표 이미지) | `appearance/google-images` | 2026-03-02 |
| G24 | title 링크 | `appearance/title-link` | 2025-12-10 |
| G25 | 스니펫 · description | `appearance/snippet` | 2026-04-20 |
| G26 | Core Web Vitals | `appearance/core-web-vitals` | 2025-12-10 |
| G27 | SEO 입문 가이드 | `fundamentals/seo-starter-guide` | 2025-12-10 |
| G28 | AI 기능과 웹사이트 | `appearance/ai-features` | 2025-12-10 |
| G29 | 생성형 AI 검색 최적화 가이드 | `fundamentals/ai-optimization-guide` | 2026-07-10 |
| G30 | 생성형 AI 콘텐츠 사용 | `fundamentals/using-gen-ai-content` | 2026-10-01 |
| G31 | 스팸 정책 | `essentials/spam-policies` | 2026-08-28 |
| G35 | 검색 문서 변경 이력 | https://developers.google.com/search/updates | 2026-10-08 |
| B1 | Bing: 사이트맵 · lastmod | https://blogs.bing.com/webmaster/2025/7/Keeping-Content-Discoverable-with-Sitemaps-in-AI-Powered-Search/ | 2025-07-31 |
| B2 | Bing: 그라운딩 · GEO | https://blogs.bing.com/search/February-2026/Elevating-the-Role-of-Grounding-on-the-AI-Web | 2026-02-12 |
| B3 | Bing: 인덱스의 역할 | https://blogs.bing.com/search/May-2026/Evolving-role-of-the-index-From-ranking-pages-to-supporting-answers | 2026-05-06 |
| B5 | IndexNow 참여 검색엔진 | https://www.indexnow.org/searchengines.json | |
| N1 | Next.js generateMetadata | https://nextjs.org/docs/app/api-reference/functions/generate-metadata | 2026-08-19 |
| N2 | Next.js sitemap | https://nextjs.org/docs/app/api-reference/file-conventions/metadata/sitemap | 2026-08-18 |
| N3 | Next.js robots | https://nextjs.org/docs/app/api-reference/file-conventions/metadata/robots | 2026-05-01 |
| N4 | Next.js Metadata · OG images | https://nextjs.org/docs/app/getting-started/metadata-and-og-images | 2026-08-25 |
| N5 | Next.js JSON-LD | https://nextjs.org/docs/app/guides/json-ld | 2026-03-02 |
| N6 | Next.js not-found | https://nextjs.org/docs/app/api-reference/file-conventions/not-found | 2026-10-06 |
| N7 | Next.js Images | https://nextjs.org/docs/app/getting-started/images | 2026-04-01 |
| N8 | Next.js Fonts | https://nextjs.org/docs/app/getting-started/fonts | 2026-05-27 |
| N9 | Next.js Link | https://nextjs.org/docs/app/api-reference/components/link | 2026-08-25 |
| N10 | Next.js htmlLimitedBots | https://nextjs.org/docs/app/api-reference/config/next-config-js/htmlLimitedBots | 2025-10-03 |
| N11 | Next.js 기본 HTML 제한 봇 목록(소스) | https://raw.githubusercontent.com/vercel/next.js/canary/packages/next/src/shared/lib/router/utils/html-bots.ts | |
| X1 | schema.org 시작 가이드 | https://schema.org/docs/gs.html | |
| X2 | web.dev Core Web Vitals | https://web.dev/articles/vitals | 2024-10-31 |
| X3 | web.dev 제목과 구역 | https://web.dev/learn/html/headings-and-sections | 2022-09-27 |
| X4 | WCAG 3.1.1 | https://www.w3.org/WAI/WCAG22/Understanding/language-of-page.html | |
| X5 | Open Graph | https://ogp.me/ | |
| X6 | GEO 논문(KDD 2024) | https://arxiv.org/abs/2311.09735 | 2024-06-28 |
| X7 | SE Ranking llms.txt 연구(벤더) | https://seranking.com/blog/llms-txt/ | 2025-11-07 |

못 연 것: 네이버 서치어드바이저 공식 가이드(도구가 사이트 접근 거부 — 5건) · 네이버 웹마스터도구 · Bing Webmaster Guidelines 본문 · 카카오톡 미리보기 문서 · 네이버 AI 브리핑 공식 안내(못 찾음).
