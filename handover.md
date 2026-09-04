# GPA Vault 인수인계 문서 v26 (2026-09-02 세션 — 신규 클러스터 "학생 건강보험 waiver" 개설)

이전 v25 문서를 대체함. v25 이하 본문은 아래에 그대로 보존.

### 0단계 대조 결과
최신 커밋 `5a956af`(09-01 handover v25)와 v25 기록 일치 — 소급 기록 불필요.

### ★ 먼저 확인할 것 (계속 유효)
- v19 **색인 수동 제출 금지**(IndexNow·구글 색인 요청 안 함).
- v21 **구글 색인 이탈에 패닉 재작성 금지.** 판단 지표는 GA4 활성 사용자 + Bing 클릭.
- v22 **LSAC 2026-07-28 규정 추적 의무.**
- v24 **`gpa-raise-calculator`는 더 손대지 말 것.**

### 이번 세션의 성격
사용자 지시는 08-25·08-26·09-01과 동일(신규·폭넓게·경쟁강도·클러스터 추가·외부 소스). **이번 주도 GSC/Bing/GA4 자료는 제공되지 않았고 참조하지 않았다.**

---

## ★★★★★ 신규 클러스터 개설: 학생 건강보험 waiver

기존 11개에 이어 **12번째 클러스터**.

### 후보 2개 → 1개 기각 (재조사하지 말 것)

| 후보 | 판정 | 근거 |
|---|---|---|
| 장애 학생 편의제공(IEP/504의 대학 전환) | 기각 | Understood.org, Wrightslaw, LD Advisory(2편), MRM Education, Potter Law, ed-testing, essentialcollegecoaches, affordablecollegesonline 등 **전문 매체 9곳+ 포화**. 전문성 우위를 주장하기 어려운 도메인이라 롱테일로도 부적합 |
| **학생 건강보험 waiver** | **채택** | 아래 |

### 왜 채택했나
- ★ **검색 결과가 전부 .edu였다** — UCI, UCSD, WashU, UMD, UCSF, DU, 버클리, UC데이비스, UCSB. 독립 학생용 가이드도 계산기도 확인되지 않았다. SAP·R2T4·repeat coursework와 **완전히 동일한 공백 패턴**이고, 이 패턴은 이제 4번째로 통했다.
- ★ **체크리스트 53번(기본값이 사용자에게 불리한 제도)에 정확히 부합.** 가만히 있으면 연 $2,000~$4,000이 자동 청구된다(UMD 기준 $2,939).

### 확인한 규정 (모두 .edu 원문 교차 확인)
- 대상 학생을 학교 플랜에 **자동 등록**하고 등록금 고지서에 보험료를 얹는다. 학부는 통상 6학점 이상이 기준.
- **waiver는 1학년도만 유효** — 매년 다시 해야 한다.
- 마감 후 **지각 창구**가 있는 학교가 많다(수수료 $50~$90, UCI $50 / 버클리 $75 / UCSF $88). 대개 2주~30일.
- 여러 학교가 **"공지를 못 읽은 것은 예외 사유가 아니다"**라고 명시(DU). 보장이 이미 구매돼 8/1로 소급 적용되기 때문.
- **중간 재검증**: 1월에 플랜이 바뀌는 학생이 응답하지 않으면 가을 승인분이 있어도 봄에 청구됨(UCSB).
- **F-1/J-1은 상당수 학교에서 waiver 불가** — 미국 고용주 플랜(미국 보험사)만 인정(WashU).
- 승인돼도 **계정에 hold가 있으면 크레딧이 반영되지 않는다**(UCSD).
- waiver 취소 시 보험료는 **일할 계산되지 않는다**(UC데이비스).

### 신규 2건 (쿼리셋 분리)

**1. `tools/health-insurance-waiver-calculator.html` (1,304단어)** — 질문: "놓치면 얼마인가"
3분기 비교(정시 $0 / 지각 창구 $50~90 / 둘 다 놓침 학기당 전액).
★ 핵심 수치: **$2,939 기준 마감 놓침 $1,470 vs 지각 신청 $75 — 약 20배 차이.** 이미 놓친 사용자에게 "오늘 지각 창구가 열려 있는지 확인"이 최고 효율 행동임을 산출로 제시.
★ 두 번째 축: **남은 재학기간 누적 손실**(3년이면 $8,817). 1학년에 성공하고 2학년에 잊는 것이 가장 흔한 손실 경로다.

**2. `blog/student-health-insurance-waiver-deadline.html` (1,341단어)** — 질문: "이게 뭐고 어떻게 처리하나"
기각 사유 대부분이 "플랜이 부실해서"가 아니라 **가입 확인 실패**이므로 이의신청 가능하다는 점, 그리고 **중간 재검증** 때문에 가을 승인분이 있어도 봄에 청구될 수 있다는 점(거의 아무도 안 다룸)을 포함.

### ★ 안전장치 (보험 주제라 특별히 처리 — 다음 세션도 이 원칙 유지)
"보험 자문 아님"을 명시하고, **waiver를 무조건 권하지 않도록 반례 2개를 양쪽 페이지에 배치**했다:
1. 타 보험에 캠퍼스 인근 네트워크가 없으면 보험료보다 out-of-network 비용이 클 수 있다
2. **대안이 무보험이면 waiver는 절약이 아니라 도박**이다 — 계산기도 "타 보험 없음"을 선택하면 **"waive하지 말라"고 명시적으로 출력**하도록 분기 처리했다

돈 절약을 다루는 도구가 사용자를 무보험으로 밀어내면 안 된다. 이 페이지를 수정할 때 이 분기를 제거하지 말 것.

### 중복 확인
`health insurance` 언급은 기존 3개 파일에서 1~3회 부수적 언급뿐. 전용 문서 없음. `college-cost-calculator`와는 역할이 다르다(총비용 추정 vs 단일 청구항목의 마감 리스크).

### 검증
파이썬 모델 ↔ jsdom 8개 시나리오 일치. getComputedStyle 3경로 확인. node --check 통과.
**작성 중 사고 2건을 배포 전에 잡았다**: ① 존재하지 않는 `blog/hidden-college-fees.html`을 참조 → 실제 파일로 교체 ② FAQ 본문에 물음표가 빠져 스키마와 7:6 불일치 → 수정 후 7:7.

---

## ★ 다음 세션이 확인/처리할 것

1. **금지 원칙 4종 유지.**
2. **★★ 최우선: 신규 페이지의 Bing 노출 점검.** v24에서 9개, v25에서 11개, 이번에 **13개**가 됐고 **여태 하나도 Bing에 잡힌 적이 없다**(가장 오래된 r2t4는 09-02 기준 3주 경과). 다음에 데이터를 받으면 이것부터 볼 것.
   - 하나라도 잡히면 신규 확장 재개.
   - 여전히 0이면 **4주 이상 걸린다는 뜻**이므로 세션 배분을 보강 쪽으로 더 옮길 것. 페이지 삭제나 전략 변경은 선택지가 아니다.
3. **08-31 보강 3건 효과 확인**: `obbba-loan-limit-calculator`, `pell-lifetime-eligibility-calculator`, `what-is-the-deans-list-gpa-requirement`(**CTR 0.24%가 기준선**).
4. **CTR 처방 확대 후보**(체크리스트 49번): `what-gpa-do-you-need-to-graduate-college`(Bing 91노출 3.56위 클릭 0), `new-act-format-2025-2026-changes`(29노출 6.59위 클릭 0), `weighted-gpa-calculator-ap-classes`(25노출 8위 클릭 0).
5. **수익화 — 임계치 근접.** 08-31 기준 세션 151/4주, 검색 클릭 33(기준 50의 66%). 돌파하면 그때 제휴 제안.
6. **계절성 총정리** — 비수기 데이터로 실패 판정 금지:
   - 교육 세금: 1~4월
   - 대학원 조교: 10~12월, 3~5월
   - 과목 결과 선택: 학기말(12월, 5월)과 철회 마감 직전(10월, 3월)
   - **학생 건강보험 waiver: 7~9월(가을 waiver 창구)과 12~1월(봄 학기·플랜 갱신). 지금이 성수기 끝자락이라 이번 클러스터는 비교적 빨리 신호가 나올 수 있다.**

## 2주 재작업 보류 현황 (09-02 기준)
- **09-07까지**: `tools/employer-tuition-assistance-calculator.html`, `blog/does-retaking-a-class-replace-your-gpa.html`
- **09-08까지**: `tools/dual-enrollment-gpa-calculator.html`, `blog/does-dual-enrollment-affect-your-gpa.html`
- **09-09까지**: `tools/graduate-assistantship-tax-calculator.html`, `blog/why-did-my-grad-stipend-paycheck-drop.html`
- **09-14까지**: `tools/obbba-loan-limit-calculator.html`, `tools/pell-lifetime-eligibility-calculator.html`, `blog/what-is-the-deans-list-gpa-requirement.html`
- **09-15까지**: `blog/incomplete-vs-withdrawal-vs-failing.html`, `blog/how-to-ask-for-an-incomplete-grade.html`
- **09-16까지**: 이번 세션분 — `tools/health-insurance-waiver-calculator.html`, `blog/student-health-insurance-waiver-deadline.html`
- **보류 해제**: 08-19 이전 전체
  (이번 세션에 **상호링크만** 추가한 6개는 보류 예외, lastmod 미갱신)

## 파일 현황 (09-02 기준)
- tools **46개** + index / blog **61개** + index / 루트 7개
- sitemap URL **113개**, tool-card 46개(미등록 도구 0), blog-card **59개**(미등록 1건 = 404 스텁)
- 전체 117개 HTML JSON-LD 오류 0, 내부링크 broken 0

## 클러스터 현황 (12개)
GPA 계산/변환 · 시험점수 · 연방지원 규정 · 학자금대출 · 전공·커리어 ROI · 유학 · 학사경고·복학 · 교육 세금 · 이중등록 · 대학원 조교 펀딩 · 과목 결과 선택 · **학생 건강보험 waiver(신규)**

### 아직 비어 있는 영역 (경쟁조사 미실시)
홈스쿨 성적증명 · 로스쿨 준비(LSAT/GPA) · CLEP/사전학습인정(CPL)
→ **기각 완료(재조사 금지)**: 유학생 F-1 재정증명, 근로장학, Academic renewal, Workforce Pell, PhD 스티펜드 비교, NCAA 자격, 장학금 displacement, 리테이크 GPA 계산기, GI Bill MHA, 성적증명 보류(stranded credits), Incomplete 전용 계산기, **장애 학생 편의제공**

### ★ 다음 신규 후보를 찾을 때 (남은 3개가 소진되면)
체크리스트 53번 구조("가만히 있으면 손해 보는 마감/기본값")가 두 세션 연속 통했다. 같은 구조의 미탐색 후보: 기숙사·식사플랜 계약 해지 마감, 등록금 환불 일정(100%/50%/0% 구간), 졸업 신청 마감(놓치면 한 학기 지연), 수강신청 후 미납으로 인한 일괄 취소(purge). 전부 .edu 중심일 가능성이 높다.

## 체크리스트 추가분 (v25 51~53번에 이어서)
54. **돈을 아끼는 도구가 사용자를 더 큰 위험으로 밀어내지 않게 분기를 넣을 것.** 09-02 건강보험 계산기는 "타 보험 없음"을 선택하면 절약액을 계산하는 대신 **waive하지 말라고 출력**한다. 절약 계산은 대안이 존재할 때만 절약이다.
55. **Related 섹션에 링크를 쓸 때 실제 파일 존재를 확인할 것.** 09-02에 존재하지 않는 `blog/hidden-college-fees.html`을 참조했다가 배포 전 전수 스캔에서 잡았다. 기억으로 파일명을 쓰지 말고 `ls blog/`로 확인할 것.
56. **FAQ 본문·스키마 동기화 검사는 물음표 기준 정규식이므로, 본문 질문이 물음표로 끝나지 않으면 카운트가 어긋난다.** 09-02에 7:6이 나온 원인이 이것이었다. 불일치가 나오면 개수만 맞추지 말고 **어느 항목이 빠졌는지 출력해서 확인**할 것.

---

## [보존] 이전 문서 v25 본문 (2026-09-01 세션까지)

# GPA Vault 인수인계 문서 v25 (2026-09-01 세션 — 신규 클러스터 "과목 결과 선택(Incomplete/W/F)" 개설)

이전 v24 문서를 대체함. v24 이하 본문은 아래에 그대로 보존.

### 0단계 대조 결과
최신 커밋 `fb5f4af`(08-31 handover v24)와 v24 기록 일치 — 소급 기록 불필요.

### ★ 먼저 확인할 것 (계속 유효)
- v19 **색인 수동 제출 금지**(IndexNow·구글 색인 요청 안 함).
- v21 **구글 색인 이탈에 패닉 재작성 금지.** 판단 지표는 GA4 활성 사용자 + Bing 클릭.
- v22 **LSAC 2026-07-28 규정 추적 의무**(이중등록 페이지 수정 시 공식 페이지 재확인).
- v24 **`gpa-raise-calculator`는 더 손대지 말 것**(중복 가설 기각, Bing에서는 정상 작동).

### 이번 세션의 성격
사용자 지시는 08-25·08-26과 동일(신규·폭넓게·경쟁강도·클러스터 추가·외부 소스). **이번 주도 GSC/Bing/GA4 자료는 제공되지 않았고 참조하지 않았다.**

---

## ★★★★★ 신규 클러스터 개설: 과목 결과 선택 (Incomplete / Withdrawal / Failing)

기존 10개에 이어 **11번째 클러스터**. 우리 Bing 최강 영역(학사 상태 + SAP + 재수강)에 바로 인접한 빈칸이다.

### 후보 4개 → 3개 기각 (재조사하지 말 것)

| 후보 | 판정 | 근거 |
|---|---|---|
| 재향군인 GI Bill MHA | 기각 | veteran.com·collegerecon·vetcalc가 **ZIP코드 BAH DB 기반 전용 계산기** 보유. military.com·bestmilitaryresume 등 해설도 다수. 체크리스트 44번 적용(Workforce Pell 기각과 동일 구조) |
| 성적증명 보류 / stranded credits | 기각 | **LegalClarity가 주별 임계금액까지 포함해 상세 선점**(테네시 $100, 미네소타 $250, 메인 $500/$2,500 등). SoFi·USNews·Ithaka도 존재. 게다가 계산 가능한 형태로 만들기 어려움 — 체크리스트 42번(도구 성립성) |
| Incomplete **전용 계산기** | 기각 | research.com이 해설 선점. 무엇보다 **우리 sap-calculator와 pace 계산이 정면 중복**(체크리스트 40번). 계산기 형태를 포기하고 아래로 전환 |
| **Incomplete / 철회 / 낙제 3자 선택** | **채택** | .edu SAP 페이지가 각각 단편적으로만 다루고, collegevaluesonline은 W vs F만 비교. **세 선택지를 GPA·완료율·등록금·기본값 축으로 한자리에 놓은 문서가 없음** |

### ★ 이번 세션의 방법론적 의의
후보 3번에서 **계산기 형태를 포기하고 블로그로 전환한 판단**이 핵심이다. 주제 자체는 좋았지만 계산기로 만들면 `sap-calculator`와 pace 계산이 겹친다. v24에서 확인했듯 구글 색인 이탈이 진행 중인 상황이라 유사 형태 페이지를 늘리는 건 리스크다. **"주제가 좋다"와 "그 형태로 만들어야 한다"는 별개 판단이다.**

### 신규 2건 (쿼리셋 분리)

**1. `blog/incomplete-vs-withdrawal-vs-failing.html` (1,529단어)** — 질문: "어느 쪽을 골라야 하나"
6행 비교표(GPA / SAP 완료율 / 학점 / 등록금 / 기본값 / 승인 필요)로 정리.

★ 핵심 인사이트 2가지:
1. **세 선택지 모두 SAP 완료율에는 동일하게 불리하다.** 완료율이 문제라면 셋 중 고르는 것으로는 아무것도 해결되지 않는다 — 해법은 다른 데서 와야 한다. 이 사실을 명시한 문서가 없었다.
2. **Incomplete만 유일하게 "방치하면 저절로 나빠지는" 선택지다.** 마감일에 자동으로 낙제로 전환되고(학교별 다음 학기말~1년), 일부 학교는 IF/FINC로 사유가 영구히 남는다. W와 F는 안정적 종료 상태인데 I만 아니다.

추가로 **Incomplete는 R2T4를 유발하지 않는다**(전체 철회가 아니므로)는 점을 명시해 기존 `r2t4-calculator`와 연결했다.

**2. `blog/how-to-ask-for-an-incomplete-grade.html` (1,143단어)** — 질문: "어떻게 요청하나"
★ 핵심: **Incomplete는 권리가 아니라 교수 재량**이다. 공표된 요건을 다 충족해도 승인 의무가 없다. 따라서 **철회 마감 前에 요청해야 거절당해도 W라는 대안이 남는다**는 타이밍 규칙이 결론이 된다.
요청서 4요소(잔여 과제 / 사유 / 증빙 / **제출 확정일**)와 승인 前 서면 확인 3가지(전환일, 강의실 폐쇄 시 제출 방법, 연장 가능 여부). 거절 시 late/retroactive withdrawal 청원 경로 안내.

### 사실 확인 (교차 검증)
UC Davis · 애리조나 · USF · KBCC(CUNY) · St. Thomas SAP 정책 페이지에서 확인:
- Incomplete는 GPA 미산입이나 **attempted-not-earned로 완료율에 산입**
- 미해결 시 자동 낙제 전환, 전환 후 **IF/FINC 별도 표기** 사례 존재
- Incomplete 해소 후에도 **다음 정기 심사까지 SAP 재평가 보류**
- 승인 요건 3종: 요청 시점에 passing / 대부분의 과제 완료 / 통제 밖 사유
정책 편차가 매우 큰 주제라 "일반적 패턴"임을 **두 페이지 모두 별도 섹션으로 명시**했다.

### 중복 확인
`incomplete` 언급은 기존 6개 파일에서 1~4회 부수적 언급뿐(sap-calculator 2회, does-withdrawing 1회). 전용 문서 없음.

---

## ★ 다음 세션이 확인/처리할 것

1. **금지 원칙 4종 유지**(색인 수동 제출 / 패닉 재작성 / LSAC 추적 / gpa-raise-calculator 손대지 않기).
2. **★ 최우선 점검: 신규 11페이지의 Bing 노출.** v24에서 신규 9페이지가 전부 Bing 노출 0으로 확인됐고, 이번에 2페이지가 더 늘어 **11페이지**가 됐다. 다음에 데이터를 받으면 이것부터 볼 것.
   - **하나라도 잡히면** 신규 확장 재개가 맞다.
   - **여전히 0이면** 08-12 생성분이 3주가 넘도록 0이라는 뜻이므로, 세션 배분을 보강 쪽으로 더 옮길 것. **페이지를 지우거나 전략을 바꾸는 선택지는 아니다.**
3. **08-31 보강 3건의 효과 확인**: `obbba-loan-limit-calculator`(기준선 Bing 23노출/7.5위, 키워드 "aggregate student loan limit graduate calculator" 20노출/8위/클릭 0), `pell-lifetime-eligibility-calculator`(348노출/클릭 6), `what-is-the-deans-list-gpa-requirement`(**CTR 0.24%가 기준선** — title 교체 효과 측정).
4. **CTR 처방 확대 후보**(체크리스트 49번): `what-gpa-do-you-need-to-graduate-college`(Bing 91노출 3.56위 **클릭 0**), `new-act-format-2025-2026-changes`(29노출 6.59위 클릭 0), `weighted-gpa-calculator-ap-classes`(25노출 8위 클릭 0). Dean's List 처방이 통했다면 여기에 같은 방식 적용.
5. **수익화 — 임계치 근접.** v18 기준 월 세션 500 또는 월 검색 클릭 50. 08-31 기준 세션 151/4주, 검색 클릭 33(66%). **돌파하면 그때 제휴 가입 제안. 그 전에는 요구하지 말 것.**
6. **계절성**(v20·v23): 교육 세금 1~4월, 대학원 조교 10~12월·3~5월. **이번 신규 클러스터도 계절성이 있다 — 학기말(12월, 5월)과 철회 마감 직전(10월, 3월)이 성수기다.** 비수기 데이터로 실패 판정 금지.

## 2주 재작업 보류 현황 (09-01 기준)
- **09-07까지**: `tools/employer-tuition-assistance-calculator.html`, `blog/does-retaking-a-class-replace-your-gpa.html`
- **09-08까지**: `tools/dual-enrollment-gpa-calculator.html`, `blog/does-dual-enrollment-affect-your-gpa.html`
- **09-09까지**: `tools/graduate-assistantship-tax-calculator.html`, `blog/why-did-my-grad-stipend-paycheck-drop.html`
- **09-14까지**: `tools/obbba-loan-limit-calculator.html`, `tools/pell-lifetime-eligibility-calculator.html`, `blog/what-is-the-deans-list-gpa-requirement.html`
- **09-15까지**: 이번 세션분 — `blog/incomplete-vs-withdrawal-vs-failing.html`, `blog/how-to-ask-for-an-incomplete-grade.html`
- **보류 해제**: `tools/scholarship-tax-calculator`, `blog/1098-t-box-5-exceeds-box-1`, 그 외 08-18 이전 전체
  (이번 세션에 **상호링크만** 추가한 6개는 보류 예외, lastmod 미갱신)

## 파일 현황 (09-01 기준)
- tools 45개 + index / blog **60개** + index / 루트 7개
- sitemap URL **111개**, tool-card 45개(미등록 도구 0), blog-card **58개**(미등록 1건 = 404 스텁 `how-to-raise-your-gpa.html`)
- 전체 115개 HTML JSON-LD 오류 0, 내부링크 broken 0

## 클러스터 현황 (11개)
GPA 계산/변환 · 시험점수 · 연방지원 규정 · 학자금대출 · 전공·커리어 ROI · 유학 · 학사경고·복학 · 교육 세금 · 이중등록 · 대학원 조교 펀딩 · **과목 결과 선택(신규)**

### 아직 비어 있는 영역 (경쟁조사 미실시)
홈스쿨 성적증명 · 장애 학생 편의제공 · 로스쿨 준비(LSAT/GPA) · CLEP/사전학습인정(CPL)
→ **기각 완료 목록(재조사 금지)**: 유학생 F-1 재정증명, 근로장학, Academic renewal, Workforce Pell, PhD 스티펜드 비교, NCAA 자격, 장학금 displacement, 리테이크 GPA 계산기, **GI Bill MHA, 성적증명 보류(stranded credits), Incomplete 전용 계산기**

## 체크리스트 추가분 (v24 48~50번에 이어서)
51. **"주제가 좋다"와 "그 형태로 만들어야 한다"는 별개 판단이다.** 09-01에 Incomplete 주제는 채택했지만 계산기 형태는 기각했다 — sap-calculator와 pace 계산이 겹치기 때문이다. 좋은 주제를 만나면 **계산기/블로그 중 어느 형태가 기존 자산과 덜 겹치는지**를 먼저 정하고 만들 것.
52. **비교 문서를 만들 때 "모든 선택지가 동일한 축"을 먼저 찾을 것.** 09-01 Incomplete/W/F 비교에서 가장 유용한 발견은 "셋 다 완료율에는 똑같이 불리하다"였다. 차이점만 나열하는 비교표는 흔하지만, **어느 축에서는 선택이 무의미한지**를 알려주는 문서는 드물고 실제로 더 유용하다.
53. **"방치하면 저절로 나빠지는 선택지"는 강력한 콘텐츠 각도다.** Incomplete가 자동으로 낙제로 전환되는 구조가 이 클러스터의 핵심 훅이 됐다. 기본값(default outcome)이 사용자에게 불리한 제도는 대체로 설명이 부실하고 검색 수요가 크다.

---

## [보존] 이전 문서 v24 본문 (2026-08-31 세션까지)

# GPA Vault 인수인계 문서 v24 (2026-08-31 세션 — 신규 9페이지의 Bing 노출이 전부 0으로 확인, 보강 우선 주간)

이전 v23 문서를 대체함. v23 이하 본문은 아래에 그대로 보존.

### 0단계 대조 결과
최신 커밋 `aeec497`(08-26 handover v23)와 v23 기록 일치 — 소급 기록 불필요.

### ★ 먼저 확인할 것 (계속 유효)
- v19 **색인 수동 제출 금지**(IndexNow·구글 색인 요청 안 함).
- v21 **구글 색인 이탈에 패닉 재작성 금지.** 판단 지표는 GA4 활성 사용자 + Bing 클릭.
- v22 **LSAC 2026-07-28 규정 추적 의무**(이중등록 페이지 수정 시 공식 페이지 재확인).

---

## ★★★★★★ 결론 1: 신규 9페이지가 Bing에서 노출 0이다 (v23 체크리스트 47번의 답)

v23이 "4세션 연속 신규 확장했는데 성과를 한 번도 확인 못 했다"고 남겼다. **이번에 확인했고, 결과가 명확하다.**

최근 4세션 신규분 — `r2t4-calculator`(08-12), `repeat-coursework-aid-calculator`(08-17), `scholarship-tax-calculator`·`1098-t-box-5-exceeds-box-1`(08-18), `employer-tuition-assistance-calculator`(08-24), `dual-enrollment-gpa-calculator`·`does-dual-enrollment-affect-your-gpa`(08-25), `graduate-assistantship-tax-calculator`·`why-did-my-grad-stipend-paycheck-drop`(08-26) — 은 **Bing Page Traffic 리포트(37개 페이지)에 단 하나도 없다. 전부 노출 0이다.** r2t4는 3주가 지났는데도 0이다.

GA4에는 잡힌다(r2t4 9조회, repeat-coursework 2, scholarship-tax 1, employer-tuition 1, graduate-assistantship 1, 1098-t 1, why-did-my-grad-stipend 1). 즉 사람이 아예 안 오는 건 아니고 **검색엔진 노출이 아직 안 붙은 상태**다.

### 반대로 성장은 전부 기존 페이지의 성숙에서 나왔다
| 페이지 | 지난주 → 이번주 Bing 노출 |
|---|---|
| does-retaking-a-class-replace-your-gpa | 450 → **931** |
| what-is-the-deans-list-gpa-requirement | 203 → **415** |
| pell-lifetime-eligibility-calculator | 183 → **348** |
| what-gpa-do-you-need-for-nursing-school | 34 → **120** |
| gpa-raise-calculator | 31 → **83** |
| sap-calculator | 23 → **53** |

전체 Bing: 노출 1,115 → **2,369(2.1배)**, 클릭 20 → **32**. GA4 활성 사용자 100 → **128**.
소스: bing 40 + yahoo 13 + duckduckgo 7 + ecosia 1 = **61** vs google **2**.

### → 그래서 이번 주는 신규 0건, 보강 3건으로 갔다
**전략은 바꾸지 않았다.** 공격적 확장은 유지한다. 다만 이번 주 한계 효용이 보강 쪽에 명백히 몰려 있었다: 신규는 3주째 노출 0인데 기존 자산은 주당 2배로 크고 있다. 사용자 지시("진짜로 할 거 없으면 안 하는 게 맞지만 전략은 바꾸지 마라")에 부합하는 판단으로 봤다.

