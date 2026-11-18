# 생활 재무 포털 (재무 계산기 & 용어 사전)

부가세·대출 이자·환율 계산기, 재무 용어 사전, 재무 FAQ, 공식 기관 자료실을 한 화면에 모은 단일 HTML 포털입니다. 별도 설치나 서버 없이 `index.html` 하나로 동작합니다.

## 폴더 구성

```
.
├── index.html            포털 본체 (이 파일 하나로 동작)
├── README.md             이 문서
├── files/                부서별 안내 PDF 42개 (영문 소문자-하이픈 파일명)
└── 이전버전/
    ├── portal-v2.html            이름 변경 직전의 부서포털_v2.html 사본 (민트 라이트 디자인 적용본)
    └── portal-v2-original.html   디자인 적용 전 원본
```

## 열어 보는 방법

1. `index.html`을 더블클릭하면 기본 브라우저에서 열립니다. (Chrome, Edge 등 최신 브라우저 권장)
   - 단, 더블클릭(`file://`)으로 열면 일부 브라우저가 다운로드 속성을 무시해 PDF를 같은 탭에서 열 수 있습니다. 자료실 버튼이 바로 저장되게 하려면 웹 서버나 사내 포털에 올려 `http://` 또는 `https://` 주소로 접속해 주세요. 로컬에서 확인하려면 이 폴더에서 `python -m http.server`를 실행한 뒤 `http://localhost:8000`으로 접속하시면 됩니다.
2. 인터넷 연결 없이도 계산기·용어 검색·FAQ가 동작합니다. 자료실의 공식 기관 링크만 연결 시 외부 사이트로 이동합니다.
3. 입력하신 값은 저장되거나 외부로 전송되지 않으며, 페이지를 새로고침하면 초기화됩니다.

## 화면별 사용법

상단 메뉴(홈 · 계산기 · 용어 사전 · FAQ · 자료실)를 누르면 해당 구역으로 이동합니다. 키보드 사용 시 맨 앞의 "본문 바로가기"로 메뉴를 건너뛸 수 있습니다.

### 1. 계산기
탭을 선택해 계산기를 바꿉니다. 금액은 숫자만 입력하시면 쉼표가 자동으로 들어갑니다. 각 탭의 **초기화**로 입력을 비우고, **결과 복사**로 계산 결과 요약 문장을 복사할 수 있습니다. 탭 선택은 방향키(←/→), `Home`, `End`로도 가능합니다.

| 계산기 | 입력 | 결과 |
|---|---|---|
| 부가세 | 입력 기준(공급가액 기준 / 합계금액 기준), 금액, 세율(기본 10%), 부가세 원 미만 처리(반올림·절사·올림) | 공급가액, 부가세, 합계금액, 계산식 |
| 대출 이자 | 대출 원금, 연 이자율, 대출 기간(년·개월), 상환 방식(원리금균등·원금균등·만기일시), 거치기간(개월) | 월 납입액, 총 이자, 총 상환액, 원금·이자 비중 막대, **상환 스케줄 보기**(회차별 납입액·원금·이자·잔액) |
| 환율 환산 | 환산 방향(외화→원화 / 원화→외화), 통화(USD·JPY·EUR·CNY·GBP·직접 입력), 환율, 환율 기준 수량(1단위당 / 100단위당), 외화 금액, 환전 수수료(선택) | 환산 결과, 적용 환율, 계산식 (**↔ 방향 바꾸기** 지원) |

계산 시 유의사항
- 부가세 계산기는 일반과세 표준세율 10% 기준입니다. 간이과세자·영세율·면세 거래는 적용 방식이 다를 수 있습니다.
- 대출 이자는 `월 이자 = 대출 잔액 × 연 이자율 ÷ 12`(원 미만 절사)로 계산한 단순 추정치이며, 중도상환수수료·변동금리·일수 계산은 반영하지 않습니다. 거치기간에는 이자만 납부하는 것으로 계산하고, 만기일시상환에는 거치기간이 적용되지 않습니다.
- 환율은 시세를 자동으로 불러오지 않고 입력하신 값을 그대로 사용합니다. 시장 환율은 한국은행 경제통계시스템(ECOS) 또는 거래 금융기관에서 확인해 입력해 주세요. 수수료는 입력한 환율에 불리한 방향으로 적용됩니다.

### 2. 용어 사전
- 재무 용어 41개를 수록했습니다.
- 검색창에 용어명, 영문 약어(예: LTV), 설명 속 단어를 입력하거나 초성(예: ㅂㄱㄱㅊㅅ)으로 검색합니다. 일치한 부분은 강조 표시되고, 입력창의 **×** 버튼으로 검색어를 지웁니다.
- 검색창 아래의 분류 버튼으로 분야별 필터를 걸 수 있으며, 결과 개수가 함께 표시됩니다.

