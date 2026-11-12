# Thanksgiving Quiz (추수감사 실시간 퀴즈)

스크린에는 **host.html**을 띄우고, 참가자는 QR로 **play.html**에 접속해 휴대폰으로 답을 고릅니다.
데이터는 Firebase Realtime Database(`thanks-giving-quiz`)에 실시간으로 저장됩니다.

## 파일
| 파일 | 역할 |
|---|---|
| host.html | 진행자 스크린 (QR 대기실 → 라운드 소개 → 문제 → 정답 공개 → 팀 순위 → 최종 결과) |
| play.html | 참가자 휴대폰 화면 (이름·팀 선택 → A/B/C/D 버튼) |
| questions.js | 3라운드 30문제 (문제 수정은 이 파일만) |
| config.js | Firebase 설정과 6개 팀 |
| style.css | 공통 디자인 |

## 배포 (GitHub Pages)
1. GitHub에서 새 저장소(예: `thanksgiving-quiz`)를 Public으로 만듭니다.
2. 위 5개 파일을 저장소 맨 위(root)에 올립니다.
3. Settings → Pages → Branch: `main` / `(root)` → Save.
4. 1~2분 뒤 `https://<아이디>.github.io/thanksgiving-quiz/host.html` 을 스크린에 띄웁니다.
   QR 코드는 같은 폴더의 play.html 주소로 자동 생성됩니다.

> 파일을 PC에서 더블클릭으로 열면 작동하지 않습니다. 반드시 GitHub Pages 주소로 여세요.

## 진행 방법
- **Space / →** : 다음 단계 (문제 시작 → 정답 공개 → 순위 → 다음 문제)
- 모든 참가자가 답하거나 시간이 끝나면 자동으로 정답이 공개됩니다.
- **Reset Scores** : 점수만 초기화 (참가자 유지, 리허설 후 사용)
- **Clear Players** : 참가자까지 모두 초기화
- 두 버튼 모두 한 번 더 눌러야 실행됩니다.

## 점수
- 정답: 최대 1,000점, 늦게 맞힐수록 최소 500점까지 줄어듭니다.
- 3라운드(Thanksgiving Initials)는 점수 2배.
- 팀 점수 = 팀원 점수의 **평균** (인원 많은 팀이 유리하지 않음).

## 보안 메모
데이터베이스는 테스트 모드(약 30일 공개)입니다. 이름은 별명으로 받고 개인정보는 넣지 마세요.
행사 후에는 Firebase 콘솔 → Realtime Database → 규칙에서 `".read": false, ".write": false` 로 바꾸면 닫힙니다.

## 이미지 출처
Zoom-In 라운드 그림: [Twemoji](https://github.com/jdecked/twemoji) (그래픽 CC-BY 4.0) — `img/` 폴더.
