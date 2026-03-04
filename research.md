# 프로젝트 협업 환경 구축을 위한 리서치 (Research Phase)

본 문서는 `plan.md`를 바탕으로 팀원과의 원활한 협업을 위해 필요한 초기 세팅(Phase 1) 요구사항을 분석한 결과입니다.

## 1. 프로젝트 구조 특성 분석

현재 시스템 아키텍처는 세 가지 주요 스택으로 분리되어 있습니다:

1. **프론트엔드**: React + Vite
2. **백엔드**: Spring Boot (Java)
3. **AI 서비스**: FastAPI (Python)

단일 저장소(Monorepo) 안에 세 가지 완전히 다른 생태계(Node.js, Java/Gradle, Python)의 코드가 공존하는 형태를 띄고 있습니다.

## 2. 발생 가능한 협업 이슈 파악

- 서로 다른 에디터 설정으로 인한 탭/스페이스, 줄바꿈(CRLF/LF) 충돌.
- 언어별로 코딩 스타일(Naming, Formatting)이 각기 달라 코드 리뷰에 피로도 발생.
- 무분별한 커밋 메시지로 인해 추후 이슈 추적(Tracking)과 체인지로그(Changelog) 작성이 어려움.
- PR 시 체크해야 할 필수 항목 누락.

## 3. 해결 방안 (협업 표준화 전략)

이러한 문제를 방지하기 위해 다음과 같은 협업 도구 및 파이프라인 세팅을 도입해야 합니다.

- **GitHub Templates**: PR 및 Issue 작성 규격화.
- **Husky & lint-staged (Node.js 기반)**: 모노레포 환경이므로, 프로젝트 최상단(root)에서 git hook을 중앙 제어 허브로 사용.
- **Commitlint**: 커밋 메시지 규칙(Conventional Commits) 강제 적용.
- **언어별 자체 Linter/Formatter**:
  - JS/TS (프론트): ESLint + Prettier
  - Java (백엔드): spotless-plugin-gradle (빌드시 포맷 확인)
  - Python (AI 서비스): Black, Flake8, isort

## 4. 액션 아이템

이 분석을 바탕으로 기존 `plan.md`에 구체적인 **팀원 협업을 위한 초기 개발 환경 구축 계획** 섹션을 추가하고, **구현 Todo List**를 세분화하여 기록합니다.
