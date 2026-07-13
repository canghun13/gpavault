# GPA Vault 인수인계 문서 v7 (2026-07-13 기준, AdSense 재검토 준비 세션 반영)

이전 v6 문서를 대체함. v6(및 그 이전 버전들)의 배경 설명은 그대로 유효하므로 필요시 참고. 이 문서는 **07-13 같은 날 진행된 두 번째 세션(AdSense "가치없는 콘텐츠" 재검토 대비 점검)**에서 바뀐 것 위주로 정리.

---

## 0. 작업 방식 (재확인)

- 매 세션 **새 GitHub 토큰**을 사용자가 발급해서 줌 → `git clone https://<TOKEN>@github.com/canghun13/gpavault.git`
- clone 직후 반드시:
  ```
  git config user.email "canghun13@naver.com"
  git config user.name "canghun13"
  ```
- 작업 → commit → push → **GitHub Pages 빌드 성공 확인까지가 "완료"** (push만 하고 안 끝난 걸로 착각하지 말 것)
- 빌드 확인: `GET /repos/canghun13/gpavault/pages/builds/latest` 폴링. 보통 30~40초면 `built`로 바뀜. 단, **연속으로 여러 커밋이 짧은 간격으로 들어오면 이전 빌드가 자동 `cancelled`되고 최신 커밋 기준으로 재시작**됨 — "멈춘 것 같다"고 오판하지 말고 `actions/runs`에서 `head_sha`로 최신 커밋 기준 run이 진행 중인지 확인할 것 (실제로 07-09 세션에 이 문제로 15분 이상 헛갈렸던 이력 있음)
- **세션 종료 시 반드시 토큰 revoke** — 사용자가 매번 직접 챙기고 있음

## 1. Public 레포 유지 (v4에서 확정, 변경 없음)
재검토 대상 아님. Private 전환 시도 금지.

## 2. 작업 빈도 방침 변경 (★ 07-11 세션에서 확정)
기존엔 "주간 작업" 개념이었으나, **07-11부로 폐기**. 사용자가 수익화에 속도를 내려고 **세션 되는 대로 자주 터치**하는 방향으로 전환. "이번 주에 이미 했으니 다음 주에" 같은 페이싱 판단 하지 말 것 — 세션이 열리면 바로 GSC 데이터 기반으로 작업 진행.

## 3. 구조 확장 보류 원칙 — 정정됨 (★ 07-09 세션에서 사용자가 직접 정정)
v4에 "색인율 50% 게이트 넘기 전까지 구조 확장 보류"라고 적혀 있던 건 **잘못된 기록**이었음. 실제 원칙:
- **툴/블로그 신규 추가(구조 확장)는 계속 진행해도 됨**, 색인율 게이트로 막을 필요 없음
- 다만 신규 페이지 만들 때는 카니발라이제이션 체크는 여전히 필수

## 4. 보강 작업 체크리스트 — llms.txt 추가됨 (★ 07-11 세션에서 정정, 매우 중요)
v4에 있던 "보강 시 3개 파일 체크리스트"는 **불완전했음**. 사용자가 07-11 세션에서 직접 지적:

> **신규든 보강이든 관계없이 llms.txt는 매번 확인 대상이다.**

**갱신된 보강 체크리스트 (4개, 신규/보강 구분 없이 이제부터 이걸로):**
1. 해당 파일 본문 (JSON-LD `dateModified` 있는 경우만 갱신 — `WebApplication` 타입은 날짜 필드 없음, `Article` 타입은 있음)
2. `sitemap.xml` → 해당 URL `lastmod` 오늘 날짜로 업데이트
3. 블로그면 `blog/index.html` → 카드를 **해당 카테고리 섹션(`cat-academics`, `cat-loans` 등) 내에서 최상단으로 이동**, 기존 위치 카드는 반드시 제거 (str_replace 두 번으로 분리: ①기존 위치에서 제거 ②최상단에 삽입). 편집 후 BeautifulSoup으로 `a.blog-card` 개수/href 중복 여부 검증 필수
4. **`llms.txt` → 해당 항목 설명 문구가 최신 상태와 어긋나지 않는지 확인, "Updated ~" 같은 날짜 표기가 있으면 오늘 날짜로 갱신**

신규 페이지 추가 시 9개 파일 체크리스트(v4 문서 참고)는 그대로 유효 — llms.txt는 원래도 포함돼 있었음.