**다음 세션 판단 기준**: 신규분이 Bing에 잡히기 시작하면(= Page Traffic 리포트에 등장) 신규 확장 재개가 맞다. 여전히 0이면 **신규 페이지가 Bing 색인에 붙는 데 걸리는 시간이 우리 예상보다 길다**는 뜻이므로, 확장 속도를 유지하되 세션당 배분을 보강 쪽으로 더 두는 게 합리적이다. 페이지를 지우거나 전략을 바꾸는 선택지는 아니다.

### 구글 / 색인 현황 (사용자 제공 자료 기준)
- 일별 노출 2~8 유지, 3개월 클릭 7. 회복 없음.
- **404 = 0건**(이번에 처음 확인, 깨끗함)
- 크롤링됨-미색인 **31 → 30**(사실상 정체)
- 발견됨-미색인 **5건**: `1098-t-box-5-exceeds-box-1`, `methodology.html`, `gpa-raise-calculator`, `repeat-coursework-aid-calculator`, `scholarship-tax-calculator` (전부 크롤 이력 없음)
- ★ **`gpa-raise-calculator` 가설 반증**: v21/v22가 "중복 판정 때문에 크롤 거부"로 보고 08-17에 차별화했는데, **여전히 크롤조차 안 됐다.** 중복 가설은 기각. 그런데 같은 페이지가 Bing에서는 83노출 6.4위에 클릭 1건이다. → 구글 고유의 크롤 예산/권위 문제로 결론. **더 손대지 말 것.**

---

## 08-31 세션 작업 (커밋 `5672f87`, push + Actions `completed/success` 확인)

### 보강 1: `tools/obbba-loan-limit-calculator.html` (954 → 1,462단어) — 수익화 1순위
**근거**: Bing 키워드 2위 `aggregate student loan limit graduate calculator`(20노출, **8위**, 클릭 0). 대학원 대출이라 수익화 가치 최상.

**발견한 문제**: 페이지에 pre-OBBBA 총액 한도 **$138,500 / $224,000 언급이 0건**이었고, 계산기는 legacy를 선택하면 aggregate를 `null`로 두어 **계산 자체를 안 했다.**

**FSA 공식 확인**(fsapartners.ed.gov NSLDS 발표, 2026-05-07 갱신):
- interim exception 대상자는 학부 sub/unsub 대출이 pre-OBBBA $138,500(보건계열 $224,000)에 **계속 산입**된다.
- 반면 신규 $100,000 / $200,000 총액에는 **학부 대출이 산입되지 않는다.**
- ★ **따라서 학부 대출이 많으면 grandfathered 지위가 오히려 불리하다.** 검증: 학부 $57,500 + 대학원 $20,000 → legacy 잔여 **$61,000** vs 신규 잔여 **$80,000**. 이 반직관적 결론을 설명하는 곳이 없어 차별화 포인트로 삼았다. 단 Grad PLUS 접근권이 그 격차보다 대개 크다는 균형 서술을 함께 넣었다.
- 보건계열 $224,000은 exception에 붙어 다니므로 exception 종료 시 $100k/$200k로 회귀.
- 2026-07-01 이전 Grad PLUS도 exception 종료 후 $257,500 평생한도에 산입(**ED 입장 번복분** — 오래된 기사들은 반대로 적혀 있으니 다음에 이 페이지 손볼 때 재확인).

**작업**: 계산기를 학부/대학원 대출 분리 입력 + 보건계열 토글로 개편해 legacy 총액 한도를 실제 산출하도록 재작성. 결과창 기본 표시 + 전 입력 즉시 재계산 + scrollIntoView 가드(체크리스트 28번) 적용. 비교표와 "구 한도가 아직 많은 사람에게 적용된다" 섹션 신설, FAQ 2개 추가.

### 보강 2: `tools/pell-lifetime-eligibility-calculator.html` (623 → 1,231단어)
**근거**: Bing 3위 자산(348노출, 클릭 6, CTR 1.72%)인데 **623단어로 얇았다.** Bing 쿼리 `does pel grant start back from 0 after 6 years`(**2위**)가 전혀 커버 안 됨(reset/expire/restore 언급 0건).

**FSA Handbook 2026-27 vol7 ch8 확인**:
- LEU는 **시간으로 리셋되지 않는다.** 전학·휴학·학점이전·성인학습자 복귀 전부 무관.
- **복원 경로 3가지**: ① 폐교(1995년 이후 공식 폐교 + **미졸업**) ② 적격 대출탕감(2017-07-01 이후, 동일 OPEID·동일 award year) ③ LEU 분쟁.
- 학교가 신청할 필요 없이 **COD에서 자동 조정**되고 결과는 NSLDS에 표시된다. 그래서 해당되는 학생도 모르고 지나간다.
- 비연방 장학금이 COA 이상이라 Pell을 반환한 경우에도 LEU가 조정된다(현행 규정).

### 보강 3: `blog/what-is-the-deans-list-gpa-requirement.html` — CTR 최적화(메타만)
**근거**: Bing 415노출인데 **클릭 1건(CTR 0.24%)**, 평균 5.25위. 순위 대비 전환이 무너져 있었다. 해당 Bing 쿼리가 전부 숫자를 묻는 짧은 질의(`dean's list gpa`, `what gpa is needed for dean's list` 등)인데 **title에 정답 수치가 없었다.**
title/description을 "3.5, 학기 GPA 기준"이라는 답을 앞세우는 형태로 교체하고 Article 스키마 description·dateModified 동기화. **본문은 이미 충분해 미변경**(1,587단어).

---

## ★ 다음 세션이 확인/처리할 것

1. **금지 원칙 3종 유지**(색인 수동 제출 / 패닉 재작성 / LSAC 추적).
2. **★ 신규 9페이지의 Bing 노출 재확인이 이번 주 최우선 점검항목.** Page Traffic 리포트에 하나라도 등장하면 신규 확장 재개. 여전히 0이면 위 "결론 1"의 판단대로 배분을 조정할 것.
3. **CTR 최적화 효과 확인.** Dean's List title 교체(08-31)가 CTR을 움직였는지. 415노출 / 0.24%가 기준선이다. 효과가 있으면 **같은 처방을 다른 고노출·저CTR 페이지에 확대**할 것 — 현재 후보: `what-gpa-do-you-need-to-graduate-college`(Bing 91노출 3.56위 **클릭 0**), `new-act-format-2025-2026-changes`(29노출 6.59위 클릭 0), `weighted-gpa-calculator-ap-classes`(25노출 8위 클릭 0).
4. **`gpa-raise-calculator`는 더 손대지 말 것.** 중복 가설 기각됐고 Bing에서는 잘 돌아간다(83노출 6.4위).
5. **수익화 — 임계치 근접.** v18 기준은 월 세션 500 또는 월 검색 클릭 50. 현재 GA4 세션 **151/4주**, 검색 클릭 **Bing 32 + 구글 ~1 = 33**. 클릭 기준 66% 도달. **Bing 성장 속도(주당 1.6~2배)가 유지되면 1~2세션 내 50 돌파 가능성이 높다.** 돌파하면 그때 제휴 가입을 제안할 것. 그 전에는 요구하지 말 것.
6. **계절성**(v20·v23): 교육 세금 1~4월, 대학원 조교 10~12월·3~5월. 비수기 데이터로 실패 판정 금지.

## 2주 재작업 보류 현황 (08-31 기준)
- **09-01까지**: `tools/scholarship-tax-calculator.html`, `blog/1098-t-box-5-exceeds-box-1.html`
- **09-07까지**: `tools/employer-tuition-assistance-calculator.html`, `blog/does-retaking-a-class-replace-your-gpa.html`
- **09-08까지**: `tools/dual-enrollment-gpa-calculator.html`, `blog/does-dual-enrollment-affect-your-gpa.html`
- **09-09까지**: `tools/graduate-assistantship-tax-calculator.html`, `blog/why-did-my-grad-stipend-paycheck-drop.html`
- **09-14까지**: 이번 세션분 — `tools/obbba-loan-limit-calculator.html`, `tools/pell-lifetime-eligibility-calculator.html`, `blog/what-is-the-deans-list-gpa-requirement.html`
- **보류 해제**: `tools/repeat-coursework-aid-calculator`, `tools/gpa-raise-calculator`(단 항목 4 참고), 그 외 08-17 이전 전체

## 파일 현황 (08-31 기준)
- tools 45개 + index / blog 58개 + index / 루트 7개
- sitemap URL 109개, tool-card 45개(미등록 도구 0), blog-card 56개
- 전체 113개 HTML JSON-LD 오류 0, 내부링크 broken 0, 구글 404 0건

## 체크리스트 추가분 (v23 44~47번에 이어서)
48. **신규 페이지가 Bing에 잡히는 데는 3주 이상 걸린다(관측치).** 08-31 기준 08-12 생성 페이지도 노출 0이었다. 신규 클러스터를 열고 1~2주 만에 성과를 판정하지 말 것. 반대로 **기존 페이지는 주당 2배씩 성숙**하므로, 어느 주에 무엇을 할지는 이 시간차를 감안해 배분할 것.
49. **고노출·저CTR 페이지를 별도로 추적할 것.** 순위가 5위인데 CTR이 0.2%면 콘텐츠가 아니라 title/description 문제일 가능성이 높다. 특히 Bing 쿼리가 숫자를 묻는 짧은 질의인데 title에 답이 없으면 그렇다. 본문을 건드리지 않고 메타만 고치는 것이 가장 싼 개선이다.
50. **계산기를 보강할 때 "그 분기를 계산하기는 하는가"부터 볼 것.** obbba 계산기는 legacy를 고르면 aggregate를 `null`로 두고 아무것도 계산하지 않고 있었다. 본문에 규정이 적혀 있어도 계산기가 그 경우를 비워두면 사용자에게는 없는 기능이다.

---

## [보존] 이전 문서 v23 본문 (2026-08-26 세션까지)

# GPA Vault 인수인계 문서 v23 (2026-08-26 세션 — 신규 클러스터 "대학원 조교 펀딩" 개설)

이전 v22 문서를 대체함. v22 이하 본문은 아래에 그대로 보존.

### 0단계 대조 결과
최신 커밋 `8946432`(08-25 handover v22)와 v22 기록 일치 — 소급 기록 불필요.

### ★ 먼저 확인할 것 (계속 유효)
- v19 최상단 **"절대 하지 말 것 — 색인 수동 제출 금지"**: IndexNow·구글 색인 요청 하지 않는다.
- v21 결론: **구글 색인 이탈에 패닉 재작성으로 반응하지 않는다.** 판단 지표는 GA4 활성 사용자 + Bing 클릭.
- v22 항목: **LSAC 2026-07-28 규정 변경 추적 의무** — 이중등록 페이지를 손볼 때 LSAC 공식 페이지 재확인 필수.

### 이번 세션의 성격
사용자 지시는 08-25와 동일(신규·폭넓게·경쟁강도·클러스터 추가·외부 소스). 이번 주도 GSC/Bing/GA4 자료는 제공되지 않았고 **참조하지 않았다.** 체크리스트 32번대로 v22의 "비어 있는 영역" 목록에서 출발해 외부 검색으로만 검증했다.

---

## ★★★★★ 신규 클러스터 개설: 대학원 조교 펀딩 (Graduate Assistantship Funding)

기존 9개에 이어 **10번째 클러스터**. v22 "비어 있는 영역" 목록의 "대학원 조교(TA/RA) 학비면제 과세" 항목이다.

### 후보 2개 정밀조사 → 1개 기각

| 후보 | 판정 | 근거 |
|---|---|---|
| **Workforce Pell** (OBBBA, 2026-07-01 시행) | 기각 | 체크리스트 41번(최근 규정 변경 선점)에 딱 맞아 유력했으나, **workforcepellmatch.com이 5만개 주정부 승인 프로그램 DB 기반 학생용 검색 도구를 이미 운영 중.** 체크리스트 33번대로 전용 DB 도구는 강한 경쟁(v20 MeritPlaybook 기각과 동일 판단). collegehelpguide·TICAS·UPCEA·AIR·NASFAA·prentus도 존재 |
| **대학원 조교 학비면제 과세** | **채택** | 아래 |

**★ Workforce Pell 관련 메모(다음 세션용)**: 기각했지만 **한 가지 각도는 아직 비어 있다** — TICAS가 우려하는 "단기 프로그램에 평생 Pell 한도(LEU)를 소진하는 문제"다. 우리 `pell-lifetime-eligibility-calculator`가 Bing 3위 자산(183노출, 5.5위)이라 연결 가능성이 있다. 다만 이건 **신규 클러스터가 아니라 기존 Pell 클러스터 확장**이므로, 클러스터 우선 지시가 없을 때 검토할 것.

### 왜 조교 학비면제가 통과했나
- 검색 결과가 **.edu 페이롤 FAQ(SIU, UIC, UIUC 등) + LegalClarity 1건 + Claimyr 포럼 1건**뿐. UIC가 자체 계산기를 두고 있으나 **소속 학생 전용**이고 공개 학생용 계산기는 확인되지 않았다.
- 체크리스트 43번(기관 간 불일치가 좋은 소재)에도 해당한다. 여기서는 기관 간이 아니라 **조항 간 불일치**다.

### ★ 핵심 규정 (이 클러스터의 존재 이유)
**IRC §117(d)(5)는 TA/RA의 대학원 학비면제를 상한 없이 소득에서 제외한다. 그런데 행정직 GA는 그 조항에서 의도적으로 제외돼 §127 적용을 받아 연 $5,250까지만 비과세다.**

동일한 패키지가 **직함만으로** 세금이 갈린다. 검증 예시(학비면제 $25,000 + 수수료 $1,200, 12% 세율):
- TA/RA → 추가 세금 **$144**
- 행정 GA → 추가 세금 **$2,514**

부수 규정(정확도상 중요):
- **면제된 수수료(lab/health/tech)는 TA/RA도 과세 대상**이다. 117(d)(5)는 tuition만 커버한다.
- 스티펜드는 직함 무관 항상 과세 임금(W-2).
- **학생 FICA 예외**로 추가 원천징수는 통상 소득세만이고 급여세(7.65%)는 빠진다. → 이 점이 `employer-tuition-assistance-calculator`와 결정적으로 다르다.
- 오분류가 실제로 발생한다. 방향은 한쪽이다 — **TA/RA인데 §127 $5,250 상한으로 처리**되는 경우.

### 신규 2건 (쿼리셋 분리)

**1. `tools/graduate-assistantship-tax-calculator.html` (1,137단어)**
차별화 = **"0원 급여" 산출**. 대학이 원천징수를 학기 말 소수 급여에 몰아서(통상 10~12월, 3~5월) 집행하기 때문에, 비현금 소득의 세금이 현금 급여를 잠식한다. SIU 등 대학 FAQ가 zero-paycheck 가능성을 명시하고 있어 근거가 확실하다. 계산기는 두 직함을 나란히 비교하고 해당 월 실수령액까지 산출한다.

**2. `blog/why-did-my-grad-stipend-paycheck-drop.html` (1,223단어)**
도구는 "내 면제가 과세 대상인가", 블로그는 "왜 이번 달 급여가 줄었나"로 쿼리셋 분리.
실행 지침 3가지를 명확히 했다: ① W-4 문제가 아니다 ② **원천징수 시작 前에 페이롤 연락**이 유일하게 유효한 조치(사후는 어렵다) ③ TA/RA면 오분류 여부를 임용장 들고 확인.

### 중복 확인 (체크리스트 40번)
기존 `employer-tuition-assistance-calculator`와 **§127 $5,250 조항이 겹친다.** 그러나:
- 대상: 일반 직장인 vs 대학원 조교
- 핵심 질문: AOTC 배분 최적화 vs 과세 여부 판정
- 급여세: 부과 vs 학생 FICA 예외

세 축이 모두 달라 별개로 성립한다고 판단했고, **양방향 상호링크로 역할을 명시**했다. 다음 세션이 이 둘을 중복으로 오판하지 말 것.

### 검증
파이썬 모델 ↔ jsdom 8개 시나리오 일치(TA/RA, 행정 GA, 0원 급여 발생, 상한 미달, 징수 분산 6회, 면제 0, 전부 0, spread=0 가드). getComputedStyle(display) 3경로 확인. node --check 통과.
세무 자문 아님 고지를 본문·FAQ·스키마 3곳에 명시하고 캠퍼스 VITA 안내 포함(체크리스트 36번).

---

## ★ 다음 세션이 확인/처리할 것

1. **색인 수동 제출 금지 / 패닉 재작성 금지 / LSAC 추적** — v19·v21·v22 원칙 유지.
2. **★ 데이터를 받으면 신규 4개 클러스터의 성과를 함께 볼 것.** 최근 4세션 동안 교육 세금(3p) → 이중등록(2p) → 대학원 조교(2p)로 빠르게 확장했는데 **아직 어느 것도 성과 데이터를 본 적이 없다.** 다음에 GSC/Bing 자료를 받으면 신규분이 Bing에 색인·랭크되는지부터 확인할 것. Bing은 통상 빠르게 잡히므로 2주면 신호가 나온다.
3. **계절성 주의.** 교육 세금 클러스터는 1~4월 판정(v20). **대학원 조교 클러스터는 10~12월과 3~5월**이 성수기다(원천징수가 그때 집행되므로 검색이 그때 몰린다). 지금(8월)은 저점이므로 비수기 데이터로 실패 판정하지 말 것.
4. **Bing 상위 페이지 보강 계속**(v21 목록 유지): `what-is-the-deans-list-gpa-requirement`(203노출), `pell-lifetime-eligibility-calculator`(183), `what-gpa-do-you-need-for-nursing-school`(34노출 4.35위). CTR 높은 소형 3개도 유효: `what-gpa-to-keep-scholarship`(40%), `average-student-loan-debt-by-major`(9.09%), `sap-calculator`(8.7%).
5. **수익화 — v18 정정 유지.** 월 세션 500 또는 월 검색 클릭 50 도달 전까지 요구하지 말 것.

## 2주 재작업 보류 현황 (08-26 기준)
- **08-31까지**: `tools/repeat-coursework-aid-calculator.html`, `tools/gpa-raise-calculator.html`
- **09-01까지**: `tools/scholarship-tax-calculator.html`, `blog/1098-t-box-5-exceeds-box-1.html`
- **09-07까지**: `tools/employer-tuition-assistance-calculator.html`, `blog/does-retaking-a-class-replace-your-gpa.html`
- **09-08까지**: `tools/dual-enrollment-gpa-calculator.html`, `blog/does-dual-enrollment-affect-your-gpa.html`
- **09-09까지**: 이번 세션분 — `tools/graduate-assistantship-tax-calculator.html`, `blog/why-did-my-grad-stipend-paycheck-drop.html`
- **보류 해제**: 08-12 이전 전체(`r2t4-calculator`, `gpa-scale`, `methodology.html`, `editorial-policy.html`, `what-is-the-deans-list-gpa-requirement`, `ib-gpa-calculator`, `percentage-to-gpa-converter`, `gpa-to-letter-grade-converter` 등)
  (이번 세션에 **상호링크만** 추가한 5개는 보류 예외, lastmod 미갱신)

## 파일 현황 (08-26 기준)
- tools **45개** + index / blog **58개** + index / 루트 7개
- sitemap URL **109개**, tool-card 45개(미등록 도구 0), blog-card 56개(미등록 1건 = 404 스텁 `how-to-raise-your-gpa.html`)
- 전체 113개 HTML JSON-LD 오류 0, 내부링크 broken 0

## 클러스터 현황 (10개)
GPA 계산/변환 · 시험점수 · 연방지원 규정 · 학자금대출 · 전공·커리어 ROI · 유학 · 학사경고·복학 · 교육 세금 · 이중등록 · **대학원 조교 펀딩(신규)**

### 아직 비어 있는 영역 (경쟁조사 미실시)
재향군인 GI Bill · 홈스쿨 성적증명 · 장애 학생 편의제공 · 로스쿨 준비(LSAT/GPA) · CLEP/사전학습인정(CPL)
→ 유학생 F-1 재정증명, 근로장학, Academic renewal, Workforce Pell, PhD 스티펜드 비교, NCAA 자격, 장학금 displacement, 리테이크 GPA 계산기는 **모두 기각 완료** — 재조사하지 말 것.

## 체크리스트 추가분 (v22 41~43번에 이어서)
44. **"최근 규정 변경"이라도 전용 DB 도구가 이미 있으면 기각할 것.** 08-26에 Workforce Pell(2026-07-01 시행)은 체크리스트 41번에 완벽히 부합했지만 workforcepellmatch.com이 5만개 프로그램 DB를 이미 갖고 있어 기각했다. **신규성과 경쟁강도는 별개로 평가해야 한다.**
45. **같은 법 조항을 다루더라도 대상·질문·부수규정이 다르면 별개 페이지로 성립한다.** §127 $5,250은 `employer-tuition-assistance`와 `graduate-assistantship-tax` 양쪽에 나오지만, 대상(직장인 vs 조교)·질문(AOTC 배분 vs 과세 판정)·급여세(부과 vs 학생 FICA 예외)가 달라 중복이 아니다. **단 반드시 양방향 상호링크로 역할을 명시할 것.**
46. **신규 클러스터를 열 때 성수기를 handover에 적을 것.** 교육 세금은 1~4월, 대학원 조교는 10~12월·3~5월이다. 적어두지 않으면 다음 세션이 비수기 데이터로 멀쩡한 클러스터를 실패 판정한다.
47. **확장 속도 대비 검증 부채를 인지할 것.** 08-18부터 4세션 연속으로 신규 클러스터를 열었고 **아직 어느 것도 성과 데이터를 확인하지 못했다.** 다음에 데이터를 받으면 신규 확장을 계속하기 전에 기존 신규분의 Bing 색인·랭크부터 점검하는 것이 맞다.

---

## [보존] 이전 문서 v22 본문 (2026-08-25 세션까지)

# GPA Vault 인수인계 문서 v22 (2026-08-25 세션 — 신규 클러스터 "이중등록" 개설, LSAC 규정 변경 선점)

이전 v21 문서를 대체함. v21 이하 본문은 아래에 그대로 보존.

### 0단계 대조 결과
최신 커밋 `10d74b2`(08-24 handover v21)와 v21 기록 일치 — 소급 기록 불필요.

### ★ 먼저 확인할 것 (계속 유효)
- v19 최상단 **"절대 하지 말 것 — 색인 수동 제출 금지"**: IndexNow·구글 색인 요청 하지 않는다.
- v21 결론: **구글 색인 이탈(31건)에 패닉 재작성으로 반응하지 않는다.** 판단 지표는 GA4 활성 사용자 + Bing 클릭.

### 이번 세션의 성격
사용자 지시: "신규를 폭넓게. 키워드 뽑고 → 리스트 → 경쟁 강도 → 강하면 롱테일. 가능하면 새 클러스터. **GSC/우리 데이터 안에서만 보지 말고** 구글·네이버·레딧 등에서 문서 수는 적은데 관심 있는 걸 찾아라."
→ 체크리스트 32번대로 **자체 데이터를 근거로 쓰지 않고** 인벤토리 빈칸 → 외부 검색 검증 순서로 진행. 이번 주 GSC/Bing/GA4 자료는 제공되지 않았고 참조하지도 않았다.

---

## ★★★★★ 신규 클러스터 개설: 이중등록(Dual Enrollment / Early College Credit)

기존 8개 클러스터에 이어 **9번째**. v21 "아직 비어 있는 영역" 목록에 있던 항목이다.

### 후보 4개 → 3개 기각 (다음 세션이 재조사하지 말 것)

| 후보 | 판정 | 근거 |
|---|---|---|
| 유학생 F-1 재정증명(I-20) | 기각 | 전부 .edu(조지아텍·FAU·TAMU·UCI·UMN·콜로라도 등)인데, **증명 금액이 학교별 COA라 범용 계산기가 성립하지 않는다.** 경쟁이 약해도 도구가 성립 안 하면 무의미 |
| 근로장학 vs 일반 알바 | 기각 | collegelens(3편), levelall, kidtocollege, collegefinance, degreecalc, research.com(2편), collegehelpguide 등 **9곳+ 포화** |
| Academic renewal | 기각 | v20에서 이미 기각 — 재조사하지 않았다 |
| **이중등록 GPA 영향** | **채택** | 아래 |

### 왜 채택했나
- 검색 결과가 **SDN 포럼 3건(2008·2019·2021), College Confidential, 7sage 3건** 등 포럼 Q&A 위주. AAMC·LSAC 공식 정책 페이지는 있으나 **학생용 정리 문서도 계산기도 없다.** 체크리스트 33번 판정("포럼 Q&A만 있으면 포화가 아니라 문서 부재 신호")에 정확히 해당.
- **18년간 같은 질문이 반복** 등장한다는 건 수요가 확실한데 아무도 안 채운 영역이라는 뜻.
- ★★ **결정적: LSAC이 2026-07-28자로 규정을 바꿨다.** 고교 재학 중 이수한 대학 과목을 LSAC GPA에서 **제외**하기 시작(제출 트랜스크립트 기준, 실질적으로 2027-2028 지원 사이클부터). **한 달도 안 된 변경**이라 기존 문서 다수(spiveyconsulting, LawHub 등)가 여전히 옛 규정을 서술 중이다. 반면 **AMCAS는 여전히 포함**한다. 두 제도가 갈라진 상태를 정리한 문서가 없다.

### 신규 2건 (쿼리셋 분리)

**1. `tools/dual-enrollment-gpa-calculator.html` (1,288단어)**
AMCAS 방식(포함) / LSAC 방식(제외) / 소속대학 institutional GPA를 나란히 산출.
★ 차별화 = **"상쇄에 필요한 A학점 수"**. 공식: `필요학점 = 이중등록학점 × (대학GPA − 이중등록GPA) ÷ (4 − 대학GPA)`.
3.7 학생이 15학점 B급 이중등록을 상쇄하려면 **A학점 약 35학점(2학기 이상)**이 필요하다. 삭제가 아니라 희석이라는 걸 수치로 보여주는 게 핵심. 대학GPA가 4.0이면 수학적으로 상쇄 불가라는 분기도 처리했다.

**2. `blog/does-dual-enrollment-affect-your-gpa.html` (1,395단어)**
"GPA가 하나가 아니다"(고교 / 소속대학 / 입시기관 3종) 구조 정리 + LSAC 변경 + AMCAS 존치.
★ 경계 조건 명시: **LSAC 제외는 "프로그램 명칭"이 아니라 "언제 수강했는가" 기준**이다. 대학 재학 중 커뮤니티칼리지에서 들은 과목은 이중등록이라 불렸어도 여전히 포함된다. 7sage에서 실제로 학생이 혼동한 지점이라 FAQ로 넣었다.
AP/IB는 시험점수 기반이라 성적이 대학 트랜스크립트에 남지 않는다는 비대칭도 정리.

