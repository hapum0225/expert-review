# 마케팅 점검표 근거 (2026-10-15 조사)

> 조사: 조사 전용 보조 AI 1명(파일 수정 불가)이 웹에서 직접 열어 확인. 확인 날짜는 모두 2026-10-15. 열람 도구가 요약 모델을 거치므로 문장은 "원문 그대로"가 아니다 — 법령 조문 · 시행일은 점검표를 판정에 쓰기 전 원문 대조를 권한다.
> 판정에 볼 파일은 Next.js 류 구조 기준의 예상 위치다.

## 항목별 근거

| 항목 | 왜 중요한가 | 근거(아래 번호) | 판정에 볼 파일 | 판정 못 하는 부분 |
|---|---|---|---|---|
| M1 | 첫 10초 안에 가치가 안 보이면 이탈이 가장 많다 | S2 · S8 · S1 | 랜딩 `app/page.tsx` · hero의 h1 · 부제 · 첫 문단 | 실제 방문자가 이해하는지 · 첫 화면에 들어오는지(렌더링 필요) |
| M2 | 대상이 불분명하면 "나와 상관없다"고 떠난다 | S5 · S8 | 랜딩 문구 · 소개 페이지 · 안내문 | 시장 적합성 |
| M3 | 모호한 버튼은 클릭은 늘려도 목표 달성을 해친다 | S5 · S8 | 버튼 컴포넌트 · 이동 대상 · 신청 페이지 제목 | 실제 눈에 띄는지 · 클릭률 |
| M4 | 폼 칸이 많을수록 사용성이 나빠진다(결제 폼 연구 — 가입 폼 적용은 추론) | S9 · S4 | 폼 컴포넌트 · 서버 검증 스키마 · `required` | 사업상 꼭 필요한 칸 · 실제 이탈률 |
| M5 | 라벨 없는 폼은 실패 · 이탈을 부르고 접근성 기준에 걸린다 | S10 · S11 · S12 · S13 · S4 | 폼의 `label` · `autocomplete` · 버튼 CSS | 화면 읽기 도구 동작 · 대비 수치 · 법적 의무 여부 |
| M6 | 허위 · 기만 후기는 법 위반이고, 외부 근거가 없으면 신뢰가 떨어진다 | S20 · S18 · S19 · S3 · S1 | 후기 · 실적 컴포넌트 · 수치 하드코딩 위치 · 안내문 | 후기 · 수치의 진위 · 실증 자료 보유 |
| M7 | 대가를 숨긴 추천은 기만 광고다(2026-06-01부터 AI 가상인물 포함) | S15 · S16 · S17 | 추천 인용 블록 · 제휴 링크 · AI 생성 인물 · 안내문 | 실제 대가 여부 · 표시의 시각 효과 |
| M8 | 근거 없는 최상급 · 효과 단정은 거짓 · 과장 광고 | S20 · S19 (최상급 전용 기준 문서는 못 찾음) | 랜딩 · 소개 · 메타데이터 문구 · 안내문 | 근거 자료 보유 · 위법 최종 판단 |
| M9 | 가격 · 조건이 늦게 보이면 신뢰를 잃고, 일부 방식은 다크패턴 규제 대상 | S30 · S27 · S28 · S3 · S5 | 가격 · 신청 페이지 · 기본 체크 상태(`defaultChecked`) · 취소 경로 | 통신판매업 해당 여부 · 실제 청구액 · 가격 적정성(평가 안 함) |
| M10 | 신청 전 걱정을 풀어 주면 이탈이 줄고 신뢰가 오른다(지어낸 질문 금지) | S6 · S3 | FAQ 컴포넌트 · 안내문 | 실제 방문자 질문과 맞는지 |
| M11 | 필수/선택 구분과 동의 방법을 어기면 법 위반 | S22 · S23 | 폼 체크박스 · 수집 필드 · 처리방침 페이지 · 저장 스키마 | 실제 보관 · 파기 운영 · 14세 미만 이용자 여부 |
| M12 | 광고 수신은 사전 동의가 원칙이고 형식이 법에 있다 | S26 (KISA 안내는 인증서 오류로 못 열음) | 가입 폼 체크박스 · 메일 템플릿 푸터 · 수신거부 링크 | 실제 발송 시간 · 동의 기록 보관 |
| M13 | 전환을 못 재면 개선을 판단할 수 없고, 분석 도구는 고지 대상 | S14 · S24 · S25 · S22 | 분석 스크립트 위치(`layout.tsx` · `next/script`) · 폼 제출 성공 이벤트 · 처리방침 | 대시보드에 실제로 잡히는지 · 개인 식별 여부 |
| M14 | 약속이 어긋나면 신뢰를 잃고, 사실을 숨기면 기만 표시 | S5 · S20 · S18 | 랜딩 · 가격 · 신청 페이지 · `metadata` 문구 · 안내 메일 | 외부로 이미 나간 문구 · 미리보기 캐시 |
| M15 | 첫 화면 밖은 시선이 급감(데스크톱 연구 — 모바일은 추론) | S7 · S5 | hero CSS(`min-h-screen` · 큰 이미지) · 반응형 클래스 | 실제 기기 화면 |
| M16 | 문의 길이 없으면 신뢰를 잃고, 판매 서비스는 표시 의무 | S3 · S8 · S30 · S29 · S31 · S33 | 푸터 · 소개 · 문의 페이지 · 사업자 정보 블록 | 통신판매업 신고 · 적용 대상 여부 · 응대 속도 |

