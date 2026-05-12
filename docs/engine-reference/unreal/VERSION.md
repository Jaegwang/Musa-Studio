# Unreal Engine — Version Reference

| Field | Value |
|-------|-------|
| **Engine Version** | Unreal Engine 5.7 |
| **Release Date** | November 2025 |
| **Project Pinned** | 2026-05-13 |
| **Last Docs Verified** | 2026-05-13 |
| **LLM Knowledge Cutoff** | May 2025 |
| **Risk Level** | HIGH — 5.5, 5.6, 5.7 모두 LLM 학습 데이터 이후 |

## Knowledge Gap Warning

LLM 학습 데이터는 UE5 약 5.3~5.4 초반까지 커버합니다. 5.5, 5.6, 5.7은 학습 데이터에 포함되지 않았거나 불완전합니다. UE API 사용 시 반드시 이 디렉토리의 레퍼런스를 먼저 확인하세요.

## Post-Cutoff Version Timeline

| 버전 | 출시 | Risk Level | 주요 테마 |
|------|------|------------|-----------|
| 5.4 | 2024년 4월 | MEDIUM | PCG Framework v2, Nanite Tessellation, Motion Matching 개선 |
| 5.5 | 2024년 11월 | HIGH | MegaLights, Enhanced Input 개선, PlayerMappableOptions 폐기 |
| 5.6 | 2025년 4월 | HIGH | Animation 시스템 개선, 렌더링 최적화 |
| 5.7 | 2025년 11월 | HIGH | Nanite Foliage, PCG Production-Ready, Linux SDL2→SDL3 전환 |

## Verified Sources

- 공식 릴리즈 노트: https://dev.epicgames.com/documentation/en-us/unreal-engine/unreal-engine-5-7-release-notes
- 마이그레이션 가이드: https://dev.epicgames.com/documentation/en-us/unreal-engine/unreal-engine-5-migration-guide
- 버전 업그레이드 가이드: https://dev.epicgames.com/documentation/en-us/unreal-engine/updating-projects-to-newer-versions-of-unreal-engine
- 신규 기능: https://dev.epicgames.com/documentation/en-us/unreal-engine/whats-new

## Key Breaking Changes (5.3 → 5.7)

### 5.5 주요 변경

- **PlayerMappableOptions 폐기** → UEnhancedInputUserSettings 사용으로 대체
- Enhanced Input 키 매핑 관련 API 변경 포함

### 5.7 주요 변경

- **Linux SDL2 → SDL3 전환** — Linux 빌드 타겟이 있을 경우 영향
- **Nanite Foliage** — 실험적 기능, 기존 foliage 워크플로우 검토 필요
- **PCG Framework** — Production-Ready 승격, API 안정화

## Known Deprecated APIs (Training Cutoff 이후)

| 폐기된 API | 대체 API | 버전 |
|-----------|---------|------|
| PlayerMappableOptions 관련 함수들 | UEnhancedInputUserSettings | 5.5 |

## Agent Instructions

이 프로젝트의 모든 코드 작업 에이전트는:
1. UE5 API 제안 전 이 파일을 확인할 것
2. 불확실한 API는 WebSearch로 공식 문서 검증 후 사용
3. 5.5 이후 변경된 Input 관련 API는 반드시 최신 문서 참조
4. Blueprint 노드 이름이 변경됐을 수 있으므로 UI 관련 작업 시 주의