### 사실 확인 (교차 검증한 것)
- AMCAS: **미전학 학점도 GPA 포함**, "High School" 연도 표기 — AAMC 공식 페이지
- LSAC: 2026-07-28 시행, 제출 트랜스크립트 기준 — LSAC transcript-summarization 페이지 + LSAC 공지 원문(7sage 인용) + LawHub
- 재수강 시 **전 시도 평균**(대체 아님) — MedEdits/AAMC
- 기관 grade forgiveness는 입시 GPA에 무효
- 이중등록 성적은 고교·대학 트랜스크립트 양쪽에 기재 — UF 이중등록 FAQ

### 중복 확인
`dual enrollment` 언급은 기존 5개 파일에서 부수적 언급뿐이고, `what-gpa-do-you-need-for-med-school`에는 **0건**이었다. LSAC/AMCAS 언급도 2개 파일 부수적. 신규 주제로 확인.
체크리스트 40번(형태 유사성) 고려: GPA 계산기 변형이 아니라 **두 입시기관 GPA 체계 비교**라는 별개 계산이고, 클러스터 주력 자산을 블로그로 두어 유사성 리스크를 낮췄다.

### 검증
파이썬 모델 ↔ jsdom 9개 시나리오 일치(4.3 클램프, 0 나눗셈, 이중등록이 더 높은 경우, GPA 4.0 경계). getComputedStyle(display) 3경로 확인. node --check 통과.

---

## ★ 다음 세션이 확인/처리할 것

1. **색인 수동 제출 금지 / 패닉 재작성 금지** — v19·v21 원칙 유지.
2. **★ LSAC 규정 변경 추적.** 이 클러스터의 핵심 자산은 "2026-07-28 변경"이다. 시행 초기라 **세부 운용이 바뀔 수 있다.** 다음에 이 페이지를 손볼 때 반드시 LSAC 공식 페이지를 재확인하고, 바뀌었으면 즉시 갱신할 것. 우리가 선점한 이유가 최신성이므로 낡으면 가치가 역전된다.
3. **이중등록 클러스터 확장 후보** — 이번엔 2페이지로만 열었다. 여지 있는 하위 주제: 이중등록 학점의 전학 인정률, 이중등록 vs AP 비용 비교, 이중등록 학생의 신입생 지위(non-degree seeking) 문제. 다만 **성과 확인 후에 확장**할 것.
4. **Bing 상위 페이지 보강 계속**(v21 목록 유지): `what-is-the-deans-list-gpa-requirement`(Bing 203노출), `pell-lifetime-eligibility-calculator`(183), `what-gpa-do-you-need-for-nursing-school`(34노출 4.35위). CTR 높은 소형 페이지 3개도 유효: `what-gpa-to-keep-scholarship`(40%), `average-student-loan-debt-by-major`(9.09%), `sap-calculator`(8.7%).
5. **교육 세금 클러스터는 1~4월 판정**(v20 유지).
6. **수익화 — v18 정정 유지.** 월 세션 500 또는 월 검색 클릭 50 도달 전까지 요구하지 말 것. v21 기준 세션 약 128/4주, 검색 클릭 27로 근접 중.

## 2주 재작업 보류 현황 (08-25 기준)
- **08-31까지**: `tools/repeat-coursework-aid-calculator.html`, `tools/gpa-raise-calculator.html`
- **09-01까지**: `tools/scholarship-tax-calculator.html`, `blog/1098-t-box-5-exceeds-box-1.html`
- **09-07까지**: `tools/employer-tuition-assistance-calculator.html`, `blog/does-retaking-a-class-replace-your-gpa.html`
- **09-08까지**: 이번 세션분 — `tools/dual-enrollment-gpa-calculator.html`, `blog/does-dual-enrollment-affect-your-gpa.html`
- **보류 해제**: `tools/r2t4-calculator`, `tools/gpa-scale`, `methodology.html`, `editorial-policy.html`(08-26), `what-is-the-deans-list-gpa-requirement`, `ib-gpa-calculator`, `percentage-to-gpa-converter`, `gpa-to-letter-grade-converter`, 그 외 08-01 이전 전체
  (이번 세션에 **상호링크만** 추가한 6개는 보류 예외, lastmod 미갱신)

## 파일 현황 (08-25 기준)
- tools **44개** + index / blog **57개** + index / 루트 7개
- sitemap URL **107개**, tool-card 44개(미등록 도구 0), blog-card 55개(미등록 1건 = 404 스텁 `how-to-raise-your-gpa.html`)
- 전체 111개 HTML JSON-LD 오류 0, 내부링크 broken 0

## 클러스터 현황 (9개)
GPA 계산/변환 · 시험점수 · 연방지원 규정 · 학자금대출 · 전공·커리어 ROI · 유학 · 학사경고·복학 · 교육 세금 · **이중등록(신규)**

### 아직 비어 있는 영역 (경쟁조사 미실시)
재향군인 GI Bill · 홈스쿨 성적증명 · 장애 학생 편의제공 · 로스쿨 준비(LSAT/GPA) · 대학원 조교(TA/RA) 학비면제 과세 · CLEP/사전학습인정(CPL)
→ **유학생 F-1 재정증명과 근로장학은 이번에 기각했으므로 목록에서 제외했다.**

## 체크리스트 추가분 (v21 37~40번에 이어서)
41. **규정이 최근 바뀐 주제를 우선 노려볼 것.** 08-25에 LSAC 2026-07-28 변경을 찾았고, 이 한 건이 클러스터 전체의 차별화 근거가 됐다. 기존 상위 문서들이 아직 옛 규정을 서술 중이라 신생 도메인도 정확성만으로 앞설 수 있다. **단 최신성이 무기이므로 갱신 책임이 따른다**(위 항목 2 참고).
42. **경쟁이 약해도 "도구가 성립하는가"를 먼저 볼 것.** F-1 재정증명은 .edu만 있어서 공백처럼 보였지만, 증명 금액이 학교별이라 범용 계산기를 만들 수 없어 기각했다. 공백 ≠ 기회다.
43. **두 기관이 같은 사안을 다르게 처리할 때가 좋은 소재다.** AMCAS는 포함하고 LSAC은 제외하는 상황처럼, 제도 간 불일치는 검색 수요가 크고 정리된 문서가 잘 없다.

---

## [보존] 이전 문서 v21 본문 (2026-08-24 세션까지)

# GPA Vault 인수인계 문서 v21 (2026-08-24 세션 — 구글 색인 이탈의 기계적 원인 규명 + Bing 3배 성장 확인)

이전 v20 문서를 대체함. v20 이하 본문은 아래에 그대로 보존.

### 0단계 대조 결과
최신 커밋 `8f177bf`(08-18 handover v20)과 v20 기록 일치 — 소급 기록 불필요.

### ★ 먼저 확인할 것
v19 본문 최상단의 **"절대 하지 말 것 — 색인 수동 제출 금지"**는 그대로 유효. IndexNow·구글 색인 요청은 하지 않는다. **아래에서 색인 이탈 31건을 다루지만, 그 대응도 수동 제출이 아니다.**

---

## ★★★★★★ 결론 1: 구글 노출 붕괴의 기계적 원인을 찾았다 — 색인 이탈

사용자가 이번에 **"크롤링됨 - 현재 색인이 생성되지 않음"** 드릴다운을 처음 제공했다(v19가 요청했던 항목). 결과:

**11건 → 31건, 3배 증가.**

포함된 페이지가 심각하다 — 구글 노출 상위권이 거의 그대로 들어있다:
`gpa-scale.html`(노출 678, 사이트 1위), `gpa-to-letter-grade-converter`(438), `college-cost-calculator`(356), `act-score-calculator`(297), `sat-score-calculator`(202), `loan-repayment-calculator`(166), `ib-gpa-calculator`(548), `what-is-the-deans-list-gpa-requirement`(504), `weighted-gpa-calculator`, `final-exam-calculator`, `financial-aid-calculator`, `gpa-calculator`, `r2t4-calculator`, `about`, `contact`, `glossary`, `editorial-policy`, `tools/` 등.

**즉 v19가 "노출 집계 축소"로 해석했던 현상의 실제 메커니즘은 색인 이탈이었다.** 노출이 준 게 아니라 페이지가 색인에서 빠졌다. 3개월 누적 노출 수치는 8월 초 이전의 잔존값이다.

### ★ 그런데 "얇아서" 빠진 게 아니다 (중요 — 패닉 재작성 금지 근거)
분량으로 검증했더니 가설이 깨졌다:
- 색인 **유지** 중: `study-abroad-financial-aid-guide` 617단어, `what-is-pslf` 749단어, `ap-credit-calculator` 1,127단어
- 색인 **이탈**: `gpa-scale` 1,815단어, `how-much-student-loan-debt-is-too-much` 1,802단어, `glossary` 1,742단어

얇은 페이지(`contact` 92단어)와 두꺼운 페이지가 함께 빠졌고, 도구와 블로그 양쪽에 걸쳐 있으며, 08-12에 보강한 `gpa-scale`도 보강 후에 빠졌다. **페이지별 콘텐츠 품질 문제가 아니라 사이트 레벨 권위 판단으로 봐야 한다.**

### ★★ 결정적 반증: Bing은 같은 콘텐츠를 전부 색인하고 1~10위에 올린다
`gpa-raise-calculator`는 구글에서 "발견됨-미색인"(크롤조차 안 됨)인데 **Bing에서는 31노출 5.13위에 클릭 1**이다. `sap-calculator`는 Bing 8.7% CTR. 같은 HTML, 정반대 결과.

**따라서 콘텐츠를 갈아엎는 대응은 근거가 없다.** 신생 저권위 도메인에 대한 구글의 색인 기준이 Bing보다 훨씬 높을 뿐이다. 시간과 외부 신호(자연 유입 링크, 브랜드 검색)로 풀리는 문제이지 리라이팅으로 풀리는 문제가 아니다.

**대응 원칙(다음 세션도 유지):** 색인 이탈을 이유로 ① 대규모 재작성 ② 페이지 삭제/통합 ③ 확장 중단 — **셋 다 하지 않는다.** 사용자 지시(공격적 확장 유지)와도 일치하고 데이터와도 일치한다.

---

## ★★★★★ 결론 2: Bing이 3배 성장했다 — 여기가 사업이다

| | 구글 (3개월) | Bing (같은 기간) |
|---|---|---|
| 노출 | 5,626 (지난주 5,644) | **1,115** (지난주 354 → **3.1배**) |
| 클릭 | 7 (변화 없음) | **20** (지난주 7 → **2.9배**) |
| CTR | 0.12% | **1.79%** |
| 평균 순위 | 53 | **약 5** |

GA4(07-27~08-23): **활성 사용자 100명**(72 → 83 → 100, 3주 연속 증가).
소스: direct 48 / **bing 28 + yahoo 13 + duckduckgo 4 = 45** / google **3**.
세션 기준으로도 bing 34 + yahoo 14 + ddg 4 + copilot.com(ai-assistant) 2 vs google 3.

**구글 유입은 3명, Bing 생태계는 45명이다. 15배.** 구글 일별 노출은 3~8로 계속 바닥(08-15는 0).

### Bing 상위 페이지 (이번 주)
| 페이지 | 노출 | 클릭 | 순위 |
|---|---|---|---|
| blog/does-retaking-a-class-replace-your-gpa | **450** (지난주 146) | 3 | 5.36 |
| blog/what-is-the-deans-list-gpa-requirement | 203 (75) | 0 | 5.34 |
| tools/pell-lifetime-eligibility-calculator | 183 (54) | 3 | 5.51 |
| blog/what-gpa-do-you-need-for-nursing-school | 34 | 1 | 4.35 |
| tools/gpa-raise-calculator | 31 | 1 | 5.13 |
| tools/sap-calculator | 23 | 2 | **8.7% CTR** |
| blog/average-student-loan-debt-by-major | 22 | 2 | **9.09% CTR** |
| blog/what-gpa-to-keep-scholarship | 5 | 2 | **40% CTR** |

---

## 08-24 세션 작업 (커밋 `e5e6027`, push + Actions `completed/success` 확인)

### 신규 1건: `tools/employer-tuition-assistance-calculator.html` (1,520단어)

v20 백로그 1순위였던 Section 127. **GPA 계산기 변형이 아니라 교육 세금 클러스터 확장**이라, 유사 페이지 누적으로 인한 색인 리스크를 키우지 않는 선택이기도 하다.

**경쟁조사**: 검색 결과가 BDO, BCLP, Cerini, CapinCrouse, Horton Group, BLR, Instead, Forbes 등 **전부 고용주/HR/회계법인용 컴플라이언스 문서**다. 직원 관점 계산기는 확인되지 않았다. "쓰여 있긴 한데 독자가 다른" 유형의 공백.

**규정 (IRS FS-2026-10 / IR-2026-55, 26 USC 127 교차 확인)**
- 연 **$5,250** 비과세. 1978년부터 동결이었으나 OBBBA로 **2026년 이후 과세연도부터 물가연동**
- ★ **등록금과 학자금 대출상환이 별도 한도가 아니라 합산 한도**다. IRS 예시 그대로: 대출에 $2,000 쓰면 등록금에는 $3,250만 남는다. 미사용분 이월 불가
- 대출상환 옵션은 OBBBA로 **영구화**(기존 2025년 말 일몰 삭제). **입사 前에 받은 대출도 대상**이고 고용주가 대주에게 직접 지급 가능
- 한도 초과분은 일반 임금 → 소득세 + **급여세(7.65%)**까지 부과
- 비과세 지원금으로 낸 등록금은 교육 크레딧 대상 불가(장학금과 동일한 double-dipping 금지)
- Section 127로 제외된 이자는 학자금 이자공제(§221)와 중복 불가
- 직무 관련성 불필요(학부·대학원 모두). 스포츠·게임·취미 과정, 식비·숙박·교통은 제외

**차별화 — 배분 최적화**: 등록금이 낮을수록 지원금을 **대출상환에 돌리는 게 유리**하다.
등록금 $4,000 + 지원금 $5,250이면 전액 등록금 사용 시 AOTC 0원, 대출로 돌리면 $4,000이 크레딧 대상으로 남아 **$2,500 차이**. 등록금 $6,000이면 $1,750 차이, $8,000이면 $312 차이, 약 $9,250 초과면 차이 없음(어차피 $4,000 이상 자기부담). **현금 이동액은 양쪽 동일**하므로 공정한 비교다.

**검증**: 파이썬 모델 ↔ jsdom 11개 시나리오 결과 일치. 한도초과, 소득제한, 부부합산, 대출배분 초과 입력, 전부 0 입력 방어 확인. getComputedStyle(display) 3경로 확인.

### 보강 1건: `blog/does-retaking-a-class-replace-your-gpa.html` (2,169 → 2,729단어)

Bing 최대 자산(450노출, 5.36위). 08-15 보류 해제됐고 v20이 보강 1순위로 지정한 건.
**Bing 롱테일 쿼리가 가리킨 실제 빈틈 2개**를 채웠다(우리 추측이 아니라 데이터 근거):
- `university transcript repeated course d then f then retake impact`(5.67위) → **재수강 성적이 더 나쁠 때**. most-recent-grade 정책이면 GPA가 오히려 나빠지고 highest-grade 정책이면 보호된다는 차이. 기존 본문에 전혀 없던 내용
- Clemson 학업사면 질문(**12노출, Bing 키워드 리포트 전체 1위**) + dual enrollment 재수강 질문 → **다른 학교에서 재수강 후 학점 이전으로 성적 대체가 되는가**. 편입학점은 grade point 없이 들어오므로 대체 불가. 역시 없던 내용

FAQ 2개 추가(본문·스키마 8:8), dateModified·sitemap lastmod 갱신.

---

## ★ 다음 세션이 확인/처리할 것

1. **색인 수동 제출 금지 — 유효.** 색인 이탈 31건을 봐도 마찬가지다. 다시 액션으로 올리지 말 것.
2. **색인 이탈에 대규모 재작성으로 반응하지 말 것.** 위 결론 1의 근거(분량 무관, Bing은 정상 색인) 참고. 31건이 40~50건으로 더 늘어도 **Bing 지표와 GA4가 성장 중이면 전략 유지**가 맞다. 판단 기준을 구글 색인 수가 아니라 GA4 활성 사용자 + Bing 클릭으로 둘 것.
3. **Bing 상위 페이지 보강 계속.** 다음 후보 순서: `blog/what-is-the-deans-list-gpa-requirement`(Bing 203노출 5.34위, **08-22 보류 해제됨**), `tools/pell-lifetime-eligibility-calculator`(183노출, 클릭 3), `blog/what-gpa-do-you-need-for-nursing-school`(34노출 4.35위, 클릭 1).
4. **CTR이 높은 소형 페이지를 눈여겨볼 것.** `what-gpa-to-keep-scholarship` 40%, `average-student-loan-debt-by-major` 9.09%, `sap-calculator` 8.7%. 노출은 적지만 전환율이 높아 노출만 늘면 바로 클릭이 된다. 이 3개는 보강 가성비가 좋다.
5. **교육 세금 클러스터는 1~4월에 판정.** (v20 항목 유지) 지금 성과 없다고 접지 말 것.
6. **수익화 — v18 정정 유지.** 월 세션 500 또는 월 검색 클릭 50 도달 전까지 제휴·광고 액션을 사용자에게 요구하지 말 것. 현재 GA4 세션 약 128/4주, Bing+구글 검색 클릭 27. **임계치에 근접하고 있다** — Bing 성장 속도(주당 3배)가 유지되면 다음 1~2세션 안에 도달할 수 있다. 도달하면 그때 제휴 가입을 제안할 것.

## 2주 재작업 보류 현황 (08-24 기준)
- **08-26까지**: `tools/r2t4-calculator.html`, `tools/gpa-scale.html`, `methodology.html`, `editorial-policy.html`
- **08-31까지**: `tools/repeat-coursework-aid-calculator.html`, `tools/gpa-raise-calculator.html`
- **09-01까지**: `tools/scholarship-tax-calculator.html`, `blog/1098-t-box-5-exceeds-box-1.html`
- **09-07까지**: 이번 세션분 — `tools/employer-tuition-assistance-calculator.html`, `blog/does-retaking-a-class-replace-your-gpa.html`
- **보류 해제**: `blog/what-is-the-deans-list-gpa-requirement`, `tools/ib-gpa-calculator`, `tools/percentage-to-gpa-converter`, `tools/gpa-to-letter-grade-converter`(08-22 해제), 그리고 08-01 이전 전체
  (이번 세션에 **상호링크만** 추가한 5개는 보류 예외, lastmod 미갱신)

## 파일 현황 (08-24 기준)
- tools **43개** + index / blog 56개 + index / 루트 7개
- sitemap URL **105개**, tool-card 43개(미등록 도구 0), blog-card 54개
- 전체 109개 HTML JSON-LD 오류 0, 내부링크 broken 0
- 클러스터 8개(v20 목록 유지, 교육 세금이 3페이지로 확대)

## 체크리스트 추가분 (v20 32~36번에 이어서)
37. **"크롤링됨-미색인"을 콘텐츠 품질 문제로 단정하지 말 것.** 08-24에 분량과 색인 여부가 무관함을 확인했고(617단어 유지 vs 1,815단어 이탈), 같은 콘텐츠를 Bing은 전부 색인해 5위권에 올렸다. 색인 이탈은 신생 도메인의 권위 문제일 수 있고, 그 경우 리라이팅으로 풀리지 않는다. **반드시 다른 검색엔진의 색인 상태를 대조 확인한 뒤 판단할 것.**
38. **사이트 건강 판단 지표를 GA4 활성 사용자 + Bing 클릭으로 둘 것.** 구글 색인 수·노출은 참고 지표다. 08-24 기준 구글 노출은 바닥인데 GA4는 3주 연속 성장(72→83→100)했다.
39. **보강 대상은 추측이 아니라 Bing 키워드 리포트에서 고를 것.** 08-24에 "재수강이 더 나쁠 때", "타교 재수강 후 학점 이전"이라는 두 빈틈은 전부 실제 Bing 쿼리에서 나왔고, 그중 하나는 키워드 리포트 전체 1위(12노출)였다. 내부 브레인스토밍으로는 안 나왔을 주제다.
40. **신규 주제를 고를 때 "기존 페이지와 형태가 유사한가"를 함께 볼 것.** 색인 이탈이 진행 중인 상황에서 10번째 GPA 계산기 변형을 추가하는 것과, 다른 클러스터를 확장하는 것은 리스크가 다르다. 08-24에 Section 127을 고른 이유 중 하나가 이것이다.

---

## [보존] 이전 문서 v20 본문 (2026-08-18 세션까지)

# GPA Vault 인수인계 문서 v20 (2026-08-18 세션 — 신규 클러스터 "교육 세금" 개설)

이전 v19 문서를 대체함. v19 이하 본문은 아래에 그대로 보존.

### 0단계 대조 결과
최신 커밋 `346d9e1`(08-17 handover 수정)과 v19 기록 일치 — 소급 기록 불필요.

### ★ 이 문서를 읽는 다음 세션이 먼저 확인할 것
아래 v19 본문 최상단의 **"절대 하지 말 것 — 색인 수동 제출 금지"** 항목은 그대로 유효하다. IndexNow·구글 색인 요청은 하지 않는다.

---

## 이번 세션의 성격
사용자 지시: "신규를 폭넓게. 키워드 뽑고 → 리스트 → 경쟁 강도 체크 → 강하면 롱테일로 뚫기. 가능하면 새 클러스터 추가. **GSC나 우리 데이터 안에서만 보지 말고** 구글/네이버/레딧 등에서 문서 수는 적은데 관심은 있는 걸 찾아라."

→ 그래서 이번 세션은 **GSC/Bing 데이터를 근거로 쓰지 않았다.** 기존 클러스터 인벤토리에서 비어 있는 영역을 먼저 뽑고, 외부 검색으로 수요·경쟁을 직접 확인하는 방식으로 진행했다. 이 접근이 실제로 데이터 안에서는 절대 안 나왔을 신규 클러스터를 찾아냈다.

---

## ★★★★★ 신규 클러스터 개설: 교육 세금 (Education Tax)

기존 클러스터는 7개였다 — GPA/시험점수/연방지원/학자금대출/전공ROI/유학/학사경고. **세금 관련 콘텐츠는 0건**이었고, 이번에 8번째 클러스터로 개설했다.

### 후보 5개 조사 → 4개 기각 (다음 세션이 같은 후보를 재조사하지 말 것)

| 후보 | 판정 | 근거 |
|---|---|---|
| PhD 스티펜드 평가 | 기각 | phdstipends.com이 living wage ratio 정규화 DB 보유, applykite·academiainsider 등 다수 |
| NCAA 자격 (core-course GPA) | 기각 | NCSA(대형 리크루팅 사이트) 계산기 + collegize.ai 존재. 추가로 **sliding scale 폐지 여부를 두고 출처 간 서술이 충돌**(NCSA는 폐지, collegize는 사용 중이라고 서술) → 정확도 리스크까지 큼 |
| Academic renewal / grade forgiveness | 기각 | untangletools, gpacalculators.net, openeducat, learn.org, academicjobs 등 7곳+. **게다가 기존 `does-retaking-a-class-replace-your-gpa`와 내부 중복** |
| 장학금 displacement | 기각 | finaid.org, Scholarships360, uAspire, collegeaidpro, thescholarshipsystem, cirkledin + **MeritPlaybook은 586개교 정책 DB 기반 전용 도구 보유**. 구조적으로 이길 수 없음 |
| **교육 세금 (장학금 과세 + AOTC 배분)** | **채택** | 아래 참고 |

### 왜 교육 세금이 통과했나
- AOTC 일반 계산기는 존재한다(taxgrids.info). **그런데 그 사이트가 스스로 "scholarship allocation은 반영하지 못한다"고 면책 문구에 명시**해 놨다. 즉 핵심 변수를 아무도 계산해주지 않는다.
- Pell↔AOTC 배분 트레이드오프를 계산해주는 학생용 도구는 확인되지 않았다. 이 전략은 Form 8863 설명서와 Journal of Accountancy에 문서화돼 있지만 전문가용 서술뿐이다.
- `1098-T Box 5 > Box 1` 검색 결과는 **Claimyr, JustAnswer, TurboTax 커뮤니티, TaxSlayer 지원문서 등 포럼 Q&A 위주**다. 같은 질문이 반복 등장할 만큼 수요는 크고, 정리된 문서와 도구는 없다 → 사용자가 요구한 "문서 수는 적은데 관심은 있는" 전형적 롱테일 공백.

### 신규 2건 (쿼리셋 분리로 상호 카니발라이제이션 방지)

**1. `tools/scholarship-tax-calculator.html` (1,542단어)**
장학금/Pell 중 과세 대상 산출 + Form 8863 election 손익 비교. 도구의 질문은 **"얼마를 신고할까"**.

★ 핵심 인사이트(이게 이 도구의 존재 이유): **과세 장학금은 부양자녀 표준공제 산정 시 "근로소득"으로 취급된다.** 2026년 부양자 표준공제 = max($1,350, 근로소득+$450), 한도 $16,100. 따라서 근로소득 없는 학생이 $4,000을 신고하면 공제가 $4,450으로 올라가 **전액 흡수 → 추가 세금 0원, AOTC 최대 $2,500은 순이익**이 된다. 대부분의 학생에게 이 거래는 공짜다.

★ 두 번째 차별화: **세금은 학생 신고서에, 크레딧은 부양자(부모) 신고서에 잡힌다.** 거래의 양쪽이 서로 다른 신고서에 떨어진다는 걸 설명하는 곳이 거의 없다.

**2. `blog/1098-t-box-5-exceeds-box-1.html` (1,561단어)**
패닉 지점 진입 콘텐츠. 블로그의 질문은 **"이 양식이 뭘 뜻하나"**.
격차가 과세액을 과대평가하는 3가지 이유를 정리: (1) 필수 교재는 학교가 모르니 Box 1에 안 잡힘 (2) 역년 vs 학년도 시점 차이(봄학기 지원금이 12월에, 등록금은 1월에 계상) (3) IRS는 양식이 아니라 실제 지출 기준으로 판단. 그리고 **양식 수치를 임의로 고치는 것은 해법이 아니라는 점**을 명시.

### 수치 근거 (전부 2026 과세연도, IRS Rev. Proc. 2025-32)
- 표준공제: 단독 $16,100 / 부부합산 $32,200 / 세대주 $24,150
- 부양자 표준공제 = max($1,350, 근로소득 + $450), 한도는 단독 금액
- AOTC = 첫 $2,000의 100% + 다음 $2,000의 25% = 최대 $2,500, 40%(최대 $1,000) 환급형
- AOTC phase-out: 단독/세대주 $80,000~$90,000, 부부합산 $160,000~$180,000 (**물가연동 안 됨**)
- LLC: 첫 $10,000의 20% = 최대 $2,000, 비환급형, phase-out 동일

### 검증
파이썬 모델을 공개 사례에 대조 일치시킴:
- TurboTax 예시(Box5 $10,000 / Box1 $8,000 → $4,000 신고 시 AOTC $2,500) ✓
- FreeTaxUSA 예시(Pell $5,000 / 등록금 $5,000 → 환급형 $1,000 + 비환급형 $1,500) ✓
jsdom 10개 시나리오 + **getComputedStyle(display) 3경로(로드/입력/버튼클릭)** 확인. 분기 전수: 제한 장학금(신고 불가), MAGI 소득제한 초과, 이미 크레딧 최대, 전부 0 입력, 부부합산, 독립학생. node --check 통과.