## 출처 (열어서 확인한 것)

| 번호 | 내용 | 주소 | 비고 |
|---|---|---|---|
| S1 | Google 유용한 콘텐츠 지침 | https://developers.google.com/search/docs/fundamentals/creating-helpful-content | 최종 갱신 2026-10-05 표시 |
| S2 | NN/g How Long Do Users Stay on Web Pages? | https://www.nngroup.com/articles/how-long-do-users-stay-on-web-pages/ | 2011-09-11 |
| S3 | NN/g Trustworthiness in Web Design | https://www.nngroup.com/articles/trustworthy-design/ | 2016-05-08 |
| S4 | NN/g Website Forms Usability | https://www.nngroup.com/articles/web-form-design/ | 2016-05-01 |
| S5 | NN/g "Get Started" Stops Users | https://www.nngroup.com/articles/get-started/ | 2017-08-20 |
| S6 | NN/g FAQs Still Deliver Great Value | https://www.nngroup.com/articles/faqs-deliver-value/ | 2014-12-21 |
| S7 | NN/g Scrolling and Attention | https://www.nngroup.com/articles/scrolling-and-attention/ | 2018-04-15 |
| S8 | NN/g 113 Design Guidelines for Homepage Usability | https://www.nngroup.com/articles/113-design-guidelines-homepage-usability/ | 발행일 미확인 |
| S9 | Baymard Minimize Form Fields | https://baymard.com/blog/checkout-flow-average-form-fields | 2024-06-26 · 결제 폼 대상 |
| S10 | W3C WCAG 2.2 | https://www.w3.org/TR/WCAG22/ | 권고 2024-12-12 · 앞부분만 열람 |
| S11 | WCAG 2.5.8 대상 크기(최소) | https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html | |
| S12 | WCAG 3.3.2 라벨 · 안내 | https://www.w3.org/WAI/WCAG22/Understanding/labels-or-instructions.html | |
| S13 | WCAG 3.3.7 중복 입력 | https://www.w3.org/WAI/WCAG22/Understanding/redundant-entry.html | |
| S14 | GA4 About key events | https://support.google.com/analytics/answer/9267568 | |
| S15 | 추천 · 보증 등에 관한 표시 · 광고 심사지침(공정위 예규 제499호) | https://www.law.go.kr/LSW/admRulInfoR.do?admRulSeq=2100000280130 | 시행 2026-06-01 · 경제적 이해관계 표시 부분만 확인 |
| S16 | 공정위 보도: 추천 · 보증 심사지침 개정(AI 가상인물) | https://www.ftc.go.kr/www/selectBbsNttView.do?pageUnit=10&pageIndex=1&searchCnd=all&key=12&bordCd=3&searchCtgry=01%2C02&nttSn=47547 | 2026-05-29 |
| S17 | 공정위 보도: 경제적 이해관계 표시 안내서 개정본 | https://www.ftc.go.kr/www/selectBbsNttView.do?pageUnit=10&pageIndex=1&searchCnd=all&key=12&bordCd=3&searchCtgry=01%2C02&nttSn=46709 | 2025-12-02 · 첨부 본문 미열람 |
| S18 | 공정위 보도: 기만적 표시 · 광고 심사지침 개정 | https://www.ftc.go.kr/www/selectBbsNttView.do?key=12&bordCd=3&nttSn=46562 | 2025-10-30 · 지침 원문 미열람 |
| S19 | 공정위 보도: 표시 · 광고 실증 운영고시 개정 | https://www.ftc.go.kr/www/selectBbsNttView.do?bordCd=3&key=12&nttSn=47957&searchCtgry=01%2C02 | 시행 2026-09-03 |
| S20 | 표시광고법 제3조 | https://www.law.go.kr/LSW/lsLawLinkInfo.do?lsJoLnkSeq=900554254&chrClsCd=010202 | 시행 2025-01-21 |
| S22 | 개인정보 보호법 제15 · 22 · 22의2 · 30조 | https://law.go.kr/LSW/lsLinkCommonInfo.do?ancYnChk=&chrClsCd=010202&lsJoLnkSeq=1016155549 (제22조 · 나머지 조문 링크는 조사 보고 원문) | 시행 2026-09-11 |
| S23 | 개인정보위 보도: 필수동의 관행 개선 | https://www.pipc.go.kr/np/cop/bbs/selectBoardArticle.do?bbsId=BS074&mCode=C020010000&nttId=10566 | 2024-09-12 |
| S24 | 개인정보위 보도: 행태정보 처리 정책 | https://www.pipc.go.kr/np/cop/bbs/selectBoardArticle.do?bbsId=BS074&mCode=C020010000&nttId=9888 | 2024-01-31 |
| S25 | 개인정보 처리방침 작성지침(2026.4 개정) 안내 | https://pipc.go.kr/np/cop/bbs/selectBoardArticle.do?bbsId=BS217&mCode=D010030000.Updated&nttId=12018 | 본문 PDF 미열람 |
| S26 | 정보통신망법 제50조(광고성 정보 전송 제한) | https://www.law.go.kr/LSW/lsLawLinkInfo.do?chrClsCd=010202&lsJoLnkSeq=1000688185&lsId=000030 | 시행 2026-10-02 |
| S27 | 공정위 보도: 전자상거래 소비자보호 지침 개정(다크패턴 6유형) | https://www.ftc.go.kr/www/selectBbsNttView.do?key=12&bordCd=3&nttSn=46527 | 시행 2025-10-24 |
| S28 | 공정위 보도: 다크패턴 모니터링 · 시정사례 | https://www.ftc.go.kr/www/selectBbsNttView.do?key=12&bordCd=3&nttSn=46476 | 2025-09-30 |
| S29 | 전자상거래법 제12조(통신판매업 신고) | https://law.go.kr/LSW/lsLinkCommonInfo.do?ancYnChk=&chrClsCd=010202&lsJoLnkSeq=1010186921 | 시행 2026-07-21 |
| S30 | 전자상거래법 제13조 · 제17조 | https://www.law.go.kr/LSW//lsLawLinkInfo.do?lsJoLnkSeq=1000527501&lsId=009318&chrClsCd=010202&print=print | 시행 2026-07-21 |
| S31 | 공정위 결정문(제10조 · 시행규칙 제7조 인용) | https://www.law.go.kr/LSW/ftcInfoP.do?ftcSeq=2001 | 2019 · 현행 조문 직접 확인 아님 |
| S33 | 공정위 통신판매업 등록현황 | https://www.ftc.go.kr/www/contents.do?key=5375 | |

못 연 것 · 못 찾은 것: NN/g value-prop · cta-buttons(404), KISA 광고성 정보 안내(인증서 오류), 공정위의 최상급 표현 전용 기준, 한국어 가입 폼 연구, 전자상거래법 제10조 본문.
