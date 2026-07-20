# GPA Vault 인수인계 문서 v11 (2026-07-20 세션 반영)

이전 v10 문서를 대체함. v10(및 그 이전 버전들)의 배경 설명은 그대로 유효하므로 필요시 참고. 이 문서는 **07-20 세션**에서 바뀐 것 위주로 맨 위에 정리하고, 이전 v10 본문은 아래에 그대로 보존.

---

## 0-★★★. 07-20 세션 — GSC 재분석 기반 보강 + 전체 파일 FAQPage 스키마 버그 스캔 (★★★★ 최신, 맨 위에서부터 읽을 것)

### 배경
07-18 두 번째 세션(신규 툴 2개 공격적 확장) 이후 이틀 만의 세션. 사용자가 첨부한 GSC Performance(지난 3개월 필터로 변경됨, 이전 세션들은 기간 표기 없었음 — 주의) + Coverage + GA4 개요 CSV 기반으로 분석 후 진행. 지시사항은 기존과 동일(신규/보강 착수 전 중복확인+경쟁조사, 롱테일 전략, AI검색 문제해결/비교분석 콘텐츠 우선, 수익화 관점 우선순위, 대시보드 없이 텍스트 분석만).

### GSC 데이터 분석 결과
- **Coverage**: 07-18과 완전 동일(리디렉션 3 / noindex 1 / 404 1 / 발견-미색인 21 / 크롤링-미색인 0) — 이틀 새 변화 없음, 특이사항 없음.
- **Performance**: 여전히 사이트 전체 클릭 0에 수렴(3개월 누적 기준 최고 클릭수 3회), 임프레션만 축적. 07-18에 만든 신규 툴 2개(percentage-to-gpa-converter, ap-credit-calculator)는 아직 페이지 리포트에 안 잡힘 — 정상(생성 후 2일), 다음 세션에서 재확인할 것.
- **신규 콘텐츠 후보 재검토(웹 검색 대신 GSC 자체 신호로 1차 스크리닝)**: SAI/EFC, PSLF, 국제 성적 환산(A-level/ATAR/CGPA), class rank, CLEP, GRE/GMAT/LSAT/MCAT 관련 쿼리 **전부 0건** — 실질적 수요 신호 없음, 신규 페이지 보류 유지가 맞다고 판단. Dean's List 클러스터는 여전히 크지만 이미 페이지 3개(what-is-the-deans-list-gpa-requirement, deans-list-vs-latin-honors, glossary)로 충분히 커버 중이라 신규 불필요. **결론: 이번 세션은 신규 페이지 없이 보강에 집중.**

### 이번 세션 우선순위 판단 (수익화 관점, 2주 보류 원칙 적용)
07-11/07-13/07-16/07-18 네 세션에 걸쳐 실제 콘텐츠 수정이 있었던 파일들을 전부 2주 보류 대상으로 계산(각각 07-25/07-27/07-30/08-01까지) — **거의 모든 상위 트래픽 페이지가 보류 중**이라는 게 이번 세션의 핵심 제약이었음. 보류 계산 시 주의: **noscript nav 일괄 스윕이나 CSS/금리 수정 같은 사이트 전역 패치는 보류 판단에서 제외**해야 함(git log 커밋 날짜만 보면 전부 07-18로 나오는데, 실제 콘텐츠 편집은 훨씬 이전인 파일이 많음 — `git log --oneline --follow -- <file>`로 실제 콘텐츠 커밋만 골라내서 확인할 것, 이번에 이 방법으로 재확인함).

**보류에 안 걸리는 파일 중 우선순위**:
1. **`blog/how-to-raise-your-gpa-in-one-semester.html`** (최우선) — 사이트 전체 임프레션 **2위**(153회, 3개월 누적), 순위 **11.02**(홈페이지 다음으로 사이트 최고 순위권)인데 **FAQ 자체가 아예 없었고 CTR이 0.65%**(클릭 1회)로 비정상적으로 낮음. 이 정도 순위에서 이 CTR은 명백한 개선 여지 → FAQ 4개 신규 작성(+FAQPage 스키마). GSC 쿼리 "can you raise cumulative gpa after a low first semester gpa 1.0"(순위 **10**, 거의 완벽 매칭), "how much can you raise your gpa in one semester" 계열 다수 쿼리에 정확 대응하는 문항 위주로 작성.
2. **`tools/sat-score-calculator.html`** — "how to add up sat score"(14회 노출, 순위 94)에 대응하는 FAQ가 없었음 → raw score→scaled score 변환 원리를 설명하는 FAQ 1개 신규 추가.

### 전체 파일 FAQPage 스키마 버그 스캔 (이번 세션에 신규 도입한 점검 방식)
07-16/07-18 세션에서 개별적으로 발견되던 "FAQ 텍스트는 있는데 FAQPage 스키마가 누락된" 버그가 반복적으로 나타나는 패턴이라, **이번엔 사이트 전체 blog+tools HTML을 스크립트로 스캔**해 한 번에 전수 확인함(정규식으로 "Frequently Asked/asked Questions" 존재 여부와 `FAQPage` 스키마 존재 여부 교차 확인). 결과 총 10개 파일에서 문제 발견:
- **스키마만 누락(FAQ 텍스트는 있음, 7개, 2주 보류 대상 아님 확인 후 전부 수정 완료)**: `blog/does-retaking-a-class-replace-your-gpa.html`, `blog/what-gpa-do-you-need-for-med-school.html`, `blog/what-is-a-good-sat-score.html`, `tools/ap-gpa-calculator.html`, `tools/final-exam-calculator.html`, `tools/gpa-raise-calculator.html`, `tools/high-school-gpa-calculator.html` — 기존 FAQ 텍스트를 그대로 JSON-LD로 스키마화(신규 문항 추가는 안 함, 순수 버그 수정). 각 파일 dateModified 필드 존재 여부 확인 후(Article 타입 3개 파일만 갱신, WebApplication 타입 4개는 필드 자체 없어 갱신 대상 아님) 07-20으로 갱신, 화면 "May 2026" 같은 정적 날짜 표기 2곳도 "Updated July 2026"으로 갱신.
- **FAQ 자체가 없음(2개, 이번 세션엔 보류 — 아래 백로그 참고)**: `blog/how-to-calculate-unweighted-gpa.html`(3개월 임프레션 2회), `blog/how-to-find-scholarships.html`(1회) — 트래픽이 거의 0에 가까워 이번 세션 우선순위(위 2개 항목)에 밀림, 신규 FAQ 작성은 다음 세션 백로그로 이관.
- **오탐 제외**: `blog/how-to-raise-your-gpa.html`은 FAQ 문제가 아니라 리디렉션 스텁 페이지(정상, `how-to-raise-your-gpa-in-one-semester.html`로 301 유사 처리) — 손대지 않음.
- **보류 중이라 스킵**: `blog/federal-vs-private-student-loans.html`(같은 유형 버그 있었지만 07-16 세션에 이미 수정된 걸로 착각했었는데 재확인 결과 아직 스키마 누락 상태 — 07-16 상호링크 편집 때문에 07-30까지 보류 대상, **다음 세션 최우선 백로그로 이관**).

**이 스캔 방식은 앞으로도 매 세션 실행할 것을 권장** — 개별 페이지를 우연히 발견하는 방식보다 훨씬 효율적이고 누락을 방지함. 스캔 스크립트 로직: `re.search(r'<h2>Frequently [Aa]sked [Qq]uestions</h2>')`로 FAQ 섹션 존재 확인 후 `'FAQPage' in content`로 스키마 존재 여부 교차 체크.

### 체크리스트 반영 및 검증
- 3개 블로그 파일(does-retaking, what-gpa-do-you-need-for-med-school, how-to-raise-your-gpa-in-one-semester) → `blog/index.html`에서 cat-academics 섹션 최상단 3개로 재배치(우선순위 순: 신규 FAQ 작성한 how-to-raise-your-gpa-in-one-semester를 맨 위, 그 다음 스키마만 고친 2개), what-is-a-good-sat-score는 원래도 cat-test 최상단이라 이동 불필요.
- sitemap.xml lastmod 9개 URL 전부 07-20 갱신 (how-to-raise-your-gpa-in-one-semester, sat-score-calculator + 스키마 버그 수정 7개).
- llms.txt 9개 항목 전부 확인 — 설명 문구가 이미 정확해 갱신 불필요(날짜 표기 없는 항목들).
- 사이트 전체(63개 HTML) JSON-LD 재검증 스크립트로 통과(오류 0건), sitemap.xml 63 URL XML 파싱 검증 통과, blog-card 31개/tools-card 24개 BeautifulSoup 중복 검증 통과(0건).
- 커밋 `9458ca2`, push 완료. `GET /repos/canghun13/gpavault/pages/builds/latest` 폴링으로 `built` 상태 확인 완료(commit sha 일치 `9458ca2`).