### 안전장치 (세금 주제라 특별히 신경 쓴 부분)
세무 자문이 아님을 본문·FAQ·스키마 3곳에 명시. IRS Pub 970과 **캠퍼스 무료 VITA 클리닉** 안내(학생에게 실제로 가장 현실적인 선택지). 범위 밖임을 명기한 항목: 주 소득세, kiddie tax, 529 연계, LLC, 대학원생/유학생, 한 가족 다수 학생.

---

## ★ 다음 세션이 확인/처리할 것

1. **색인 수동 제출 금지 — v19 최상단 항목 유효.** 다시 액션으로 올리지 말 것.
2. **신규 클러스터 성과 확인.** 교육 세금 클러스터는 **계절성이 강하다** — 1098-T는 1월 말 발송, 신고 마감은 4월. 지금(8월)은 검색량 저점이므로 **8~11월 데이터로 실패 판정하지 말 것.** 진짜 판정 시점은 2027년 1~4월이다. 이 점을 모르면 다음 세션이 "성과 없다"고 오판하고 클러스터를 접을 수 있다.
3. **Bing Webmaster 데이터를 계속 받을 것**(v19 결론 유지). 구글 GSC만 보면 오판한다.
4. **`gpa-raise-calculator` 색인 여부** — 08-17 중복 해소가 통했는지 검증 필요.
5. **`methodology.html`** — 미색인 나머지 1건. 08-26까지 보류.
6. **Bing 상위 페이지 보강** — `does-retaking-a-class-replace-your-gpa`(Bing 146노출/5.09위)가 보류 해제 상태. 보강 1순위.
7. **수익화 — v18 정정 유지.** 월 세션 500 또는 월 검색 클릭 50 도달 전까지 제휴·광고 액션을 사용자에게 요구하지 말 것.

## 2주 재작업 보류 현황 (08-18 기준)
- **08-22까지**: `tools/ib-gpa-calculator.html`, `tools/percentage-to-gpa-converter.html`, `tools/gpa-to-letter-grade-converter.html`, `blog/what-is-the-deans-list-gpa-requirement.html`
- **08-26까지**: `tools/r2t4-calculator.html`, `tools/gpa-scale.html`, `methodology.html`, `editorial-policy.html`
- **08-31까지**: `tools/repeat-coursework-aid-calculator.html`, `tools/gpa-raise-calculator.html`
- **09-01까지**: 이번 세션분 — `tools/scholarship-tax-calculator.html`, `blog/1098-t-box-5-exceeds-box-1.html`
- **보류 해제**: 08-01 세션분 전체 및 그 이전(`does-retaking-a-class-replace-your-gpa`, `sap-calculator`, `pell-*`, `financial-aid-calculator`, `how-many-as-to-raise-gpa`, `gpa-calculator`, `weighted-gpa-calculator` 등)
  (이 중 6개는 이번 세션에 **상호링크만** 추가 — 보류 예외, lastmod 미갱신)

## 파일 현황 (08-18 기준)
- tools **42개** + index / blog **56개** + index / 루트 7개
- sitemap URL **104개**, tool-card 42개(미등록 도구 0), blog-card 54개(미등록 2건 = 404 스텁 `how-to-raise-your-gpa.html`, index)
- 전체 108개 HTML JSON-LD 오류 0, 내부링크 broken 0

## 클러스터 현황 (8개)
GPA 계산/변환 · 시험점수(SAT/ACT/AP/IB) · 연방지원 규정(SAP/Pell/R2T4/Repeat Coursework/IPA/OBBBA) · 학자금대출 · 전공·커리어 ROI · 유학 · 학사경고·복학 · **교육 세금(신규)**

### 아직 비어 있는 영역 (다음 확장 후보, 경쟁조사 미실시)
유학생(F-1 재정증명·CPT/OPT) · 재향군인 GI Bill · 근로장학(Federal Work-Study) · 고교 이중등록/조기대학 · 홈스쿨 성적증명 · 장애 학생 편의제공 · 로스쿨(LSAT/GPA) · 고용주 학비지원(Section 127 $5,250)
→ 이 중 **Section 127 고용주 학비지원**은 교육 세금 클러스터와 자연스럽게 이어지고, OBBBA로 학자금 상환까지 영구 적용 대상이 됐으므로 다음 확장 1순위로 검토할 만하다.

## 체크리스트 추가분 (v19 30~31번에 이어서)
32. **신규 클러스터를 찾을 때는 우리 GSC/Bing 데이터 밖에서 시작할 것.** 자체 데이터는 이미 순위가 잡힌 주제만 보여주므로 구조적으로 신규 영역이 안 나온다. 기존 클러스터 인벤토리를 먼저 뽑아 "비어 있는 칸"을 나열한 뒤, 외부 검색으로 수요·경쟁을 직접 확인하는 순서가 맞다. 08-18에 이 방식으로 교육 세금 클러스터를 찾았다.
33. **경쟁 판정 시 "전용 도구가 있는가"와 "포럼 Q&A만 있는가"를 구분할 것.** 검색 결과가 10건이어도 전부 Claimyr/JustAnswer/커뮤니티 답변이면 그건 포화가 아니라 **정리된 문서가 없다는 신호**다. 반대로 결과가 적어도 전용 DB 기반 도구(MeritPlaybook 586개교 DB)가 하나 있으면 그쪽이 훨씬 강한 경쟁이다.
34. **경쟁 사이트의 면책 문구를 읽을 것.** taxgrids.info가 "scholarship allocation은 반영 못 함"이라고 스스로 적어둔 덕분에 정확한 빈틈을 특정할 수 있었다. 경쟁자가 못 한다고 밝힌 것이 곧 우리 차별화 지점이다.
35. **계절성 있는 클러스터는 판정 시점을 handover에 못 박을 것.** 교육 세금은 1~4월이 성수기다. 비수기 데이터로 실패 판정하면 멀쩡한 클러스터를 접게 된다.
36. **세금·법률처럼 자격이 필요한 주제는 "자문 아님" 고지를 본문·FAQ·스키마 3곳에 넣고, 무료 공적 창구(VITA 등)를 안내할 것.**

---

## [보존] 이전 문서 v19 본문 (2026-08-17 세션까지)

# GPA Vault 인수인계 문서 v19 (2026-08-17 세션 — Bing이 실질 채널임을 데이터로 확인 + 구글 노출 미회복 재진단)

이전 v18 문서를 대체함. v18 이하 본문은 아래에 그대로 보존.

### 0단계 대조 결과
최신 커밋 `760ab83`(08-12 CSS 수정)과 v18 기록 일치 — 소급 기록 불필요.

---

## ★★★★★★ 절대 하지 말 것 — 색인 수동 제출 금지 (사용자 확정 방침, 2026-08-17 명문화)

**IndexNow 제출, 구글 URL 검사/색인 생성 요청, 그 밖의 모든 수동 색인 제출을 하지 않는다. 검색엔진이 자연스럽게 크롤링해 가도록 둔다.**

- 이것은 사용자가 **구글 색인 논의 때 이미 지시했던 사항**이다. 그런데 v17~v19 인수인계 문서 어디에도 기록되지 않았고, 그 결과 **4개 세션 연속으로 "IndexNow 제출이 최우선 액션"이라고 반복 제안**하는 사고가 났다. 지시를 문서화하지 않은 것이 근본 원인이다.
- 이미 배포된 IndexNow 키 파일(`/4ecbb2cc...txt`)은 **그대로 둔다**. 파일이 존재하는 것 자체는 무해하며, 삭제도 별도 작업이므로 사용자 지시 없이 건드리지 않는다. **단 그 키로 제출 API를 호출하지 않는다.**
- 색인이 안 되는 페이지를 발견해도 대응은 **수동 제출이 아니라 내부 원인 제거**다: 중복 판정 해소, 내부링크 보강, 얇은 분량 보강, sitemap lastmod 갱신까지가 우리가 하는 일의 전부다. (08-17에 `gpa-raise-calculator` 중복 해소로 처리한 방식이 올바른 예시.)
- **다음 세션이 이 항목을 다시 액션 아이템으로 올리면 그 자체가 실수다.**

### 함께 새긴 교훈 — 사용자 구두 지시는 즉시 문서화할 것
세션 중 사용자가 내린 방침성 지시(하지 말 것 / 바꾸지 말 것 / 우선순위)는 **그 세션 handover에 반드시 남긴다.** 남기지 않으면 다음 세션이 데이터만 보고 정반대 결론을 내리고, 사용자는 같은 말을 반복하게 된다. 이번 IndexNow 건이 정확히 그 사례다.

---

## ★★★★★ 결론 1: 구글 노출은 회복되지 않았다. 그리고 그건 이제 중요한 문제가 아니다

v18이 "다음 세션에 노출 회복 여부를 확인하고, 2주 지나도 한 자릿수면 사이트 차원 재진단"이라고 남겼다. **회복 안 됐다.**

일별 노출: 08-04 53 → 08-05 9 → ... → 08-10 11 → 08-11 12 → 08-12 8 → 08-13 8 → 08-14 3 → 08-15 0.
붕괴 이전이 하루 200~350이었으니 **11일 연속 98% 수준 하락 유지**.

**그런데 클릭은 3개월 누적 8 → 7로 거의 변화가 없다**(1건은 롤링 윈도우에서 빠진 것). 노출만 죽고 클릭은 그대로다.

### 웹 조사 결과 — v18의 외부요인 판단은 유지되나, 해석이 달라져야 한다
- 8/1~3과 8/5~6에 서드파티 추적기 변동성 확인, 구글은 **여전히 업데이트 미확정**. 마지막 확정 업데이트는 6월 스팸 업데이트(6/26 종료).
- 보고된 사례들이 서로 모순됨(7/22부터 하락한 곳, 8/6에 회복한 곳, 70% 빠졌다가 몇 시간 뒤 복구된 곳). 즉 **단일 원인의 코어 업데이트가 아님**.
- **★ 가장 중요한 관찰**: Barry Schwartz 지적 — 순위 변동 자체가 매년 덜 중요해지고 있다. 구글이 순위와 무관하게 퍼블리셔로 보내는 트래픽을 계속 줄이고 있고, **대형 퍼블리셔들이 구글 검색 차단을 진지하게 검토 중**이다. "구글이 콘텐츠를 크롤링하고 구글이 방문자를 보낸다"는 교환이 뒤집혔다. 순위를 가장 집요하게 추적하는 사이트가 **밑에서 줄어들고 있는 채널을 최적화하고 있는** 상황일 수 있다.
- 진단법: 노출 대폭 하락 + 클릭 소폭 하락 = 품질 강등이 아니라 노출 집계 축소.

**→ 우리 데이터가 정확히 그 패턴이다. 사이트 차원 재진단 결과: 사이트 문제 아님. 구글 채널 자체가 축소된 것.**

---

## ★★★★★ 결론 2: Bing이 이 사이트의 실질 채널이다 (이번 세션 최대 발견)

사용자가 이번에 Bing Webmaster 데이터를 처음 제공했고, 그림이 완전히 뒤집혔다.

| | 구글 (3개월) | Bing (같은 기간) |
|---|---|---|
| 노출 | 5,644 | 354 |
| 클릭 | 7 | **7** |
| CTR | 0.12% | **1.98%** |
| 평균 순위 | 53 | **약 5** |

**Bing은 구글의 1/16 노출로 같은 클릭 수를 만든다.** 키워드 리포트 기준 CTR은 10%(70노출/7클릭)까지 나온다.

GA4도 같은 방향이다(07-20~08-16, 활성 사용자 83 — 직전 72에서 증가):
- **bing 21 + yahoo 11 + duckduckgo 2 = 34** vs **google 4**
- 세션 기준으로도 bing 25 + yahoo 12 + duckduckgo 2 + copilot.com(ai-assistant) 2 vs google 4
- direct 42명이 최다 — 여기에 AI 어시스턴트 경유 유입이 섞여 있을 가능성이 높음

Yahoo·DuckDuckGo·Copilot이 전부 Bing 인덱스를 쓰므로, **실질적으로 검색 유입의 89%가 Bing 생태계**다.

### ★ Bing 쿼리는 전부 롱테일 대화형이다 — 우리 전략이 맞았다는 증거
- "what weighted gpa is b- average with an ap and 3 honors classes" (8노출, 6.5위)
- "how many grades needed to raise gpa 12 in 20 credits to 19 overall" (4노출)
- "how grades from study abroad affect undergraduate financial aid" (**1위**)
- "does ibsu completely overwrite a failing grade on the cumulative gpa calculation once the unit is successfully retaken"
- "ifi have two associates degress how much of my federal pell lifetime eligibilty have i used?" (오타 포함)
- "what isthe average student loan balance for social science majors in usa" (**1위, 클릭 1**)

전부 Copilot 스타일 자연어 문장이다. **롱테일 + 니치 연방규정 전략이 Bing에서는 실제로 1~10위를 만들고 있다.** 구글에서 40~80위인 것과 대조적.

### Bing 상위 페이지 (구글과 완전히 다른 순서)
| 페이지 | Bing 노출 | Bing 순위 | 구글 노출 |
|---|---|---|---|
| blog/does-retaking-a-class-replace-your-gpa | **146** | 5.09 | 1 (45위) |
| blog/what-is-the-deans-list-gpa-requirement | 75 | 5.45 | 504 |
| tools/pell-lifetime-eligibility-calculator | 54 | 5.13 | 24 |
| blog/what-gpa-do-you-need-to-graduate-college | 16 | **2.94** | 175 |
| blog/average-student-loan-debt-by-major | 8 | 3.38 | **0** (클릭 2, CTR 25%) |

**★ 구글 노출이 0인데 Bing에서 클릭이 나오는 페이지들이 있다**(average-student-loan-debt-by-major, what-gpa-to-keep-scholarship, how-to-calculate-cumulative-gpa 등). 구글 페이지 리포트에 아예 안 나오는 페이지가 약 10개.

### → 전략 변경 아님, 평가 지표 변경
사용자 지시대로 **공격적 확장 전략은 그대로 유지**한다. 바꿀 것은 성과를 무엇으로 판단하느냐다.
**앞으로 세션 성과 판단은 Bing 순위/CTR + GA4 사용자 수를 1차 지표로, 구글 노출은 참고 지표로 볼 것.** 구글 노출이 회복되지 않아도 그것만으로 콘텐츠 품질 문제라고 판단하지 말 것.

---

## 08-17 세션 작업 내역 (커밋 `e76c7b0`, push + Actions `completed/success` 확인)

### 신규 1건: `tools/repeat-coursework-aid-calculator.html` (1,661단어)

**선정 경위 — 후보 2개 조사, 1개 기각**
Bing 최대 자산이 리테이크 클러스터(`does-retaking-a-class-replace-your-gpa`, 146노출 5.09위, GA4 조회 2위)라 여기서 확장하기로 함.
1. **Retake/Grade Replacement GPA 계산기** → **기각**. 경쟁 7곳+ (best-calculators, pearson.com, cgpacalculatoronline, thegpacalculator, gpagradecalculator, gpacalculators.net, kean.edu). 완전 포화.
2. **Repeat Coursework 지원금 자격 계산기** → **채택**. 검색 결과가 .edu 9곳(UCF, 애리조나, Southern Connecticut, Stockton, UWG, UTRGV, GSU, Temple, CCS) + 독립 계산기 1곳(cumgpacalculator, 경고 박스 수준)뿐. SAP·R2T4와 동일한 공백 패턴.

**규정 (34 CFR, .edu 9곳 교차 확인)**
- 이미 통과한 과목은 **Title IV 지원 재수강 1회만** 허용. 3번째 시도는 지원 대상 아님.
- 낙제(F)/철회(W) 과목은 **통과할 때까지 무제한** 지원 가능.
- 통과 기준 = **D 이상** 또는 P/S/CR. (전공은 C 이상을 요구하는데 지원 규정상으론 이미 "통과"라 함정)
- **재수강을 W/F로 끝내도 1회는 소진됨**(UWG 명시). 이게 학생들이 가장 억울해하는 지점.
- 이전 시도에 지원금을 안 받았어도 규정 적용(시도 횟수 기준, 자금 출처 무관).
- 제외된 학점은 **재학 상태 산정에서 빠짐** → Pell intensity 하락, 6학점 미만이면 Direct Loan 차단.
- 교내/주정부 장학금은 실제 등록 학점 기준이라 대개 영향 없음(CCS).
- SAP는 반대 방향: 지원금이 안 나온 시도도 attempted credits에 포함됨.

**차별화**: .edu 페이지들은 시나리오 표만 제시하고 끝난다. 이 도구는 제외 후 실제 aid-eligible 학점 → 재학 상태 → Pell 손실 금액 → **비재수강 학점 몇 개를 더 들으면 무력화되는지**까지 계산. "15학점 중 3학점 제외는 손실 0, 12학점 중 3학점 제외는 Pell 25% 손실" — 같은 재수강인데 시간표에 따라 결과가 갈린다는 게 핵심 인사이트.

**검증**: UCF(12→9), Temple(15→12), CCS(12→9) 공개 사례와 계산 일치. jsdom 8개 시나리오 + **getComputedStyle(display) 3경로 확인**(v18 교훈 반영). 0 나눗셈, 제외>총합 역전 입력 방어 확인. 신규 9개 체크리스트 전항목 적용(noscript 99개 파일, 중복 0).

**카니발라이제이션 방지**: `pell-enrollment-intensity-calculator`와 역할 분리 — 이 도구는 "어느 학점이 세는가", Pell 도구는 "센 학점이 얼마가 되는가". 상호링크로 명시.

### 보강 1건: `tools/gpa-raise-calculator.html` (1,155 → 1,321단어) — 미색인 원인 해소

v18이 다음 세션 과제로 남긴 건. GSC 발견됨-미색인 2건 중 1건이고, nav로 100개 파일에서 링크되는데도 크롤링이 안 됨 → `blog/how-many-as-to-raise-gpa.html`(2,215단어, 노출 591/17.31위)과의 중복 판정으로 확정.

실제로 확인해보니 title 개념이 동일("How Many A's Do You Need")하고 H2도 등급대체/초기학기영향/학점수가 겹쳤음.

**블로그는 사이트 최고 성과 페이지라 손 안 댐. 도구 쪽만 차별화:**
- title/description을 **reachability(도달 가능성)** 축으로 전환
- 중복 H2 2개를 **"GPA 상한선(ceiling)"** 개념으로 교체 — 블로그가 안 다루는 각도.
  상한 = (기존 quality points + 4.0 × 잔여학점) ÷ 총학점.
  검산: 2.4/60완료/60잔여 → 3.2(3.5는 수학적으로 불가능), 2.4/30완료/90잔여 → 3.6. 같은 GPA인데 타이밍만으로 선택지가 갈림.
- 역할 분담 명시: **블로그 = 개수 질문, 도구 = 도달 가능 여부.** llms.txt에도 명기.

---

## ★ 다음 세션이 확인/처리할 것 (우선순위순)

1. ~~IndexNow 제출~~ → **영구 금지. 아래 "절대 하지 말 것" 항목 참고. 다시 제안하지 말 것.**
2. **Bing Webmaster 데이터를 매번 받을 것.** 이번에 처음 받았는데 판단이 완전히 바뀌었다. 구글 GSC만 보면 "죽은 사이트"로 오판하게 된다. Page Traffic Report + Keyword Report 두 개면 충분.
3. **`gpa-raise-calculator` 색인 여부 재확인.** 이번 차별화가 통했는지가 "중복 판정 → 크롤링 거부" 가설의 검증이다. 여전히 미색인이면 가설이 틀린 것이므로 다른 원인(nav 링크 과다로 인한 저품질 신호 등)을 봐야 한다.
4. **`methodology.html`** — 미색인 2건 중 나머지. 08-12에 617→1,016단어로 보강 + h1/스키마 추가했으므로 그 효과를 확인만 하면 됨. 08-26까지 보류라 이번엔 손대지 않았다.
5. **Bing 상위 페이지 우선 보강 검토.** `does-retaking-a-class-replace-your-gpa`(146노출)가 압도적 1위인데 08-15에 보류 해제됐다. 다음 세션에 보강 후보 1순위. `what-gpa-do-you-need-to-graduate-college`도 Bing 2.94위로 클릭 직전.
6. **수익화 — v18 정정 유지.** 월 세션 500 또는 월 검색 클릭 50 도달 전까지 제휴·광고 액션을 사용자에게 요구하지 말 것. 현재 GA4 세션 약 108/4주, 검색 클릭 14/3개월로 임계치 한참 아래. 다만 **Bing CTR이 2%라 트래픽이 늘면 전환이 실제로 발생할 구조**는 확인됐다.

## 2주 재작업 보류 현황 (08-17 기준)
- **08-22까지**: `tools/ib-gpa-calculator.html`, `tools/percentage-to-gpa-converter.html`, `tools/gpa-to-letter-grade-converter.html`, `blog/what-is-the-deans-list-gpa-requirement.html`
- **08-26까지**: `tools/r2t4-calculator.html`, `tools/gpa-scale.html`, `methodology.html`, `editorial-policy.html`
- **08-31까지**: 이번 세션분 — `tools/repeat-coursework-aid-calculator.html`, `tools/gpa-raise-calculator.html`
- **보류 해제**: 08-01 세션분 전체(`sap-calculator`, `pell-*`, `student-income-protection`, `financial-aid-calculator`, `12-vs-15-credits`, `does-withdrawing`, `how-to-appeal-a-sap-suspension`, `what-gpa-to-keep-scholarship`, `student-loan-repayment-plans-2026`, **`does-retaking-a-class-replace-your-gpa`**), `loan-repayment-calculator`, `how-many-as-to-raise-gpa`, `sat-score-calculator`, `final-exam-calculator`, `gpa-calculator`, `weighted-gpa-calculator` 등
  (이 중 4개는 이번 세션에 **상호링크만** 추가 — 보류 예외, lastmod 미갱신)

## 파일 현황 (08-17 기준)
- tools **41개** + index / blog 55개 + index / 루트 7개
- sitemap URL **102개**, tool-card 41개(미등록 도구 0), blog-card 53개
- 전체 106개 HTML 파일 JSON-LD 오류 0, 내부링크 broken 0

## 체크리스트 추가분 (v18 22~25번에 이어서)
26. **구글 GSC만으로 사이트 건강을 판단하지 말 것.** 08-17에 구글 노출 98% 하락 상태에서 Bing 순위는 평균 5위, CTR 2%, GA4 사용자는 오히려 증가(72→83)였다. 반드시 Bing Webmaster + GA4를 함께 볼 것.
27. **노출과 클릭을 분리해서 볼 것.** 노출 대폭 하락 + 클릭 유지 = 노출 집계 축소이지 품질 강등이 아니다. 이 경우 콘텐츠 개편으로 대응하지 말 것.
28. **새 계산기는 반드시 결과창 기본 표시(`result-box show`) + 전 입력에 `oninput` + 로드 시 1회 실행으로 만들 것.** 클릭 한 경로에만 의존하면 v18에서 겪은 "아무것도 안 보임" 사고가 재발한다. 검증은 실제 style.css 주입 후 `getComputedStyle(display)`를 로드/입력/클릭 3경로에서 확인.
29. **미색인 페이지를 만나면 먼저 "내부 중복"을 의심할 것.** nav로 100개 파일에서 링크되는데도 크롤링이 안 된다면 링크 부족이 아니라 중복 판정이다. 이때 **성과가 좋은 쪽은 절대 건드리지 말고 안 좋은 쪽만 차별화**할 것.
30. **색인 수동 제출(IndexNow, 구글 색인 생성 요청 등)은 하지 않는다.** 사용자 확정 방침. 위 "절대 하지 말 것" 섹션 참고. 자연 크롤링에 맡긴다.
31. **작업 보고 시 화면 확인용 링크는 "이번 세션에 시각적으로 변한 모든 페이지"를 빠짐없이 줄 것.** 신규 페이지만 주면 안 된다. 본문 섹션을 교체·추가한 기존 페이지, 카드가 추가된 index 페이지, 헤더/푸터 파셜을 건드려 전 페이지에 영향이 가는 경우까지 포함한다. 08-17에 신규 1개만 주고 본문이 교체된 `gpa-raise-calculator`와 카드가 추가된 `tools/index.html`을 누락한 사고가 있었다.

---

## [보존] 이전 문서 v18 본문 (2026-08-12 세션까지)

# GPA Vault 인수인계 문서 v18 (2026-08-12 세션 — 노출 폭락 원인규명 + 색인 병목 해소 확인 + 신규 확장 재개)

이전 v17 문서를 대체함. v17 이하 본문은 아래에 그대로 보존.

---

## 0-★★★★★★★★★★. 08-12 세션 — 이번 세션의 3대 결론 (다음 세션은 여기부터 읽을 것)

### 0단계 대조 결과
`git log` 최신 커밋 `0b336b6`(08-08, handover 갱신)과 v17 마지막 기록이 정확히 일치 — 소급 기록 불필요. 07-25 사고 재발 없음.

### ★★★ 결론 1: 노출 98% 폭락은 우리 사이트 문제가 아니다 (전략 변경 금지)

일별 노출: 08-03 266 → **08-04 53 → 08-05 9 → 08-06 20 → 08-07 5 → 08-08 5 → 08-09 3**.
v17에서 "GSC 지연일 가능성 높음, 단정하지 말 것"으로 보류했던 건인데, **지연이 아니라 실제 하락으로 확정**됐다(추가 며칠 데이터가 전부 한 자릿수로 확정됨).

**웹 조사 결과 원인은 외부 요인으로 판단:**
- 2026-08-01~03에 Semrush Sensor, Mozcast, Sistrix, AccuRanker, Algoroo 등 **주요 변동성 추적기가 일제히 스파이크**. 업계 전반에서 급격한 트래픽 손실 보고.
- 구글은 **공식 업데이트를 확정하지 않았고**, Search Status Dashboard에도 8/1~8/6 사이 랭킹/색인/크롤링/서빙 장애 기록 없음. 마지막 확정 업데이트는 2026-06 스팸 업데이트.
- 한 분석에서 **"노출 44% 감소 vs 클릭 11% 감소"** 패턴 보고 — 순위 강등이 아니라 측정/집계 효과라는 신호.

**우리 데이터도 같은 모양이다**: 평균 순위는 40~70대 유지, 클릭은 오히려 08-04에 1건 발생. 순위가 죽은 게 아니라 노출 집계가 죽었다.

**기술 점검 결과 사이트 이상 없음**: noindex 오삽입 없음(의도된 2건 = 404 스텁, privacy-policy만), canonical 누락은 privacy-policy 1건뿐(정상), robots.txt/sitemap 정상, GA4 활성 사용자 72명으로 안정적(직전 76에서 소폭 감소, 붕괴 아님).

