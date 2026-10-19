# 설정 화면 (텔레그램 미니 앱) 파일

텔레그램 `/settings` 버튼이 여는 설정 화면입니다. 설계: `docs/텔레그램-미니앱-설계.md`.

## GitHub Pages 에 올릴 파일 (공개 저장소 `kidguard-panel` 의 맨 위 폴더)

- `index.html`
- `panel.css`
- `core.js`
- `panel.js`

`tests/` 와 이 `README.md` 는 올리지 않아도 됩니다. 빌드 과정은 없습니다 (파일을 그대로 복사).

## 비밀 정보 없음

이 폴더에는 봇 토큰·비밀번호·아이 이름·설정 값이 없습니다. 아이 설정은 노트북이 버튼 주소의 `#` 뒤에 넣어 보내고
(브라우저가 서버로 보내지 않음), 바꾼 값은 텔레그램(`web_app_data_send`)으로만 노트북에 갑니다. 외부 스크립트·글꼴·CDN 을
쓰지 않고, CSP 로 모든 네트워크 연결을 막았습니다.

## 시험

- `node panel/tests/run.mjs` — 순수 함수 시험 (주소 읽기 kg1·kg2, 압축 풀기, 바뀐 키, 검사, 크기, v2 글, 최신 값 알리기, 기록 값 정리).
- `node panel/tests/interop.mjs <입력> <출력>` — 노트북(C#)이 만든 주소를 화면 코드로 풀고 보낼 글을 만든다. 직접 쓰지 않고
  `tests/KidGuard.Core.Tests/PanelInteropTests.cs` 가 node 가 있으면 불러서, 그 글을 다시 노트북 검사(`PanelChanges.Check`)에 넣는다.
  kg2 주소의 출력 모양은 `interop.mjs` 맨 위 설명을 보세요 (구역별 v1 글, v2 글 하나, 최신 값 받기 글).
- `node panel/tests/render.mjs <사진 폴더>` — 전역 playwright 로 예전(kg1) 화면은 390×844, 탭 화면(kg2)은 360×844 로 열어
  탭·📊 기록(밝은·어두운 테마)·최신 값 줄(초록·노랑·빨강)·여러 탭 저장·최신 값 받기를 확인하고 사진을 남깁니다 (기본 `tests/shots/`).
