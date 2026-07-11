# GPA Vault 인수인계 문서 v5 (2026-07-11 기준)

이전 v4 문서를 대체함. v4의 배경 설명(레포 구조, Public 유지 결정 등)은 그대로 유효하므로 필요시 v4 참고. 이 문서는 **07-09, 07-11 세션에서 바뀐 것 + 새로 확정된 원칙** 위주로 정리.

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

## 8. 알아둬야 할 사실 (student loan 정책, 2026-07 기준)
- **SAVE 플랜은 2026-07-01부로 RAP(Repayment Assistance Plan)로 대체됨**
- **REPAYE는 이미 존재하지 않음** — SAVE에 흡수됐다가 SAVE 자체가 없어졌으므로 "REPAYE" 검색 유입은 오래된/혼동된 검색 의도. RAP 또는 IBR로 안내하는 게 맞음
- **PAYE, ICR은 기존 대출자(2026-07-01 이전 대출, 이후 신규 대출/통합 안 한 경우)만 2028-07-01까지 한시적 유지**, 신규 대출자는 이용 불가 (RAP 또는 Tiered Standard만 가능)
- 관련 콘텐츠 작성 시 이 팩트 기준으로 일관되게 서술할 것 (`loan-repayment-calculator.html`, `student-loan-repayment-plans-2026.html`에 이미 반영됨)

## 9. GSC 현황 (07-11 기준)
- 색인: 20 / 미색인(발견됨-현재 색인 안 됨): 29 — **변화 없음, 아직 이른 시점** (07-08 noscript 수정 반영까지 통상 1~3주 소요, 재촉하지 말 것)
- **새로 발견된 이슈**: "크롤링됨 - 현재 색인이 생성되지 않음" 1건 — 09일 리포트엔 없던 카테고리. 어떤 URL인지 이번 리포트로는 특정 불가 (GSC URL 검사 스크린샷 필요). 다음 세션에 리포트 받으면 계속 있는지 확인
- 404: "유효성 검사: 시작됨"으로 전환 — 07-09에 만든 리다이렉트 스텁을 구글이 인지하고 검증 중인 것으로 보임, 긍정적 신호
- 리디렉션 3건: **조사 대상 아님** (사용자 확인)

## 10. 관찰 중 / 재평가 보류 항목
- `blog/how-to-raise-your-gpa-in-one-semester.html`: 07-07에 title 변경(질문형으로), 순위는 11위권으로 양호하나 CTR이 GSC "지난 3개월 통합" 데이터라 새 title 효과가 아직 제대로 안 섞여 들어와 있음. **최소 2~3주 더 지난 후 재평가**, 지금 또 손대면 성급한 판단
- `college-cost-calculator.html`, `act-score-calculator.html`: 위 7번 참고, 헤드 키워드 경쟁 압도적이라 당분간 관망

## 11. 신규 후보 (백로그, 착수 안 함)
- SSAT percentile calculator — 검색 볼륨 작음(월 노출 4 수준), 우선순위 낮음
- IB GPA 클러스터(`ib gpa calculator`, `ib to gpa` 등, 합산 노출 ~19) — 기존 `ib-gpa-calculator.html`에 FAQ 보강 필요 (아직 미착수)

## 12. 파일 현황
- tools: 21개 + index (`sat-percentile-calculator.html`이 가장 최근 신규, 07-07)
- blog: 27개 + index
- 전체 sitemap URL: 53개 (변동 없음, 이번 세션엔 신규 페이지 추가 안 함)

## 13. 다음 세션 시작 전 체크리스트
1. 이 문서(v5) 먼저 정독
2. 새 GSC Performance/Coverage export 받아서 09일/11일 데이터와 비교 (특히 "크롤링됨-미색인 1건"이 계속 있는지, 색인 20/29가 움직였는지)
3. 새 GitHub 토큰 발급받기
4. clone 후 `git config` 설정 잊지 말 것
5. 작업 시 **신규는 9개 파일 체크리스트, 보강은 4개 파일 체크리스트(본문/sitemap/blog-index/llms.txt) 누락 금지** — llms.txt 빠뜨리면 사용자가 바로 지적함
6. college-cost-calculator, act-score-calculator는 별도 지시 없으면 건드리지 않기
7. 리디렉션 이슈는 조사하지 않기 (사용자 확인됨)
8. 작업 완료 후 커밋/푸시 → Pages 빌드 `built` 확인까지 끝내고, **사용자가 직접 확인해야 할 URL을 클릭 가능한 링크로 정리해서 제시** (사용자는 영어를 몰라서 콘텐츠 검수가 아니라 화면이 깨졌는지만 육안 확인함 — 문구 검수 요청하지 말 것)
9. 세션 끝나면 토큰 revoke 리마인드
