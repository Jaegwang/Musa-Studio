# Technical Preferences

<!-- Populated by /setup-engine. Updated as the user makes decisions throughout development. -->
<!-- All agents reference this file for project-specific standards and conventions. -->

## Engine & Language

- **Engine**: Unreal Engine 5.7
- **Language**: C++ (primary), Blueprint (gameplay prototyping)
- **Rendering**: [TO BE CONFIGURED — Lumen/Nanite 활성화 여부, Forward/Deferred 선택]
- **Physics**: Chaos (UE5 기본)

## Input & Platform

<!-- Written by /setup-engine. Read by /ux-design, /ux-review, /test-setup, /team-ui, and /dev-story -->
<!-- to scope interaction specs, test helpers, and implementation to the correct input methods. -->

- **Target Platforms**: PC (Steam)
- **Input Methods**: Gamepad, Keyboard/Mouse
- **Primary Input**: Gamepad
- **Gamepad Support**: Full
- **Touch Support**: None
- **Platform Notes**: 쿼터뷰 액션 ARPG — 게임패드 기준 UI/UX 설계. 모든 UI는 D-pad/스틱 탐색 지원 필요. hover-only 인터랙션 금지.

## Naming Conventions

- **Classes**: Prefix+PascalCase — Actor(`A`), Object(`U`), Struct(`F`), Interface(`I`) (예: `AMusaCharacter`, `UDamageDeliveryComponent`, `FCharacterStats`)
- **Variables**: PascalCase (예: `MoveSpeed`, `CurrentHealth`)
- **Booleans**: `b` prefix + PascalCase (예: `bIsAlive`, `bCanAttack`, `bIsGrounded`)
- **Events/Delegates**: DECLARE_DYNAMIC_MULTICAST_DELEGATE 매크로; 이름은 PascalCase (예: `OnHealthChanged`, `OnEnemyKilled`)
- **Files**: PascalCase, 클래스명 매칭, prefix 제외 (예: `MusaCharacter.h`, `MusaCharacter.cpp`)
- **Blueprints/Levels**: PascalCase, 타입 prefix 포함 (예: `BP_MusaCharacter`, `L_TestLevel`, `WBP_HUD`)
- **Constants**: PascalCase (예: `MaxHealth`, `DefaultMoveSpeed`), 매크로는 ALL_CAPS

## Performance Budgets

- **Target Framerate**: 60fps
- **Frame Budget**: 16.6ms
- **Draw Calls**: 2000 (비-Nanite 메시 기준; Nanite 메시는 자체 예산 적용)
- **Memory Ceiling**: 8GB VRAM / 16GB RAM (PC 권장 사양 기준)

## Testing

- **Framework**: Unreal Automation Testing Framework (빌트인 `FAutomationTestBase`)
- **Minimum Coverage**: 전투 공식, 피 흡수 메커니즘, AI 상태 머신, 캐릭터 파라미터 시스템
- **Required Tests**: Balance formulas, gameplay systems

## Forbidden Patterns

<!-- Add patterns that should never appear in this project's codebase -->
- [None configured yet — 아키텍처 결정이 확정되면 추가]

## Allowed Libraries / Addons

<!-- Add approved third-party dependencies here. Only add when actively integrating, not speculatively. -->
- StateTree (빌트인 플러그인 — .uproject에서 활성화됨)
- GameplayStateTree (빌트인 플러그인 — .uproject에서 활성화됨)
- MotionWarping (빌트인 플러그인 — .uproject에서 활성화됨)
- AnimationWarping (빌트인 플러그인 — .uproject에서 활성화됨)

## Architecture Decisions Log

<!-- Quick reference linking to full ADRs in docs/architecture/ -->
- [No ADRs yet — use /architecture-decision to create one]

## Engine Specialists

<!-- Written by /setup-engine when engine is configured. -->
<!-- Read by /code-review, /architecture-decision, /architecture-review, and team skills -->
<!-- to know which specialist to spawn for engine-specific validation. -->

- **Primary**: unreal-specialist
- **Language/Code Specialist**: ue-blueprint-specialist (Blueprint 그래프) 또는 unreal-specialist (C++)
- **Shader Specialist**: unreal-specialist (전용 셰이더 스페셜리스트 없음 — primary가 Materials 담당)
- **UI Specialist**: ue-umg-specialist (UMG 위젯, CommonUI, 입력 라우팅, 위젯 스타일링)
- **Additional Specialists**: ue-gas-specialist (Gameplay Ability System, 어트리뷰트, 게임플레이 이펙트), ue-replication-specialist (멀티플레이어 추가 시 활성화)
- **Routing Notes**: C++ 아키텍처 및 전반적인 엔진 결정은 primary 호출. Blueprint 그래프 아키텍처는 Blueprint 스페셜리스트. GAS 관련 어빌리티/어트리뷰트 코드는 GAS 스페셜리스트. 모든 UI 구현은 UMG 스페셜리스트.

### File Extension Routing

<!-- Skills use this table to select the right specialist per file type. -->
<!-- If a row says [TO BE CONFIGURED], fall back to Primary for that file type. -->

| File Extension / Type | Specialist to Spawn |
|-----------------------|---------------------|
| 게임 코드 (.cpp, .h files) | unreal-specialist |
| 셰이더 / 머티리얼 (.usf, .ush, Material assets) | unreal-specialist |
| UI / 스크린 (.umg, UMG Widget Blueprints) | ue-umg-specialist |
| 씬 / 레벨 (.umap, .uasset) | unreal-specialist |
| 플러그인 / 네이티브 확장 (.uplugin, 모듈) | unreal-specialist |
| Blueprint 그래프 (.uasset BP classes) | ue-blueprint-specialist |
| 일반 아키텍처 리뷰 | unreal-specialist |