### 다음 세션 백로그 (갱신됨)
1. **`blog/federal-vs-private-student-loans.html`** — FAQPage 스키마 누락 버그(07-16 상호링크 편집으로 07-30까지 보류였으나 07-30 지나면 최우선으로 수정할 것)
2. `blog/how-to-calculate-unweighted-gpa.html`, `blog/how-to-find-scholarships.html` — FAQ 섹션 자체가 없음(신규 작성 필요), 다만 3개월 임프레션이 각각 2회/1회로 매우 낮아 우선순위는 낮음. 다음 GSC export에서 임프레션이 늘었는지 먼저 확인 후 착수 여부 판단할 것
3. **신규 페이지**: 이번 세션도 특별히 새로 발굴된 후보 없음(SAI/EFC, PSLF, 국제 성적 환산, class rank 전부 GSC 신호 0). 다음 세션 시작 시 새 GSC export로 재확인
4. **07-18 두 번째 세션 신규 툴 2개**(percentage-to-gpa-converter, ap-credit-calculator) — 다음 세션에서 Coverage/Performance 리포트에 잡히기 시작했는지 확인할 것
5. **전체 FAQPage 스키마 스캔은 매 세션 반복 권장** — 위 스캔 스크립트 로직 참고, 새로 만든 페이지나 아직 스캔 안 한 페이지에서 추가로 발견될 수 있음

### AdSense 재검토 관련
사용자가 이번 세션에 언급 없음. v10에서 "제출 완료 확인, 결과 여부는 다음에 확인"으로 격하된 상태 그대로 유지 — 결과 나왔는지 다음 세션에 물어볼 것(최우선 체크리스트는 아님).

---

## 0-★★★★. 07-20 같은 날 두 번째 세션 — "신규 없이 보강만 했냐" 지적 반영, 신규 툴 1개 추가

### 배경
위 첫 번째 세션에서 "이번엔 신규 없이 보강만 했다"고 보고하자, 사용자가 명확히 반박: **"조회수는 많은데 문서수(경쟁)가 적은 롱테일을 우리가 먼저 잡아놓지 않으면 계속 정체된다, 많이는 안 해도 되니 신규를 반드시 하라"**는 지시. GSC 자체 신호가 없다고 신규를 포기하는 것은 잘못된 판단이었음 — GSC 신호는 "우리가 이미 그 페이지를 갖고 있을 때만" 쌓이는 것이므로, 신규 후보 발굴은 GSC가 아니라 **웹 검색으로 경쟁 강도를 직접 측정**해야 한다는 걸 이번에 재확인함. **다음에도 "GSC에 신호가 없다"는 이유만으로 신규를 보류하지 말 것.**

### 후보 검토 (6개 후보를 웹 검색으로 경쟁 강도 확인, 5개 기각)
1. **LSAC GPA 계산기(로스쿨)** — 검색 1회에 Magoosh, Juriseducation, gpa-calculator.com, num8ers, zenocalculator, classmeme 등 **6개 경쟁사 즉시 확인** → 기각
2. **AMCAS/BCPM GPA 계산기(의대)** — smartcgpa, cumgpacalculator, sciencegpacalculator, gpalift, aspiringmd 등 **5개+ 경쟁사** → 기각
3. **UK 학위등급→GPA 변환기** — expatica, easyquickgrade, gradecalculatortools, smartcgpa, do-calculate, cgpacalculation, cgpato-percentage 등 **8개 경쟁사**, 국제 성적 환산 전체가 이미 포화 시장임을 재확인 → 기각(모니터링 유지 원칙 재확인)
4. **PSAT/National Merit Selection Index 계산기** — CollegeVine, PrepScholar(2건), ArborBridge, TheCollegePanda, test-ninjas, num8ers(2건) 등 **8개 경쟁사** → 기각
5. **NCAA 자격 core-course GPA 계산기** — NCSA, PrepScholar, Collegize, CourtTrackPro, HonestGame + NCAA 공식 문서 다수 → 경쟁 포화+ 규정 정확도 리스크(SAI/EFC와 유사한 성격, 잘못되면 실제 자격 문제로 이어짐) → 기각
6. **RAP(신규 대출 상환 플랜) 계산기** — thecollegeinvestor, studentloanplanner, edcapny, paychecktaxcalculator, fincalcapp, dreambiggerfinancial, studentloancoach 등 **7개 경쟁사**(현재 매우 핫한 주제라 오히려 경쟁이 제일 치열함), 게다가 우리 사이트 `student-loan-repayment-plans-2026.html`이 이미 RAP를 깊이 다루고 있어 신규 페이지를 만들면 자기잠식 위험도 있음 → 기각

7. **학자금 대출 이자 자본화(interest capitalization) 계산기** — 웹 검색 결과 전용 계산기를 제공하는 곳이 **toolcr.com 단 1곳**뿐이었고(나머지는 mefa/studentloansherpa/tateesq/nerdwallet/credible 등 설명형 글만 있고 계산기 없음), 우리 사이트 자체를 검색해도 `financial-aid-calculator.html`, `student-loan-calculator.html` 등 6개 파일에 "capitalize"라는 단어가 **한두 문장씩만** 스쳐 지나갈 뿐 전용 계산기나 깊은 설명이 없는 것을 확인 — **명확한 공백** → **채택**

### 실제 작업: 신규 툴 1개
**`tools/interest-capitalization-calculator.html`** — deferment/forbearance/grace period 종료 시 미납 이자가 원금에 얹히는(자본화되는) 금액을 계산하고, 그로 인해 상환기간 전체에 걸쳐 추가로 발생하는 비용까지 보여주는 계산기. 입력: 현재 잔액, 연이율, 유예 개월수, 기존 미납이자(선택), 상환기간. 계산 로직(단리 방식, 연방 학자금 대출 표준 방식)은 node로 사전 검증(예: $30,000/6.52%/12개월 → $1,956 자본화, 상환기간 전체 추가비용 $2,668 — 자본화된 이자 자체보다 상환기간 전체 추가비용이 항상 더 크다는 점을 본문에서 명시적으로 설명, "문제해결/비교분석" 지향 지시에 부합). 자본화 트리거(유예 종료/플랜 전환/통합 등)가 최근 몇 년간 반복적으로 바뀌었다는 점을 명시하고 studentaid.gov 확인을 권장하는 문구 포함(SAI/EFC류처럼 규정이 자주 바뀌는 주제라 과도하게 단정적인 서술은 피함). FAQPage 5문항 포함.

기존 `tools/student-loan-calculator.html`(월납입금·총비용 계산), `tools/loan-repayment-calculator.html`(플랜 비교)과는 명확히 다른 문제(유예 후 자본화로 인한 잔액 증가분 자체를 보여주는 것)를 다루므로 카니발라이제이션 아님.

신규 페이지 체크리스트 9개 항목 전부 적용: (1) 페이지 자체 (2) `assets/partials/header.html` 드롭다운 Tuition & Loans 섹션 추가 (3) noscript nav 61개 파일 일괄 스크립트 치환(상대/루트 경로 패턴 둘 다 처리, 중복 삽입 0건 검증) (4) `tools/index.html` 카드 추가(25개, href 중복 0건) (5) `sitemap.xml`(64 URL) (6) `llms.txt` (7) 관련 기존 페이지 상호링크 2곳(`how-to-lower-student-loan-interest-rate.html`, `how-to-lower-your-student-loan-payments.html` — **둘 다 07-13 세션에 금리 수정으로 07-27까지 2주 보류 대상이었지만, "신규 페이지의 상호링크 추가는 2주 보류 원칙의 예외"라는 v8/0-D에서 확립된 원칙을 적용해 진행. 이때 해당 두 파일의 sitemap lastmod는 갱신하지 않음** — 이 역시 과거 deans-list-vs-latin-honors 세션(f444d58)에서 확립된 처리 방식과 동일: 상호링크만 추가된 보류 파일은 lastmod를 건드리지 않는다).

사이트 전체(65개 HTML) JSON-LD 재검증 통과(오류 0건), sitemap.xml 64 URL 파싱 검증 통과, tools-card 25개 중복 0건. 커밋 `2c0c441`, push 완료, Pages 빌드 `built` 확인 완료(commit sha 일치).

### 이번 세션에서 배운 점 (다음 세션에도 적용)
- **"GSC에 신호가 없다"는 신규 보류의 충분한 근거가 아니다.** 우리 사이트에 없는 페이지는 애초에 GSC 임프레션이 잡힐 수가 없다 — 신규 후보 발굴은 매번 **웹 검색으로 경쟁사 수를 직접 세는 방식**으로 해야 하며, 경쟁사가 1~2곳 이하인 진짜 틈새를 찾을 때까지 여러 후보를 기각해나가는 과정 자체가 정상이다(이번에도 6개 중 5개 기각 후 1개 채택).
- 이번에 기각된 5개 후보(LSAC/AMCAS GPA, UK 학위환산, PSAT, NCAA 자격, RAP)는 전부 "이미 5개 이상의 경쟁사가 존재"가 기각 사유였음 — 나중에 재검토할 때도 이 기준(경쟁사 5곳 이상이면 사실상 포화로 간주)을 참고할 것. 반대로 이번 채택 기준(경쟁사 1곳 이하)도 향후 스크리닝 기준으로 유지.
- **사용자가 "많이는 안 해도 되니 신규를 반드시"라고 했을 때는 개수보다 방향 전환 자체가 핵심** — 이번처럼 신규 1개라도 제대로 만드는 것으로 충분히 지시를 충족함.

