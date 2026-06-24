# 개인 프로필 / 포트폴리오 사이트

정적 HTML · CSS · JavaScript로 만든 1페이지 개인 소개 사이트입니다.
콘텐츠는 `content.json`에서 불러와 화면에 렌더링하며, GitHub Pages로 자동 배포됩니다.

## ✨ 특징

- **빌드 도구 없는 순수 정적 사이트** — HTML 한 파일로 동작
- **콘텐츠 분리** — 텍스트/프로젝트/연락처를 `content.json`에서 관리, HTML 수정 없이 내용 변경 가능
- **반응형 디자인** — 모바일 우선, 760px 이상에서 2열 그리드
- **스크롤 인터랙션** — 섹션 등장 애니메이션, 현재 위치에 따라 내비게이션 활성화
- **GitHub Pages 자동 배포** — `main` 브랜치 push 시 GitHub Actions로 배포

## 📁 구성

```
.
├── index.html                      # 마크업 · 스타일 · 스크립트 (단일 파일)
├── content.json                    # 소개/기술/프로젝트/연락처 콘텐츠
└── .github/workflows/deploy-pages.yml  # GitHub Pages 배포 워크플로
```

## 🚀 로컬 실행

`content.json`을 `fetch`로 불러오기 때문에 `file://`로 직접 열면 JSON 로딩이 막힙니다.
간단한 로컬 서버로 실행하세요. (JSON 로딩 실패 시에는 HTML에 내장된 기본 콘텐츠가 표시됩니다.)

```bash
# Python
python -m http.server 8000

# 또는 Node
npx serve .
```

이후 브라우저에서 `http://localhost:8000` 접속.

## ✏️ 콘텐츠 수정

`content.json`을 편집하면 사이트 내용이 바뀝니다.

| 키 | 설명 |
| --- | --- |
| `meta` | 로고, 상단 라벨, 이름, 푸터 문구 |
| `about` | 히어로 소개 문구, 소개글 제목·내용 |
| `skills` | 보유 기술 제목·설명과 `items` 배열 |
| `projects` | 프로젝트 제목·설명과 `items` (각 `title`, `description`) |
| `contact` | 연락처 항목 (`label`, `text`, `url`) — `http(s)` 링크는 새 탭으로 열림 |

## 🌐 배포

`main` 브랜치에 push하면 [deploy-pages.yml](.github/workflows/deploy-pages.yml) 워크플로가
저장소 전체를 GitHub Pages 아티팩트로 업로드하여 배포합니다.
저장소 **Settings → Pages → Source**를 **GitHub Actions**로 설정하면 활성화됩니다.