**→ 전략 변경하지 않았다.** 업계 공통 권고가 "확정 안 된 변동성에 대규모 개편으로 반응하는 것이 일시적 흔들림을 진짜 손실로 만드는 방법"이다. **다음 세션에서 반드시 할 일: 노출이 회복됐는지 확인.** 회복됐으면 외부 요인 확정, 2주 지나도 한 자릿수면 그때 사이트 차원 재진단.

### ★★★ 결론 2: 색인 병목이 사실상 해소됐다 → 신규 확장 재개 근거

사용자가 준 Coverage 드릴다운(발견됨 — 현재 색인이 생성되지 않음) 기준:
- **23건 → 2건** (2026-07-25부터 급감, 08-07까지 2 유지)
- 남은 2건: `methodology.html`, `tools/gpa-raise-calculator.html`

v17이 신규를 0건으로 묶은 근거는 "크롤링됨-미색인 0→11"이었는데, **이번 export에는 그 항목이 없어서 판단 불가**(사용자 지시: 색인은 준 자료로만 판단). 주어진 자료만 보면 색인 병목을 이유로 신규를 막을 근거가 없어서 **신규 확장 재개**로 판정했고 실제로 신규 1건 진행함.

**다음 세션 주의**: 가능하면 "크롤링됨 — 현재 색인이 생성되지 않음" 드릴다운도 같이 받을 것. 이 수치가 다시 늘고 있으면 v17의 판단(확장 중단 → 통합/강화 전환)이 여전히 유효하다.

### ★★★ 결론 3: 홈페이지 배지 9개가 전부 dofollow 외부링크였다 (수정 완료)

`index.html` 하단 디렉터리 배지 — newtool.site, foundrlist, fazier, findly.tools, twelve.tools, pitchwall, kittylaunch, sellwithboost, **boostdomainrating** — 9개 전부 `rel`에 nofollow가 없어 dofollow 상태였음. 배지 상호교환은 구글 링크 스팸 정책이 명시적으로 지목하는 패턴이고, 특히 boostdomainrating은 이름부터 DR 부양 목적이라 리스크가 크다.

**전부 `rel="nofollow sponsored"` 적용함.** 중요: **사용자의 디렉터리 등록 전략 자체는 전혀 건드리지 않았다.** 우리가 받는 인바운드 링크 가치와 GA4 referral 유입은 그대로이고, 우리가 밖으로 내보내는 추천 신호만 제거한 순수 방어 조치다. **앞으로 새 배지를 추가할 때도 반드시 `rel="nofollow sponsored"`를 붙일 것.**

노출 폭락과의 인과관계는 주장하지 않음 — 하락 시작(08-04)이 boostdomainrating 배지 추가(08-06)보다 앞선다.

---

## 08-12 세션 실제 작업 내역 (커밋 `5396b95`, push + Pages 빌드 `built` 확인 완료)

### 신규 1건: `tools/r2t4-calculator.html` (1,705단어)

중도 휴학 시 받은 연방 지원금을 얼마나 반환해야 하는지 계산하는 도구.

**후보 선정 과정 (3개 조사, 2개 기각)**
1. **GPA→퍼센트 전용 페이지** — gpatopercentage.com, convertgpa.com, num8ers, calcullatr, gpacalc.app, gdx.in, assignmentdude, ouruniversitypedia 등 **8곳+** → 기각. 대신 `gpa-scale.html` 보강으로 흡수(아래 참고).
2. **유학 학자금 대출** — SoFi, Credible, Earnest, Sallie Mae, LendEDU, College Finance, GoOverseas, internationalstudentloan 등 **8곳+**(대형 렌더 소유 사이트 다수) → 기각.
3. **R2T4** — 검색 결과가 **전부 개별 대학 .edu 페이지**(PCOM, 오리건대, Massasoit, St. Lawrence, TAMIU, 캐피털대 등) **+ 저품질 범용 계산기 1곳(calculatorshub.net)뿐** → **채택**. SAP·Pell 계산기가 통했던 것과 정확히 같은 공백 패턴.

**차별화 3가지 (경쟁 .edu 페이지들이 안 다루는 것)**
1. **3분할 표시** — 학교 반환분 / 본인 대출분 / 보조금 초과지급분. 대부분의 .edu 페이지는 "돈을 물어낼 수도 있습니다"에서 끝난다.
2. **등록금 환불이 클수록 학생이 더 손해** — 학교 반환분 상한이 `등록금 × 미이수율`이라, 등록금이 낮으면 학교 몫이 줄고 학생 몫이 커진다. 저학비 통학생이 비싼 사립 기숙사생보다 더 많이 물어내는 구조. 또한 등록금 환불과 R2T4는 별개 절차라 환불받아도 계산은 그대로 돌아간다.
3. **2026-07-01 규정 개정 반영** — 신규 규정 적용 기준이 처리일이 아니라 **최종 출석일(LDA)**이라 6/30 휴학은 7월에 처리돼도 구 규정 적용. R2T4 freeze date 폐지, **Full Refund Withdrawal Exemption**(관대한 환불정책 학교가 "미출석 처리"로 계산 자체를 건너뛸 수 있는 선택 조항) 신설.

**★ 규정 확정 과정 (다음에 R2T4 건드릴 때 반드시 참고)**
보조금(grant) 상환 상한 규정이 출처마다 표현이 달랐음:
- De Anza: "학생 몫 × 50%"
- GTCC / CUNY Hostos / WVNCC: "학생 몫 − 보조금 총액의 50%" (Title IV grant protection)

**연방 워크시트 방식인 후자로 확정.** 근거: GTCC 공개 실사례가 `$2,775 × 50% = $1,387.50`을 차감해 잔액 $6.25 → $50 미만이라 면제로 계산되며, 이 방식이어야 숫자가 맞아떨어짐. De Anza 쪽은 우연히 비슷한 값이 나오는 케이스의 단순화로 판단.
그 외 확정 사항: 60% 초과 시 100% 이수 / 5일 이상 예정 휴식은 분모·분자 양쪽에서 제외 / 반환 순서 = 무보조 Direct → 보조 Direct → PLUS → Pell → FSEOG(대출이 앞이라 학생 몫이 대출에 먼저 흡수됨) / 보조금 초과지급 $50 이하 면제 / 대출분은 약속어음 정상 조건대로 상환(즉시 청구 아님) / 보조금 초과지급은 약 45일 내 상환 또는 상환약정 없으면 전국 어느 학교에서도 연방지원 자격 상실.

**검증**: 파이썬으로 공식 구현 → **오리건대 공개 예시(75일 중 22일 = 29.3%, $1,074.43 / $2,592.57)와 PCOM 예시(미이수 70.8% × $17,822 = $12,618)에 대조 일치** 확인 → jsdom으로 6개 시나리오(기본/고액 등록금/보조금 초과지급 실제 발생/60% 경과/50달러 면제 경계/0 나눗셈 방어) 실행해 파이썬 기준값과 전부 일치. `node --check` 통과.

**체크리스트**: 신규 9개 항목 전부 적용 — 페이지/canonical/WebApplication+FAQPage(FAQ 7개, 본문·스키마 7:7)/header.html 드롭다운(Tuition & Loans)/noscript nav 98개 파일 일괄 스윕(중복 삽입 0)/tools/index.html 카드(40개, 중복 0)/sitemap.xml(101 URL)/llms.txt/상호링크 4곳.

### 보강 1: `tools/gpa-scale.html` (1,371 → 2,004단어)

08-10 보류 해제된 파일이고, v17이 "허브 재정의는 다음 세션으로 이월"로 남긴 대상. 사이트 **최대 노출(677회)인데 83위**.

**★ 발견: GPA→퍼센트 역방향 쿼리 클러스터가 사이트 커버리지 0건이었음.**
GSC에 `4.0 gpa to percentage`(5), `2.8 gpa to percentage`(5), `gpa in percentage`(6), `3.94 gpa to percentage`(18위), `4.5 gpa to percentage`(16위) 등 **56개 쿼리 / 노출 103회**가 쌓였는데, 사이트 전체에 GPA→퍼센트 방향을 다루는 곳이 한 군데도 없었음(percentage→GPA 방향만 존재). 대부분 68~93위라 구글이 gpa-scale.html로 억지 매칭시키던 상태.

**차별화**: 경쟁사 8곳이 전부 쓰는 `퍼센트 = GPA × 25` 공식을 실제로 검산했더니 **4.0에서만 맞고 그 아래는 전부 과소평가**. 3.0(B, 83~86%) → 75%(C), 2.0(C, 73~76%) → 50%(낙제), 0.7 → 17.5%. **최대 오차 42.5%p.** 11행 대조표로 제시하고 "letter grade를 다리로 삼아 범위를 읽으라"는 정확한 방법을 제시. 검산 근거를 우리 페이지 기존 환산표로 삼아 내부 정합성도 확보.
추가 헤지: 누적 GPA는 평균이라 애초에 단일 퍼센트로 역산 불가능하며, 기관이 퍼센트를 요구하면 registrar가 보유한 학교 자체 평균을 받는 게 우선이라는 점 명시.

**허브 재정의(카니발라이제이션 정리)**: 본문 상단과 FAQ에서 "이 페이지는 참조 차트, 실제 숫자 변환은 저쪽"이라고 두 converter(`percentage-to-gpa-converter`, `gpa-to-letter-grade-converter`)로 명시적 라우팅. Related에도 percentage converter 추가. FAQ 3개 신규(본문·스키마 9:9 일치). sitemap lastmod 08-12, llms.txt 갱신.

### 보강 2: `methodology.html`(617→1,016단어) + `editorial-policy.html`(367→718단어)

**★ 두 파일 모두 `<h1>`이 아예 없었고 JSON-LD도 0건이었음** — 사이트 전체에서 이 둘만 그런 상태였다. h1 추가 + AboutPage 스키마 추가.
`methodology.html`은 GSC 발견됨-미색인 2건 중 1건이고, 내부링크가 4개뿐이었음(얇은 분량 + 약한 내부링크 = 크롤링 우선순위 하락의 전형).

- **methodology**: "연방 지원금 자격 계산기" 섹션 신설 — SAP/Pell 2종/IPA/OBBBA 한도/R2T4 8종을 FSA Handbook·34 CFR 668 근거와 함께 설명(이 계산기군에 대한 방법론이 통째로 빠져 있었음). "수치 검증 절차" 섹션 신설(공개된 연방 워크드 예시와 대조하는 실제 관행 서술 — E-E-A-T). 내부링크 4 → 15개.
- **editorial-policy**: **"How we make money" 섹션 신설** — v17이 정한 "제휴 승인 전 `affiliate-disclosure.html` 금지" 원칙을 지키면서, **현재 제휴가 없다는 사실을 명시**하고 도입 시 공개·`sponsored` 마킹 원칙을 미리 명문화. 연방 대출을 사설로 리파이낸스하면 연방 보호가 영구 소멸된다는 경고를 광고주 사정으로 약화시키지 않는다는 원칙도 명문화(v17 "절대 하지 말 것" 항목의 문서화). "규정이 바뀌는 주제 처리 방식" 섹션 신설(SAVE→RAP 서술을 실제로 정정했던 이력을 근거로 사용).

**주의**: 이건 허위 표시가 아니다 — "제휴 수수료를 받습니다"가 아니라 "현재 제휴 없음 + 도입 시 이렇게 하겠다"는 서술이다. 실제 승인 후에는 v17 체크리스트대로 `affiliate-disclosure.html` 신설 + 이 문단 갱신이 필요하다.

### 검증
사이트 전체 105개 파일 JSON-LD 오류 0, sitemap.xml 101 URL 파싱/중복 0, tool-card 40개·blog-card 53개 중복 0, 내부링크 전수 스캔 broken 0(`/favicon.ico` 2건은 루트 절대경로 오탐, 파일 존재 확인), 수정 파일 전체 태그 밸런스 통과, R2T4 JS `node --check` + jsdom 6시나리오 통과.

### 이번 세션 오탐 기록 (다음 세션이 같은 착각 반복하지 말 것)
`tools/index.html` 카드 수를 셀 때 `class="tool-card"`로 정확히 매칭하면 **39개가 아니라 38개**로 나와 "gpa-calculator 카드 누락"으로 오판했었음. 실제로는 `gpa-calculator.html`이 `class="tool-card featured"`라 정규식에서 빠진 것. **카드 카운트 정규식은 `class="tool-card[^"]*"`로 쓸 것.** blog-card도 `<a class="blog-card" ... href=...` 순서라 href가 뒤에 온다 — 속성 순서를 가정한 정규식 쓰지 말 것.

---

## 08-12 기준 GSC / GA4 데이터 (지난 3개월 / GA4 07-14~08-10)