### 다음 세션 백로그 (추가)
6. **신규 툴 `interest-capitalization-calculator.html`도 다음 세션에서 GSC Coverage/Performance 반영 여부 확인할 것** (07-18 두 개 신규 툴과 함께 추적)
7. 이번에 기각된 후보들은 재검토 주기를 두고 다시 볼 것: RAP는 특히 시의성이 높은 주제라 SAVE 전환 관련 검색량이 계속 늘어날 가능성 있음 — 다만 이미 `student-loan-repayment-plans-2026.html`이 다루고 있어 신규 페이지보다는 **그 파일의 보강**(보류 해제되는 07-25 이후) 쪽으로 접근할 것

---

## 0-★★. 07-18 두 번째 세션 — "확장이 너무 없다, 공격적으로 하자" (★★★ 최신, 맨 위에서부터 읽을 것)

### 배경
사용자가 이번 세션에 명확한 방향 전환을 지시함:
- AdSense 재검토는 **저번에 이미 제출했다고 사용자가 확인** — 더 이상 매 세션 첫머리에 체크할 필요 없음 (v9까지 유지되던 "다음 세션 시작 시 최우선 확인" 항목 해제)
- **"신규가 너무 없다, 카테고리도 확장이 필요하다, 경쟁이 세더라도 롱테일로 붙어봐야 한다, 안일하게 하지 말고 공격적으로"** — 지금까지 세션들이 보강 위주로 흘러온 것에 대한 명확한 방향 수정 지시. 앞으로도 매 세션 보강만으로 안주하지 말고 신규 확장을 적극적으로 검토할 것

### 신규 후보 검토 (경쟁 강도 웹 검색 기반, 4개 후보 중 2개 채택)
사용자 지시대로 착수 전 전부 (1) 기존 파일 중복 확인 (2) 웹 검색으로 경쟁 강도 확인을 거침:

1. **SAI/EFC 계산기** (Student Aid Index, 구 Expected Family Contribution) — GSC에 관련 검색은 없었지만 재정지원 카테고리 확장 후보로 검토. 웹 검색 결과 finaid.org, mefa.org(주정부 기관), thecollegeinvestor.com, collegemoneymethod.com 등 **권위 있는 사이트가 이미 다수 포진** — 연방 공식 SAI 공식 자체도 매년 바뀌는 복잡한 계산이라 정확도 유지 부담도 큼 → **보류**
2. **PSLF(공공서비스 대출탕감) 계산기** — studentloanplanner.com, mentormoney.com, financialtoolset.com 등 **이미 정교한 전용 계산기가 다수 존재**, 자격요건도 복잡(고용주/대출종류/상환플랜 4중 조건) → **보류**
3. **AP 점수 예측 계산기**(raw score → 1~5점 예측) — fiveable.me, apscorehub.com, apscorecalc.com, ivytp.com 등 **극도로 포화된 시장**(과목별 40개+ 전용 계산기 생태계) → **회피 결정**
4. **AP 학점/등록금 절감액 계산기** (AP 시험 점수 → 대학 학점 인정 → $ 절감액, 위 3번과는 다른 앵글: 점수 예측이 아니라 "받은 점수로 뭘 얻는지") — 경쟁 확인 결과 apushcalculator.com 정도만 유사한 앵글로 존재, 나머지는 전부 점수 예측 계산기라 이 앵글은 상대적 공백 → **채택**
5. **Percentage to GPA Converter** — GSC에 "90 to gpa", "87 to gpa", "97 to gpa", "5.0 to 4.0 gpa converter", "gpa converter 9 to 4", "gpa to 100 scale" 등 **숫자 직접 변환 롱테일 쿼리가 수십 개** 누적돼 있는데, 기존 `gpa-to-letter-grade-converter.html`은 인터랙티브 계산기가 **letter↔GPA만 지원**하고 percentage/타 스케일 직접 입력은 정적 차트로만 존재 — 실제 기능 갭 확인 → **채택**

### 실제 작업: 신규 툴 2개
1. **`tools/percentage-to-gpa-converter.html`** (신규) — (1) 퍼센트/숫자 성적 → GPA 즉시 변환(표준 93/90/87... vs 대체 90/80/70/60 브레이크포인트 토글), (2) 5.0/7.0/9.0/10.0/100점 스케일 GPA → 미국 4.0 스케일 변환(비례식). `tools/gpa-to-letter-grade-converter.html`(letter↔GPA, FAQ로 percentage 몇 개만 다룸)과는 입력 방식과 핵심 기능이 명확히 달라 카니발라이제이션 아님 — 서로 상호링크로 연결. FAQPage 스키마 5문항 포함
2. **`tools/ap-credit-calculator.html`** (신규) — AP 시험 과목별(24개 과목) 점수 입력 → 최소 인정 점수(3+/4+/5) 선택 → 총 학점 + 예상 등록금 절감액(공립 재학생/공립 타주/사립 3단가 선택) 계산. 과목별 학점 기준은 공개적으로 통용되는 baseline 수치(Calc BC 8학점, 어학 6-8학점, 스튜디오아트 0학점 등) 사용, "공식 수치 아님, 학교별 상이, College Board AP Credit Policy Search로 확인" 면책 명시. 등록금 단가는 educationdata.org 2025-26 데이터 인용($411/공립재학생, $1,179/공립타주, $1,496/사립, 1개월 전 갱신 소스). `tools/ap-gpa-calculator.html`(AP 수업 성적→가중GPA)과는 완전히 다른 의도(시험 점수→학점인정)라 카니발라이제이션 아님 — 상호링크 추가. FAQPage 스키마 5문항 포함

두 계산기 모두 신규 페이지 9개 파일 체크리스트 전항목 적용: (1) 페이지 자체 (2) `assets/partials/header.html` 드롭다운 Academics 섹션에 추가 (3) noscript nav 57개 파일 일괄 치환(스크립트로 양쪽 상대경로 패턴 모두 처리, 중복 삽입 없음 확인) (4) `tools/index.html` 카드 2개 추가(24개, BeautifulSoup href 중복 0건 검증) (5) `sitemap.xml`(61 URL, XML 파싱 검증 통과) (6) `llms.txt` 신규 항목 2개 (7) 관련 기존 페이지 상호링크(`ap-gpa-calculator.html`→AP Credit Calculator, `gpa-calculator.html`→Percentage to GPA Converter — 둘 다 오늘 이미 손댄 파일이라 2주 보류 규칙과 무관). JS 계산 로직은 node로 사전 단위 테스트(90%→A−/3.7, 87%→B+/3.3, 7.25/10스케일→2.90 등) 확인 후 반영.

노스크립트 nav 스윕은 사이트 전체 57개 파일에 걸쳐 실행됐지만, **2주 재작업 보류 중인 파일들(gpa-scale.html 등)에는 nav 링크 삽입 외 다른 변경이 없음을 diff로 개별 확인** — 보류 원칙 위반 아님(신규 페이지의 사이트 전역 내비게이션 반영은 07-16 0-B 세션에서 이미 "재작업 보류 원칙은 신규 페이지 제작에 적용 안 됨"으로 정리된 사항).

커밋 `ba33140`, push 완료, Pages 빌드 `built` 확인 완료(commit sha 일치). 사이트 전체 65개 파일 JSON-LD 재검증 통과, sitemap(61 URL) XML 파싱 검증 통과, tools/index.html 24개 카드 / blog/index.html 29개 카드 모두 중복 0건.

### 추가: 신규 블로그 1건 (사용자 지적 반영)
신규 툴 2개만 만들고 블로그는 안 만든 것에 대해 사용자가 "블로그는 신규 없어?"라고 지적 — 07-16 세션(0-C)에서도 동일한 패턴의 지적이 있었고 그때 정리한 원칙("신규 확장이 툴 하나로 끝나면 안 되고 블로그도 있어야 함, 툴+블로그 짝짓기로 카니발라이제이션 없이 확장")을 이번에도 놓쳤던 것 — **다음 세션부터는 신규 툴을 만들 때 짝이 되는 블로그도 항상 같은 세션에 함께 검토할 것 (자동으로 떠올릴 것, 지적받고서야 하지 말 것)**.

