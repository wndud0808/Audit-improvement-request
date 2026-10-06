# 변경 기록

새 버전은 기존 파일을 덮어쓰지 않고 `-vN` 이름으로 추가합니다.

## v1
- `index-v1.html`: 개선 요청 보드 (Firebase 연결 버전, Google 로그인만)
  - 팀별 요청 카드 (접기/펼치기), 요청 칸(전체 권한) / 회신 칸(로그인 사용자)
  - 사진 붙여넣기·선택·끌어놓기, 탭 추가/이름 변경/삭제, 카드별 이력
- `database-rules-v1.json`: Realtime Database 보안 규칙
  - 전체 권한: 관리자 3개 Google 계정
  - 이력(`logs`)은 추가만 가능
- 설정 전 `index-v1.html`의 `FIREBASE_CONFIG` 값(`REPLACE_ME`)을 새 프로젝트 값으로 바꿔야 합니다.

## v2
- `index-v2.html`: v1 기능 그대로 + 아래 변경
  - 사진 용량 축소: 붙여넣을 때 바로 긴 변 1024px 이하, WebP(미지원 시 JPEG)로 압축, 한 장당 약 220KB 이하로 맞춤
  - 엑셀 내보내기 버튼 추가 (전체 권한만): 현재 탭의 모든 팀 요청을 CSV로 내려받음. 양식은 추후 지정 예정 (`exportHeader`, `exportRow` 함수만 수정)
- `database-rules-v1.json` 그대로 사용 (규칙 변경 없음)

## v3
- `index-v3.html`: v2 기능 그대로 + 아래 변경
  - 사진 삭제 버튼을 사진 아래에 "이 사진 삭제"로 표시 (기존 작은 × 버튼 대체)
  - 실수 방지를 위해 한 번 누르면 "한 번 더 누르면 삭제"로 바뀌고, 4초 안에 다시 누를 때만 삭제
  - 요청 사진(전체 권한)과 회신 사진(모두) 모두 삭제 후 다시 붙여넣기 가능

## v4
- `index-v4.html`: v3 기능 그대로 + 아래 변경
  - 사진 크게 보기: 마우스 휠로 확대/축소(커서 위치 기준), 확대 상태에서 드래그로 이동
  - 사진 클릭: 2배 확대 ↔ 원래 크기, 화면 우상단 +, −, 원래 크기, 닫기 버튼 추가
  - 배경 클릭 또는 Esc로 닫기

## v5
- `index-v5.html`: v4 기능 + Firebase 프로젝트 연결 완료
  - 프로젝트: audit-improvement-measures (Realtime Database 위치: asia-southeast1)
  - FIREBASE_CONFIG에 실제 값 적용 (v4까지는 REPLACE_ME 자리표시자였음)
  - 동작하려면 Firebase 콘솔에서 Authentication(Google 로그인)과 Realtime Database 규칙(database-rules-v1.json), 승인된 도메인 설정이 되어 있어야 함

## v6
- `index-v6.html`: v5 기능 + 분류(폴더) 기능
  - 팀 안에 관리자가 분류를 만듦 (추가, 수정, 삭제). 분류는 팀마다 따로 관리
  - 요청 카드에서 분류를 고르면 그 분류 칸 아래로 묶여 보임. 분류가 없는 요청은 "미분류"
  - 분류를 지우면 안의 요청은 미분류로 돌아감 (요청은 지워지지 않음)
- `database-rules-v2.json`: `cats` 항목이 추가된 규칙. **v1 규칙을 이 파일 내용으로 바꿔 게시해야 분류가 저장됩니다.**

## v7
- `index-v7.html`: v6 기능 + 사진 붙여넣기 안내 보강
  - 카드 제목 등 요청/회신 칸 밖에서 붙여넣으면 "사진을 넣을 칸을 먼저 클릭" 안내가 뜸 (이전에는 아무 반응 없음)
  - 사진 저장 성공/실패, 이미지 읽기 실패를 화면 아래 안내 문구로 표시

## 고정 주소 (index.html)
- `index.html`은 항상 최신 버전(현재 v7)과 같은 내용입니다.
- 주소: https://wndud0808.github.io/Audit-improvement-request/ (업데이트해도 주소는 바뀌지 않음)
- 새 버전(vN)을 만들 때는 `index-vN.html`을 추가하고, 같은 내용을 `index.html`에도 복사합니다.
- 이전 버전 파일(index-v1.html ~ )은 기록용으로 그대로 둡니다.

## v8
- 새 Firebase 프로젝트(improve-board-2)로 설정 변경 (기능은 v7과 동일)
- Realtime Database: asia-southeast1 (싱가포르)
- 규칙: database-rules-v2.json 게시 필요
- `index.html`도 v8과 같은 내용으로 갱신

## v9
- 관리자 전용 "분류 이동" 선택 상자를 카드 제목 오른쪽에 추가 (접힌 상태에서도 바로 이동)
- 펼친 카드 안의 중복 분류 선택은 제거
- `index.html`도 v9와 같은 내용으로 갱신
