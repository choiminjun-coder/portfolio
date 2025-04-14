---

👋 관련 업무 </h2>  
안녕하세요! 유니티 개발자 최민준입니다
<br><br>

• 유니티 개발 시작 2021년 9월 (현재 4년차)

<br><br>
---

🛠️ 본 포트폴리오는 직접 구현한 기능 및 시스템만 정리하였습니다.

---

# 🎮 진행 프로젝트



# 🧩 퍼즐 게임 (팀 프로젝트, 개발자 2인 협업)

🔗 [GitHub Repository](https://github.com/dreamerschoiminjun/puzzle-game)  
⏱ 진행 기간: 2024.03.01 ~ 2024.10.31  
장르: 퍼즐  

총 인원: 개발자 3인

프로젝트 스타일: 유니티 기본 시스템 실습 · 외부 에셋 연동 · 협업 기반 기능 구현 프로젝트

주요 구현 요소
1. 캐릭터 이동 시스템 (TPS 방식 이동)
2. 퍼즐 스테이지 로직 (색상 변화, 조건 체크, 클리어 시스템, UI 연동)
3. 엔딩 연출 (폭발 이펙트 및 시각 효과 포함)

---

### 🔧 주요 시스템 및 코드 설계

#### ▶ 🕹️ 캐릭터 이동 시스템 (NewPlayer.cs)

TPS 스타일의 자유 이동 구현 및 애니메이션 상태 제어 분리 설계

- Aim() – 마우스 회전값을 기반으로 카메라 각도와 캐릭터 방향 제어  
- Move() – 입력 방향에 따라 이동 벡터 계산 및 속도 적용  
- Jump() – 점프 입력 처리, 착지 여부는 OnCollisionEnter()에서 복구  
- Animator 파라미터 (isWalking, isRunning)를 이동 상태에 따라 제어

✅ 카메라와 캐릭터 이동 벡터를 분리하여 시점 기반의 자유 이동 구현  
✅ Input 처리, 물리 이동, 애니메이션 상태 제어를 기능별로 분리하여 유지보수성 강화

---

#### ▶ 🧩 색상 순환 퍼즐 시스템 (ColorChanger.cs)

색상이 주기적으로 변화하며, 퍼즐 조건에 사용될 수 있도록 설계된 상태 머신 구성

- InvokeRepeating() – 일정 시간 간격으로 색상 순환 메서드 반복 실행  
- ChangeColor() – 색상 배열을 순회하며 오브젝트 색상 변경  
- GetCurrentColor() – 현재 색상을 외부에서 참조할 수 있도록 반환

✅ 색상 상태를 외부에서 읽을 수 있는 getter 제공으로 구조화된 의존성 설계  
✅ 색상 순환을 자동화하여 퍼즐과 연동되는 상태 기반 로직 구현 가능

---

#### ▶ 🧠 퍼즐 조건 및 클리어 시스템 (ColorCounter.cs)

색상과 태그 일치 여부 기반으로 퍼즐 카운트를 계산하고 UI 및 클리어 조건 연동

- OnTriggerEnter() – 플레이어가 색상 블록에 접근 시 UI 활성화 및 태그 저장  
- Update() – E/R 키 입력 처리 및 조건에 따라 카운트 증가/초기화 실행  
- IncrementColorCount() – 현재 색상과 태그가 일치할 때 해당 색상 카운트 증가  
- ResetCounts() – 모든 색상 카운트를 초기화  
- GetCountDisplayText() – UI에 표시할 색상 카운트 문자열 반환  
- CheckStageClearCondition() – 조건 충족 시 클리어 처리, 초과 시 리셋

✅ 색상 태그/값 비교 기반의 퍼즐 논리 구현, UI와 연동되어 직관적 피드백 제공  
✅ 클리어 조건 및 예외(초과) 상황을 함수로 분리하여 관리 용이성 확보

---

#### ▶ 💥 엔딩 연출 시스템 (ExplosionEffect.cs)

물리 연동 기반 폭발 효과 구현으로 연출과 게임 플레이를 연결

- OnCollisionEnter() – 충돌 감지 시 폭발 연출 메서드 호출  
- Explode()  
  - Instantiate() – 폭발 이펙트 생성  
  - transform.localScale *= – 이펙트 스케일 확대  
  - Physics.OverlapSphere() – 범위 내 오브젝트 탐색  
  - AddExplosionForce() – 물리 반응 적용  
- OnDrawGizmos() – 디버깅용 폭발 범위 시각화

✅ 단순 연출이 아닌 실제 물리 반응과 연동된 연출 시스템 구성  
✅ 가시성 확보를 위한 개발용 Gizmo 처리도 병행하여 디버깅 편의성 향상

---

### ✨ 핵심 기술 요약

1. FSM(상태 기반) 구조와 실시간 입력 반영을 조합한 자유 이동/조작 시스템 구현
2. 색상 순환 로직과 태그 기반 비교를 활용한 논리형 퍼즐 구성
3. 퍼즐 해석, UI 연동, 클리어 조건 등을 함수로 분리하여 구조화
4. 실제 물리 반응과 연계된 폭발 이펙트를 활용한 엔딩 연출
5. 이동, 퍼즐, UI 연동 등을 모듈 단위로 나누어 유지보수성 확보

---

<br><br>


---

# 🔫 FPS 미니게임 (팀 프로젝트, 개발자 1인 협업)

🔗 [GitHub Repository](https://github.com/dreamerschoiminjun/fps)  
⏱ 진행 기간: 2024.09.01 ~ 2024.09.30  
장르: 1인칭 FPS + 서바이벌  
총 인원: 개발자 2인 
프로젝트 스타일: 무료 에셋 제한 조건, 시스템 직접 구현 및 실무 중심 멘토링형 프로젝트

주요 구현 요소
1. 캐릭터 시스템
2. 전투 시스템
3. 적 시스템
4. 아이템 시스템
5. UI 및 사운드 시스템
---

### 🔧 주요 시스템 및 코드 설계

▶ 🕹️ 캐릭터 시스템 (player.cs)

FPS 형태 캐릭터 이동 및 조준, 발사, 애니메이션 제어 포함한 전투 구현  
GetInput() – 키보드 입력 수집 (Horizontal, Vertical)  
Aim() – 마우스 회전값 기반 TPS 시점 조정 및 카메라 각도 제한  
Move() – 입력 방향 + 카메라 방향 기반 이동 벡터 생성  
Jump() – 점프 입력 시 AddForce()로 물리 기반 점프 적용  


✅ 총알 방향은 Raycast 기반 정확 타겟팅 적용  
✅ 총기 발사 애니메이션과 스탯 반영 공격력 처리  
✅ 충돌 대상별 데미지 처리 분기 구성 (EnemyStats / AlienStats)  


---

▶ 🔫 전투 시스템 (Bullet.cs)  
총알의 수명 및 충돌 판정과 데미지 적용 로직 구현
BulletAttack() – 마우스 입력 시 발사 애니메이션, 쿨타임 체크, 총알 발사  
ShootProjectile() – Raycast로 명중 지점 계산 후 총알 생성 및 방향 지정
Start() – 플레이어의 CharacterStats로부터 공격력 연동  
FixedUpdate() – 일정 시간 경과 후 총알 자동 제거  
OnTriggerEnter() – 적과 충돌 시 데미지 적용 및 파괴

✅ 총알 방향은 Raycast 기반 정확 타겟팅 적용  
✅ 총기 발사 애니메이션과 스탯 반영 공격력 처리  
✅ 충돌 대상별 데미지 처리 분기 구성 (EnemyStats / AlienStats)  

---

▶ 	👾 적 시스템 (EnemySpawn.cs, EnemyStats.cs, Beam.cs)

일정 시간마다 플레이어 주변 랜덤 위치에 적 등장  
EnemyStats – 데미지 처리 및 사망 시 점수 증가  
Beam.cs – VolumetricLine 기반 시각 효과 + Raycast로 지속 데미지

✅ 사망 시 즉시 랜덤 위치로 리스폰 → 끊김 없는 서바이벌 흐름 유지  
✅ 시각 이펙트 + 피해를 주는 광선형 공격 구현  
✅ 점수 시스템과 연계된 적 처치 로직 포함  


---

▶ 💎 아이템 시스템 (Item.cs, GameItem.cs)

충돌 기반 효과 발동 및 지속 시간 조절 구조 설계  
OnTriggerEnter() – 충돌 시 아이템 효과 자동 발동  
ApplyEffect() – ID 기반으로 효과 분기 처리  
효과는 Coroutine을 통해 일정 시간 후 자동 복구

✅ 7종 아이템 효과 (무적, 회복, 속도 증가, 공격력 강화 등)  
✅ 효과별 지속 시간, 복구 처리를 코루틴으로 구현  
✅ 충돌만으로 발동되는 직관적 아이템 시스템  


---

▶ 🔊 UI 및 사운드 시스템 (Score.cs, UIManager.cs, ButtonActions.cs, mainstagebgm.cs, menubgm.cs, player.cs)

생존 시간 및 적 처치 수 기반 점수 증가
TextMeshPro, Slider 등을 통한 실시간 UI 출력
버튼 클릭 시 씬 전환, 게임 종료, 키 가이드 토글 등 구현
스테이지/메뉴에 따라 다른 BGM 재생

✅ 전투 성과가 즉각 UI에 반영되는 구조  
✅ 기능별 분리된 UI 시스템으로 유지보수 용이  
✅ 씬별 BGM 분리 + 총기 사운드를 통한 타격감 피드백 구현  

---

### ✨ 핵심 기술 요약

1. Raycast 기반 조준 시스템과 총알 발사를 포함한 FPS 전투 구조 구현
2. 총기 사운드, 애니메이션, 공격력 강화 아이템 등과 연계된 전투 흐름 설계
3. 랜덤 낙하형 연출(비행기), UI 연동 점수 시스템 등 몰입도 높은 게임 구성
4. 7종 아이템 효과를 Coroutine으로 제어하여 전투의 변칙성과 전략성 부여
5. 모든 시스템을 스크립트 단위로 분리하여 단독 개발자 관점의 구조화 설계
---

<br><br>


---

# 🎮 TPS 로그라이크 게임 (외주 디자이너 1인 협업)

⏱ 진행 기간: 2022.09.20 ~ 2025.03.01  
장르: 로그라이크

총인원: 개발자 1인, 디자이너 1인

스타일: Unity 입문부터 함께한 대표 프로젝트, 창업 및 상업화를 목표로 외부 자원과 자금을 적극 활용한 실전형 개발 프로젝트

주요 구현 요소
1. 캐릭터 시스템
2. 전투 시스템
3. 적 시스템
4. 아이템 시스템
5. UI 시스템

---

## 🔧 주요 시스템 및 코드 설계

### 🎮 캐릭터 시스템

** 캐릭터 스탯 관리(CharacterStats.cs)**  
Start() - 초기 체력/재화 설정  
AddToInventory() - 인벤토리 아이템 추가  
Update() - 주기적 체력 회복  
RegenerateHealth() - 체력 자동 회복 로직  

✅ 체력, 공격력, 속도, 스킬 쿨타임 등 전투 및 이동에 필요한 핵심 스탯 관리  
✅ 아이템, 상태이상, 재화, 치명타 등 다양한 속성 통합 구조  

** TPS 방식의 캐릭터 조작(Player.cs)**  
Start() - 컴포넌트 초기화 및 상태 설정  
Update() - 입력 및 상태 제어 루프  
Move(), Aim(), Jump(), Dodge() - TPS 조작 로직  
HandleWeaponSwitch() - 무기 전환 (근접 ↔ 원거리)  

✅ TPS 시점 기준 이동, 회피, 점프, 조준, 무기 전환  
✅ 근/원거리 무기 방식에 따라 입력 처리 및 애니메이션 연동  

** 입력 및 조작 시스템(KeyBindingManager.cs)**  
Start() - 기본 키 설정 및 UI 초기화  
StartRebinding() - UI 클릭 시 키 변경 대기  
WaitForKeyInput() - 입력 수신 및 중복 체크  
SaveKey(), LoadKey() - PlayerPrefs 연동  

✅ 사용자 지정 키 매핑 지원, 실시간 변경 및 저장 가능  
✅ 기능별 키 설정 구조화 + UI 연동  

---

### 🗡️ 전투 시스템

** 근접 공격 시스템 (MeleeAttackModule.cs)**  
HandleCombo() - 3타 콤보 및 연계 공격 처리  
TriggerCombo() - 콤보별 애니메이션 처리  
CancelMeleeAttack(), ResetMeleeCombo() - 공격 상태 초기화  

✅ 3타 콤보 공격 구조  
✅ 보조공격/스킬 연계 가능  
✅ 애니메이션 트리거와 타격 판정 분리  

** 원거리 공격 시스템(RangedAttackModule.cs)**  
HandleRangedAttack() - 발사체 기반 일반 공격  
HandleSkill() - 스킬 발사체 전환 및 스탯 적용  
ShootProjectile() - Raycast 기반 조준 및 발사  

✅ 발사체 기반 원거리 공격 및 스킬 모드 전환  
✅ 스탯 기반 발사력, 쿨타임, 독속성 연계  

** 근접 무기 충돌 감지 시스템 (PlayerWeaponTrigger.cs)**  
EnableHit(), DisableHit() - 애니메이션 이벤트 기반 타격 제어  
OnTriggerEnter() - 충돌 시 적 체력 감소  

✅ 근접 무기와 적 충돌 감지  
✅ 애니메이션 타이밍에 맞춘 타격 처리  

---

###  👾 적 시스템

**적 추적 및 공격 AI 시스템(enemymove.cs)**  
Update() - 거리 체크 및 추적/공격 상태 관리  
ChasePlayer() - NavMesh 기반 이동  
PerformAttack() - 공격 애니메이션 + 데미지 처리  
HandleDeath() - 사망 애니메이션, 드랍, 제거  

✅ NavMesh를 활용한 자동 추적 및 공격  
✅ 사망 후 드랍 및 제거까지 연동  

**적 상태 및 스탯 관리(EnemyStats.cs)**  
Start() - 초기 체력 설정  
상태 필드 - 체력, 공격력, 상태이상 누적 및 지속 시간  

✅ 적의 체력/공격력/속도와 상태이상 누적 수치 관리  
✅ 상태이상 지속시간 및 Tick 주기 별도 설정 가능  

**상태이상 적용 시스템(Element.cs)**  
CheckAndApplyStatusEffects() - 누적 수치 100 도달 시 상태 적용  
HandleStatusEffects() - 상태이상별 Tick 데미지 처리  
ApplyXXXStatus(), ApplyXXXDamage() - 효과별 처리  

✅ 화상, 감전, 중독, 출혈, 빙결 등 상태이상 시스템  
✅ 이펙트 프리팹과 데미지 로직 통합  

**적 사망 및 드랍 시스템(Enemy.cs)**  
DropItem() - 확률 기반 아이템 드랍  
DropItemOfType() - 드랍 아이템 구성  

✅ 확률 기반 아이템 드랍 구조  
✅ 캐릭터 스탯 기반 드랍률 보정 지원  

**몬스터 처치 통계 시스템(KillMonster.cs)**  
InitializeMonsterDictionary() - 스테이지 별 몬스터 초기화  
IncreaseMonsterKillCount() - 처치 수 기록  

✅ 스테이지/종류별 몬스터 처치 수 기록  

---

### 💎 아이템 시스템

**아이템 효과 처리(GameItem.cs)**  
ApplyEffect() - 아이템 ID에 따라 스탯 변화 적용  
ApplyItemXXEffect() - 스탯 변경 로직 정의  

✅ 최대 200개까지 확장 가능한 스탯 기반 효과 처리 구조  
✅ 쿨타임 감소, 체력 증가, 속도 증가 등 효과 다양  

**아이템 등록 및 초기화 (CommonItem.cs)**  
Awake() - 초기화 및 기본 아이템 등록  
ScriptableObject로 등록된 아이템 생성  

✅ 기본 아이템 리스트 관리  
✅ 공통 아이템 정보를 ScriptableObject로 분리  

---

### 🧭 UI 시스템

**체력 UI 시스템(HealthBarController.cs, UpdateHealthText.cs)**  
Update() - 체력 비율 및 수치 표시 업데이트  
초록 바 위치, 길이 조절  

✅ 체력 비율 기반 UI + 수치 텍스트 표시  

**자원 UI 시스템(UpdateMoney.cs, UpdateSpirit.cs)**  
UpdateMoneyText(), UpdateSpiritText() - 골드/영혼 실시간 출력  

✅ 골드 및 영혼 수치 실시간 표시  

**플레이 타이머 시스템(Timer.cs)**  
Update() - 시간 측정 및 UI 반영  
StartTimer(), StopTimer(), ResetTimer() - 시간 제어  

✅ 게임 플레이 시간 표시 및 리셋/정지 기능 포함  

---

## ✨ 핵심 기술 요약

1. TPS 시점 기반의 이동, 회피, 무기 전환 시스템을 모듈화하여 구현
2. 입력 및 스탯에 따라 근/원거리 공격 방식 전환 가능하도록 설계
3. 콤보 기반 근접 공격과 Raycast 기반 원거리 조준 및 발사 시스템 구축
4. 상태이상 누적 수치와 Tick 데미지를 적용한 전투 구조 구현
5. 스탯 기반 아이템 효과 적용 및 ScriptableObject 방식의 데이터 관리
6. 키 바인딩, UI 연동 등 사용자 설정 기능을 포함한 유저 편의성 확보
7. 전반적인 시스템을 클래스 단위로 분리하여 유지보수성과 확장성 강화

---

## 🧑‍💻 사용 언어

- **C#**  
  Unity 기반 게임 시스템 전반을 구성하는 주 프로그래밍 언어로 사용
  
  ---

## 🧰 사용 기술 요약

- 🎮 **Unity**  
  FSM, Animator, Coroutine, Raycast, NavMesh 등 Unity의 주요 기능을 활용한 시스템 개발

- 💻 **C#**  
  클래스 단위 모듈화, 인터페이스 활용, 확장성을 고려한 구조 설계

- 🔧 **GitHub**  
  버전 관리, 이슈 관리, 협업 흐름에 기반한 커밋 및 PR 관리 경험
  
  ---
