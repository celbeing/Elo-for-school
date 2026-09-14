# ♟️ 우리 반 체스리그 (Classroom Chess Elo System)

초등·중등 학급 및 동아리 체스 리그 운영을 위한 **경량형 반응형 웹 애플리케이션**입니다. 별도의 서버 호스팅이나 복잡한 데이터베이스 구축 없이, **단일 HTML 파일**과 **구글 스프레드시트(Google Apps Script)**만으로 데이터 저장 및 다중 사용자 열람 환경을 제공합니다.

---

## 📌 주요 특징

* **단일 파일 배포 (Standalone HTML):** 별도의 빌드 과정 없이 `Elo for school.html` 파일 하나를 더블클릭하는 것만으로 브라우저에서 즉시 실행됩니다.
* **구글 스프레드시트 클라우드 연동:** Google Apps Script(GAS)를 백엔드 DB로 활용하여 여러 기기(태블릿, 크롬북, 스마트폰)에서 최신 전적과 레이팅을 실시간 동기화합니다.
* **역할 기반 접근 제어 (Admin/Viewer Mode):**
  * **관리자(교사):** 선수 등록/삭제, 경기 결과 입력, 전적 취소, JSON 백업/복원, 비밀번호 변경.
  * **뷰어(학생):** 순위표 열람, 전적 및 승률 검색, 개인별 레이팅 변동 그래프 확인 (데이터 수정/삭제 차단).
* **Elo 레이팅 알고리즘 적용:** 표준 Elo 산출 공식($K=32$, 초기값 $1200$)을 바탕으로 기대 승률과 경기 결과에 따른 점수 변동을 자동 계산합니다.
* **반응형 대시보드 & 시각화:** Recharts 기반의 레이팅 변동 선 그래프 및 백/흑 진영별 전적 막대그래프를 제공합니다.

---

## 🚀 빠른 시작 가이드

### 1. 프로그램 실행하기
1. 본 저장소의 [`Elo for school.html`](./Elo_for_school.html) 파일을 다운로드합니다.
2. 다운로드한 파일을 크롬(Chrome)이나 웨일(Whale) 등 최신 웹 브라우저로 엽니다.
3. 바로 오프라인(로컬 스토리지 기반)으로 사용하거나, 아래 절차에 따라 구글 시트와 연동합니다.

---

### 2. 구글 스프레드시트 연동 (클라우드 DB 구축)

학생들과 데이터를 공유하거나 브라우저 캐시 초기화와 무관하게 데이터를 안전하게 보관하려면 구글 스프레드시트와 연동하세요.
**주의: 교사용 데이터는 연동 전에 반드시 우측 하단의 "내보내기"로 저장하세요. 연동 후에는 모든 데이터가 더미 파일로 덮어씌워집니다.**

#### Step 1: 시트 사본 만들기
1. [구글 스프레드시트 템플릿 사본 만들기](https://docs.google.com/spreadsheets/d/1yr9QJAsDvAs2isxLhI5Jdx0zWChv6YRa02t344xsKpQ/copy?usp=sharing) 시트의 사본을 만듭니다.

![사본 만들기](https://github.com/user-attachments/assets/d40549ad-d52c-4d3e-9eaa-078094316533)

2. 스프레드시트의 1행 A열(`A1`)에 아래 초기 JSON 문자열이 들어있는지 확인합니다:
   ```json
   {"title":"우리 반 체스리그","players":[],"matches":[]}

![JSON 문자열 확인](https://github.com/user-attachments/assets/8c2a16c7-25ea-4689-acf2-45b4449b80d7)

3. 함께 복제된 Apps Script 파일을 엽니다.

![Apps Script 파일 열기](https://github.com/user-attachments/assets/795e30dc-5a9e-468a-b486-33c7f043cced)

4. Apps Script를 새로 배포합니다.

![Apps Script 새 배포](https://github.com/user-attachments/assets/20781314-7432-4619-904e-047b1c8a298c)

![Apps Script 새 배포](https://github.com/user-attachments/assets/a12084bc-ee94-432a-b463-545fb151d414)

![Apps Script 새 배포](https://github.com/user-attachments/assets/774d9e6a-cca0-41c8-ac00-3729716a8a7a)

![Apps Script 새 배포](https://github.com/user-attachments/assets/cb9e2333-8daf-4461-8d18-dd0e4e8e25a4)

![Apps Script 새 배포](https://github.com/user-attachments/assets/7480a995-26cd-43f9-a5ff-5f24192c473b)

![Apps Script 새 배포](https://github.com/user-attachments/assets/ba89b1a8-ebed-4014-b03b-0d5f9872f986)

![Apps Script 새 배포](https://github.com/user-attachments/assets/435decdc-3044-404b-b6d1-92f66ea25459)

5. 배포된 웹 앱 URL을 복사합니다.

![웹 앱 URL 복사](https://github.com/user-attachments/assets/b8ab41cf-cdb4-4081-a222-c4835daed60b)

![웹 앱 URL 복사](https://github.com/user-attachments/assets/c9391b2a-fba8-4ad4-a219-b1a8e87c661f)

![웹 앱 URL 복사](https://github.com/user-attachments/assets/e10607ef-6620-46d0-b530-4e50157bdb15)

![웹 앱 URL 복사](https://github.com/user-attachments/assets/b848d17c-34c6-4db9-af88-f4a64f75e9a3)

6. 동기화가 완료되었습니다.

![동기화 완료](https://github.com/user-attachments/assets/7e60f1e1-9d37-436e-9ee6-e1e1fbda7929)
**클라우드 동기화가 완료된 후에는 비밀번호를 변경하여 관리자모드 접근을 제한하세요.**