### 3. FAQ
- 맨 위의 **검색창**에 키워드를 입력하면 질문·답변·근거 전체에서 찾아 해당 FAQ만 보여 줍니다. 띄어쓰기로 구분한 여러 단어는 모두 포함된 항목만 남기고, 일치한 낱말은 강조되며, 답변 본문에서 일치한 항목은 자동으로 펼쳐집니다. 검색어를 지우면(입력창의 ×) 자동으로 펼쳐진 항목은 다시 접힙니다.
- 검색창 아래의 **분류 버튼**(전체 · 부가가치세 · 대출·이자 · 환율 · 이용 안내 · 연말정산 · 재무제표·지표 · 증빙)을 누르면 해당 분류만 보입니다. 키워드와 분류는 함께 적용되며, 현재 표시 개수는 "총 18개 중 N개 표시"로 나타납니다.
- 질문을 누르면 답변이 펼쳐지고, 오른쪽 위의 **모두 펼치기**로 지금 보이는 항목을 한 번에 열고 닫습니다.
- 새 FAQ를 추가할 때는 `<details class="faq">` 항목의 질문 앞에 `<span class="faq-cat">분류명</span>`을 넣거나, 분류 표시가 필요 없으면 `<details class="faq" data-cat="분류명">`처럼 지정하세요. 분류 버튼은 이 값을 읽어 자동으로 만들어집니다.
- 각 답변 하단에 근거 법령·확인처를 적어 두었습니다. "확인 필요"로 표시된 항목은 원문 확인 후 사용해 주세요.
- 「생활 재무·세금 기초 가이드」와 「재무 용어집」을 인용한 항목은 `files/03-finance-life-finance-tax-basics.pdf`, `files/03-finance-glossary.pdf`와 제목이 같습니다. (FAQ 안의 인용은 텍스트이며 링크는 아닙니다.)

### 4. 자료실
홈택스, 국세청, 국가법령정보센터, 금융감독원(파인 포함), 금융위원회, 한국은행(ECOS 포함), DART, KIND, KRX 정보데이터시스템 등 공식 기관 사이트 링크 모음입니다. 세부 가이드와 최신 개정 내용은 각 기관 사이트에서 확인해 주세요.

**부서별 안내 자료 목록**: 자료실 아래쪽에 `files/` 폴더의 PDF 42개를 부서별로 묶어 파일명·설명·용량·다운로드 버튼으로 보여 줍니다.
- 설명은 각 PDF 첫 페이지의 안내 문구를 그대로 옮겼고, 용량은 실제 파일 크기입니다. (KB = 1,024byte)
- 버튼 링크는 `files/영문-파일명.pdf` 상대 경로이고 `download` 속성이 있어, 새 창 없이 한글 이름(예: `인재상_조직문화_소개서.pdf`)으로 저장됩니다.
- 목록을 수정하려면 `index.html`의 `var DL=[` 배열에서 항목을 추가·수정하세요. 항목 형식은 `[부서번호, 부서, 저장될 한글 파일명, files 안의 실제 파일명, 설명, 용량(byte)]`입니다. 용량은 파일 속성의 "바이트" 값을 넣습니다.

## 부서별 안내 자료 (`files/`)

파일명은 `부서번호-팀-내용.pdf` 형식의 영문 소문자·숫자·하이픈이며, 한글 원래 이름은 오른쪽 열에 남겨 두었습니다. 영문명은 한글 파일명을 옮긴 번역 이름이므로, 팀 호칭이 다르면 원하시는 표기로 알려 주세요.