## 5. 최신 커밋 상태
```
933c97f AdSense 재검토 준비: 2025-26 대출 금리 → 2026-27로 전면 수정(11개 파일), Grad PLUS 자격 변경 반영, methodology.html/editorial-policy.html 신설, 800단어 미만 2개 파일 보강, blog/index.html 재정렬 (07-13 두번째 세션)
916e70b handover.md v6 업로드
fc278c5 Add FAQ + FAQPage schema: how-many-as-to-raise-gpa.html + ib-gpa-calculator.html (07-13 첫번째 세션)
216f4df handover.md v5 업로드 (사용자 수동 커밋)
d55c8dd Refresh stale 'Updated June 2026' date mention in llms.txt for how-much-student-loan-debt-is-too-much
7a9d265 Reinforcement checklist follow-up: dateModified + blog/index.html reorder
3701c94 Add FAQ + FAQPage schema (5개 파일, 07-11 GSC 데이터 기반)
a0357ec / b09b582 Update robots.txt (사용자 수동 커밋)
33468f9 Add missing FAQPage schema to 4 tools + loan-repayment REPAYE/PAYE/ICR FAQ + 404 redirect stub (07-09)
c8f80ee 이전 세션(v4 문서 기준 최신)
```

## 6. 07-09 세션 작업 내역
- **버그 발견 및 수정**: `act-score-calculator`, `sat-score-calculator`, `loan-repayment-calculator`, `college-cost-calculator` 4개 tools 페이지에 FAQ 텍스트는 있는데 FAQPage 스키마가 누락돼 있었음 (v4에 "완료"로 잘못 기록됐던 부분) → 전부 추가 완료
- **loan-repayment-calculator.html**: REPAYE/PAYE/ICR 2026년 현황 FAQ 2개 추가 (실제 정책 조사 결과 반영 — 아래 8번 참고)
- **404 오류 수정**: GSC에 잡힌 404가 `/blog/how-to-raise-your-gpa.html` (오타 URL, 실제 파일 없음, 아마 예전 외부 백링크). GitHub Pages는 서버 리다이렉트 미지원이라 `blog/how-to-raise-your-gpa.html`에 canonical + meta refresh 리다이렉트 스텁 페이지 생성함 → sitemap엔 미포함 (콘텐츠 페이지 아님)
- 리디렉션 3건은 원인 미특정 (URL 리스트 없어서), **사용자가 "안 봐도 된다"고 명시적으로 확인함 — 앞으로 리디렉션 이슈는 조사 대상에서 제외**

## 7. 07-11 세션 작업 내역
GSC 데이터(Performance + Coverage, 07-11 export) 분석 후 웹 검색으로 경쟁 강도까지 확인하고 진행:

- **전략적 판단 (중요)**: `college-cost-calculator`, `act-score-calculator`가 타겟하는 헤드 키워드(`college cost calculator`, `act calculator` 등)는 Sallie Mae, College Board(BigFuture), Calculator.net, Niche 같은 초고권위 사이트가 SERP 상위 장악 중. 이미 title/meta는 잘 되어 있어서 **온페이지 추가 수정으로는 지금 승산 없음** → 이번 세션엔 건드리지 않기로 결정. 앞으로도 이 두 페이지는 "권위가 쌓일 때까지 관망" 대상으로 분류, 매번 재작업 시도하지 말 것
- **FAQ + FAQPage 스키마 보강 (5개 파일)**, 순위 10~55위 사이 "임박한" 페이지 위주:
  1. `blog/what-is-the-deans-list-gpa-requirement.html` — "dean college gpa requirements", "how to get on the dean's list" 문구 FAQ 추가
  2. `tools/gpa-scale.html` — "5.0 GPA scale" 관련 FAQ 추가
  3. `blog/how-much-student-loan-debt-is-too-much.html` — FAQ 섹션 신규 생성, "is $40,000 in student loans a lot" 등 정확 문구 매칭
  4. `blog/student-loan-repayment-plans-2026.html` — FAQ 섹션 신규 생성, "old ibr vs rap", PAYE 2028 종료 등 반영
  5. `tools/grade-calculator.html` — "course grade calculator", "class calculator" 문구 FAQ 추가
- 5개 전부 **보강 체크리스트 4개 항목**(본문/sitemap/blog-index/llms.txt) 순서대로 처리 완료

## 8. 07-13 세션 작업 내역 (일요일 작업 앞당김)
GSC Performance/Coverage export (07-13) + GA4 리포트(06-15~07-12) 분석 후 웹 검색으로 경쟁 강도 확인하고 진행:

- **가장 임팩트 큰 페이지 발견**: `blog/how-many-as-to-raise-gpa.html`이 최근 60일 노출 **193회로 전체 사이트 1위** (2위인 college-cost-calculator의 141회보다도 높음), 순위 27.92, 실제 클릭 2건 발생 중 — FAQ 텍스트는 있었는데 FAQPage 스키마가 **누락**돼 있었음 (07-09에 발견했던 것과 같은 유형의 버그, 이 파일은 그때 점검 대상에서 빠져 있었음). FAQPage 스키마 추가 + GSC 쿼리 갭 대응 FAQ 3개 신규 작성("how many credits...", "how much can I raise my GPA in one year", "how many points does one A raise your GPA")
- **IB GPA 클러스터 (v5 백로그 11번 항목 착수)**: `tools/ib-gpa-calculator.html`도 동일한 버그(FAQ 텍스트 있음, 스키마 없음) 발견 → FAQPage 스키마 추가 + IB 클러스터 쿼리("ib points to gpa", "ib grade conversion", "ib score to gpa" 등, 관련 쿼리 순위 40~75대) 대응 FAQ 3개 신규 작성. 경쟁 강도 웹 검색 결과 초고권위 사이트 없이 중소 사이트들끼리 경쟁 중인 니치 — 온페이지 보강으로 승산 있다고 판단
- 두 파일 모두 **보강 체크리스트 4개 항목** 순서대로 처리 (`how-many-as-to-raise-gpa`는 blog라 blog/index.html cat-academics 섹션 최상단으로 이동까지 완료 / `ib-gpa-calculator`는 tools라 blog-index 항목 해당 없음, WebApplication 타입이라 본문 dateModified도 해당 없음)
- **college-cost-calculator, act-score-calculator**: 지시 없어 이번에도 건드리지 않음 (v5 원칙 유지)
- **07-11에 보강한 5개 파일**(dean's list, gpa-scale, student-loan-debt-too-much, repayment-plans-2026, grade-calculator)은 손댄 지 2일밖에 안 지나 **이번 세션엔 재작업하지 않음** — 색인/순위 반영에 시간 필요, 성급한 재작업 방지 원칙 유지
- **NOINDEX 커버리지 이슈 확인**: 07-13 Coverage 리포트에 새로 "NOINDEX 태그에 의해 제외됨" 1건이 잡혔는데, 확인 결과 **버그 아님** — 07-09에 만든 404 리다이렉트 스텁(`blog/how-to-raise-your-gpa.html`)에 의도적으로 `<meta name="robots" content="noindex">`를 넣어뒀던 것. 구글이 이제 이 페이지를 크롤링해서 noindex를 인지했다는 뜻이므로 오히려 정상 동작. 앞으로도 이 카테고리에 뜨는 건 정상으로 간주할 것

## 9. 07-13 두 번째 세션 — AdSense "가치없는 콘텐츠" 재검토 준비 (★ 중요, 새 토큰으로 별도 진행)
사용자가 예전에 AdSense에서 "가치없는 콘텐츠"로 반려된 적 있다고 언급, 재신청 전 점검 요청. (참고: 다른 사이트 autocalchub도 같은 사유로 반려된 이력 있음 — 거기선 800단어 미만 페이지 11개 보강으로 대응했었음.) gpavault는 점검 결과가 좀 달랐음:

- **단어수 감사**: 전체 48개 콘텐츠 페이지 중 800단어 미만은 단 2개뿐(`student-loan-calculator.html` 728, `semester-gpa-calculator.html` 764) — autocalchub처럼 단어수가 주범은 아니었음. 그래도 이 2개는 진짜 유용한 신규 섹션(대출 상태/서비서 설명, Pass/Fail·Withdrawal·Incomplete가 GPA에 어떻게 반영되는지)을 추가해서 각각 1006단어/1053단어로 보강함
- **★ 진짜 문제 발견: 연방 학자금 대출 금리가 통째로 구식이었음.** 사이트 전체가 "2025–26년도 금리"(undergrad 6.39%, grad 7.94%, PLUS 8.94%)를 기본값/예시로 쓰고 있었는데, **2026-07-01부로 2026–27년도 금리(undergrad 6.52%, grad 8.07%, PLUS 9.07%)로 이미 바뀐 상태** — 즉 오늘(07-13) 기준 사이트에 있는 숫자가 실제로 틀린 정보였음. 웹서치로 공식 신규 금리 확인(Dept of Education 5월 국채 경매 기준) 후:
  - 영향받은 **11개 파일** 전수 수정: `tools/student-loan-calculator.html`, `scholarship-savings-calculator.html`, `student-loan-vs-salary.html`, `loan-repayment-calculator.html`, `college-cost-calculator.html`, `blog/how-to-lower-your-student-loan-payments.html`, `room-board-vs-off-campus.html`, `student-loan-repayment-plans-2026.html`, `federal-vs-private-student-loans.html`, `how-to-lower-student-loan-interest-rate.html`, `how-to-find-scholarships.html`
  - 금리 숫자만 바꾼 게 아니라 **모든 달러 예시(월 납입액/총액/이자 절감액 등)를 새 금리로 다시 계산**해서 일관되게 반영 (예: $35,000 대출 10년 상환 $389→$398/월 등)
  - **추가로 발견한 사실**: 2026-07-01부로 신규 프로그램/신규 학교 등록하는 대학원생은 **Grad PLUS 대출 자체가 폐지**됨(기존 진행 중인 프로그램 대출자는 계속 가능) — `federal-vs-private-student-loans.html`에 이 내용도 반영
  - 11개 파일 전부 sitemap lastmod 갱신, Article 타입 6개는 dateModified + 화면 "Updated" 텍스트도 갱신, blog인 6개는 blog/index.html 해당 카테고리(`cat-loans`, `cat-costs`) 최상단으로 재정렬 완료
- **E-E-A-T 신뢰 신호 보강**: `methodology.html`(계산기별 공식/출처/갱신주기 설명), `editorial-policy.html`(콘텐츠 제작·검수 프로세스, 가짜 저자 프로필 안 쓰는 이유, 정정 정책) 신규 생성 → 전 페이지 footer에 링크 추가, about.html에서도 링크, sitemap 추가
- 이 모든 변경 커밋(`933c97f`) 후 push, Pages 빌드 `built` 확인 완료

**다음 세션 필독**: 이 작업은 "재검토 요청 제출 전 사전 점검"임. **실제 AdSense 대시보드에서 재검토(review request) 제출은 사용자가 직접 해야 하는 액션** — 다음 세션 시작 시 사용자가 제출했는지, 제출했다면 결과가 나왔는지 먼저 확인할 것. autocalchub 케이스 참고하면 심사에 통상 며칠~1-2주 소요.

## 10. 알아둬야 할 사실 (student loan 정책, 2026-07 기준 — 위 9번 반영해서 갱신)
- **SAVE 플랜은 2026-07-01부로 RAP(Repayment Assistance Plan)로 대체됨**
- **REPAYE는 이미 존재하지 않음** — SAVE에 흡수됐다가 SAVE 자체가 없어졌으므로 "REPAYE" 검색 유입은 오래된/혼동된 검색 의도. RAP 또는 IBR로 안내하는 게 맞음
- **PAYE, ICR은 기존 대출자(2026-07-01 이전 대출, 이후 신규 대출/통합 안 한 경우)만 2028-07-01까지 한시적 유지**, 신규 대출자는 이용 불가 (RAP 또는 Tiered Standard만 가능)
- **연방 학자금 대출 금리는 매년 7월 1일 갱신됨** (5월 10년 국채 경매 기준) — **2026–27년도(2026-07-01~2027-06-30 신규 대출) 금리: undergrad 6.52%, grad unsub 8.07%, PLUS 9.07%.** 다음 갱신은 2027-07-01. 사이트에 금리 예시 넣을 때마다 이 날짜 기준으로 최신인지 확인할 것 — 이번 세션에 발견한 것처럼 "작년 회계연도" 숫자가 그대로 남아있기 쉬움
- **Grad PLUS 대출은 2026-07-01부로 신규 프로그램/신규 학교 등록 대학원생에게 폐지됨** (기존 진행 중인 프로그램 대출자는 계속 가능)
- 관련 콘텐츠 작성 시 이 팩트 기준으로 일관되게 서술할 것

## 11. GSC / GA4 현황 (07-13 기준, 첫 번째 세션에서 확인)
- **색인: 20 / 미색인 합계 35** (리디렉션 3 + noindex 1(정상, 위 9번 세션과 별개로 08번 참고) + 404 1(검증 중) + 발견-미색인 29 + 크롤링-미색인 1) — 색인 20/발견-미색인 29는 **07-11 대비 변화 없음**, 아직 이른 시점
- "크롤링됨 - 현재 색인이 생성되지 않음" 1건: 07-11에도 있던 이슈, 07-13에도 여전히 존재. 여전히 URL 특정 불가 (page-level 리스트가 export에 없음)
- 404 유효성 검사: 계속 "시작됨" 상태 유지 (아직 완료 안 됨, 정상 진행 중으로 판단)
- 리디렉션 3건: **조사 대상 아님** (사용자 확인, 유지)
- **GA4 (06-15~07-12, 4주)**: 세션 총 127건 중 Direct 104 / Organic Search 11 / Referral 9 / AI Assistant 1 — **오가닉 유입이 극히 적음**, 트래픽 대부분 직접 방문(사용자 본인 테스트 접속 포함 가능성 있음). 총수익 $0 — 이번 세션에 AdSense "가치없는 콘텐츠" 반려 이력이 원인 중 하나였다는 게 확인됨 (위 9번 참고)
- Organic 유입이 낮은 이유는 순위 자체가 낮기 때문(대부분 쿼리가 50~100위)이라 GSC 반영 지연 문제라기보다는 **아직 성장 초기 단계**로 보임

## 12. 관찰 중 / 재평가 보류 항목
- `blog/how-to-raise-your-gpa-in-one-semester.html`: 07-07 title 변경 효과 재평가는 최소 07-21 이후로 미룰 것
- `college-cost-calculator.html`, `act-score-calculator.html`: 헤드 키워드 경쟁 압도적이라 당분간 관망
- `blog/how-many-as-to-raise-gpa.html`, `tools/ib-gpa-calculator.html`: 07-13 첫 세션에 막 보강함, 최소 2주 후 재평가
- **AdSense 재검토 결과 대기 중** — 위 9번 참고, 다음 세션 시작 시 최우선 확인 사항

## 13. 신규 후보 (백로그, 착수 안 함)
- SSAT percentile calculator — 검색 볼륨 작음(월 노출 4 수준), 우선순위 낮음. **07-13 사용자에게 착수 여부 물어봤고 "보류"로 명시적 결정함** — 색인 병목 해소 전까지는 신규보다 기존 페이지 보강이 우선이라는 논리에 사용자 동의
- IB GPA 클러스터는 07-13 첫 세션에 착수 완료, 백로그에서 제거
- 신규 페이지 후보 추가 발굴 안 됨 (기존 21개 tools + 27개 blog로 주요 쿼리 커버리지 양호)

## 14. 파일 현황
- tools: 21개 + index (`sat-percentile-calculator.html`이 가장 최근 신규, 07-07)
- blog: 27개 + index
- 루트: about, methodology(신규), editorial-policy(신규), privacy-policy, contact, index
- 전체 sitemap URL: 55개 (methodology.html, editorial-policy.html 추가로 +2, 콘텐츠 신규 페이지는 없음)

## 15. 다음 세션 시작 전 체크리스트
1. 이 문서(v7) 먼저 정독
2. **AdSense 재검토 제출/결과 여부 먼저 확인** (위 9번 참고) — 사용자가 제출했는지, 결과 나왔는지부터 물어볼 것. 통과 시 이슈 종결하고 이 항목 문서에서 제거. 반려 시 사유 재분석 필요(이번엔 금리 최신화 + E-E-A-T 페이지 추가로 대응했으니, 그래도 반려되면 다른 원인 — 예: 사이트 전체가 계산기 템플릿 구조라 "自動化된 콘텐츠"로 보일 가능성 — 을 원점에서 재검토)
3. 새 GSC Performance/Coverage export + GA4 export 받아서 07-13 데이터와 비교 (특히 "크롤링됨-미색인 1건" 지속 여부, 색인 20/29 변동 여부, Organic Search 세션 비중 변화)
4. 새 GitHub 토큰 발급받기
5. clone 후 `git config` 설정 잊지 말 것
6. 작업 시 **신규는 9개 파일 체크리스트, 보강은 4개 파일 체크리스트(본문/sitemap/blog-index/llms.txt) 누락 금지** — llms.txt 빠뜨리면 사용자가 바로 지적함
7. college-cost-calculator, act-score-calculator는 별도 지시 없으면 건드리지 않기
8. 리디렉션 이슈는 조사하지 않기 (사용자 확인됨)
9. 07-11에 보강한 5개 파일 + 07-13에 보강한 2개 파일(how-many-as-to-raise-gpa, ib-gpa-calculator)은 최소 2주는 재작업하지 말 것 — 색인 반영 시간 필요
10. **연방 대출 금리는 매년 7월 1일 갱신됨을 기억할 것** — 다음 갱신은 2027-07-01이니 그 전까지는 6.52%/8.07%/9.07%가 맞는 숫자. 매 세션 시작 시 "지금 몇 월인지" 확인해서 회계연도 넘어갔으면 사이트 전체 금리 재점검
11. 작업 완료 후 커밋/푸시 → Pages 빌드 `built` 확인까지 끝내고, **사용자가 직접 확인해야 할 URL을 클릭 가능한 링크로 정리해서 제시** (사용자는 영어를 몰라서 콘텐츠 검수가 아니라 화면이 깨졌는지만 육안 확인함 — 문구 검수 요청하지 말 것)
12. 세션 끝나면 토큰 revoke 리마인드