- **`blog/ap-credit-vs-placement.html`** (신규, 1,524단어) — 오늘 만든 `ap-credit-calculator.html`과 짝. "AP credit"과 "AP placement"의 실질적 차이(학점 총량 감소 여부)를 비교표 + 워크스루 예시(Maria/Devon)로 설명, 4가지 결과 조합 비교표, 학교 유형별 정책 경향, 전략적 활용법. 경쟁 확인 결과 sparkl.me 등 유사 주제 텍스트 글은 이미 존재하지만, 오늘 만든 인터랙티브 계산기와 결합된 자산이라는 차별점으로 진행 결정. 반대로 percentage-to-gpa-converter.html 짝 블로그(국제 성적 스케일 비교 등)는 **오늘 만든 툴 페이지 자체 본문이 이미 breakpoint/스케일 변환 설명으로 충분히 두꺼워서(FAQ 5개 포함) 별도 블로그를 만들면 같은 세션 내 자기잠식 위험이 크다고 판단해 보류** — 이 판단 기준(같은 세션에 만든 툴의 본문이 이미 깊으면 블로그 생략 가능)은 다음에도 참고할 것
- blog/index.html cat-academics 최상단 카드 추가(30개, 중복 0건), sitemap.xml(62 URL), llms.txt, `ap-credit-calculator.html`에 상호링크 추가. 커밋 `dfacf37`, push 완료

### 추가 작업 (같은 세션 계속 진행 — 사용자가 "할 수 있는 만큼 계속 하라"고 명시적으로 요청)

**백로그 보강 2건 마저 처리** (바로 아래 "다음 세션 참고사항"에 있던 v9 이월 항목 1, 2번):
- `tools/student-loan-vs-salary.html` — FAQPage 스키마 누락 버그 수정(기존 3문항 있었는데 스키마 없었음, 이 세션에서만 벌써 4번째 동일 유형 버그 발견) + FAQ 신규 2개("percent of income", "minimum salary threshold" 쿼리 대응)
- `blog/what-is-a-good-gpa-in-college.html` — 동일 버그 수정 + FAQ 신규 2개("good cumulative gpa", "is a 3.75 gpa good" 정확매칭)
- 둘 다 sitemap/blog-index/llms.txt 체크리스트 반영. 커밋 `5ce5acd`

**신규 블로그 추가 1건** (v8 0-D 백로그 "A(비교 페이지)" 후보 중 착수):
- `blog/deans-list-vs-latin-honors.html` (1,216단어) — Dean's List(학기 단위, 반복 가능) vs Latin Honors(졸업 시 1회, 누적GPA 기반)의 핵심 차이, Fixed GPA cutoff vs percentile-of-class 두 산정 방식 비교, 왜 한쪽만 받는 경우가 생기는지 실제 시나리오, 이력서 기재 전략. 경쟁 확인 결과 대학 registrar 개별 페이지 위주라 상대적으로 덜 포화됨 확인 후 진행
- blog/index.html cat-academics 최상단(31개 카드), sitemap(63 URL), llms.txt, 상호링크 3곳(what-is-a-good-gpa-in-college.html, what-is-the-deans-list-gpa-requirement.html[2주 보류 대상이지만 신규 페이지 링크 추가 예외 적용], glossary.html). 커밋 `f444d58`, push 및 빌드 확인 완료

이로써 이번 세션 v9 백로그 3개 항목(financial-aid-calculator 보강은 첫 세션에 완료, student-loan-vs-salary/what-is-a-good-gpa-in-college 보강은 이번에 완료) 전부 소진, v8 0-D 백로그 "Dean's List vs Latin Honors" 항목도 완료 — 아래 "다음 세션 참고사항"의 관련 문구는 갱신된 것으로 간주.

### AdSense 재검토 관련 (갱신)

사용자가 이번 세션에 **재검토를 이미 제출했음을 확인**. 결과 여부는 아직 언급 없음 — 다음 세션에서 결과 나왔는지 확인할 것(최우선 체크리스트에서는 제외, 일반 확인 사항으로 격하).

### 다음 세션 참고사항
- **방향 전환 유지**: 앞으로 매 세션 보강 작업과 별개로 신규 확장 후보를 적극적으로 검토할 것. "경쟁이 세다"는 이유만으로 후보를 통째로 기각하지 말고, 경쟁이 센 헤드 키워드 안에서도 **차별화된 롱테일 앵글**(예: 점수 예측 대신 학점/비용 환산, 인도 CGPA 대신 미국 숫자 성적)이 있는지 먼저 확인
- **백로그 갱신**: v9의 `student-loan-vs-salary.html`, `what-is-a-good-gpa-in-college.html` FAQ 보강 항목은 그대로 유효(이번 세션엔 신규 확장에 집중하느라 보류)
- **다음 신규 후보(모니터링)**: SAI/EFC — 경쟁은 세지만 검색량 자체는 매우 큰 카테고리라 GSC에 관련 노출이 잡히기 시작하면 재검토. Dean's List vs Latin Honors 비교 글(v8 0-D 백로그, 계속 유효). 국제 성적 환산(A-level, ATAR 등) — 이번엔 검토 안 했으나 다음 세션 후보로 고려 가능
- **신규 툴 2개는 아직 GSC/색인 반영 전** — 다음 세션에서 Coverage 리포트에 잡히는지 확인할 것

---


## 0-★. 07-18 세션 작업 내역 (★★ 최신, 맨 위에서부터 읽을 것)

### GSC 데이터 분석 (07-18 export, 07-16 대비 큰 변화 없음)
- Coverage: 심각한 문제 구성 07-16과 동일 — 리디렉션 3(조사 안 함) / noindex 1(정상, 404 스텁) / 404 1(검증 중) / 발견-미색인 21 / 크롤링-미색인 0. 07-16에 21건으로 줄었던 "발견됨-미색인"이 07-18에도 21건 유지 — 색인 진행이 정체된 건 아니고 이 시점에 새로 추가된 페이지(act-superscore-calculator, new-act-format 블로그, glossary, grad-plus-vs-private-loans)가 아직 발견-대기 큐에 쌓여있을 가능성 있음. 다음 세션에서 계속 관찰할 것.
- Performance: 상위 쿼리/페이지 리스트가 07-16 세션들에서 분석한 것과 거의 동일한 롱테일 클러스터로 구성돼 있어(전체 사이트 클릭 여전히 0에 수렴, 노출만 축적 중) 새로운 클러스터 발굴보다는 **기존 백로그(0-A 섹션 하단 다음 세션 백로그) 우선 처리**로 판단하고 진행함.
- 07-16에 신규 생성한 4개 페이지(act-superscore-calculator, new-act-format-2025-2026-changes, glossary, grad-plus-vs-private-loans-2026)는 아직 이번 Performance 리포트 상위 페이지 리스트에 노출되지 않음 — 생성 후 2일 시점이라 정상, 인덱싱/랭킹 반영에 시간 필요.

### 이번 세션 우선순위 판단 (수익화 관점)
2주 재작업 보류 대상 파일(07-16 세션 5개 파일, 07-13/07-11 세션 파일들)을 모두 제외한 뒤, 임프레션과 현재 순위(1페이지 근접도)를 기준으로 아래 4개 파일을 이번 세션 작업 대상으로 선정:

1. **`blog/what-gpa-do-you-need-to-graduate-college.html`** (55 노출, 순위 **11.42** — 홈페이지 다음으로 사이트 전체 2번째로 좋은 순위, 1페이지 진입 임박) — GSC 쿼리 "what does your gpa need to be to graduate"(순위 11, 정확히 이 페이지 타겟 의도와 일치)에 직접 대응하는 FAQ 문항이 없었음(제목엔 반영돼 있지만 FAQ 텍스트로는 없었음) → **최우선으로 선정**
2. **`tools/gpa-calculator.html`** (14 노출, 순위 24.29, 사이트 대표 GPA 계산기) — 기존과 동일한 유형의 버그 재발견: FAQ 텍스트(5개 문항)는 있는데 **FAQPage 스키마가 누락**돼 있었음. 순위도 괜찮은 편이라 스키마 추가로 리치 스니펫 노출 시 CTR 개선 기대
3. **`tools/financial-aid-calculator.html`** (17 노출) — v8 문서 0-A 섹션 백로그 1번 항목, 이미 착수 승인된 상태. "will i qualify for financial aid calculator", "how much financial aid can i get" 등 자격/한도 관련 쿼리에 대응하는 FAQ가 없었음(기존 FAQ는 계산기 사용법 위주) → 신규 FAQ 2개 추가
4. **`blog/weighted-gpa-calculator-ap-classes.html`** — 임프레션 자체는 GSC 페이지 리스트 상위에 없지만, **또 동일한 유형의 버그** 발견: FAQ 텍스트(4개 문항, "Weighted vs unweighted GPA" 섹션 포함)는 있는데 FAQPage 스키마가 누락돼 있었음. 이 페이지는 **v8 0-D 섹션에서 백로그로 남겨뒀던 "Weighted vs Unweighted GPA 비교 전용 페이지" 신규 제작 아이디어를 재검토하다가 발견** — 확인해보니 이 기존 글 안에 이미 "Weighted vs unweighted GPA: which matters for college admissions?" H2 섹션 + 상세 비교표 + FAQ까지 있어서, **신규 페이지를 또 만들면 카니발라이제이션**이었음. → **신규 페이지 제작 대신 이 기존 글의 스키마 버그 수정으로 대체 결정**, v8 백로그의 해당 항목은 이걸로 해소된 것으로 간주하고 제거