| 부서 폴더(원래 이름) | 현재 파일 | 원래 파일명 |
|---|---|---|
| 01_인사HR_채용안내 | `files/01-hr-talent-culture-guide.pdf` | 인재상_조직문화_소개서.pdf |
|  | `files/01-hr-job-posting-2026-h1.pdf` | 채용공고_2026년_상반기.pdf |
| 02_영업마케팅_제품소개 | `files/02-sales-customer-support-guide.pdf` | 고객지원_안내서.pdf |
|  | `files/02-sales-product-service-intro.pdf` | 제품서비스_소개서.pdf |
| 03_재무회계_생활재무 | `files/03-finance-life-finance-tax-basics.pdf` | 생활_재무세금_기초가이드.pdf |
|  | `files/03-finance-glossary.pdf` | 재무_용어집.pdf |
| 04_기획경영지원_회사소개ESG | `files/04-planning-esg-activities.pdf` | ESG_활동_소개서.pdf |
|  | `files/04-planning-company-intro.pdf` | 회사_소개서.pdf |
| 05_설비자재유통팀 | `files/05-equipment-product-catalog.pdf` | 설비자재_제품카탈로그.pdf |
|  | `files/05-equipment-order-delivery-guide.pdf` | 주문납품_거래안내서.pdf |
| 06_수주영업팀_레미콘 | `files/06-readymix-product-guide.pdf` | 레미콘_제품안내서.pdf |
|  | `files/06-readymix-shipping-transaction-procedure.pdf` | 출하_거래절차_안내서.pdf |
| 07_Vision전략팀 | `files/07-vision-division-strategy-intro.pdf` | 부문_비전전략_소개서.pdf |
|  | `files/07-vision-business-portfolio-guide.pdf` | 사업포트폴리오_안내서.pdf |
| 08_MD팀_건자재하우징 | `files/08-md-product-registration-quality-requirements.pdf` | 상품등록_품질요건_안내.pdf |
|  | `files/08-md-partner-listing-proposal-guide.pdf` | 협력사_입점제안_가이드.pdf |
| 09_총무팀_근무환경안전 | `files/09-general-affairs-emergency-response.pdf` | 비상대응_행동요령.pdf |
|  | `files/09-general-affairs-facility-guide.pdf` | 시설이용_안내서.pdf |
| 10_프리콘팀 | `files/10-precon-construction-method-brochure.pdf` | 공법기술_브로슈어.pdf |
|  | `files/10-precon-service-intro.pdf` | 프리콘_서비스소개서.pdf |
| 11_CM팀_건설사업관리 | `files/11-cm-service-intro.pdf` | CM_서비스소개서.pdf |
|  | `files/11-cm-schedule-quality-safety-standards.pdf` | 공정품질안전_관리기준.pdf |
| 12_경영개선팀_혁신윤리 | `files/12-improvement-pi-promotion-guide.pdf` | 업무혁신_PI추진_가이드.pdf |
|  | `files/12-improvement-code-of-ethics.pdf` | 윤리강령_행동규범.pdf |
| 13_자금팀_대금지급 | `files/13-treasury-financial-fraud-prevention.pdf` | 금융사기_예방안내.pdf |
|  | `files/13-treasury-partner-payment-procedure.pdf` | 협력사_대금지급_절차안내서.pdf |
| 14_회계팀_증빙결산 | `files/14-accounting-reading-financial-statements.pdf` | 재무제표_읽는법.pdf |
|  | `files/14-accounting-evidence-submission-guide.pdf` | 증빙제출_가이드.pdf |
| 15_신사업팀_오픈이노베이션 | `files/15-new-business-feasibility-basics.pdf` | 사업성검토_기초.pdf |
|  | `files/15-new-business-proposal-guide.pdf` | 사업제안_가이드.pdf |
| 16_재무기획팀_예산관리 | `files/16-fin-planning-pnl-valuation-basics.pdf` | 손익_가치평가_기초.pdf |
|  | `files/16-fin-planning-budget-request-guide.pdf` | 예산편성_신청안내.pdf |
| 17_HR팀_직원생애주기 | `files/17-hr-new-hire-onboarding-guide.pdf` | 신규입사자_온보딩_가이드.pdf |
|  | `files/17-hr-policy-public-guide.pdf` | 인사제도_공개안내.pdf |
| 18_IB본부팀_기업금융 | `files/18-ib-service-intro.pdf` | IB_서비스소개서.pdf |
|  | `files/18-ib-funding-terms-guide.pdf` | 자금조달_용어안내.pdf |
| 19_리서치센터팀 | `files/19-research-usage-guide.pdf` | 리서치_이용안내서.pdf |
|  | `files/19-research-investment-indicators-glossary.pdf` | 투자지표_용어해설집.pdf |
| 20_대안투자본부팀 | `files/20-alt-invest-esg-responsible-investment-principles.pdf` | ESG_책임투자_원칙.pdf |
|  | `files/20-alt-invest-understanding-guide.pdf` | 대안투자_이해안내서.pdf |
| 21_주식채권운용본부 | `files/21-asset-mgmt-philosophy-process-intro.pdf` | 운용철학_프로세스_소개서.pdf |
|  | `files/21-asset-mgmt-allocation-risk-basics.pdf` | 자산배분_리스크관리_기초.pdf |

## 유의사항

- 정보 기준일은 2026년 11월 11일입니다. 세율·법령·기한은 이후 바뀔 수 있습니다.
- 계산 결과와 용어 설명은 참고용입니다. 실제 세액·이자·환전액은 세법, 금융기관 약정, 적용 환율에 따라 달라질 수 있으며, 세무·법률 판단이 필요한 사항은 세무사·법무 검토를 권고드립니다. 특정 매매나 투자에 대한 권유가 아닙니다.

## 파일명 규칙

- 새로 추가하는 파일은 한글·공백 없이 영문 소문자, 숫자, 하이픈(`-`)만 사용합니다. (예: `files/22-team-service-intro.pdf`)
- 포털 본체는 항상 `index.html`로 두고, 이전 판은 `이전버전/` 폴더에 보관합니다.