**Performance (지난 3개월)**
- 총 클릭 **8** / 총 노출 **5,613** / CTR 0.14% / 평균 순위 약 53 — v17(5,580)과 사실상 동일. **즉 최근 1주일이 노출을 거의 못 보탰다**(위 결론 1 참고).
- 기기별: 데스크톱 4,502노출/5클릭(58.6위), 모바일 1,099노출/3클릭(**17.21위**), 태블릿 12. **모바일 순위 우위 계속 유지** — 모바일 화면 깨짐은 계속 신경 쓸 것.
- 국가별: 미국 3,924노출/7클릭, 영국 136/1클릭. 인도 208, 캐나다 193, 베트남 182, 필리핀 101(Dean's Lister 항목과 연결), 한국 30(**5.83위** — 가장 좋은 순위).

**페이지별 (노출 상위)**
| 페이지 | 노출 | 클릭 | 순위 | 코멘트 |
|---|---|---|---|---|
| tools/gpa-scale.html | 677 | 0 | 83.07 | 이번 세션 보강함 |
| blog/how-many-as-to-raise-gpa.html | 591 | 4 | **17.31** | 여전히 사이트 최고 성과 |
| tools/ib-gpa-calculator.html | 548 | 0 | **40.00** | 08-08 총점표 보강 효과 아직 미반영 |
| blog/what-is-the-deans-list-gpa-requirement.html | 501 | 1 | 38.78 | 08-08 보강 효과 아직 미반영 |
| tools/gpa-to-letter-grade-converter.html | 438 | 0 | 79.87 | |
| tools/college-cost-calculator.html | 355 | 0 | 63.67 | 관망 유지 |
| tools/act-score-calculator.html | 296 | 0 | 71.49 | 관망 유지 |
| blog/how-to-raise-your-gpa-in-one-semester.html | 208 | 1 | **11.98** | 순위 최상위권 |
| tools/sat-score-calculator.html | 202 | 0 | 43.10 | |

**1페이지권에 근접한 쿼리(20위 이내) — 다음 세션 우선 후보**
`gpa to letter grade converter`(6위), `dean's lister vs latin honors` 계열(6~9.5위, 4~5개 변형), `2.34 gpa with 36 on act`(9위), `convert grades to letters`(9위), `ib diploma gpa calculator`/`ib weighted gpa calculator`(11위), `minimum gpa to graduate college`(11위), `is dean's list based on cumulative or by semester`(15위), `gwa for dean's list`(16위), `percentage to gpa calculator`(17위), `what gpa is needed for deans list`(17위).
→ **Dean's List 클러스터가 20위 이내 쿼리를 가장 많이 갖고 있다**(08-08 보강분이 아직 GSC에 반영 전이라 더 오를 여지 있음). 다만 해당 파일은 08-22까지 보류.

**GA4 (07-14~08-10, 4주)**
- 활성 사용자 **72**(직전 76), 신규 71, 이벤트 742, 평균 참여시간 51초
- 소스: direct 41 / **bing organic 11 / yahoo organic 9 / google organic 4** / copilot.com(AI) 2 / referral 4(foundrlist, kittylaunch, newtool.site, twelve.tools)
- **★ Bing(11)+Yahoo(9)=20명 vs Google(4명) — 격차가 v17(16 vs 5)보다 더 벌어졌다.** IndexNow 제출의 가치가 더 커졌다. **[무효 — 2026-08-17 확정: 색인 수동 제출 금지. 문서 최상단 "절대 하지 말 것" 참고.]**
- 조회수 2위가 여전히 `does-retaking-a-class-replace-your-gpa`(16조회/15명, 이탈률 26.7%) — GSC 노출은 거의 없는데 GA4 사용자는 많은 Bing/AI/direct 경유 페이지.
- 홈페이지 이탈률 67%(직전 73%에서 개선) — 여전히 사이트 내 최악 수준.

---

## ★★★ 08-12 세션 사후 수정 — 신규 계산기 결과창이 안 보이던 버그 (커밋 `7aa403a`)

사용자가 스크린샷으로 "값을 바꿔도 결과가 아무것도 안 나온다"고 리포트. 원인과 조치:

- **구조**: `assets/css/style.css`의 `.result-box`는 `display:none`이고 `.result-box.show`일 때만 `display:block`이 된다. 즉 계산기 결과창은 JS가 `show` 클래스를 붙여야만 화면에 나타난다.
- **문제**: `r2t4-calculator.html`이 이 노출을 **버튼 클릭 한 번에만 의존**하는 설계였다. 사용자 환경에서 그 한 경로가 작동하지 않으면 결과가 전혀 안 보인다.
- **조치**: 클릭 의존 구조 자체를 제거했다. (1) 결과창을 `class="result-box show"`로 기본 표시 (2) 입력 5개 전부에 `oninput="calculate()"` 부착해 값 변경 즉시 재계산 (3) 페이지 로드 시 `readyState` 확인 후 1회 실행 (4) 버튼의 `scrollIntoView`를 `try/catch` + `typeof` 가드로 감싸 스크롤 실패가 계산을 막지 못하게 함.
- **전수 점검 결과**: 계산기 40개 중 나머지 39개는 `classList.add('show')`(37개) 또는 `style.display='block'`(high-school-gpa-calculator) 방식으로 정상 처리되고 있음을 확인했다. **문제는 이번 신규 파일 1개뿐이었다.**

### ★ 검증 방식의 구멍 (이게 진짜 교훈, 반드시 반영할 것)
기존 jsdom 테스트는 `element.textContent`만 읽어서 **계산값이 맞는지만 확인하고, 그 결과가 실제로 화면에 보이는지는 전혀 검증하지 않았다.** 그래서 6개 시나리오를 "전부 통과"로 보고했는데도 사용자 화면엔 아무것도 안 떴다.

**앞으로 계산기를 만들거나 고칠 때는 jsdom 테스트에 반드시 다음을 포함할 것:**
1. 실제 `assets/css/style.css`를 `<style>`로 주입할 것 (링크만 걸면 jsdom이 CSS를 안 읽어서 display 판정이 무의미하다)
2. `window.getComputedStyle(box).display`가 `none` → `block`으로 바뀌는지 확인할 것
3. 세 경로를 각각 확인할 것: **페이지 로드 직후 / `input` 이벤트 dispatch / 버튼 `.click()`**
4. `pretendToBeVisual: true` 옵션을 줄 것

테스트 스크립트 패턴은 이 커밋의 작업 로그 참고. **"계산이 맞다"와 "사용자에게 보인다"는 별개의 검증 항목이다.**

---

## ★★★ 수익화 우선순위 정정 (08-12, v17 판단 수정)

v17이 "제휴는 트래픽 하한이 없으니 1순위"라고 판정했고 이번 세션도 그걸 그대로 반복해서 사용자에게 제휴 가입을 권했는데, **사용자가 "트래픽이 저것밖에 안 되는데 제휴가 되겠냐"고 지적했고 그 지적이 맞다.**

**정정된 판단:**
- "트래픽 하한이 없다"는 것과 "지금 수익이 난다"는 것은 완전히 다른 얘기다. 월 활성 사용자 72명, 검색 CTR 0.14%, 3개월 누적 클릭 8회 상태에서는 **제휴 전환 기대값도 사실상 0**이다. 리드당 $100짜리 제휴라도 리드가 0건이면 0원이다.
- 즉 지금 단계에서 **AdSense냐 제휴냐를 따지는 것 자체가 의미가 없다.** 둘 다 0원이고, 병목은 수익화 수단 선택이 아니라 트래픽이다.
- **따라서 매 세션 사용자에게 제휴 가입을 재촉하지 말 것.** W-8BEN 등 사용자 시간을 쓰게 만드는 액션인데 지금은 수익 기대값이 0이라 요구할 근거가 약하다.
- **재개 조건**: 월 세션 500 이상 또는 검색 클릭 월 50회 이상에 도달하면 그때 제휴 가입을 다시 제안할 것. 그 전까지는 콘텐츠·색인·순위에만 집중한다.
- v17의 "AdSense 재심사는 색인 60개+월 500세션까지 보류" 판정은 유지. 결과적으로 **수익화 관련 액션은 전부 트래픽 임계치 도달 시까지 동결**이 맞다.

---

## ★ 다음 세션이 반드시 확인/처리할 것 (우선순위순)

1. **IndexNow 제출 — 아직도 안 됨(2세션째 이월).** 샌드박스 egress에서 `api.indexnow.org` / `www.bing.com` / `yandex.com` 전부 **403 `host_not_allowed`**로 차단됨(이번 세션에도 재시도해서 확인). 키 파일은 정상 배포돼 있음. **v17 "Sonnet 실행 결과" 섹션의 curl 명령을 사용자 본인 터미널에서 1회 실행하면 끝.** Bing/Yahoo 유입이 Google의 5배인 지금, 그리고 Google 노출이 죽어 있는 지금 효과가 가장 크다. **[무효 — 2026-08-17 확정: 색인 수동 제출 금지. 문서 최상단 "절대 하지 말 것" 참고.]**
2. **노출 회복 여부 확인** — 08-10 이후 일별 노출이 두 자릿수 이상으로 돌아왔는지. 회복됐으면 외부 요인 확정이고 아무것도 안 해도 된다. 2주 지나도 한 자릿수면 그때 사이트 차원 재진단 착수.
3. **"크롤링됨 — 현재 색인이 생성되지 않음" 드릴다운 확보** — v17의 11건이 줄었는지 확인 필요. 이번 export엔 없었음.
4. **제휴 프로그램 가입 — 재촉하지 말 것(08-12 정정).** 위 "수익화 우선순위 정정" 섹션 참고. 월 세션 500 또는 월 검색 클릭 50에 도달하기 전까지는 제휴·광고 관련 액션을 사용자에게 요구하지 않는다. 승인 전 제휴 링크·`affiliate-disclosure.html` 생성 금지는 그대로 유효.
5. **AdSense 재심사 — 계속 보류.** v17 판정 기준("색인 60개 이상 + 월 세션 500 이상") 미달 상태 유지. 단, 이번 세션에 E-E-A-T 페이지 2개를 실질 보강했고 색인 병목도 풀린 정황이라, 다음 세션에 색인 수치를 보고 재판정할 가치는 있다.
6. **`tools/gpa-raise-calculator.html`** — 발견됨-미색인 2건 중 나머지 1건. 1,147단어이고 nav로 100개 파일에서 링크되는데도 크롤링이 안 됐다는 건 `blog/how-many-as-to-raise-gpa.html`(2,163단어, 사이트 최고 성과 페이지, 17위)과의 **중복 판정 가능성이 높다**. 이번 세션엔 시간상 미착수. 다음 세션에서 두 파일을 열어 역할 분담(도구 vs 설명)을 title/H1/본문 수준에서 명시적으로 갈라줄 것. **단 `how-many-as-to-raise-gpa.html` 쪽은 건드리지 말 것**(사이트 최고 성과 페이지, 리스크 대비 이득 없음) — 도구 쪽만 손볼 것.

## 2주 재작업 보류 현황 (08-12 기준)
- **08-15까지 보류**: 08-01 세션 신규/편집분 — `tools/sap-calculator.html`, `tools/pell-*`(2개), `tools/student-income-protection-calculator.html`, `tools/financial-aid-calculator.html`, `blog/12-vs-15-credits-financial-aid-trap.html`, `blog/does-withdrawing-a-class-affect-financial-aid.html`, `blog/how-to-appeal-a-sap-suspension.html`, `blog/what-gpa-to-keep-scholarship.html`, `blog/student-loan-repayment-plans-2026.html`, `blog/does-retaking-a-class-replace-your-gpa.html`
  (이 중 4개는 이번 세션에 **상호링크만** 추가했으므로 보류 예외 적용, lastmod·dateModified 미갱신 — 원래 시한 유지)
- **08-22까지 보류**: 08-08 세션 편집분 — `tools/ib-gpa-calculator.html`, `tools/percentage-to-gpa-converter.html`, `tools/gpa-to-letter-grade-converter.html`, `blog/what-is-the-deans-list-gpa-requirement.html`
- **08-26까지 보류**: 이번 세션(08-12) 편집분 — `tools/r2t4-calculator.html`, `tools/gpa-scale.html`, `methodology.html`, `editorial-policy.html`
- **보류 해제(작업 가능)**: `tools/loan-repayment-calculator.html`(07-27), `blog/how-many-as-to-raise-gpa.html`, `tools/gpa-raise-calculator.html`, `tools/sat-score-calculator.html`, `tools/final-exam-calculator.html`, `blog/what-gpa-do-you-need-for-nursing-school.html`, `tools/sat-percentile-calculator.html`, `tools/gpa-calculator.html`, `tools/weighted-gpa-calculator.html`

## 파일 현황 (08-12 기준)
- tools: **40개** + index (`r2t4-calculator.html`이 최신 신규, 08-12)
- blog: 55개 + index
- 루트: about, methodology, editorial-policy, privacy-policy, contact, glossary, index
- 전체 sitemap URL: **101개**
- 카드: tool-card 40개, blog-card 53개 (blog 파일 55개 중 2개는 카드 없음 — 404 스텁 `how-to-raise-your-gpa.html`, index)

## 체크리스트 추가분 (v17 15~21번에 이어서)
22. **새 디렉터리 배지를 `index.html`에 추가할 때는 반드시 `rel="nofollow sponsored"`를 붙일 것.** 08-12에 기존 9개를 일괄 수정했다. dofollow로 두면 링크 스팸 정책 리스크가 생긴다.
23. **확정되지 않은 구글 변동성에 대규모 개편으로 반응하지 말 것.** 08-12에 노출이 98% 빠졌지만 업계 전반 현상이었고 순위·GA4는 멀쩡했다. 노출과 클릭·순위를 분리해서 볼 것 — 노출만 빠지고 순위가 유지되면 집계 이슈일 가능성이 높다. **먼저 변동성 추적기와 Search Status Dashboard를 웹 검색으로 확인한 뒤 판단할 것.**
24. **카드 카운트 정규식은 `class="tool-card[^"]*"`**(featured 변형 존재). blog-card는 `class`가 `href`보다 앞에 온다 — 속성 순서 가정 금지.
25. **h1/스키마 누락 전수 스캔을 주기적으로 돌릴 것.** 08-12에 `methodology.html`·`editorial-policy.html` 둘 다 h1도 JSON-LD도 없는 상태로 오래 방치돼 있었다. FAQPage 스키마 스캔은 하고 있었지만 h1 존재 여부는 아무도 안 보고 있었다.


---

## [보존] 이전 문서 v17 본문 (2026-08-08 세션까지)

# GPA Vault 인수인계 문서 v17 (2026-08-07 Opus 분석 세션 — 수익화 방침 확정 + 정체 원인 진단)

이전 v16 문서를 대체함. v16 이하 본문은 아래에 그대로 보존. 이 세션은 **Opus가 분석·기획만 담당하고 실제 파일 작업은 Sonnet이 수행하는 분업 세션**이라, 맨 위 섹션은 "Sonnet에게 넘긴 작업 지시"와 "사용자가 새로 확정한 수익화 방침" 두 가지가 핵심.

---

## 0-★★★★★★★★★. 08-07 세션 (Opus 분석) — 수익화 방침 전환 + "크롤링됨-미색인 11건" 신규 경고 신호

### 0단계 대조 결과
`git log` 최신 커밋은 `1fffc3f`(2026-08-06, "Update index.html"). v16 마지막 기록은 `6a751db`(08-01)까지였으므로 **1건 미기록 발견**. 확인 결과 사용자가 직접 커밋한 것으로, `index.html` 하단 배지 영역에 `boostdomainrating.com` 백링크 배지 `<a>` 3줄 추가한 것이 전부(콘텐츠 변경 없음). 소급 섹션을 따로 만들 필요는 없다고 판단하고 여기 언급으로 갈음. **참고: 사용자가 백링크 디렉터리(sellwithboost, boostdomainrating, foundrlist, twelve.tools, newtool.site 등)에 직접 등록을 진행 중임 — GA4 referral 유입이 실제로 잡히고 있음.**

### ★★★ 사용자가 이번 세션에 새로 확정한 수익화 방침 (이후 모든 세션에 적용, 절대 잊지 말 것)

> **"우린 구글 애드센스에 의존하지 않는다. 다양한 제휴 광고 수익화가 되는 거면 다 할 거고, Opus가 판단해서 애드센스는 게시 탈락 시 재심사를 판단하고 다른 제휴나 광고사도 마찬가지다. 애드센스보다 다른 제휴나 광고하는 것이 이득일 시에는 해당 방향으로 나에게 추천할 것."**

해석 및 운영 원칙:
1. **AdSense는 여러 수익원 중 하나일 뿐이며 우선순위 1번이 아니다.** 지금까지 세션들이 "AdSense 재심사 통과"를 암묵적 최종 목표로 삼아 저분량 페이지 보강 등을 진행해온 관성이 있는데, 이 전제는 폐기됨.
2. **재심사 여부는 Opus가 판단한다.** 사용자에게 "재심사 제출했냐"고 매 세션 물어보는 체크리스트 항목은 폐기. 대신 데이터를 보고 "지금 재심사를 넣는 게 맞는지"를 Opus가 판정해서 보고할 것.
3. **다른 제휴/광고사도 동일하게 Opus가 판정한다.** 승인 가능성, 트래픽 요건, 우리 콘텐츠와의 적합성, 예상 수익을 근거로 판단.
4. **AdSense보다 유리한 대안이 있으면 그쪽을 능동적으로 추천할 것.** 사용자가 먼저 물어보길 기다리지 말 것.

### ★★★ 08-07 Opus 판정: AdSense 재심사는 지금 넣지 말 것 (근거 포함)

**판정: 보류. 최소 "색인된 페이지 60개 이상 + 월 세션 500 이상" 두 조건을 동시에 만족할 때까지 재심사 제출 금지.**

근거 3가지:
1. **Google 자체가 이미 콘텐츠 품질에 부정 신호를 냈다.** 이번 Coverage에서 "크롤링됨 — 현재 색인이 생성되지 않음"이 **0건 → 11건**으로 신규 발생(아래 데이터 섹션 참고). 이건 Googlebot이 페이지를 실제로 읽고 나서 "색인할 가치 없음"으로 판단했다는 뜻이며, AdSense 반려 사유였던 "가치 없는 콘텐츠"와 정확히 같은 판단축이다. 이 상태에서 재심사를 넣는 건 같은 사유로 재반려당할 확률이 높고, 반복 반려는 계정 이력에 불리하게 쌓인다.
2. **통과해도 지금 트래픽에선 수익이 사실상 0원이다.** GA4 4주 기준 활성 사용자 76명. 교육/금융 니치 RPM을 넉넉히 $15로 잡아도 월 $1~2 수준. 재심사 준비에 드는 세션 시간의 기회비용이 훨씬 크다.
3. **AdSense는 다른 수익원의 전제조건이 아니다.** Mediavine 본진이 "AdSense 정책 위반 이력 없을 것"을 요구하긴 하지만 이는 *승인*이 아니라 *정책 준수*를 뜻하며, Journey/Ezoic/제휴는 AdSense와 무관하게 진행 가능하다. 즉 AdSense를 기다리느라 다른 수익화를 늦출 이유가 전혀 없다.

### ★★★ 08-07 Opus 추천: 수익화 우선순위 (AdSense보다 유리한 대안이 실제로 존재함)

**결론: 지금 단계에서 압도적 1순위는 "제휴(affiliate)"이고, 디스플레이 광고(AdSense 포함)는 전부 후순위다.**

이유의 핵심은 **제휴만 트래픽 하한선이 없다**는 점이다. 디스플레이 광고 수익은 트래픽에 정비례하므로 월 76명에선 어떤 네트워크를 붙여도 0원에 수렴한다. 반면 제휴는 건당 정액이라 **전환 1건만 발생해도 현재 AdSense 1년치를 넘는다.** 게다가 우리 사이트의 대출/학비 계산기 페이지는 "학자금 대출 상환액을 계산하고 있는 사람" = 미국 금융 제휴 중 단가가 가장 높은 오디언스와 정확히 일치한다.

웹 검색으로 확인한 2026년 8월 기준 사실관계(다중 소스 교차확인):

| 수익원 | 트래픽 요건 | 예상 단가 | 판정 |
|---|---|---|---|
| **제휴 — 학자금 대출/리파이낸스** (SoFi, Credible, College Ave, Earnest 등) | **없음** | SoFi 기준 리드당 $100~150 보고됨. Credible은 웹사이트 URL만으로 신청 가능 | **1순위, 즉시 착수** |
| **제휴 — 장학금 플랫폼** (Bold.org, Going Merry, Scholarships.com 등) | 없음 | CPL(가입당) 소액이나 전환율 높음 | 2순위 |
| **제휴 — 시험대비/교재** (Princeton Review, Magoosh, Amazon Associates 등) | 없음 | 5~20% 커미션, 단가 낮음 | 3순위, ACT/SAT 페이지 한정 |
| **Journey by Mediavine** | **월 1,000 세션** (2026-01-15부로 10,000→1,000으로 완화됨) | AdSense보다 높은 RPM | 트래픽 도달 시 AdSense 대신 이쪽 |
| **Ezoic** | 없음(2023년에 하한 폐지) | RPM $5~25 보고되나 편차 큼 | 비추천 — 사이트 속도/UX 저하 리스크가 계산기 사이트엔 치명적 |
| **Monumetric** | 월 10,000 PV + 셋업비 $99 | RPM $10~20 | 나중 후보 |
| **Mediavine 본진** | 연 광고수익 $5,000 (기준이 세션수→수익으로 변경됨) | 최상위권 | 한참 뒤 |
| **Raptive** | 월 100,000 PV | 최상위권 | 한참 뒤 |
| **AdSense** | 없음 | 최하위권 RPM | **보류 (위 판정 참고)** |

**즉 사용자 질문("애드센스보다 다른 게 이득이냐")에 대한 답은 명확히 "그렇다"** — 제휴가 지금 압도적으로 유리하고, 디스플레이 광고를 굳이 붙인다면 AdSense가 아니라 **월 1,000 세션 도달 시 Journey by Mediavine**이 정답이다. 현재 월 세션이 약 90건이므로 1,000 세션은 10배 성장이 필요하지만, 임프레션이 3개월새 1,517→5,580으로 3.7배 늘어난 추세를 보면 비현실적 목표는 아니다.

**다음 세션이 반드시 확인/처리해야 할 제휴 관련 실무 사항 (아직 아무것도 착수 안 됨):**
- **사용자 액션 필요**: 제휴 프로그램 가입은 계정·세금정보(W-8BEN)가 필요해서 Opus/Sonnet이 대신 못 함. 사용자에게 Impact.com / CJ / ShareASale / Awin / Amazon Associates 중 어디에 가입할지 안내하고 승인 여부를 받아와야 진행 가능. **가입 승인 전까지는 사이트에 제휴 링크를 넣지 말 것.**
- **승인 나기 전에 미리 만들면 안 되는 것**: `affiliate-disclosure.html`을 미리 만들어두는 건 금지. 실제 제휴 관계가 없는데 "제휴 수수료를 받습니다"라고 쓰면 허위 표시가 되고, 오히려 AdSense/신뢰도에 마이너스다. **첫 프로그램 승인 직후에 만들 것.**
- **승인 후 필수 체크리스트(그때 적용)**: (1) `affiliate-disclosure.html` 신설 + 전 페이지 footer 링크 (2) 제휴 링크 전부 `rel="sponsored nofollow"` (3) 링크가 들어간 페이지 상단에 짧은 고지문 (4) `editorial-policy.html`에 "How we make money" 섹션 추가 — 이건 E-E-A-T에도 플러스 (5) 광고 네트워크 붙일 때만 `ads.txt` 생성(현재 없음, 지금은 불필요).
- **절대 하지 말 것**: 대출 상환/학자금 페이지는 YMYL(돈·건강 직결) 영역이라, 제휴 수익 때문에 "리파이낸스하세요" 같은 편향된 권유를 본문에 섞으면 검색 순위와 신뢰도 양쪽에서 손해다. 기존의 중립적 서술(특히 "연방 대출을 사설로 리파이낸스하면 연방 보호가 영구 소멸된다"는 경고)은 제휴 도입 후에도 절대 약화시키지 말 것.

### GSC / GA4 데이터 분석 (GSC 지난 3개월 / GA4 07-10~08-06)

**Coverage — 이번 세션 최대 이슈**
- 리디렉션 3 (조사 안 함, 사용자 확인 사항 유지) / noindex 1 (정상, 404 스텁) / 404 1 (검증 시작됨)
- **발견됨 — 미색인: 21 → 23** (거의 정체)
- **크롤링됨 — 미색인: 0 → 11 (신규 발생, 이번 세션 최대 경고 신호)**
- 색인 추이(차트 기준, 커버리지는 약 2주 지연): 07-01에 32건 → 07-11에 **41건**으로 점프 후 07-24까지 41 유지. 미색인은 39.
- **해석**: 07-25 세션(신규 16개 이상)과 08-01 세션(신규 4개)에서 대량 확장한 페이지들이 이제 크롤링 큐에 진입했는데, Google이 그중 11개를 읽고 나서 색인하지 않기로 판단했다. "발견됨-미색인"(아직 안 읽음)과 달리 **"크롤링됨-미색인"은 품질/중복 판단이 개입된 상태**라 성격이 완전히 다르다. 즉 **지금 사이트의 병목은 "페이지가 부족한 것"이 아니라 "이미 만든 페이지의 절반이 색인되지 않는 것"이다.**
- **여기서 나오는 전략 전환**: 지난 3세션(07-25/08-01×2)의 공격적 신규 확장 기조는 이 시점에서 일단 멈추는 게 맞다. 페이지를 더 늘리면 미색인 더미만 커진다. **이번 세션은 "이미 순위가 잡힌 소수 페이지를 1페이지권으로 밀어올리는 통합·강화"에 집중**하고, 신규는 0건으로 간다. (다음 세션에서 크롤링됨-미색인 11건이 줄었는지 반드시 재확인할 것. 안 줄면 카니발라이제이션 정리가 더 필요하다는 뜻.)
- **GSC UI에서 사용자가 직접 확인해줘야 하는 것**: CSV export에는 URL 목록이 안 들어있음. "크롤링됨 — 현재 색인이 생성되지 않음" 11건이 **어떤 URL인지** GSC 화면에서 확인해서 다음 세션에 알려주면 진단 정확도가 크게 올라감.

**Performance (지난 3개월)**
- 총 클릭 **8** / 총 노출 **5,580** / CTR 0.14% / 평균 순위 약 53
- 07-27 세션 대비: 노출 1,517 → 5,580 (**3.7배**), 클릭 6 → 8. **노출은 확실히 성장 중, 클릭은 정체.** 원인은 명확: 대부분 쿼리가 40~95위라 클릭이 물리적으로 안 나옴.
- 일별 노출 추이: 07-24 123 → 07-31 **359**(최고) → 08-03 266 → 08-04 53 → 08-05 9. **08-04/05 급락은 GSC 데이터 지연(보통 2~3일)일 가능성이 높지만, 실제 하락일 수도 있으니 다음 export에서 반드시 재확인할 것.** 지금 단정하지 말 것.
- 기기별: 데스크톱 4,473노출/5클릭(순위 58.5), 모바일 1,095노출/3클릭(**순위 17.16**). **모바일 순위가 데스크톱보다 압도적으로 좋다** — 모바일 화면 깨짐은 수익에 직결되므로 계속 신경 쓸 것.
- 국가별: 미국 3,902노출/7클릭이 압도적. 그 외 인도 207, 캐나다 193, 베트남 182, **필리핀 100**(아래 Dean's List 항목과 연결됨).

**페이지별 (노출 상위, 순위 병기)**
| 페이지 | 노출 | 클릭 | 순위 | 코멘트 |
|---|---|---|---|---|
| tools/gpa-scale.html | 677 | 0 | 83.07 | 노출 1위인데 순위 최악 — 아래 카니발라이제이션 항목 참고 |
| blog/how-many-as-to-raise-gpa.html | 590 | 4 | **17.26** | 여전히 사이트 최고 성과 페이지 |
| tools/ib-gpa-calculator.html | 548 | 0 | **40.00** | **노출+순위 조합이 가장 좋은 미개척 페이지** |
| blog/what-is-the-deans-list-gpa-requirement.html | 499 | 1 | 38.77 | 롱테일 꼬리가 사이트에서 제일 긺 |
| tools/gpa-to-letter-grade-converter.html | 438 | 0 | 79.87 | 카니발라이제이션 의심 |
| tools/college-cost-calculator.html | 355 | 0 | 63.67 | 관망 유지 |
| tools/act-score-calculator.html | 294 | 0 | 71.50 | 관망 유지 |
| blog/how-to-raise-your-gpa-in-one-semester.html | 208 | 1 | **11.98** | 순위 최상위권 |
| tools/sat-score-calculator.html | 202 | 0 | 43.10 | |

**★ 새로 발견한 구조 문제: percentage↔GPA 숫자 변환 쿼리의 3중 카니발라이제이션**
"77 to gpa", "85 to gpa", "90 in gpa", "3.4 gpa to percentage" 류의 숫자 직접 변환 쿼리가 GSC 상위 1,000개 쿼리 중 **200개 이상**을 차지하는데(개별 노출은 1~5회씩이라 눈에 안 띄지만 합산하면 사이트 최대 클러스터), Google이 이 쿼리들에 대해 우리 페이지 3개를 뒤섞어 노출시키고 있고 셋 다 순위가 나쁘다:
- `tools/gpa-scale.html` 677노출 / 83위
- `tools/gpa-to-letter-grade-converter.html` 438노출 / 80위
- `tools/percentage-to-gpa-converter.html` 77노출 / 61위 ← **정작 이 쿼리 전용으로 만든 페이지가 노출이 제일 적다**
즉 07-18에 "기능 갭이 있다"며 만든 전용 페이지가 기존 두 페이지에 밀려 제 역할을 못 하고 있음. 세 페이지가 서로의 신호를 갉아먹는 전형적 패턴. **역할 분담을 title/H1/내부링크 수준에서 명시적으로 갈라줘야 함**(아래 Sonnet 지시 B 참고).

**GA4 (07-10~08-06, 4주)**
- 활성 사용자 **76**(직전 세션 67에서 소폭 증가), 신규 77, 이벤트 781, 평균 참여시간 48초
- 소스: direct 48 / **yahoo organic 9 / bing organic 7 / google organic 5** / copilot.com(AI 어시스턴트) 2 / referral 5(foundrlist, kittylaunch, newtool.site, twelve.tools)
- **★ 중요: Bing(7)+Yahoo(9)=16명 > Google(5명).** Google보다 Bing/Yahoo가 우리를 훨씬 잘 색인·노출하고 있다. Google 색인 병목이 풀릴 때까지 **Bing 쪽을 적극 공략하는 게 비용 대비 효율이 훨씬 좋다** → IndexNow 도입 권장(아래 지시 D). **[무효 — 2026-08-17 확정: 색인 수동 제출 금지. 문서 최상단 "절대 하지 말 것" 참고.]**
- copilot.com 경유 유입이 계속 잡힘 → `llms.txt` 유지 전략이 실제로 작동 중이라는 방증. 계속 갱신할 것.
- 페이지별 조회수 2위가 `does-retaking-a-class-replace-your-gpa`(16조회/**15명**, 이탈률 26.7%) — GSC 노출은 거의 없는데 GA4 사용자는 많다. Google 외 경로(Bing/AI/direct)로 들어오는 페이지. 이탈률도 사이트 평균보다 훨씬 좋음.
- 홈페이지 이탈률 73%로 사이트 내 최악 — 홈에서 툴로 넘어가는 동선이 약하다는 신호(당장 손대진 않되 기록해둠).

### 2주 재작업 보류 현황 (08-07 기준, `git log --follow --numstat`로 재계산)
**주의: 얕은 클론(`--depth`)으로 clone하면 파일 히스토리가 전부 "신규 생성"으로 보여서 보류 계산이 완전히 틀어진다. 이번 세션에 실제로 겪었음 — 반드시 `git fetch --unshallow` 또는 full clone 후 계산할 것.**

- **작업 가능(보류 해제됨)**: `tools/ib-gpa-calculator.html`(마지막 콘텐츠 편집 07-13), `blog/what-is-the-deans-list-gpa-requirement.html`(07-11), `tools/gpa-to-letter-grade-converter.html`(07-02), `tools/percentage-to-gpa-converter.html`(07-18), `blog/how-many-as-to-raise-gpa.html`(07-13), `tools/sat-score-calculator.html`(07-20), `tools/final-exam-calculator.html`(07-02), `blog/what-gpa-do-you-need-for-nursing-school.html`(07-16), `tools/sat-percentile-calculator.html`(07-06)
- **08-10까지 보류**: `tools/gpa-scale.html`, `tools/loan-repayment-calculator.html` (둘 다 07-27 편집)
- **08-15까지 보류**: 08-01 세션 신규/편집분 전부 — `tools/sap-calculator.html`, `tools/pell-*`(3개), `tools/student-income-protection-calculator.html`, `tools/financial-aid-calculator.html`, `blog/12-vs-15-credits-financial-aid-trap.html`, `blog/does-withdrawing-a-class-affect-financial-aid.html`, `blog/how-to-appeal-a-sap-suspension.html`, `blog/what-gpa-to-keep-scholarship.html`, `blog/student-loan-repayment-plans-2026.html`, `blog/does-retaking-a-class-replace-your-gpa.html`

### 신규 콘텐츠 후보 검토 — 이번 세션은 **신규 0건**으로 결정 (근거 명시)
사용자가 과거에 "보강만 하지 말라"고 여러 번 지적했던 걸 알고 있으나, **이번엔 신규를 안 하는 게 맞다고 판단한 명확한 새 근거가 있음**: 위의 "크롤링됨-미색인 11건". 페이지를 더 만들면 색인 안 되는 더미가 커질 뿐이다. 그래도 형식적으로 넘기지 않고 웹 검색으로 후보 3건을 실제로 조사했고, 전부 경쟁 포화로 기각됨:
1. **IB 총점(24~45) → GPA 전용 페이지** — smartcgpa(2페이지), gradecalculatortools(2페이지), num8ers, lanterna, ishcmc, profcurious, knowledgeumacademy 등 **7곳+ 확인** → 기각. 단, **우리 `ib-gpa-calculator.html`이 이미 40위에 있으므로 신규 페이지 대신 그 페이지 보강으로 흡수**하는 게 정답(지시 A).
2. **PSLF 고용주 자격 판정 도구** — studentloansherpa, tateesq(2페이지), medschooldebtcalculator, usfinancecalculators 등 **5곳+**, 게다가 연방 공식 "PSLF Employer Search Tool"이 SERP를 장악 → 기각. 공식 정부 도구가 있는 주제는 앞으로도 후보에서 제외할 것.
3. **SSAT 퍼센타일 계산기** — GSC에 "ssat percentile calculator"(9), "ssat score calculator"(6) 노출이 잡히긴 하나 합산 15회로 작고, SSAT는 중학교 입시라 우리 핵심 독자(대학생/고등학생)와 오디언스가 다르며 제휴 수익성도 낮음 → 기각(과거 세션들의 보류 결정 유지).

---

## Sonnet에게 넘긴 작업 지시 (08-07, 4건 — 실행 결과는 Sonnet이 이 아래에 append할 것)

전부 **보강/기술 작업이며 신규 페이지는 0건**. 우선순위순.

- **A. `tools/ib-gpa-calculator.html` — IB 총점(24~45) 쿼리 흡수** (최우선). 548노출/40위로 노출·순위 조합이 사이트 최고인데 클릭 0. 현재 변환표가 **과목별 점수(1~7)만** 다루고 **디플로마 총점(24~45)은 FAQ 1개로 "총점 말고 과목별로 계산하세요"라고 회피**하고 있음. 그런데 GSC 쿼리는 "38 ib score to gpa", "40 ib score to gpa", "34/35/36/37 ib score to gpa", "ib diploma score to gpa", "ibdp score to gpa", "ib points to gpa" 등 **총점으로 묻는 쿼리가 다수**. 총점→GPA 근사 대응표 + FAQ 추가. **차별화 포인트(경쟁사 7곳이 안 하는 것): TOK/EE 보너스 3점 때문에 같은 42점이라도 과목점수 42인지 보너스 포함 42인지에 따라 GPA가 달라진다는 점을 표에 명시**하고, 총점 변환은 어디까지나 근사치이며 과목별 변환이 정식 방법이라는 헤지를 유지할 것.
- **B. percentage↔GPA 3중 카니발라이제이션 정리**. `percentage-to-gpa-converter.html`(숫자/타 스케일 → 4.0 변환 도구)와 `gpa-to-letter-grade-converter.html`(letter↔GPA 변환 도구)의 역할을 title/meta/H1/상호링크에서 명시적으로 분리하고, 서로를 "이 쿼리는 저쪽으로" 유도하도록 내부링크 문구를 정리. **`gpa-scale.html`은 08-10까지 보류 중이라 이번엔 손대지 말 것** — 허브 역할 재정의는 다음 세션으로 이월.
- **C. `blog/what-is-the-deans-list-gpa-requirement.html` — 롱테일 FAQ 보강**. 499노출/38.77위. 확인된 공백 3종: (1) **"cumulative vs semester" 정확 표현 쿼리**가 15~62위로 이미 가까움("is dean's list based on cumulative or by semester" 15위, "is dean's list by semester or cumulative" 20위, "do you get dean's list every semester" 41위) — 본문 H2엔 개념이 있으나 이 표현의 FAQ가 없음 (2) **"what percentage of students make the dean's list"**(64위) 커버 0 (3) **필리핀식 표현 "Dean's Lister" / "GWA"가 사이트 전체에 0건**인데 관련 쿼리 12회+ 잡히고 필리핀 국가별 노출이 100회. 광고 단가는 낮지만 경쟁이 사실상 없어 공짜로 먹는 순위. 추가로 "president's list gpa"/"chancellor's list gpa" 계열도 비교표에만 있고 FAQ가 없음.
- **D. IndexNow 도입 (기술)**. GA4상 **Bing(7)+Yahoo(9) 유입이 Google(5)보다 많음**. 정적 사이트라 루트에 키 파일 하나 올리면 끝이고, Google 색인 병목과 무관하게 Bing/Yahoo 색인 속도를 올릴 수 있음. 랜덤 hex 키 생성 → `/{key}.txt` 루트 배치 → Bing/IndexNow 엔드포인트로 sitemap URL 제출. **주의: 이 키 파일은 sitemap.xml에 넣지 말 것**(콘텐츠 페이지가 아님, 404 스텁을 sitemap에서 뺐던 것과 같은 논리). **[무효 — 2026-08-17 확정: 색인 수동 제출 금지. 문서 최상단 "절대 하지 말 것" 참고.]**

**보류(다음 세션 이후)**: `gpa-scale.html` 허브 재정의(08-10 이후), 제휴 링크·`affiliate-disclosure.html`(프로그램 승인 후), 홈페이지 이탈률 73% 개선.

---

## Sonnet 실행 결과 (08-08, 커밋 `ca08ede`)

A~D 전부 완료. 신규 페이지 0건(지시 준수). 커밋/푸시 완료, Pages 빌드 `built` + Actions `completed/success` 확인 완료(commit sha `ca08ede` 일치).

**A. `tools/ib-gpa-calculator.html`** — 총점(24~42) → GPA 표 19행 신규 추가. 표의 모든 값을 사이트 기존 과목별(1~7) 환산표와 수학적으로 일치하도록 선형보간 계산 후, 별도 파이썬 스크립트로 소스 공식과 19/19 전수 대조 검증(일치). TOK/EE 보너스 3점 때문에 동일 총점(예: 42)도 실제 GPA가 다를 수 있다는 설명을 highlight-box로 추가(예시: 6과목 만점+보너스0 vs 6과목평균6.5+보너스3, 둘 다 총점42지만 GPA 4.00 vs 3.85로 실제 0.15 차이) — 경쟁사 7곳 중 이 앵글을 다루는 곳 없음. 43~45점은 6과목만으로는 도달 불가능(최대 42)해서 항상 보너스 포함이라는 사실도 명시. FAQ 2개 개정(본문+JSON-LD 동기화 확인). **43~45점 구간은 조합이 너무 다양해 표에서 의도적으로 제외**하고 대신 "과목별 계산기 사용 권장" 문구로 헤지 — 다음 세션에서 이 구간 처리가 부족하다는 판단이 들면 재검토.

**B. `percentage-to-gpa-converter.html` ↔ `gpa-to-letter-grade-converter.html`** — 기존에 percentage→letter 단방향 링크만 있던 비대칭을 발견, 양방향으로 수정. letter 페이지는 "범위(range) 제공", percentage 페이지는 "정확한 숫자 변환" 프레이밍으로 meta description·본문 문구를 분리해서 역할을 명시적으로 갈랐음. `gpa-scale.html`은 지시대로 미터치.

**C. `blog/what-is-the-deans-list-gpa-requirement.html`** — 신규 H2 "Dean's Lister and GWA"(필리핀) 섹션 추가: GWA 1.75 기준(다수 소스 교차검증: gwacalculator.blog, gwacalculatr.com, gwacal.com 등 5곳+ 일치), GPA와 반대로 낮을수록 우수하다는 점, UP은 명칭이 다르다(University/College Scholar)는 예외까지 반영. FAQ 4개 신규(cumulative vs semester 정확 표현 매칭 / "몇 %가 받나" — BestColleges·Scholarships360·JobLoving 등 교차검증해 "10~25%"로 범위 표기, 특정 블로그 하나의 단정적 수치는 인용 안 함 / President's·Chancellor's List / Dean's Lister·GWA), 본문 FAQ와 JSON-LD 9/9 개수·내용 일치 확인. 1,216→1,771단어. blog/index.html cat-academics 최상단 재배치 완료(카드 53개, 중복 0).

**D. IndexNow** — 랜덤 hex 키(64자) 생성, `/{key}.txt` 루트에 배치해서 이번 커밋에 포함(sitemap.xml에는 미포함, 지시 준수). **단, 실제 IndexNow API로 URL을 제출하는 POST/GET 호출 자체는 이번 세션에서 실행하지 못함** — bash_tool 네트워크 egress 허용목록에 `api.indexnow.org`/`bing.com`이 없어서 시도 시 `403 host_not_allowed`(우리 쪽 egress 프록시가 막은 것, IndexNow 서버 응답 아님) 반환됨. web_fetch 툴도 "이전 검색/fetch 결과에 없는 URL은 못 연다"는 제약이 있어 우회 불가. 키 파일 자체는 이번 커밋으로 정상 배포됐고(Actions 성공 확인), **제출만 남은 상태**. **[무효 — 2026-08-17 확정: 색인 수동 제출 금지. 문서 최상단 "절대 하지 말 것" 참고.]**

**다음 사람(사용자 또는 향후 세션)이 해야 할 일 — 매우 간단, 5분 이내:**
```bash
curl -X POST https://api.indexnow.org/indexnow \
  -H "Content-Type: application/json; charset=utf-8" \
  -d '{
    "host": "gpavault.com",
    "key": "4ecbb2cc89f059e8138b521308eb76716c0ce520c587b424a65a5b2d171fd774",
    "keyLocation": "https://gpavault.com/4ecbb2cc89f059e8138b521308eb76716c0ce520c587b424a65a5b2d171fd774.txt",
    "urlList": ["https://gpavault.com/", "https://gpavault.com/tools/gpa-calculator.html", ... (sitemap.xml의 100개 URL 전체)]
  }'
```
사용자 본인 컴퓨터 터미널이나 이 저장소를 다루는 다음 세션(네트워크 제한 없는 환경)에서 위 curl 1회만 실행하면 끝남. urlList는 sitemap.xml에서 자동 추출 가능(`python3 -c "import re; print(re.findall(r'<loc>(.*?)</loc>', open('sitemap.xml').read()))"`). **다음 세션 필독**: 이 항목이 처리됐는지 먼저 확인하고, 안 됐으면 최우선으로 처리할 것 — 키 파일만 있고 제출을 안 하면 아무 효과가 없음.

**검증**: 사이트 전체 JSON-LD 재검증 통과(오류 0), sitemap.xml 100 URL 파싱 통과(중복 0), blog-card 53개/tool-card 39개 중복 0, 내부링크 전수 스캔 broken 0(템플릿 `{{BASE}}` 플레이스홀더는 정상 제외 처리), 수정 파일 전체 태그 밸런스(div/p/a/table/tr/td/th/h2/ul/li) 개별 확인 통과.

---

## [보존] 이전 문서 v16 본문 (2026-08-01 세션까지)

# GPA Vault 인수인계 문서 v16 (2026-08-01 세션 반영, "연방 지원금 자격 계산" 클러스터 신설)

이전 v15 문서를 대체함. v15(및 그 이전 버전들)의 배경 설명은 그대로 유효하므로 필요시 참고. 이 문서는 같은 날(08-01) 진행된 두 번째 대형 세션 — **"연방 지원금 자격 계산" 클러스터 신설(Pell 계산기 3개 + 블로그 1개)**을 맨 위에 정리하고, 이전 v15 본문은 아래에 그대로 보존. (참고: `41fa806` UI 버그 수정 커밋은 v15에 기록이 누락됐었음 — 사소한 1줄 CSS 수정이라 별도 소급 섹션 없이 이 자리에서 언급만 하고 넘어감.)

---

## 0-★★★★★★★★. 08-01 세션(2차) — "연방 지원금 자격 계산" 클러스터 신설: Pell 계산기 3개 + 블로그 1개

### 배경
직전 턴에서 "기획만 담당" 지시로 경쟁조사 후 실행 프롬프트만 산출했고, 이번 세션에서 그 프롬프트를 그대로 받아 실행함. 사용자가 "수량 정하지 말고 최대한 할 수 있는 부분까지 하라"고 지시해서 계획된 A-1~A-4 전부(여력 되면만 하려 했던 A-4까지) 완료함.

### 0단계 대조 결과
`git log` 최신 커밋(`41fa806`)과 handover.md v15 마지막 기록이 일치 — 소급 기록 불필요. 단, `41fa806`(sap-calculator.html % UI 버그 수정)이 v15 본문에 직접 언급은 안 돼 있었음(파일현황 숫자는 일치해서 실질적 문제는 없었음).

### 경쟁조사 근거 (직전 "기획" 턴에서 사전 확인, 이번 세션에서 재확인)
"Pell enrollment intensity", "Pell lifetime eligibility 600%" 검색 결과가 전부 개별 대학 .edu 페이지 + 연방 공식 핸드북(fsapartners.ed.gov)뿐이고 독립 계산기가 0개 — SAP 계산기와 정확히 같은 공백 패턴. IPA(소득보호공제)는 경쟁사들이 숫자를 서로 다르게 쓰고 있어($7,040/$7,600/$11,510 혼재) 정확한 현행 수치 확보 자체가 차별화 요소였음.

### 중복확인 결과
`grep -ril "enrollment intensity\|lifetime eligibility\|LEU\|income protection\|work-study\|full-time"`로 확인한 결과, "enrollment intensity"는 `pell-grant-changes-2026-27.html`에 FAQ 한 줄 스치듯 언급(공식 비례표나 계산기는 없음), "lifetime eligibility/LEU"는 사이트 전체 0건, "income protection allowance"는 `does-internship-affect-financial-aid.html`에 개념만 언급되고 정확한 금액은 없었음(오히려 이번 신규 계산기가 그 공백을 채움) — 셋 다 진짜 공백 확인, 신규 진행.

### 실제 작업

**1) 신규 툴: `tools/pell-enrollment-intensity-calculator.html`**
수강학점 → Pell 비례배분율 계산(학점÷전일제기준×100, 100% 상한). FSA Handbook Vol7 Ch3 공식 비례표(12=100%~1=8%)로 로직 검증 완료, node로 사전계산 + jsdom으로 시나리오 3개(9학점/12학점/18학점 초과) 실제 동작 검증. "학점 1개 추가 시 금액 차이"를 강조하는 게 핵심 차별화(9→10학점 = $295.80 차이). Pell만 이 방식을 쓰고 나머지 Title IV 프로그램은 구간제라는 비대칭을 본문 핵심으로 서술.

**2) 신규 툴: `tools/pell-lifetime-eligibility-calculator.html`**
600% LEU 잔여 계산(600−현재LEU, ÷100×연간지급액, ÷50=잔여 전일제학기수). FSA Handbook Vol7 Ch8 공식 예시(LEU 537.605% → 잔여 62.395%)로 실제 사례 대조 검증까지 완료. "SAP과 달리 LEU는 이의신청 불가"라는 대비를 SAP appeal 글과 상호링크로 연결.

**3) 신규 블로그: `blog/12-vs-15-credits-financial-aid-trap.html`**
"12학점의 함정" — 연방 전일제 기준(12학점)과 4년 졸업 필요 페이스(15학점)의 3학점 격차가 Pell 평생한도·SAP 150% 여유·졸업기간 세 가지에 동시에 영향을 준다는 문제해결형 글. **작성 중 자체 재검산으로 오류 발견 및 수정**: 초안에 "SAP 150% 한도 소진율 12학점 111% vs 15학점 89%"라는 구체 수치를 넣었으나, node로 재계산한 결과 무결점 시나리오에서는 양쪽 다 동일하게 66.7%로 나와 완전히 틀린 주장이었음 → "느린 페이스 자체가 아니라 느린 페이스+평균 완주율(NSC 데이터 75%)의 결합이 진짜 리스크"라는 정확한 설명으로 전면 수정. NSC 통계(28%가 1학년에 30학점 이상 이수, 9/12 완주율)는 Higher Ed Dive·EdSource의 원문 보도로 재검증 후 사용. **이번 세션에서 배운 점: 그럴듯해 보이는 구체적 수치를 만들 때는 반드시 실제 공식으로 재계산해서 검증할 것 — 문장이 자연스럽다고 숫자가 맞는 건 아니다.**

**4) 신규 툴: `tools/student-income-protection-calculator.html`** (계획상 "여력 되면"이었으나 완료)
학생 소득보호공제(IPA) $11,770(2026-27, 부양학생 본인소득 기준)와 초과분 50% 산입 로직. Federal Register 공식 고시, FSA Handbook 2026-27판, CollegeData, The Mather Group 등 4곳+ 교차검증. 근로장학금(work-study) 소득은 전액 별도 제외라는 점을 명확히 구분. **독립학생용 수치는 확인 안 해서 의도적으로 스코프에서 제외**하고 본문/FAQ에 명시적으로 헤지함(부양학생 본인소득 전용이라고 라벨링).

### 체크리스트 적용
- 신규 툴 3개 전부 9개 체크리스트: 본문/canonical/WebApplication+FAQPage 스키마/header.html 드롭다운(Tuition & Loans 섹션)/noscript nav 일괄 스윕(91→92→94개 파일, 매 단계 중복 삽입 0건 확인)/tools/index.html 카드(39개, 중복 0)/sitemap.xml/llms.txt/상호링크.
- 신규 블로그 1개도 동일 체크리스트(blog/index.html cat-loans 최상단 카드, 53개 중복 0).
- 상호링크 6곳: `sap-calculator.html`(신규 3건 링크 추가, 당일 작성분이라 hold 해당 없음), `pell-grant-changes-2026-27.html`(07-27 편집분, 보류 예외 적용·lastmod 미갱신), `financial-aid-calculator.html`(07-08 이후 보류 아니라 정상 편집+lastmod 갱신), `does-internship-affect-financial-aid.html`(07-25 편집분, 보류 예외 적용·lastmod 미갱신).

### 검증
사이트 전체(102개 파일) JSON-LD 재검증 통과(오류 0), sitemap.xml 100 URL 파싱/중복 통과, blog-card 53개/tool-card 39개 전부 중복 0, 내부링크 전수 스캔 broken 0, FAQPage 스키마 누락 재스캔 0건, 신규 파일 전체 태그 밸런스 통과, 계산기 3개 전부 node --check(JS 문법) + jsdom(실제 DOM 시뮬레이션 시나리오별) 이중 검증 통과.

### 다음 세션 백로그
1. **2주 재작업 보류(08-15까지)**: `tools/pell-enrollment-intensity-calculator.html`, `tools/pell-lifetime-eligibility-calculator.html`, `tools/student-income-protection-calculator.html`, `blog/12-vs-15-credits-financial-aid-trap.html`, `tools/sap-calculator.html`(이번에 링크 추가로 재편집), `tools/financial-aid-calculator.html`. `pell-grant-changes-2026-27.html`, `does-internship-affect-financial-aid.html`은 링크 추가만이라 원래 보류 시한 유지.
2. 계획에 있던 "장학금 displacement의 좁은 앵글"(어떤 지원금부터 깎이나 + 6개 주 금지법)은 미착수, 다음 세션 후보로 유효.
3. 새 Pell 계산기 3개+블로그 1개 관련 GSC 신호는 당연히 아직 없음(발행 당일) — 다음 세션에서 노출/색인 발생 여부 확인. SAP 클러스터(같은 날 오전 발행)도 아직 확인 안 됨, 같이 볼 것.
4. `student-income-protection-calculator.html`의 독립학생용 IPA 수치는 확인 안 하고 스코프 제외했음 — 필요시 다음 세션에서 studentaid.gov로 확인 후 독립학생 케이스 추가 고려.

---


## 0-★★★★★★★. 08-01 세션 — SAP(Satisfactory Academic Progress) 클러스터 신설

### 배경
이번 세션은 이전 턴(07-27 세션 직후)에서 별도로 "기획만 담당, 실행 금지" 요청으로 경쟁조사와 실행 프롬프트만 먼저 산출했고, 이번 세션에서 그 프롬프트를 그대로 받아 실행했다. 경쟁조사 결과: Latin honors/AMCAS BCPM/LSAC GPA/RAP 단독/class rank 계산기는 전부 전용 경쟁 사이트 4~10곳 이상 확인되어 재확인 없이 기각. 반면 "SAP calculator"·"67% completion rate" 검색 결과는 전부 개별 대학(.edu) 페이지뿐이고 전국 단위 독립 경쟁 사이트가 없어 최우선 채택.

### 0단계 대조 결과
`git log` 최신 커밋(`dab4005`, 07-27)과 handover.md v14 마지막 기록 세션이 정확히 일치 — 소급 기록 불필요했음(07-25 사고가 재발하지 않은 것 확인).

### 중복확인 결과 — 계획을 실행 중 일부 수정함
사전 계획에는 "SAP vs 학사경고 차이" 블로그(A-2)도 포함되어 있었으나, `grep -ril`로 확인한 결과 **`blog/academic-probation-vs-suspension-vs-dismissal.html`이 이미 본문+FAQ에서 "SAP는 등록사무처가 아닌 재정지원처가 관장하는 별도의 연방 요건"이라는 핵심 구분을 명확히 다루고 있어 A-2는 중복 판단, 스킵**하고 대신 그 구분 설명을 SAP 계산기 자체의 explainer/FAQ에 흡수시켰다. 마찬가지로 계획에 있던 "여력 되면" 항목인 **President's List vs Dean's List 비교(클러스터 B)도, `blog/what-is-the-deans-list-gpa-requirement.html`에 이미 President's List/Dean's List/Honor Roll/Chancellor's List 4단계 비교표가 존재함을 확인하고 착수하지 않음.** 이렇게 중복확인이 사전 웹 검색 경쟁조사만으로는 못 잡는 "우리 사이트 자체 중복"을 잡아낸 사례이니, 다음 세션도 계획 단계의 후보를 그대로 밀어붙이지 말고 실행 중에도 재확인할 것.

### 실제 작업 (커밋 1개로 완료)

**1) 신규 툴: `tools/sap-calculator.html`**
- 입력 6개(누적GPA/GPA요건/총 시도학점/총 이수학점/이수율요건%/학위 총 필요학점), 출력은 3개 기준(GPA·이수율·150% 최대기간)을 한 화면에 pass/fail로 동시 표시.
- 핵심 차별화: 이수율 미달 시 "67%(또는 커스텀 요건) 도달까지 추가로 통과해야 할 학점 수"를 역산 공식 `(target*attempted - earned)/(1-target)`으로 계산해 보여줌. node로 사전 검증(시도80/이수48/목표67% → 17학점 필요, 수기 계산과 일치) + jsdom으로 시나리오 3개(이수율 미달/전항목 통과/150% 초과) 실제 DOM 시뮬레이션 검증 완료.
- **버그 발견 및 수정**: 최초 작성 시 JS 문자열 내 어퍼스트로피 이스케이프를 `\\'`(백슬래시 2개)로 잘못 입력해 문자열이 조기 종료되는 문법 오류 2건 발생 — `node --check`로 즉시 발견해 `\'`로 수정. **다음 세션도 JS 문자열에 아포스트로피(you'd, that's 등)가 들어가면 `node --check`로 반드시 문법 검증할 것 — 육안으로는 안 보이는 종류의 버그였음.**
- FAQ 5개(본문+스키마): SAP 정의, 67%가 정확히 150% 규정의 수학적 하한이라는 점(임의의 숫자가 아님), 학사경고와의 차이, W/F가 이수율에 미치는 영향, 미달 시 절차.

**2) 신규 블로그: `blog/does-withdrawing-a-class-affect-financial-aid.html`**
- "W는 GPA에 영향 없다"는 통념에서 한 단계 더 들어가 "그래도 SAP 이수율(attempted 산입)에는 영향을 준다"는 점을 핵심으로. R2T4(Title IV 반환) 60% 규정도 다뤘고, **웹 검색으로 2026-07-01부로 R2T4 규정이 개정되었다는 최신 사실**(Full Refund Withdrawal Exemption 신설 등)까지 확인해 반영. 1,032단어, FAQ 5개.

**3) 신규 블로그: `blog/how-to-appeal-a-sap-suspension.html`**
- 승인/기각 사유를 표로 명확히 대비(의료·사망·재해 등은 승인, 바쁜 알바·일반적 재정난은 명시적으로 기각 대상이라는 점을 여러 대학 정책에서 교차검증). 이의신청 필수 3요소(무슨 일이 있었는지/무엇이 바뀌었는지/구체적 학업계획) + 승인 후 "financial aid probation" 처리 방식까지. 929단어, FAQ 5개.

### 체크리스트 적용
- 신규 툴 9개 체크리스트 전항목: 본문/canonical/WebApplication+FAQPage 스키마/header.html 드롭다운(Academics 섹션에 추가)/noscript nav 일괄 스윕(90개 파일, 중복 삽입 0건 확인)/tools/index.html 카드(36개, 중복 0)/sitemap.xml/llms.txt/상호링크.
- 신규 블로그 2건도 동일 체크리스트(헤더 드롭다운·noscript는 블로그 특성상 미해당) — blog/index.html cat-academics 최상단 카드(52개, 중복 0), sitemap, llms.txt, 상호링크.
- 상호링크 5곳: `academic-probation-vs-suspension-vs-dismissal.html`(SAP 계산기 링크 2곳, 07-25 편집분이라 보류 예외 적용·lastmod 미갱신), `fafsa-special-circumstances-appeal.html`(SAP appeal 글 링크, 동일하게 보류 예외·lastmod 미갱신), `what-gpa-to-keep-scholarship.html`(withdraw 글 링크, 이 파일은 마지막 실질 편집이 07-08이라 보류 대상 아니었으므로 정상 편집 + dateModified·sitemap lastmod 08-01로 갱신).

### 검증
- 사이트 전체(98개 파일) JSON-LD 재검증 통과(오류 0).
- sitemap.xml 96 URL(93→96), XML 파싱 통과, 중복 0.
- blog-card 52개/tool-card 36개 전부 중복 0.
- 내부링크 전수 스캔 broken 0.
- 신규/수정 파일 전체 태그 밸런스(div/p/table/tr/td/th/a/li) 개별 확인 통과.
- FAQPage 스키마 누락 재스캔 — 이번엔 0건(07-27 세션에 4건 다 고쳤던 게 유지되고 있음 확인).

### 다음 세션 백로그
1. **2주 재작업 보류(사용자가 예외 지시 안 하는 한 준수)**: `tools/sap-calculator.html`, `blog/does-withdrawing-a-class-affect-financial-aid.html`, `blog/how-to-appeal-a-sap-suspension.html`, `blog/what-gpa-to-keep-scholarship.html`, `blog/student-loan-repayment-plans-2026.html`, `blog/does-retaking-a-class-replace-your-gpa.html`은 08-15까지 보류. `academic-probation-vs-suspension-vs-dismissal.html`, `fafsa-special-circumstances-appeal.html`은 링크 추가만(보류 예외)이라 원래 보류 시한(08-08) 그대로 유지.
2. 새 SAP 계산기 관련 GSC 신호는 당연히 아직 없음(발행 당일) — 다음 세션에서 노출/색인 발생 여부 확인.
3. 사용자가 "토큰은 알아서 관리하니 언급 금지"라고 명시함 — **다음 세션부터 토큰 revoke 리마인드를 하지 말 것.** 이 지침은 이 저장소 작업 전반에 적용되는 사용자 선호로 간주.
4. 사용자가 "선점 효과 보려면 2주 보류 무시하고 진행"이라고 지시한 사례가 이번 세션에 있었음(클러스터 C/D) — **이건 일반 원칙 변경이 아니라 그 순간의 명시적 지시였음.** 다음 세션에서 별도 지시가 없으면 기본값(2주 보류 준수)으로 돌아갈 것. 사용자가 다시 "진행해"라고 하면 그때 예외 적용.

### 08-01 세션 연장 — "계속" 요청 후 클러스터 C/D 실행 (사용자가 2주 보류 원칙에 대해 예외 지시)
같은 세션에서 "계속" 요청을 받아 남은 백로그를 조사한 결과, 클러스터 D/C 둘 다 대상 파일이 2주 보류 중이라 일단 "다음 세션에 하자"고 보고했으나, **사용자가 "미리 선점 효과를 봐야 하니 진짜 아닌 것 아니면 진행해"라고 명시적으로 지시**해서 2주 보류를 무시하고 그대로 실행함. **이번처럼 사용자가 명시적으로 보류 예외를 지시하면 따를 것 — 단, 이런 지시가 없으면 기본값은 여전히 2주 보류 준수.**

- **클러스터 E (장학금 2~4년차 유지조건) — 스킵 확정**: `meritplaybook.com`이라는 전용 경쟁사(학교별 유지조건 페이지 프로그래매틱 수백 개 + 유료 커스텀 리포트 상품) 발견, "진짜 아니다 싶은 것"에 해당한다고 판단해 사용자 지시("진짜 아니다 싶은거 말고는 진행")에 따라 이번에도 스킵. 일반 설명 콘텐츠로는 재추천하지 않음. 착수하려면 이 경쟁사 대비 확실한 도구화 차별화부터 다시 고민할 것.

- **클러스터 D 실행 완료 — `blog/student-loan-repayment-plans-2026.html`에 FAQ 2개 보강**: 신규 페이지 대신 기존의 이미 두꺼운(2,257단어) 글에 흡수시킴(자기잠식 방지). 웹 검색으로 두 사실 모두 다중 소스 교차검증 완료(Yahoo Finance, tateesq.com, Credible, paychecktaxcalculator.net, SwitchWize, KU 공식 재정지원 페이지 등 6곳+): ① IBR은 Standard 10년 상환액이 상한이지만 RAP엔 그런 상한이 없어 고소득자는 RAP이 오히려 더 비쌀 수 있음 ② RAP→IBR로 전환하면 RAP에서 쌓은 납입 횟수가 IBR 탕감 카운트로 이월 안 됨(반대 방향인 IBR→RAP는 이월됨, PSLF는 플랜 무관하게 별도로 카운트). FAQ 본문+스키마 추가, dateModified/방문자 표시 날짜/sitemap lastmod 08-01로 갱신, llms.txt 설명 갱신.

- **클러스터 C 실행 완료 — `blog/does-retaking-a-class-replace-your-gpa.html`에 신규 섹션+FAQ 보강**: 기존에 있던 애매한 "대학원 지원에 영향 있나요?" 섹션을 AMCAS/LSAC/SAP 각각의 구체적 사실로 교체. 웹 검색으로 3개 시스템 각각 교차검증(AMCAS는 학교공식 페이지, LSAC는 Magoosh/test-ninjas/7sage, SAP는 Chaffey College/Minnesota State 시스템 정책/Fullerton College/PSU 등 다수 학교 SAP 정책 문서로 확인) — 셋 다 학교의 성적사면(academic renewal/grade replacement)을 인정하지 않고 원래 성적을 그대로 계산에 포함시킨다는 공통점, 단 SAP의 GPA 요소는 학교마다 약간의 재량 차이가 있을 수 있어 그 부분만 헤지 문구 추가(PSU 사례처럼 SAP GPA에서는 사면을 인정하는 학교도 있으나 이수율/최대기간 요소는 예외 없이 항상 포함됨). FAQ 본문+스키마 추가, `tools/sap-calculator.html` 상호링크 추가, dateModified/읽기시간/sitemap lastmod 08-01로 갱신, llms.txt 설명 갱신.

- **공통 교훈**: 계획 단계 경쟁조사(외부 웹 검색)만으로는 부족하고, 실행 직전 (1) 웹 검색 경쟁사 재확인 (2) 우리 사이트 기존 관련 파일을 직접 열어 이미 얼마나 다뤄져 있는지 확인, 이 두 가지를 다시 거쳐야 함. 계획 단계에서 "신규 페이지"로 분류했던 것도 실행 시점엔 "기존 페이지 보강"이 맞는 경우가 많았음(이번에 클러스터 C, D 둘 다 그랬음) — 기존 페이지가 이미 두꺼우면 신규 페이지보다 보강이 자기잠식 위험이 없고 효율적.

---


## ⚠️ 0-★★★★★★★. 07-27 세션 시작 전 발견: 07-25 세션이 handover.md에 전혀 기록되지 않았음 (매우 중요, 재발 방지 원칙)

07-27 세션 시작 시 이 문서(v13, 07-21 세션까지 기록)를 정독하고 `git log`로 실제 커밋 이력을 대조한 결과, **07-25에 커밋 10개(신규 페이지 16개 이상, 카테고리 2개 신설, 버그 수정 2건)가 이미 저장소에 반영되어 있었는데 handover.md 갱신이 통째로 누락**되어 있었음. 즉 직전 세션이 작업은 다 해놓고 문서화를 빠뜨린 것. 이 때문에 07-27 세션은 시작하자마자 `git log --pretty=format:"%h %ad %s"`로 실제 커밋을 전수 확인하고, 파일 목록(`ls tools/*.html blog/*.html`)으로 실제 페이지 수를 재파악하는 데 추가 시간을 써야 했음(문서상 21 tools/27 blog로 알고 있었으나 실제는 36 tools/52 blog였음).

**원인 추정**: 07-25 세션은 커밋 10개를 연달아 빠르게 진행하는 공격적 확장 세션이었고, 아마 세션 종료 시점에 handover.md 갱신 단계를 건너뛴 것으로 보임(또는 세션이 예기치 않게 끊겼을 가능성).

**재발 방지 원칙 (다음 세션에도 반드시 적용)**: 작업 내용이 아무리 많아도, **세션을 마무리하기 전 handover.md 갱신은 커밋/push 체크리스트의 필수 마지막 단계**이며 절대 생략 불가. 다음 세션은 시작하자마자 `git log`로 handover.md 최신 기록 시점과 실제 최신 커밋 시점이 일치하는지부터 대조 확인할 것 — 이번처럼 어긋나 있으면 그 차이를 먼저 소급 기록한 뒤에 새 작업을 시작해야 함.

07-25 세션 내용은 원 커밋 메시지를 근거로 아래 "0-A25" 섹션에 소급 재구성함.

---

## 0-★★★★★★. 07-27 세션 — Pell Grant 신규 블로그 + 보강 2건 + 전체 FAQPage 스키마 버그 스캔

### 배경
일요일 작업을 앞당겨 진행. 첨부된 GSC Performance/Coverage(2026-07-27 export) + GA4 개요(06-29~07-26) 분석 후, 웹 검색으로 경쟁 강도 확인하며 신규/보강 진행. 지시사항은 기존과 동일: 신규 착수 전 중복확인+경쟁조사, 롱테일 키워드 전략, AI검색 대응 문제해결/비교분석 콘텐츠 우선, 수익화 관점 우선순위, 대시보드 없이 텍스트 분석만.

### GSC/GA4 데이터 분석 결과
- **Coverage**: 리디렉션 3(조사 안 함) / noindex 1(정상) / 404 1(검증 중) / **발견됨-미색인 21**(수 주째 21로 정체 — 07-25 세션에서 sitemap이 66→92 URL로 급증했는데도 변화 없음. 07-25 신규 페이지 다수가 아직 Google 발견/색인 대기열에 진입조차 못한 것으로 추정. 다음 세션에서 계속 관찰 필요) / 크롤링됨-미색인 0.
- **Performance**: 3개월 누적 클릭 여전히 한 자릿수(전체 6회 — 데스크톱 3, 모바일 3), 노출은 1,517회 축적. 페이지별 1위는 `blog/how-many-as-to-raise-gpa.html`(419노출, 클릭 4, 순위 18.67 — 사이트 최고 성과 페이지). 쿼리 713개 중 클릭 발생 쿼리는 0건(개별 쿼리 노출은 전부 클릭 0으로 집계 — GSC 프라이버시 임계값으로 클릭이 발생한 구체 쿼리는 별도 비식별 처리된 것으로 추정, 페이지 리포트의 클릭 6건과는 별개 집계).
- **GA4(06-29~07-26)**: 활성 사용자 67명, 세션 대부분 direct(47명)/bing·google organic(각 4명)/copilot.com AI어시스턴트 경유(3명) — 오가닉 유입 여전히 미미.

### 2주 재작업 보류 현황 (07-25 세션이 워낙 방대해서 사이트 대부분이 보류 상태)
`git log --follow --numstat`로 각 파일의 "실제 콘텐츠 편집"(노스크립트 스윕/스키마버그수정/JS버그수정 제외) 최종 시점을 재계산한 결과, **07-25 세션에서 실제로 콘텐츠를 편집/신설한 파일 전부가 08-01~08-08까지 보류 대상**. 보류에 안 걸리는 고노출 페이지 위주로 이번 세션 대상 선정.

### 신규 후보 검토 (웹 검색 경쟁조사, 3개 후보 중 1개 채택)
1. **AP vs IB 비교 콘텐츠** — ivywise.com, medicalaid.org, bemoacademicconsulting.com, apscorehub.com, scoreatthetop.com, virtualcollegecounselors.com 등 **6개+ 경쟁사 즉시 확인** → 기각
2. **Class rank percentile calculator** — collegevine.com, meetyourclass.com, smartcgpa.com, classrankcalculator.com(페이지 3개), quadeducationgroup.com, gradecalculatortools.com, everydaybudd.com 등 **8개+ 경쟁사** → 기각 (과거 세션에서도 이미 보류 결정했던 항목, 이번에 경쟁조사로 재확인)
3. **Pell Grant 2026-27 변경사항(OBBBA)** — 사이트 자체 검색 결과 `how-does-financial-aid-work.html`, `study-abroad-financial-aid-guide.html`, `what-gpa-to-keep-scholarship.html`, `financial-aid-calculator.html` 4개 파일에 Pell Grant가 스치듯 언급만 될 뿐 전용 콘텐츠 없음 — 명확한 공백 확인. 웹 검색으로 SAI $14,790 컷오프("Pellionaire 루프홀" 폐쇄), 해외소득 AGI 재산입, 가족사업/농장 자산 FAFSA 제외(2건은 오히려 유리해짐), "15학점 요건" 루머가 실제로는 통과되지 않은 사실까지 다건 교차검증(NASFAA, Federal Student Aid 공식, Citizens Bank, ScholarshipsAndGrants.us 등) → **채택**. 참고로 Workforce Pell(단기 직업훈련 프로그램 대상 신규 Pell)은 workforcepellmatch.com 등 전용 사이트가 이미 있고 우리 사이트 핵심 독자층(학위과정 대학생)과도 결이 달라 이번엔 다루지 않음.

### 실제 작업

**1) 신규: `blog/pell-grant-changes-2026-27.html`** (1,079단어) — "Pell Grant Changes for 2026–27: Who Loses Eligibility Under OBBBA". 변경사항 비교표(SAI 컷오프/해외소득/가족사업자산/COA초과아너/학점요건) + 각 항목 상세 설명 + "15학점 루머는 사실이 아님" 정정 섹션 + FAQ 5개(FAQPage 스키마). 신규 페이지 체크리스트 적용: `blog/index.html` cat-loans 최상단 카드 추가(50개, 중복0), `sitemap.xml`(93 URL), `llms.txt`, 상호링크 1곳(`how-does-financial-aid-work.html` Related 섹션에 추가 — 이 파일은 07-08 이후 보류 아니어서 정상 편집, dateModified/sitemap lastmod 07-27 갱신).

**2) 보강: `tools/loan-repayment-calculator.html`** — GSC에서 "student loan repayment plan calculator"(10)/"income based student loan repayment calculator"(9)/"federal loan repayment calculator"(6)/"student loan income based repayment calculator"(6)/"calculate student loan repayment"(6) 등 **한 클러스터에 40+ 노출이 몰려있는데도 기존 본문엔 RAP/IDR 실제 계산 공식이 없었음**(기존 FAQ는 SAVE→RAP 연혁, Graduated 비교, Parent PLUS 정도만 다룸). 웹 검색으로 RAP 계산식 교차검증(SoFi, Edfinancial 공식 서비서, NerdWallet, fincalcapp.com, paychecktaxcalculator.net, repaysmarter.com 등 다수 일치) 후 AGI 구간별 요율표(1%~10%, $10,000 구간당 1%p, 부양가족당 -$50, 최저 $10/월) + 예시($50,000 AGI/부양가족1명 → $116.67/월) 신규 섹션 추가. **부수적으로 기존 서술의 사실 오류도 발견해 정정**: 기존 본문이 RAP을 "discretionary income 기반"이라고 잘못 설명하고 있었음(실제로는 AGI 전체 기반 구간제 — discretionary income 방식은 IBR 등 구세대 플랜의 특징) → 본문 수정. FAQ 1개 신규(본문+스키마). sitemap lastmod, llms.txt 갱신.

**3) 보강: `tools/gpa-scale.html`** — "percentage to gpa 5.0 scale"(7)/"gpa 5.0 scale"(4)/"gpa and percentage conversion"(4) 쿼리에 대응하는 FAQ가 없었음(기존 FAQ는 5.0 스케일 개념 설명뿐, 퍼센트→5.0 변환 방법은 없었음). "먼저 4.0 스케일로 변환 후, 실제로 가중과목(AP/IB/Honors)일 때만 보너스를 더하라"는 FAQ 신규 추가(본문+스키마) — 가중 여부 확인 없이 퍼센트를 곧장 5.0으로 환산하면 과대평가된다는 점을 명시. sitemap lastmod 갱신.

**4) 사이트 전체 FAQPage 스키마 버그 재스캔 (매 세션 반복 권장 원칙에 따라 실행) — 4건 발견 및 수정**
- `blog/what-is-a-good-act-score.html`, `tools/student-loan-calculator.html`, `tools/semester-gpa-calculator.html` — FAQ 텍스트는 있었으나 스키마 누락(신규 문항 추가 없이 스키마화만).
- `blog/federal-vs-private-student-loans.html` — **07-20 세션부터 "다음 세션 최우선 백로그"로 넘어오던 항목**(07-16 상호링크 편집으로 07-30까지 보류 대상이었으나, 스키마만 추가하는 순수 버그 수정은 애초에 보류 예외 대상이라 그대로 진행). 이 항목으로 백로그 완전 해소.

### 검증
- 사이트 전체(95개 파일) JSON-LD 문법 재검증(python json.loads) 통과 — 오류 0건.
- `sitemap.xml` 93 URL, XML 파싱 검증 통과, 중복 0건.
- `blog/index.html` 카드 50개, BeautifulSoup href 중복 검증 0건.
- 사이트 전체 내부링크(anchor 제외, 절대/상대경로 모두) 전수 스캔 — broken link 0건.
- 신규/수정 파일 전체 태그 밸런스(div/p/table/tr/td/th) 개별 카운트 검증 통과.

### 이번 세션에서 배운 점 (다음 세션 참고)
- **handover.md 갱신 누락은 다음 세션에 실질적 시간 손실을 유발한다** — 이번처럼 실제 파일 상태를 처음부터 재조사해야 했음. 세션 종료 전 마지막 체크리스트 항목으로 반드시 확인할 것.
- 07-25 세션처럼 한 세션에 커밋이 많아지면(10개), 사이트 대부분이 2주 보류에 걸려 다음 1~2세션은 보강 후보가 급격히 줄어드는 부작용이 있음 — 신규 확장 세션 다음에는 자연스럽게 "기술 점검/버그 스캔 위주" 세션이 되는 게 정상 패턴이라고 인식할 것(이번 세션이 그 예).
- Pell Grant처럼 사이트에 "스치듯 언급만 있고 전용 콘텐츠 없는" 주제는 `grep -ril`로 빠르게 스캔하면 신규 후보 발굴에 효율적 — 이번 세션에 사용한 방법, 다음에도 재사용할 것.

### 다음 세션 백로그
1. **07-25 세션 신규 페이지들이 아직 GSC Coverage/Performance에 전혀 안 잡힘** — 다음 세션에서 발견됨-미색인 21건이 줄었는지, 신규 페이지들이 노출 리스트에 등장하기 시작했는지 확인할 것
2. 07-25/07-27 세션에서 편집한 파일들은 각각 08-01~08-08까지 2주 재작업 보류 (세부 목록은 위 "2주 재작업 보류 현황" 참고, 다음 세션 시작 시 `git log --follow --numstat`로 재계산 권장)
3. `college-cost-calculator.html`, `act-score-calculator.html` — 계속 관망 유지 (원칙 변경 없음)
4. AdSense 재검토 결과 — 최근 세션들에서 언급 없음, 다음 세션에서 다시 물어볼 만함(급하지 않음)

---

## 0-A25★★★★★. 07-25 세션 (소급 기록 — 원 세션이 handover.md 갱신을 누락해서 07-27 세션이 git log 기반으로 재구성함)

**주의**: 아래 내용은 실시간 기록이 아니라 커밋 메시지(`2588ac2`, `9ab41d8`, `c71f626`, `3570f07`, `c78f35b`, `24cf122`, `e9320f2`, `3671eee`, `0792a21`, `c8fbba7`, 전부 2026-07-25)를 근거로 07-27 세션이 재구성한 요약임. 세부 경쟁조사 근거나 검증 로그 원본은 남아있지 않으므로, 특정 판단의 세부 맥락이 필요하면 커밋 메시지 원문(`git log --pretty=full 68ccb9b..c8fbba7`)을 직접 확인할 것.

### 신설된 카테고리 2개
- **Compare(비교) 카테고리** 신설 — `blog/index.html`에 "🆚 Comparisons" 섹션 최상단 배치. 이번 세션에 Compare 콘텐츠 3건 추가(academic-probation-vs-suspension-vs-dismissal, cosigner-release-requirements-compared, ai-academic-integrity-gpa-impact 등 포함).
- **Majors & Careers 카테고리** 정식 신설 (기존 "Career & ROI"에서 확장) — 신규 계산기 5종(major-switch-cost, minor-value, transfer-credit-loss, credit-overload, grad-school-application-cost) 추가.

### 신규 Tool 8개
`academic-probation-calculator`, `major-switch-cost-calculator`, `minor-value-calculator`, `transfer-credit-loss-calculator`, `credit-overload-calculator`, `grad-school-application-cost-calculator`, `obbba-loan-limit-calculator`, `study-abroad-cost-calculator`, `cosigner-release-calculator`, `internship-cost-calculator` (총 10개 — 위 8개는 대표 예시, 전체는 tools 디렉터리 참고)

### 신규 Blog 16개 (대표)
`academic-probation-vs-suspension-vs-dismissal`, `professional-degree-list-obbba`, `does-studying-abroad-affect-your-gpa`, `study-abroad-financial-aid-guide`, `study-abroad-gpa-requirements`, `cosigner-release-requirements-compared`, `ai-academic-integrity-gpa-impact`, `major-minor-combinations-real-examples`, `double-major-vs-minor-vs-switching-majors`, `transfer-vs-switch-major`, `parent-plus-old-vs-new-rules`, `internship-vs-study-abroad`, `does-internship-affect-financial-aid`, `fafsa-special-circumstances-appeal`, `fafsa-id-verification-2026`, `what-is-pslf`, `readmission-petition-after-dismissal`, `switch-majors-while-on-academic-probation` (18개, 정확한 목록은 `blog/` 디렉터리 참고)

### 사실관계 긴급 수정
`student-loan-repayment-plans-2026.html` — 기존 서술("SAVE는 예정대로 RAP로 대체")이 부정확했음을 발견해 정정: 실제로는 **2026-03-10 연방항소법원 판결로 SAVE가 강제종료(vacated)**된 것이며, 약 700만 명이 이자면제 관용유예로 전환되고 탕감 크레딧이 적립 안 되는 상태이며, 자동 이관이 아니라 본인이 studentaid.gov에서 직접 신청해야 한다는 점을 반영.

### 버그 수정
- 계산기 폼 라벨이 2줄로 줄바꿈될 때 입력창 정렬이 어긋나는 버그 — 9개 파일에 `align-items:end` 일괄 적용(major-switch-cost, minor-value, transfer-credit-loss, credit-overload, grad-school-application-cost, study-abroad-cost, academic-probation, obbba-loan-limit, interest-capitalization).
- `does-internship-affect-financial-aid.html` meta description 태그 오삽입, `what-is-pslf.html` FAQ 스키마 `@context` 오타, `professional-degree-list-obbba.html` meta description 오삽입 — 발견 즉시 수정.
- `blog/index.html` 카드 이동 작업 중 `str_replace`로 `cat-loans` 닫는 div가 실수로 삭제되는 사고 발생 → 즉시 발견 후 복구(이후 div/section 태그 밸런스 카운트 검증을 재검증 루틴에 추가한 것으로 보임).

### 저분량 페이지 보강 (애드센스 심사 대비)
`blog/internship-vs-study-abroad.html`(444→731단어), `blog/what-is-pslf.html`(465→730단어), `blog/fafsa-id-verification-2026.html`(491→707단어) 확장 + `blog/fafsa-special-circumstances-appeal.html` 1세대 학생 FAQ 1건 추가.

### 체크리스트/검증 (커밋 메시지 기준)
각 세션마다 헤더 드롭다운, noscript nav 일괄 스윕(파일 수는 62~81개로 세션 진행에 따라 누적 증가), `tools/index.html`/`blog/index.html` 카드 추가(중복 0건 검증), `sitemap.xml`(66→92 URL로 누적 증가), `llms.txt` 반영, 사이트 전체 JSON-LD 재검증(오류 0건) 완료된 것으로 커밋 메시지에 기록되어 있음.

### 07-25 세션 최종 커밋 해시
`3671eee` → `e9320f2` → `24cf122` → `c78f35b` → `3570f07` → `c71f626` → `6a7b87a` → `9ab41d8` → `0792a21` → `2588ac2` → `c8fbba7`(마지막)

---


## 0-★★★★★. 07-21 세션 — 사용자 버그 리포트: 과목 추가/삭제 계산기 번호매김+레이아웃 버그 5개 파일 수정

### 배경
사용자가 `tools/gpa-calculator.html` 스크린샷을 보내며 "Course 1, 3, 5"처럼 번호가 건너뛰고 삭제(×) 버튼이 행 사이에 어긋나 보인다고 리포트. 새 토큰(`github_pat_11AJ...OADUYAsRLKG1j`)으로 재클론해서 확인.

### 원인 분석
실제로는 별개의 2가지 버그였고, "과목을 추가/삭제하는" 동일 패턴을 쓰는 파일이 총 6개(`gpa-calculator`, `semester-gpa-calculator`, `ap-gpa-calculator`, `ib-gpa-calculator`, `weighted-gpa-calculator`, `high-school-gpa-calculator`) 있어서 **전체를 다 점검**함(1개만 고치고 끝내지 않은 것 — 이런 "동일 패턴 검색 후 일괄 점검"은 07-20 세션의 FAQPage 스키마 전수 스캔과 같은 접근 방식, 앞으로도 버그 리포트 받으면 습관화할 것):

1. **레이아웃 버그** (`gpa-calculator.html`, `semester-gpa-calculator.html` 2개만 해당): `grid-template-columns`가 3칸(`1fr auto auto`)으로 정의돼 있는데, 삭제 버튼이 조건부(`courseCount > 1`)로 4번째 자식으로 추가되면서 그리드가 다음 줄로 밀려 ×버튼이 행 사이에 뜬 것처럼 보임. 다른 4개 파일은 애초에 4칸 그리드였거나(`ap-gpa-calculator`, `ib-gpa-calculator`, `weighted-gpa-calculator` — 첫 행엔 빈 placeholder `<div></div>`를 넣어 항상 4칸을 채움) 애초에 번호 라벨이 없는 구조(`high-school-gpa-calculator`)라 이 버그가 없었음.
2. **번호 매김 버그** (`high-school-gpa-calculator.html` 제외 5개 전부): 과목 추가 시 쓰는 내부 증가 카운터(`courseCount`/`n`)를 화면 라벨("Course N")로 그대로 재사용 — 삭제 후에도 남은 과목 라벨이 재정렬되지 않고 원래 붙었던 번호가 그대로 남음.

### 수정 내용
- 라벨에 `course-label` 클래스 부여
- 과목 추가/삭제 시마다 `renumberCourses()` 함수를 호출해 현재 남아있는 라벨들을 순서대로 1,2,3...으로 재계산
- 레이아웃 버그가 있던 2개 파일은 `grid-template-columns`에 4번째 컬럼 추가
- `ib-gpa-calculator.html` 수정 중 `str_replace`로 인한 중복 닫는 중괄호(`}`) 오류 발생 → 즉시 재확인 후 수정(교훈: 함수 중간에 새 함수를 삽입하는 edit을 할 땐 기존 닫는 괄호까지 old_str에 포함시켜야 함, 안 그러면 중복 괄호로 문법 깨짐 — 이번엔 JS 문법 검증(node `new Function()`)으로 바로 걸러냄)

### 검증 방법 (이번에 새로 도입 — 다음에도 활용할 것)
JS 로직 버그는 육안 diff만으론 확신하기 어려워서 **jsdom을 설치해 실제 브라우저 동작을 시뮬레이션**함: 5개 파일 전부에 대해 "초기 3개 → 2개 추가(5-6개) → 임의로 2개 삭제" 시나리오를 재현해서 라벨이 정상적으로 1,2,3...으로 재정렬되는지, 그리드 자식 개수가 컬럼 수와 항상 맞는지 코드로 직접 확인 후 커밋함. (`npm install jsdom --no-save`로 설치, 재사용 가능)

### 체크리스트 및 검증
2주 재작업 보류 원칙은 이번엔 적용하지 않음 — **순수 JS 버그 수정(텍스트/SEO 콘텐츠 변경 없음)은 보류 대상이 아니라는 원칙을 이번에 새로 확립**(기존엔 noscript nav 스윕만 예외였는데, 여기에 "기능 버그 수정"도 예외로 추가). `semester-gpa-calculator.html`은 07-13 세션에 800단어 미만 보강으로 07-27까지 콘텐츠 보류 대상이었지만 이번 수정은 콘텐츠가 아니라 JS 로직이라 문제없이 진행.

사이트 전체 JSON-LD 재검증 통과(오류 0건). 커밋 `68ccb9b`, push 완료, Pages 빌드 `built` 확인 완료.

### 다음 세션 백로그 (추가)
9. 이번처럼 사용자가 스크린샷으로 버그를 리포트하면, **같은 UI 패턴을 쓰는 다른 파일들도 항상 같이 점검할 것**(이번엔 6개 중 5개가 실제로 버그 있었음 — 하나만 보고 끝냈으면 5개를 놓쳤을 것)

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
68ccb9b 버그 수정: 과목 추가/삭제 계산기 5개 파일의 번호 매김 + 레이아웃 버그 (사용자 스크린샷 리포트 대응, 07-21 세션)
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

## 14. 파일 현황 (08-01 세션 2차 기준 최신화)
- tools: 39개 + index (`pell-enrollment-intensity-calculator.html`, `pell-lifetime-eligibility-calculator.html`, `student-income-protection-calculator.html`이 가장 최근 신규, 08-01)
- blog: 54개 + index (`12-vs-15-credits-financial-aid-trap.html`이 가장 최근 신규, 08-01)
- 루트: about, methodology, editorial-policy, privacy-policy, contact, glossary, index
- 전체 sitemap URL: 100개
- 카테고리 구조: Tools(Academics/Tuition & Loans/Test Scores/Majors & Careers), Blog(🆚 Comparisons/GPA & Academics/Student Loans/College Costs/Test Scores/Majors & Careers), Glossary(단일 허브), About

## 15. 다음 세션 시작 전 체크리스트 (08-01 세션 2차 기준 최신화)
1. 이 문서(v16) 먼저 정독 — 실제 git log 최신 커밋과 이 문서의 마지막 기록 세션이 일치하는지부터 대조할 것 (어긋나 있으면 먼저 소급 기록)
2. 새 GSC Performance/Coverage export + GA4 export 받아서 직전 데이터와 비교 (특히 "발견됨-미색인 21건" 변동 여부, 07-25/08-01 신규 페이지들이 리포트에 등장하기 시작했는지)
3. 새 GitHub 토큰 발급받기
4. clone 후 `git config` 설정 잊지 말 것
5. 작업 시 **신규는 9개 파일 체크리스트, 보강은 4개 파일 체크리스트(본문/sitemap/blog-index/llms.txt) 누락 금지**
6. college-cost-calculator, act-score-calculator는 별도 지시 없으면 건드리지 않기
7. 리디렉션 이슈는 조사하지 않기 (사용자 확인됨)
8. **2주 재작업 보류 파일 확인**: `git log --follow --numstat`로 노스크립트 스윕/스키마버그수정/JS버그수정을 제외한 "실제 콘텐츠 편집" 최종일을 파일별로 재계산할 것. 08-01 세션(2차) 신규/편집분은 08-15까지 보류.
9. **연방 대출 금리는 매년 7월 1일 갱신됨을 기억할 것** — 다음 갱신은 2027-07-01이니 그 전까지는 6.52%/8.07%/9.07%가 맞는 숫자
10. 작업 완료 후 커밋/푸시 → Pages 빌드 `built` 확인까지 끝내고, **사용자가 직접 확인해야 할 URL을 클릭 가능한 링크로 정리해서 제시** (사용자는 영어를 몰라서 콘텐츠 검수가 아니라 화면이 깨졌는지만 육안 확인함 — 문구 검수 요청하지 말 것)
11. **세션 종료 전 이 문서(handover.md) 갱신은 필수 마지막 단계**
12. **토큰 관련: 사용자가 "토큰은 알아서 관리하니 앞으로 언급 금지"라고 명시적으로 요청함 — 이후 세션에서는 토큰 revoke를 리마인드하지 말 것.**
13. JS 문자열에 아포스트로피(you'd, that's, it's 등)가 들어간 경우 `node --check`로 문법 검증할 것 — 08-01 세션에 `\\'` 이중 이스케이프 오타로 문법 오류 2건 발생했었음 (육안으로는 안 보이는 버그)
14. 입력칸 옆에 단위(%, $)를 `<span>`으로 붙이지 말 것 — input이 width:100%라 다음 줄로 밀려서 그리드 행 높이가 어긋남. 단위는 라벨 텍스트에 "(%)" 식으로 넣을 것.
15. **본문에 구체적인 수치 주장(비교표의 %, 계산 결과 예시 등)을 넣을 때는 반드시 실제 공식으로 재계산해서 검증할 것.** 08-01 세션(2차)에서 "SAP 150% 소진율 12학점 111% vs 15학점 89%"라는 그럴듯한 수치를 초안에 넣었으나 node로 재계산한 결과 완전히 틀렸음을 발견해 전면 수정한 사례가 있었음 — 문장이 자연스럽게 읽힌다고 숫자가 맞는 게 아니다.
16. **CSS를 수정/추가하기 전에 style.css 전체(특히 `@media` 반응형 블록)를 먼저 훑어서 이미 비슷한 처리가 있는지 확인할 것.** 08-01 세션에 `.explainer table`에 표 스타일이 없는 걸 발견하고 급하게 `display:block; overflow-x:auto`를 새로 추가했는데, 알고 보니 사이트에는 이미 `@media(max-width:768px)` 안에 전역 `table{}` 반응형 규칙(`!important`로 인라인/후행 스타일까지 덮어쓰도록 설계됨)이 있었음 — 그걸 무시하고 데스크톱까지 적용되는 잘못된 스코프로 중복 규칙을 넣어서 두 번째로 고쳐야 했음. 사용자가 크게 화냈던 사례. **되는 대로 땜빵하지 말고, 기존 메커니즘부터 파악한 뒤에 거기 맞춰 최소 변경으로 고칠 것.**

17. **★ 수익화 방침(08-07 사용자 확정): AdSense에 의존하지 않는다.** 제휴/광고사 중 되는 건 전부 한다. AdSense 재심사 여부도, 다른 제휴/광고사 채택 여부도 **Opus가 데이터로 판단**한다(사용자에게 "재심사 하셨어요?"라고 매 세션 묻는 관성 폐기). AdSense보다 유리한 대안이 있으면 먼저 능동적으로 추천할 것. 08-07 판정 = **제휴 1순위(트래픽 하한 없음), 디스플레이는 월 1,000세션 도달 시 Journey by Mediavine, AdSense 재심사는 "색인 60개+월 500세션" 전까지 보류.** 상세 근거는 맨 위 v17 섹션 참고.
18. **제휴 프로그램 승인 전에는 사이트에 제휴 링크도, `affiliate-disclosure.html`도 만들지 말 것** — 실체 없는 고지문은 허위 표시다. 승인 후 체크리스트는 v17 섹션에 정리해둠.
19. **`git clone --depth`(얕은 클론) 금지.** 얕게 받으면 모든 파일 히스토리가 "신규 생성"으로 보여서 2주 재작업 보류 계산이 통째로 틀어진다(08-07 세션에 실제로 겪음). 이미 얕게 받았으면 `git fetch --unshallow` 후 계산할 것.
20. **Bing/Yahoo 유입이 Google보다 많다는 사실을 잊지 말 것**(08-07 GA4: Bing 7 + Yahoo 9 vs Google 5). Google 색인 병목에만 매달리지 말고 Bing 쪽 최적화(IndexNow, Bing Webmaster Tools)도 같이 챙길 것. **08-08 갱신: IndexNow 키 파일은 배포됨(`/4ecbb2cc89f059e8138b521308eb76716c0ce520c587b424a65a5b2d171fd774.txt`), 실제 URL 제출은 샌드박스 네트워크 제한으로 아직 안 됨 — "Sonnet 실행 결과" 섹션의 curl 명령 참고해서 다음 사람이 실행할 것.** **[무효 — 2026-08-17 확정: 색인 수동 제출 금지. 문서 최상단 "절대 하지 말 것" 참고.]**
21. **"크롤링됨 — 현재 색인이 생성되지 않음" 건수를 매 세션 반드시 확인할 것.** 이 수치가 늘고 있으면 신규 페이지 확장을 멈추고 기존 페이지 통합/강화로 전환하는 신호다(08-07에 0→11로 신규 발생해서 그 세션 신규를 0건으로 결정함).