### 신규 콘텐츠 검토 결과 (진행 안 함, 이유 명시)
- 사용자가 신규 콘텐츠 착수 시 중복 확인 + 경쟁 키워드 조사를 요청함에 따라, "weighted GPA to unweighted GPA 변환" 관련 신규 페이지 여부를 웹 검색으로 확인함 — num8ers.com이 `weighted-to-unweighted-gpa-converter` 전용 페이지를 이미 운영 중이며 콘텐츠 완성도도 높음. 게다가 위에서 확인했듯 **우리 사이트 자체에 이미 이 주제를 다루는 페이지가 2개**(`tools/weighted-gpa-calculator.html`— FAQ로 변환 공식 보유, `blog/weighted-gpa-calculator-ap-classes.html`— 서술형 비교 섹션 보유) 존재해서 3번째 페이지를 만드는 건 자기잠식 위험이 큼 → **신규 페이지 보류, 기존 2개 페이지 보강으로 충분하다고 판단**(이번 세션엔 위 4번 항목으로 blog 쪽만 스키마 수정, tool 쪽은 07-16에 이미 FAQ 추가되어 07-30까지 재작업 보류 대상)
- 그 외 완전히 새로운 검색의도를 가진 미커버 쿼리 클러스터는 07-18 GSC 데이터에서 추가 발견되지 않음 — 신규 페이지 후보 없음, 이번 세션은 보강 위주로 진행

### 실제 작업 내역 (4개 파일, 보강 체크리스트 4개 항목 적용)
1. `blog/what-gpa-do-you-need-to-graduate-college.html` — FAQ 신규 1개("What GPA do you actually need to be to graduate?", GSC 쿼리 정확 매칭), dateModified/화면 날짜 07-18 갱신, blog/index.html cat-academics 섹션 최상단 이동
2. `tools/gpa-calculator.html` — FAQPage 스키마 신규 추가(버그 수정, 기존 5개 FAQ 텍스트 그대로 스키마화, 신규 문항 추가는 안 함 — 명확한 쿼리 갭이 없었음)
3. `tools/financial-aid-calculator.html` — FAQ 신규 2개("will I qualify", "how much can I get" 자격/한도 문의 대응)
4. `blog/weighted-gpa-calculator-ap-classes.html` — FAQPage 스키마 신규 추가(버그 수정, 기존 4개 FAQ 텍스트 그대로 스키마화, weighted→unweighted 변환 관련 신규 FAQ는 추가 안 함 — 자매 파일 `tools/weighted-gpa-calculator.html`에 이미 거의 동일한 FAQ가 07-16에 추가돼 있어 중복/근접 콘텐츠 위험 판단), dateModified/화면 날짜 07-18 갱신, blog/index.html cat-academics 섹션 최상단 이동(그래프-college와 나란히 최상단 2개)

전부 sitemap.xml lastmod 07-18 갱신 완료. llms.txt는 4개 파일 전부 확인했으나 설명 문구가 이미 정확해 갱신 불필요.

blog/index.html 카드 29개 / href 중복 0건 검증(BeautifulSoup). 4개 파일 + 사이트 전체 63개 파일 JSON-LD 문법 검증(python json.loads) 통과, sitemap.xml(59 URL) XML 파싱 검증 통과.

### 이번 세션에 건드리지 않은 것
- `college-cost-calculator.html`, `act-score-calculator.html` — 관망 유지 (원칙 변경 없음)
- 07-16 세션 5개 파일(gpa-to-letter-grade-converter, degree-roi-calculator, weighted-gpa-calculator[tool], what-gpa-do-you-need-for-nursing-school, loan-repayment-calculator) — **07-30까지 재작업 보류 유지**
- 07-11/07-13 보강 파일들 — 각각 07-25/07-27까지 보류 유지 (v8 문서 그대로)
- `tools/sat-score-calculator.html` — 임프레션 93으로 높은 편이지만 확인 결과 이미 FAQPage 스키마 정상 존재 + sat-percentile-calculator.html과의 카니발라이제이션 방지 FAQ까지 잘 되어 있어 버그 없음, 순위(42.61)도 나쁘지 않아 이번 세션 후순위로 보류(백로그 유지 안 함, 특별한 개선 여지가 안 보임)
- 백로그 2, 3번(`tools/student-loan-vs-salary.html` 2 노출, `blog/what-is-a-good-gpa-in-college.html` 8 노출) — 임프레션이 아직 낮아 이번 세션은 위 4개 대비 우선순위 밀림, 백로그 유지(아래 참고)

### 다음 세션 백로그 (갱신됨)
1. `tools/student-loan-vs-salary.html` — FAQ 신규(현재 FAQ 자체 없음), "student loan minimum salary" 등 대응
2. `blog/what-is-a-good-gpa-in-college.html` — FAQ 신규(현재 FAQ 자체 없음), "is a 3.75 gpa good in college" 등 대응
3. (v8에서 이관됐던 "Weighted vs Unweighted GPA 비교 페이지" 신규 제작 아이디어는 이번 세션에 기존 페이지로 충분히 커버됨이 확인되어 **백로그에서 제거**)
4. (v8 0-D "Dean's List vs Latin Honors" 비교 페이지 아이디어는 계속 유효 — 착수 안 함, 다음 세션 후보)
5. 신규 페이지: 이번 세션 특별히 새로 발굴된 후보 없음. 다음 세션 시작 시 새 GSC export로 재확인

### AdSense 재검토 관련
사용자가 이번 세션에도 재검토 제출 여부를 언급하지 않음 — **다음 세션 시작 시 반드시 먼저 확인할 것** (계속 유효, v8/v7 문서와 동일).

---

## 0-A. 07-16 세션 작업 내역 (★ 최신, 맨 위에서부터 읽을 것)

### 배경 및 지시사항
사용자가 이번 세션에서 추가로 준 지침 (앞으로도 계속 적용):
- **AI 검색(예: ChatGPT/Perplexity 등)에서는 도메인 권위보다 콘텐츠 자체의 문제해결/비교분석 품질이 더 중요**하다는 사용자 판단 — 이후 신규/보강 작업은 이 방향(비교표, 구체적 케이스 비교, "왜"에 대한 답)을 우선시할 것
- 신규 콘텐츠 착수 전 **기존 파일과의 중복(카니발라이제이션) 확인 필수** + **웹 검색으로 경쟁 강도 확인 후 롱테일 키워드 위주로 진행**
- **수익화(AdSense 트래픽/클릭) 관점에서 우선순위 판단** — 임프레션 크고 순위 개선 여지 큰 페이지부터
- 대시보드/시각화 자료 만들지 말고 **분석 결과는 텍스트로만** 보고

### GSC 데이터 분석 결과 (07-16 export, Performance + Coverage)
- **Coverage 개선 확인**: 07-13에 있던 "크롤링됨 - 현재 색인이 생성되지 않음" 1건이 07-16엔 **0건으로 해소됨**. "발견됨 - 현재 색인 생성되지 않음"도 29건 → **21건으로 감소** (색인 진행 중, 긍정적 신호). 리디렉션 3 / noindex 1(정상, 의도된 것) / 404 1(검증 중)은 기존과 동일, 조사 불필요.
- **Performance 쿼리 분석**: 아직 전체 사이트 클릭 0에 가까움(과거 대비 큰 변화 없음, 07-13 기준 4주 GA4 오가닉 세션 11건 수준 언급됐던 것과 일관). 그러나 노출은 꾸준히 쌓이고 있고, 특히 아래 롱테일 클러스터들이 순위 70~100위권에 몰려 있어 온페이지 보강 여지가 큼:
  1. **percentage-to-GPA 숫자 변환 쿼리 클러스터** ("90 to gpa", "87 to gpa", "97 to gpa", "b in gpa" 등 15개 이상 변형, 대부분 순위 90~100위) — `gpa-to-letter-grade-converter.html`이 정확히 이 의도에 맞는 페이지인데 **FAQ 텍스트는 있었지만 FAQPage 스키마가 누락**돼 있었음 (07-09/07-13에 발견된 것과 동일한 유형의 버그, 이 파일은 그동안 점검 대상에서 빠져 있었음)
  2. **weighted-to-unweighted GPA 변환 쿼리** ("weighted gpa to gpa", "convert weighted to unweighted gpa" 등 5개) — `weighted-gpa-calculator.html`은 이미 두 값을 나란히 계산해주는 툴이지만 이 변환 관련 FAQ가 없었음
  3. **nursing GPA prerequisite 쿼리** ("what gpa do you need for nursing prerequisites", "minimum gpa for nursing school", "whats the average gpa for nursing school acceptance") — `blog/what-gpa-do-you-need-for-nursing-school.html`이 이미 순위 31.81(사이트 내 4번째로 좋은 순위)까지 올라와 있어 소폭 보강만으로 1페이지 진입 가능성 있다고 판단
  4. **degree ROI 비교 쿼리 클러스터** ("degree roi calculator", "grad school roi calculator", "law school roi calculator", "college roi calculator" 등 7개) — `degree-roi-calculator.html`도 **FAQ 텍스트는 있는데 FAQPage 스키마 누락** 버그 발견 (동일 유형)
  5. **student loan repayment plan 비교 쿼리** ("graduated repayment calculator", "parent plus loan repayment calculator" 등, 전체 repayment 관련 쿼리 임프레션 합산 시 사이트 내 최대 규모 클러스터) — `loan-repayment-calculator.html`(사이트 전체 2위 임프레션, 124회)은 FAQ 스키마는 이미 있었지만 Graduated/Parent PLUS 관련 FAQ가 빠져 있었음

