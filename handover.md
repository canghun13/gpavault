# GPA Vault 인수인계 문서 v9 (2026-07-18 세션 반영)

이전 v8 문서를 대체함. v8(및 그 이전 버전들)의 배경 설명은 그대로 유효하므로 필요시 참고. 이 문서는 **07-18 세션(GSC 데이터 재분석 + 보강)**에서 바뀐 것 위주로 맨 위에 정리하고, 이전 v8 본문은 아래에 그대로 보존.

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
