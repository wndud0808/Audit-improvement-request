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