- **경쟁 강도 웹 검색**: "percentage to GPA" 계열은 num8ers.com, gradeconvert.com, convertgpa.com, smartcgpa.com 등 다수의 중소 사이트가 이미 경쟁 중이나 대부분 인도 CGPA(10점 스케일) 중심 — 미국 GPA 특화 롱테일("90 to gpa" 같은 초단문 쿼리)은 상대적으로 빈 틈이 있다고 판단, 온페이지 보강으로 진행 결정. degree ROI, nursing GPA, repayment plan comparison 클러스터는 초고권위 사이트(대학 공식 사이트 정도만 상위 노출)가 장악하고 있지 않아 보강 승산 있음으로 판단.
- **college-cost-calculator, act-score-calculator**: v5~v7 원칙대로 이번에도 건드리지 않음 (헤드 키워드 경쟁 압도적, 지시 없으면 관망 유지)
- **신규 페이지 필요성 재검토**: 기존 21개 tools + 27개 blog가 주요 쿼리 코호트를 이미 커버하고 있어, 이번 세션도 v7과 동일하게 **신규 페이지 대신 기존 페이지 보강**이 우선이라고 판단 (완전히 새로운 쿼리 의도를 가진 미커버 클러스터가 GSC 데이터상 발견되지 않음). 신규 페이지 후보는 계속 없음.

### 실제 작업 내역 (5개 파일, 전부 보강 체크리스트 4개 항목 적용)
1. **`tools/gpa-to-letter-grade-converter.html`** — FAQPage 스키마 신규 추가(버그 수정) + percentage-to-GPA 관련 FAQ 4개 신규(90/87/95·97/B 관련 숫자 변환 쿼리 대응)
2. **`tools/degree-roi-calculator.html`** — FAQPage 스키마 신규 추가(버그 수정) + ROI 비교 FAQ 2개 신규(law school/grad school ROI 비교, ROI vs 단순 cost-vs-salary 비교 — 사용자가 요청한 "비교분석" 스타일 콘텐츠)
3. **`tools/weighted-gpa-calculator.html`** — weighted→unweighted 변환 FAQ 1개 신규 추가 (기존에 FAQPage 스키마는 있었음, 항목만 추가)
4. **`blog/what-gpa-do-you-need-for-nursing-school.html`** — FAQ 섹션 신규 생성(기존엔 FAQ 자체가 없었음) + FAQPage 스키마 신규 + 3개 문항(prerequisites GPA, minimum GPA, average acceptance GPA), Article dateModified 07-16 갱신, 화면 "Updated July 2026" 텍스트 갱신, blog/index.html cat-academics 섹션 최상단으로 이동
5. **`tools/loan-repayment-calculator.html`** — 기존 FAQPage 스키마에 문항 2개 추가(Graduated vs Standard 비교, Parent PLUS 대출의 상환 플랜 제약 — 역시 "비교분석" 스타일)

전부 sitemap.xml lastmod 07-16 갱신 완료. llms.txt는 5개 파일 전부 확인했으나 문구가 이미 최신이라 갱신 불필요(날짜 표기 없음, 설명 문구도 변경 내용과 어긋나지 않음).

blog/index.html 카드 재정렬 후 BeautifulSoup으로 카드 27개 / href 중복 0건 검증 완료. 5개 파일 전부 JSON-LD 문법 검증(python json.loads) 통과, HTML 파싱 이상 없음 확인.

커밋 `520779a`, push 완료, Pages 빌드 `built` 확인 완료 (commit sha 일치 확인).

