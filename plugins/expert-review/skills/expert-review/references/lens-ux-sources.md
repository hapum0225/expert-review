# 렌즈 UX/UI(X) — 항목별 근거 (v0.3 · 2026-11-12)

> 공개판 근거 파일. 작성자 쪽 판본은 비공개 작업 문서(Norman · Nielsen · 시각 디자인 원칙을 요약한 내부 디자인 원칙 문서와 첫 적용 프로젝트의 화면 게이트)를 함께 인용한다 — 공개판에는 그 문서들이 요약한 공개 원전만 적었다.
> 2026-11-11: WCAG 2.2(W3C 권고안 2024-12-12)와 NN/g 10원칙(2024-01-30 검토판) 페이지를 열어 번호 · 제목 · 등급을 대조했다(WCAG 조문 문장은 페이지 요약으로 확인 · 원문 문장 대조 전). Apple HIG · Material 페이지는 열었으나 본문이 읽히지 않아 수치는 미확인이다.

| 항목 | 출처 | 등급 판단 |
|---|---|---|
| X1 위계의 수단 · 화면별 순위 | 시각 디자인 원칙(구조 → 여백 → 글자 → 색 순서 · 색만으로 위계를 해결하지 않는다) — 내부 원칙 문서 요약 · 공개 원전 단일 문서 없음 · 화면별 순위 2~3단(먼저 볼 것 · 다음 할 일 · 필요할 때만 찾는 것)은 정리 예시 — 공개 원전 미대조라 추정 · 참고만 | 추정(작성자 설계 기준 — 독립된 공개 원전 미대조 · 대상 프로젝트가 채택했으면 그 규칙으로) |
| X2 글자 크기 사다리 | 같은 원칙 · 모바일 본문 14px 하한은 플랫폼 관행(공식 하한 수치 원문 미확인) | 추정(작성자 설계 기준 · 프로젝트 타입 스케일이 있으면 그 규칙) |
| X3 묶음과 들여쓰기 | 게슈탈트 근접성(Nielsen Norman Group 글 — 원문 미열람) | 방향성 |
| X4 행 구분 | 시각 디자인 원칙(조회 · 모니터링 화면은 정렬과 열 구조) | 추정(작성자 설계 기준 — 독립된 공개 원전 미대조 · 대상 프로젝트가 채택했으면 그 규칙으로) |
| X5 라벨 열 정렬 | 같은 원칙 | 추정(작성자 설계 기준 — 독립된 공개 원전 미대조 · 대상 프로젝트가 채택했으면 그 규칙으로) |
| X6 발견가능성 | Don Norman, *The Design of Everyday Things*(발견가능성 · 원문 미열람) | 방향성 |
| X7 피드백 | NN/g 10원칙 1 Visibility of System Status(https://www.nngroup.com/articles/ten-usability-heuristics/ · 2026-11-11 열람) · Norman 피드백 | 방향성 |
| X8 표식 | Norman Affordance / Signifier | 방향성 |
| X9 매핑 | Norman Mapping | 방향성 |
| X10 오류 예방 | NN/g 10원칙 5 Error Prevention · Norman 제약 | 방향성 |
| X11 오류 복구 | NN/g 10원칙 9 Help Users Recognize, Diagnose, and Recover from Errors | 방향성 |
| X12 재인 | NN/g 10원칙 6 Recognition Rather than Recall | 방향성 |
| X13 일관성 | NN/g 10원칙 4 Consistency and Standards | 방향성 |
| X14 상태 7종 | 시각 디자인 원칙(필수 검토 상태: empty · loading · success · error · disabled · partial · edge case) | 추정(작성자 설계 기준 — 독립된 공개 원전 미대조 · 대상 프로젝트가 채택했으면 그 규칙으로) |
| X15 색 단독 구분 금지 | WCAG 2.2 SC 1.4.1 Use of Color(A) — https://www.w3.org/TR/WCAG22/ · 2026-11-11 대조 | 확립(표준) |
| X16 터치 · 간격 | WCAG 2.2 SC 2.5.8 Target Size (Minimum)(AA) 24×24 CSS px · 예외 5종(간격 · 동등 조작 · 인라인 · 사용자 에이전트 · 필수) — 2026-11-11 대조 · W3C 이해 문서 https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html · Apple HIG 44×44pt · Material 48×48dp(원문 본문 읽기 실패 · 미확인) | 확립(24px · 예외 포함) · 추정(44/48 — 원문 확인 전 판정 근거로 쓰지 않음) |
| X17 좁은 화면 | 시각 디자인 원칙(반응형 · 320 · 390 · 1280 너비 확인 관행) | 추정(작성자 설계 기준 — 독립된 공개 원전 미대조 · 대상 프로젝트가 채택했으면 그 규칙으로) |
| X18 보이스 | NN/g 10원칙 2 Match Between the System and the Real World · 대상 프로젝트의 말투 규칙(있을 때) · 장식용 이모지 아이콘 = unslop 신호(Icons) · Hallmark Floor 11 — 두 곳 다 한 곳 자료 | 방향성(사용자 언어) · 확립(프로젝트 규칙이 있을 때 — 말투 혼용 · 이모지는 규칙이 있을 때만 결함) |
| X19 화면 비노출 | 대상 프로젝트 규칙(CLAUDE.md · AGENTS.md · 디자인 가이드의 비노출 목록) · 규칙이 없을 때 = 개인정보 최소 노출 원칙 | 확립(확인된 프로젝트 규칙) · 추정(규칙 · 허용 범위 미확인 시) |
| X20 접근성 기본 | WCAG 2.2 SC 1.3.1 Info and Relationships(A) · 1.4.3 Contrast (Minimum)(AA) 4.5:1 · 큰 글자 3:1 · 2.1.1 Keyboard(A) · 2.2.2 Pause, Stop, Hide(A) · 2.4.7 Focus Visible(AA) · 3.3.2 Labels or Instructions(A) · 2.3.3 Animation from Interactions(AAA) — 2026-11-11 대조 · `prefers-reduced-motion`은 충족 방법 중 하나(W3C 기법 C39 https://www.w3.org/WAI/WCAG22/Techniques/css/C39 · 이해 문서 https://www.w3.org/WAI/WCAG22/Understanding/animation-from-interactions.html — Codex 검토가 열람 · 이 세션은 미열람) | 확립(표준) — 2.3.3은 AAA라 목표 적합성 수준에 따라 필수 여부 구분 |
| X21 AI 기본값 흔적 | unslop `references/signs.md` 「Signs of slop」 64개 10분야 — Damir Sokolovsky(@heydamir) · https://github.com/heydamir/unslop · **CC BY 4.0**(2026-11-11 원문 열람 · 이 항목은 그 목록을 요약 · 번역한 변형본이다). 같은 방향의 다른 자료 = Hallmark Floor 2 · 9 · 11(Together AI · MIT) | 추정(한 사람 자료 · 판정 근거로 쓰지 않음) |
| X22 다시 만들 때 보존 | Hallmark README의 Redesign 절에 설명된 `--before` · `--kept` 검사 아이디어(링크 · 입력칸 · 동작 · 제목을 먼저 기록하고 하나라도 빠지면 실패) — https://github.com/nutlope/hallmark · MIT · 2026-11-11 README · SKILL.md 사본 열람 · 검사 스크립트의 실제 동작은 미확인 · 원칙 = NN/g 10원칙 3 User Control and Freedom · 4 Consistency and Standards | 방향성(원칙) · 추정(검사 방식 — 참고만) |
| X23 취소 · 해지 · 탈퇴 경로 | 「전자상거래 등에서의 소비자보호에 관한 법률」 제21조의2(온라인 인터페이스 운영에 있어서 금지되는 행위) 제1항 — 제3호(구매 · 이용 · 회원가입 · 계약체결 또는 구매취소 · 회원탈퇴 · 계약해지 선택항목 사이에 크기 · 모양 · 색깔 등 시각적으로 현저한 차이를 두어, 특정 항목만 선택할 수 있거나 반드시 선택해야 하는 것으로 잘못 알게 할 우려가 있는 행위) · 제4호(정당한 사유 없이 취소 · 탈퇴 · 해지 절차를 구매 · 가입 · 계약 절차보다 복잡하게 설계하거나 다른 방법으로만 가능하게 제한해 방해) · 제5호(이미 한 선택 · 결정의 변경을 팝업 등으로 반복 요구해 자유로운 의사결정을 방해 — 대통령령 기간 이상 요구를 받지 않도록 선택할 수 있게 하면 제외). [시행 2026. 7. 21.] [법률 제21312호, 2026. 1. 20., 일부개정] · https://www.law.go.kr/LSW/lsSideInfoP.do?lsiSeq=282793&joNo=0021&joBrNo=02&docCls=jo&urlMode=lsScJoRltInfoR&efYd=20260721 (2026-11-12 원문 열람 · 2027. 1. 21. 시행 예정판도 같은 도구 출력에서 조문 문장이 같았다). 같은 법 시행령 제27조의2: 제5호 단서의 기간 = **7일** [시행 2026. 7. 21.] [대통령령 제36507호] · https://www.law.go.kr/LSW/lsSideInfoP.do?lsiSeq=288143&joNo=0027&joBrNo=02&docCls=jo&urlMode=lsScJoRltInfoR (2026-11-12 원문 열람). 같은 조 제2항의 공정위 지침은 미열람 · 원칙 = NN/g 10원칙 3 User Control and Freedom | 확립(전자상거래 · 통신판매 사업자일 때 — 위법 최종 판단은 하지 않음) · 방향성(그 밖) |

## 저작자 표시
- X21은 heydamir/unslop의 「Signs of slop」을 요약 · 번역한 것이다. Part of unslop by Damir Sokolovsky (@heydamir), CC BY 4.0 — https://creativecommons.org/licenses/by/4.0/ . 원문에서 고르고 줄였으며 한국어로 옮겼다(변경 있음).
- X22의 검사 방식은 nutlope/hallmark(MIT)의 `redesign` 설명에서 아이디어만 가져왔다(코드 · 문장 복사 없음).

## 갱신 이력
- 2026-11-12 v0.3: X1에 화면별 순위 2~3단 · X23 취소 · 해지 · 탈퇴 경로 신설(전자상거래법 제21조의2 원문 확인).
- 2026-11-09 v0.1 신설 · 비교 시험 0회.
- 2026-11-11 v0.2 일반화: X18 · X19를 대상 프로젝트 규칙 기준으로 · X20에 움직임 줄이기 · X21 · X22 신설 · WCAG · NN/g 대조.