### 이번 세션에 건드리지 않은 것 (재확인)
- `college-cost-calculator.html`, `act-score-calculator.html` — 관망 유지
- 07-11 보강 5개(dean's list, gpa-scale, student-loan-debt-too-much, repayment-plans-2026, grade-calculator), 07-13 첫 세션 보강 2개(how-many-as-to-raise-gpa, ib-gpa-calculator) — **아직 2주 안 지남(07-16 기준 07-25/07-27이 재작업 가능 시점)**, 손대지 않음
- `student-loan-calculator.html`, `semester-gpa-calculator.html` (07-13 두 번째 세션에 800단어 미만 보강됨), `scholarship-savings-calculator.html` (같은 세션에 보강) — 2주 이내라 재작업 보류 대상으로 새로 편입 (아래 다음 세션 체크리스트에 반영)
- `financial-aid-calculator.html`, `student-loan-vs-salary.html`, `blog/what-is-a-good-gpa-in-college.html` — 후보로 검토했으나 이번 세션 5개에 밀려 보류, 다음 세션 백로그로 이관 (아래 참고)

### 다음 세션 백로그 (신규 착수 후보, 우선순위순)
1. `tools/financial-aid-calculator.html` — "will i qualify for financial aid calculator", "financial aid cal" 등 쿼리 대응 FAQ 보강 (이미 FAQPage 스키마 있음, 항목만 추가하면 됨)
2. `tools/student-loan-vs-salary.html` — "student loan minimum salary", "salary threshold for student loan repayment" 등 대응 FAQ 신규 (현재 FAQ 자체 없음, 임프레션은 아직 낮으니 우선순위 1번보다 낮음)
3. `blog/what-is-a-good-gpa-in-college.html` — "is a 3.75 gpa good in college", "what is a good cumulative gpa" 등 대응 FAQ 신규
- 사용자에게 착수 여부 물어보지 않고 바로 진행해도 되는 원칙(v7 2번 항목) 유지되는 한, 다음 세션 시작 시 새 GSC export로 우선순위 재확인 후 바로 진행

### AdSense 재검토 관련
사용자가 이번 세션에 재검토 제출 여부를 언급하지 않음 — **다음 세션 시작 시 반드시 먼저 확인할 것** (v7 문서 9번, 15번 체크리스트 항목 그대로 유효).

---

## 0-B. 07-16 같은 날 두 번째 세션 — 신규 콘텐츠 확장

### 배경
사용자가 "보강만 하지 말고 신규도 필요하다, 최근에 너무 안 했다, 확장이 필요한 시점"이라고 명시적으로 요청. 색인 반영 대기 중이라 보강 위주로 진행해온 원칙은 유효하지만, 신규 페이지 자체를 아예 안 만든 지 오래됐다는 지적(마지막 신규 툴은 07-07 sat-percentile-calculator)에 따라 신규 1건을 제대로 만들어 진행.

### 신규 페이지 후보 검토 과정 (중복 방지 위해 기존 파일 전수 확인)
- **President's List GPA 요건** — 검토했으나 `blog/what-is-the-deans-list-gpa-requirement.html`에 이미 "Dean's List vs Honor Roll vs President's List" 비교표로 다뤄지고 있어 **카니발라이제이션 우려로 기각**
- **Subsidized vs Unsubsidized 대출 비교** — `federal-vs-private-student-loans.html`과 `student-loan-calculator.html`에 이미 상당히 다뤄지고 있어 **보류** (쿼리 볼륨도 분산되어 있어 신규 페이지보다는 향후 보강 후보로 백로그 이관)
- **do you have to pay back a scholarship / how much is a scholarship worth** — 쿼리 자체가 파편화(각 1회 노출 수준)돼 있어 독립 신규 글로는 얇은 콘텐츠(thin content) 위험 판단, **보류**
- **ACT Superscore Calculator** — GSC에 "act superscore calculator", "superscore act calculator", "act test superscore calculator" 등 뚜렷한 클러스터 존재. 웹 검색으로 확인한 결과 test-ninjas.com, tampalanguagecenter.com 등 소규모 사이트들이 이미 전용 계산기를 운영 중 — 즉 수요는 검증됐고 초대형 권위 사이트가 독점하고 있지 않아 **승산 있다고 판단, 신규 진행 결정**. 특히 GSC에 함께 잡힌 "act score calculator without science", "act score calculator no science" 쿼리가 실제로 **2025년 Enhanced ACT 개편(Science 섹션 선택制 전환, superscore는 English+Math+Reading 3과목만 반영)**과 정확히 일치함을 웹 검색으로 확인 — 시의성 있고 정확한 콘텐츠 작성 가능
- 기존 `tools/act-score-calculator.html`(단일 응시 회차 점수 계산)과는 기능이 명확히 다름(다중 응시 회차의 섹션별 최고점을 조합) — 중복 아님. `act-score-calculator.html` 자체는 v5부터 이어진 "관망 원칙"(헤드 키워드 경쟁 압도적)에 따라 **이번에도 편집하지 않음**, 대신 새 페이지에서 그쪽으로 링크만 걸어 내부 링크 구조 확장

### 실제 작업
1. **`tools/act-superscore-calculator.html` 신규 생성** (1,072 단어) — 최대 3회 응시분의 English/Math/Reading(+선택 Science) 입력 → 섹션별 최고점 자동 조합 → superscore 계산. Enhanced ACT(2025~) vs Legacy ACT 방식 비교표, 아이비리그 학교별 superscore 정책 차이(하버드·프린스턴은 미적용), superscore 기반 재응시 전략, FAQ 5개(FAQPage 스키마 포함) 수록. WebApplication + FAQPage 스키마 2개 모두 JSON 문법 검증 통과
2. **`assets/partials/header.html`** — 데스크톱/모바일 드롭다운 네비 "Test Scores" 섹션에 신규 항목 추가 (중앙 관리 파일이라 이 한 곳만 수정하면 전체 페이지 실제 노출 네비에 자동 반영됨)
3. **noscript 네비게이션 (54개 파일 전체)** — 스크립트로 일괄 치환 (`act-score-calculator` 링크 뒤에 `act-superscore-calculator` 링크 삽입, 상대경로(`../tools/`)와 루트경로(`tools/`) 두 패턴 모두 처리). `editorial-policy.html`, `methodology.html`은 원래부터 축약형 네비(Tools/Blog/About만 있음)라 대상 아님, 정상
4. **`tools/index.html`** — Test Scores 섹션에 신규 카드 추가, BeautifplSoup으로 22개 카드 전부 href 중복 없음 검증 완료(기존 21+신규 1)
5. **`sitemap.xml`, `llms.txt`** — 신규 URL 항목 추가
6. **`blog/what-is-a-good-act-score.html`** — "Related tools and guides"에 신규 계산기 링크 1줄 추가(상호링크), dateModified 07-16 갱신, sitemap lastmod도 갱신. 이 파일은 2주 재작업 제한 대상이 아니었음(마지막 수정 07-07)

커밋 `c928066`, push 완료, Pages 빌드 `built` 확인 완료 (commit sha 일치 확인). 전체 사이트 JSON-LD 문법 재검증(site-wide) 및 sitemap.xml XML 파싱 검증 통과.

### 다음 세션 백로그 갱신
0-A 섹션의 백로그(financial-aid-calculator, student-loan-vs-salary, what-is-a-good-gpa-in-college FAQ 보강)에 아래 항목 추가:
4. **신규 후보**: Subsidized vs Unsubsidized федeral loan 비교 콘텐츠 — 쿼리 볼륨이 더 쌓이면 독립 블로그 글 검토, 아직은 기존 파일들에 분산 보강하는 쪽이 안전
5. **신규 후보**: 스콜라십 상환 의무 여부(do you have to pay back a scholarship) — 쿼리 볼륨 추이 지켜보고 축적되면 착수

### 이번 세션 원칙 재확인 (다음 세션에도 적용)
- 색인 대기 중인 보강 완료 파일 재작업 금지 원칙은 **신규 페이지 제작에는 적용되지 않음** — 신규는 언제든 만들어도 됨, 다만 항상 기존 파일과의 카니발라이제이션 먼저 확인
- 신규 페이지 만들 때 체크리스트: (1) 페이지 자체 (2) `assets/partials/header.html` 드롭다운 (3) 전체 파일 noscript nav 일괄치환 (4) `tools/index.html` 또는 `blog/index.html` 카드 (5) `sitemap.xml` (6) `llms.txt` (7) 관련 기존 페이지에 상호링크 1곳 이상

---

## 0-C. 07-16 세 번째 세션 — 신규 블로그 글도 필요하다는 지적 반영

### 배경
사용자가 "블로그는 안 만들어?"라고 재차 지적 — 신규 확장이 툴 하나로 끝나면 안 되고 블로그 쪽도 신규가 필요하다는 취지. 0-B에서 만든 `act-superscore-calculator.html`과 자연스럽게 묶이면서도 그 자체와는 다른 앵글의 블로그 주제를 찾아 진행.

### 주제 선정 과정
- 신규 툴(superscore)과 겹치지 않으면서 카니발라이제이션 없는 블로그 주제를 찾기 위해 사이트 전체에서 "Enhanced ACT"(2025~2026 ACT 개편) 키워드를 검색했으나 **0건** — 사이트 어디에도 ACT 시험 자체가 어떻게 바뀌었는지(문항 수, 시간, Science 선택제, 응시료 등)를 정면으로 다루는 콘텐츠가 없었음. `what-is-a-good-act-score.html`은 퍼센타일 기준표 위주, 신규 `act-superscore-calculator.html`은 superscore 계산 방식 위주로만 Enhanced ACT를 짧게 언급 — 둘 다 "포맷이 왜/어떻게 바뀌었는지" 자체는 다루지 않음 → **완전히 빈 자리 확인, 카니발라이제이션 우려 없이 진행**
- 웹 검색으로 정확한 사실관계 확인(Kaplan, Magoosh, PrepScholar, test-ninjas 등 교차 확인): 문항수 215→131(Science 제외 시), English 75→50문항, Math 60→45문항(5지선다→4지선다), Reading 40→36문항, Science는 선택制로 전환되어 컴포지트에서 제외되고 별도 STEM 점수(Math+Science 평균)로 분리, 코어 시험시간 175분→125분, 문항당 시간 약 18~22% 증가. 롤아웃: 2025년 4월(온라인 내셔널) → 2025년 9월(종이 내셔널, 전체 3과목 컴포지트 적용) → 2026년 봄(스쿨데이/국제, 전환 완료). 2026년 기준 Legacy ACT는 완전히 폐지되어 선택지 자체가 없음 — 이 사실관계로 정확도 있는 비교분석형 콘텐츠 작성 가능하다고 판단

### 실제 작업
1. **`blog/new-act-format-2025-2026-changes.html` 신규 생성** (1,339단어) — "New ACT Format 2025–2026: Enhanced ACT vs. Legacy ACT". Enhanced vs Legacy 비교표(문항수/시간/Science 처리방식), 롤아웃 타임라인 표, Science 선택 여부 판단 기준, 기존 학습자료가 여전히 유효한지, superscore에 미치는 영향(신규 계산기로 CTA 링크), "더 쉬워진 건가?" 등 비교분석·문제해결 위주 구성. FAQ 5개 + FAQPage 스키마, Article 스키마 모두 포함. 문법 검증 통과
2. **`blog/index.html`** Test Scores 섹션에 카드 추가 (28개 카드, 중복 없음 확인)
3. **`sitemap.xml`, `llms.txt`** 신규 URL 반영
4. **상호링크**: `tools/act-superscore-calculator.html`과 `blog/what-is-a-good-act-score.html` 양쪽의 "Related tools and guides"에 신규 글 링크 추가 (전자는 오늘 신규 생성 파일이라 제한 없음, 후자는 마지막 수정이 오늘(07-16) 이지만 같은 세션 내 후속 수정이라 문제 없음 — sitemap lastmod/dateModified는 이미 07-16으로 반영돼 있어 재갱신 불필요)

커밋 `5a02acd`, push 완료. GitHub Actions "pages build and deployment" 워크플로에서 해당 커밋 `completed success` 확인(legacy `/pages/builds/latest` API는 일시적으로 이전 커밋을 보여주는 지연이 있었으나, Actions 로그 기준으로는 정상 배포 확인됨 — 다음 세션에서 한 번 더 최신 커밋 기준으로 빌드 상태 재확인 권장). 사이트 전체 JSON-LD 재검증, sitemap.xml 파싱 검증 통과, blog-card 28개/tool-card 22개 중복 없음 확인.

### 이번 세션에서 배운 점 (다음 세션 참고)
- "보강 위주로 진행"이 곧 "신규는 안 해도 된다"는 뜻이 아님 — 사용자가 명시적으로 지적하기 전까지 신규 착수가 뜸했던 점 반성. 앞으로는 **보강 작업과 별개로, 매 세션 최소 신규 후보 1~2개는 항상 함께 검토**할 것
- 신규 툴을 만들 때는 그 툴과 자연스럽게 짝을 이루는 블로그 글(또는 반대로 블로그를 만들 때 짝이 되는 툴)도 같이 고려하면 카니발라이제이션 걱정 없이 신규 콘텐츠를 늘릴 수 있음 — 이번 superscore 계산기 + Enhanced ACT 개편 설명 글 조합이 좋은 예시

---

## 0-D. 07-16 네 번째 세션 — "확장을 더 많이 해야 한다" / 장기 롱테일 전략 논의 + 신규 콘텐츠 유형 2개 도입

### 배경
사용자가 "지금 페이지 수가 너무 적다, 색인이 반쯤 잡힌 지금이 확장할 때다, tool/blog 말고 추가할 만한 게 있나?"라고 요청. **바로 만들지 말고 먼저 방향을 정하자**는 사용자 요청에 따라, 실행 전에 옵션을 정리해서 논의 후 결정하는 방식으로 진행함(이 패턴은 앞으로도 "구조적 결정"이 필요한 순간에는 반복 적용할 것 — 예: 새 콘텐츠 유형 도입, 사이트 구조 변경 등).

### 논의된 옵션과 결론
tool/blog 외 콘텐츠 유형 후보로 다음을 제시:
- **A. "X vs Y" 비교 전용 페이지** — AI 검색이 비교분석 콘텐츠를 선호한다는 기존 원칙과 가장 직접적으로 부합. 페이지당 검색의도 뚜렷하고 경쟁 상대적으로 낮음
- **B. 용어사전(Glossary)** — 정의성 롱테일 쿼리("what is X") 대량 흡수에 유리, 확장성 좋음
- **C. "Is X worth it" 판단형 페이지** — degree-roi-calculator, is-college-degree-worth-the-debt.html과 결이 겹칠 위험 있어 보류
- **D. 주(state)별 정보 페이지** — 페이지 수는 폭발적으로 늘릴 수 있으나 정확성 유지 부담과 E-E-A-T 리스크 커서 지금 규모에는 보류 결정

**사용자 결정: A+B 병행**, 단 "가치없는 콘텐츠로 안 걸리게" 퀄리티 담보 조건부.

### 품질 안전장치 (다음에도 이 원칙 유지)
- **B(용어사전)의 핵심 리스크**: 용어별 개별 페이지 20~30개를 만들면 정의 한두 줄짜리 얇은 페이지가 무더기로 생겨 AdSense "가치없는 콘텐츠" 재검토에 불리하게 작용할 수 있음 → **개별 페이지 대신 단일 허브 페이지**로 구성해 해결 (용어당 정의+예시+관련 툴 링크 포함, 전체 분량 확보). 향후 특정 용어의 검색량이 GSC에서 확인되면 그때 개별 페이지로 승격하는 방식으로 확장할 것 (지금은 승격 안 함)
- **A(비교 페이지)**: 기존 tool/blog와 동일한 품질 기준(800~1200단어, 비교표+FAQ+스키마) 그대로 적용하면 리스크 없음 — 이미 검증된 방식 반복

### 실제 작업
1. **`glossary.html` 신규 생성** (루트 경로, 1,759단어) — "GPA & Academics"(9개) / "Financial Aid & Loans"(13개) / "Test Scores"(6개) 3개 카테고리, 총 28개 용어. 용어당 정의 + 실용적 설명 + 관련 기존 툴/블로그로 내부링크. `DefinedTermSet`/`DefinedTerm` 스키마 사용(용어사전에 가장 적합한 schema.org 타입). 카테고리 점프 목차(TOC) 포함
2. **헤더 네비게이션 구조 변경**: `assets/partials/header.html`에 최상위 메뉴 **Glossary**를 Blog와 About 사이에 신규 추가 (데스크톱+모바일 양쪽) → Tools / Blog / Glossary / About 4개 구조로 확장. noscript nav 58개 파일 전체에 스크립트로 일괄 반영(전체 tool-list 버전과 축약형 버전 둘 다 처리)
3. **`blog/grad-plus-vs-private-loans-2026.html` 신규 생성** (1,584단어) — "Grad PLUS vs. Private Loans for Grad School: What Changed in 2026". 2026년 7월 1일부로 Grad PLUS 대출이 신규 차입자에게 차단된 정책(OBBBA 법안) 반영. Legacy borrower vs New borrower 판정 기준, Grad PLUS/Direct Unsubsidized/Private Loan 3자 비교표, 신규 연방 대출 한도, PSLF 관련 함정(Tiered Standard는 PSLF 미적용, RAP 별도 신청 필요), 진행 중인 법적 소송 현황까지 언급(구체적 수치는 계속 유동적이라 "학교에 직접 확인" 안내 포함해 정확성 리스크 관리). 웹 검색으로 Kaplan/Credible/여러 대학 재정지원처 공식 페이지 교차 확인해 사실관계 정확도 확보
4. **`blog/index.html`** Student Loans 섹션에 카드 추가 (29개 카드, 중복 없음 확인) — glossary.html은 tool/blog 어디에도 속하지 않는 독립 콘텐츠라 인덱스 카드 없음(내비게이션 메뉴로만 접근)
5. **`sitemap.xml`, `llms.txt`** 신규 URL 2개 반영 (glossary.html은 새 "## Reference" 섹션으로 llms.txt에 분리 등록)
6. **상호링크**: `federal-vs-private-student-loans.html`의 "Related tools and guides"에 신규 Grad PLUS 글 링크 추가, dateModified/sitemap lastmod 07-16 갱신 (이 파일은 07-13에 금리 수정만 있었고 2주 재작업 제한 대상 아님)

커밋 `3f74eb2`, push 완료. GitHub Actions 빌드 `completed success` 확인 완료. 사이트 전체 JSON-LD 재검증(63개 파일 변경분 포함) 통과, sitemap.xml 파싱 검증 통과(59개 URL), blog-card 29개 중복 없음 확인.

### 다음 세션 참고사항
- **A(비교 페이지) 후보 백로그** (이번에 Grad PLUS 1건 진행, 나머지는 다음 세션에):
  - Weighted vs Unweighted GPA — 왜 다르게 계산되는지, 대학 입시 관점, 학교별 가중치 스케일 예시 등 깊이 있는 별도 글 (지금은 weighted-gpa-calculator.html 안에 짧은 FAQ로만 존재)
  - Dean's List vs Latin Honors(cum laude 등) — 재학 중 우등 vs 졸업 시 우등, 시점이 달라 dean's-list 글과도 안 겹침
  - (ACT vs SAT는 헤드키워드 경쟁 너무 세서 계속 제외)
- **B(용어사전) 확장 전략**: 지금은 허브 1페이지, 다음 GSC 데이터에서 특정 용어("discretionary income", "capitalized interest" 등)의 검색 임프레션이 확인되면 그 용어만 골라 독립 페이지로 승격 검토. 무분별하게 개별 페이지부터 늘리지 말 것
- **사이트 구조가 Tools/Blog/Glossary/About 4단으로 늘어났음** — 다음에 새 콘텐츠 유형(예: C나 D)을 추가로 도입하게 되면 헤더 네비게이션 공간과 모바일 드롭다운 구조를 다시 검토해야 할 수 있음

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
2c0c441 신규 툴 추가: tools/interest-capitalization-calculator.html — 학자금 대출 이자 자본화 계산기. 6개 후보 웹 검색 경쟁조사 후 5개 기각(LSAC/AMCAS GPA, UK 학위환산, PSAT, NCAA 자격, RAP 전부 경쟁사 5곳+), capitalization은 경쟁사 1곳뿐이라 채택. 신규 페이지 체크리스트 9개 항목 전부 적용 (07-20 두번째 세션)
9458ca2 GSC 07-20 재분석 기반 보강: how-to-raise-your-gpa-in-one-semester.html FAQ 신규(임프레션 2위·순위11 페이지, CTR 개선 목적) + sat-score-calculator.html FAQ 1개 + 전체 스캔으로 발견한 FAQPage 스키마 누락 버그 7건 일괄 수정 (07-20 세션)
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
9. 07-11에 보강한 5개 파일 + 07-13에 보강한 2개 파일(how-many-as-to-raise-gpa, ib-gpa-calculator)은 최소 2주는 재작업하지 말 것 — 색인 반영 시간 필요 (★ 07-16 추가: `gpa-to-letter-grade-converter.html`, `degree-roi-calculator.html`, `weighted-gpa-calculator.html`, `blog/what-gpa-do-you-need-for-nursing-school.html`, `loan-repayment-calculator.html` 5개도 동일하게 07-30까지 재작업 보류. 상세는 맨 위 0-A 섹션 참고)
10. **연방 대출 금리는 매년 7월 1일 갱신됨을 기억할 것** — 다음 갱신은 2027-07-01이니 그 전까지는 6.52%/8.07%/9.07%가 맞는 숫자. 매 세션 시작 시 "지금 몇 월인지" 확인해서 회계연도 넘어갔으면 사이트 전체 금리 재점검
11. 작업 완료 후 커밋/푸시 → Pages 빌드 `built` 확인까지 끝내고, **사용자가 직접 확인해야 할 URL을 클릭 가능한 링크로 정리해서 제시** (사용자는 영어를 몰라서 콘텐츠 검수가 아니라 화면이 깨졌는지만 육안 확인함 — 문구 검수 요청하지 말 것)
12. 세션 끝나면 토큰 revoke 리마인드
