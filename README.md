<div align="center">
    <img src="https://capsule-render.vercel.app/api?type=waving&color=84f0ee&height=180&text=Unity%20Developer&animation=&fontColor=000000&fontSize=40" />
</div>

<div align="center"> 
    <h2 style="border-bottom: 1px solid #21262d; color: #c9d1d9;"> 👋 관련 업무 </h2>  
    <div style="font-weight: 700; font-size: 15px; text-align: center; color: #c9d1d9;">
        안녕하세요! 유니티 개발자 최민준입니다.<br>
    </div>
</div>

<br><br>

<div align="center"> 
    <h2 style="border-bottom: 1px solid #21262d; color: #c9d1d9;"> 🛠️ 개발 경력 </h2> 
    <div style="font-weight: 700; font-size: 15px; text-align: center; color: #c9d1d9;">
        • 유니티 개발 시작 2021년 9월 (현재 4년차)
    </div>
</div>

<br><br>

<div align="center"> 
    <h2 style="border-bottom: 1px solid #21262d; color: #c9d1d9;"> 🎮 진행 프로젝트 </h2> 
</div>

---

---


<br><br>

---


# 🎮 퍼즐 게임 (팀 프로젝트, 외부 개발자 2인 협업)

🔗 [GitHub Repository](https://github.com/dreamerschoiminjun/puzzle-game)  
⏱ 진행 기간: 2024.03.01 ~ 2024.10.31  
장르: 퍼즐  
참여 인원: 외부 개발자 2인 팀  
역할: 캐릭터 제어 시스템, 퍼즐 색상 로직, UI 연동, 컬러 카운터 시스템, 엔딩 연출 담당  
주요 구현 요소: FSM 기반 이동, 컬러 기반 스테이지 클리어 구조, 폭발 연출

---

### 🔧 주요 시스템 및 코드 설계

#### ▶ 캐릭터 이동 & 조작 (NewPlayer.cs)

TPS 스타일의 자유 이동 구현 및 애니메이션 상태 제어 분리 설계

- Aim() – 마우스 회전값을 기반으로 카메라 각도와 캐릭터 방향 제어  
- Move() – 입력 방향에 따라 이동 벡터 계산 및 속도 적용  
- Jump() – 점프 입력 처리, 착지 여부는 OnCollisionEnter()에서 복구  
- Animator 파라미터 (isWalking, isRunning)를 이동 상태에 따라 제어

✅ 카메라와 캐릭터 이동 벡터를 분리하여 시점 기반의 자유 이동 구현  
✅ Input 처리, 물리 이동, 애니메이션 상태 제어를 기능별로 분리하여 유지보수성 강화

---

#### ▶ 컬러 체인지 퍼즐 시스템 (ColorChanger.cs)

색상이 주기적으로 변화하며, 퍼즐 조건에 사용될 수 있도록 설계된 상태 머신 구성

- InvokeRepeating() – 일정 시간 간격으로 색상 순환 메서드 반복 실행  
- ChangeColor() – 색상 배열을 순회하며 오브젝트 색상 변경  
- GetCurrentColor() – 현재 색상을 외부에서 참조할 수 있도록 반환

✅ 색상 상태를 외부에서 읽을 수 있는 getter 제공으로 구조화된 의존성 설계  
✅ 색상 순환을 자동화하여 퍼즐과 연동되는 상태 기반 로직 구현 가능

---

#### ▶ 퍼즐 해석 & 스테이지 클리어 조건 (ColorCounter.cs)

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

#### ▶ 엔딩 폭발 이펙트 및 시각 효과 (ExplosionEffect.cs)

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

- FSM(상태 기반) 구조와 실시간 입력 반영을 조합한 자유 이동/조작 시스템  
- 실시간 상태 순환 퍼즐 오브젝트와 사용자 입력 상호작용을 통한 논리 기반 퍼즐 처리  
- UI 실시간 연동 + 색상 비교 기반 클리어 로직 설계  
- 실제 게임 플레이와 상호작용하는 물리 기반 폭발 이펙트 구현
<br><br>
---


<br><br>

---

# 🎮 FPS 미니게임 (개인 프로젝트)

🔗 [GitHub Repository](https://github.com/dreamerschoiminjun/fps-minigame)  
⏱ 진행 기간: 2024.09.01 ~ 2024.09.30  
장르: 1인칭 FPS + 서바이벌  
참여 인원: 단독  

기획/프로그래밍/시스템 구성을 모두 단독으로 구현  
플레이어는 총기를 활용해 적을 처치하며 생존 시간을 늘려 점수를 획득하고, 주변에서 랜덤하게 등장하는 아이템으로 능력을 강화할 수 있음

---

### 🔧 주요 시스템 및 코드 설계

▶ 캐릭터 이동 & 전투 시스템 (player.cs)

FPS 형태 캐릭터 이동 및 조준, 발사, 애니메이션 제어 포함한 전투 구현  
GetInput() – 키보드 입력 수집 (Horizontal, Vertical)  
Aim() – 마우스 회전값 기반 TPS 시점 조정 및 카메라 각도 제한  
Move() – 입력 방향 + 카메라 방향 기반 이동 벡터 생성  
Jump() – 점프 입력 시 AddForce()로 물리 기반 점프 적용  
BulletAttack() – 마우스 입력 시 발사 애니메이션, 쿨타임 체크, 총알 발사  
ShootProjectile() – Raycast로 명중 지점 계산 후 총알 생성 및 방향 지정

✅ 마우스 기준 시점 연동 이동 구현  
✅ 총알 방향은 Raycast 기반 정확 타겟팅 적용  
✅ 총기 사운드, 애니메이션, 아이템 효과 포함한 발사 로직 설계

---

▶ 총알 처리 로직 (Bullet.cs)  
총알의 수명 및 충돌 판정과 데미지 적용 로직 구현

Start() – 플레이어의 CharacterStats로부터 공격력 연동  
FixedUpdate() – 일정 시간 경과 후 총알 자동 제거  
OnTriggerEnter() – 적과 충돌 시 데미지 적용 및 파괴

✅ 충돌 대상에 따라 EnemyStats / AlienStats로 분기 처리  
✅ CharacterStats와 연동되어 실시간 스탯 반영

---

▶ 캐릭터 상태 관리 및 UI (CharacterStats.cs)

체력, 이동속도, 공격력, 점프력 등 플레이어 스탯 구성  
UpdateHealthUI() – Scrollbar + TextMeshPro를 통한 체력 UI 실시간 반영  
healthRegenTimer – 일정 시간마다 체력 자동 회복  
사망 시 UI 출력 및 Time.timeScale 0 처리

✅ UI와 연동된 체력 상태 관리 구조  
✅ 자연스러운 회복, 죽음 조건, UI 반응 포함

---

▶ 아이템 시스템 (Item.cs, GameItem.cs)

충돌 기반 효과 발동 및 지속 시간 조절 구조 설계  
OnTriggerEnter() – 충돌 시 아이템 효과 자동 발동  
ApplyEffect() – ID 기반으로 효과 분기 처리  
효과는 Coroutine을 통해 일정 시간 후 자동 복구

✅ 7종 아이템 효과 (무적, 회복, 속도 증가, 공격력 강화 등)  
✅ 효과별 지속 시간, 복구 처리를 코루틴으로 구현

---

▶ 낙하 비행기 연출 (PlaneCrash.cs, PlaneGravity.cs)

SpawnPlane() – 일정 시간마다 플레이어 주변에 비행기 생성  
PlaneGravity.cs – 중력처럼 낙하하며, 특정 높이 이하 시 제거

✅ 랜덤성과 물리 반응이 결합된 배경 연출  
✅ 시각적/위험 요소로서의 기능 동시에 수행

---

▶ 적 생성 및 공격 구조 (EnemySpawn.cs, EnemyStats.cs, Beam.cs)

일정 시간마다 플레이어 주변 랜덤 위치에 적 등장  
EnemyStats – 데미지 처리 및 사망 시 점수 증가  
Beam.cs – VolumetricLine 기반 시각 효과 + Raycast로 지속 데미지

✅ 사망 시 즉시 랜덤 위치로 리스폰 → 끊김 없는 서바이벌 흐름 유지  
✅ 시각 이펙트 + 피해를 주는 광선형 공격 구현

---

▶ 점수 시스템 및 UI 연동 (Score.cs, UIManager.cs, ButtonActions.cs)

생존 시간 및 적 처치 수 기반 점수 증가  
TextMeshPro, Slider 등을 통한 실시간 UI 출력  
버튼 클릭 시 씬 전환, 게임 종료, 키 가이드 토글 등 구현

✅ 전투 성과가 즉각 UI에 반영되는 구조  
✅ 기능별 분리된 UI 구조

---

▶ BGM 및 사운드 구성 (mainstagebgm.cs, menubgm.cs, player.cs)

스테이지/메뉴에 따라 다른 BGM 재생  
총기 발사 시 PlayOneShot()으로 사운드 출력

✅ 씬별 BGM 분리로 몰입감 강화  
✅ 총기 사운드를 통한 타격감 피드백 구현

---

### ✨ 핵심 기술 요약

- Unity 기반 전투, 이동, UI, 점수, 아이템, 사운드 등 게임의 전체 흐름을 1인 설계 및 개발  
- Raycast 기반 FPS 타겟팅, 애니메이션 연동, 스탯 설계, 효과 반영 등 실제 게임과 유사한 로직 구성  
- 모든 시스템을 클래스 단위로 분리하여 확장성과 유지보수성 확보
<br><br>
---

# 🎮 TPS 로그라이크 게임 (외주 디자이너 1인 협업)

🔗 GitHub Repository  
⏱ 진행 기간: 2022.09.20 ~ 2025.03.01  
장르: TPS 로그라이크 / 혼자 개발

외주 디자이너와 협력하여 시스템 기획 및 전투, 적 AI, 아이템, UI까지 전반적인 게임 구조를 단독 개발.  
TPS 시점 전투, 상태이상, 아이템 효과 등 로그라이크 특유의 반복성과 성장 구조를 중심으로 구현.

---

## 🔧 주요 시스템 및 코드 설계

### 🎮 캐릭터 시스템

**주요 기능(CharacterStats.cs)**  
Start() - 초기 체력/재화 설정  
AddToInventory() - 인벤토리 아이템 추가  
Update() - 주기적 체력 회복  
RegenerateHealth() - 체력 자동 회복 로직  

✅ 체력, 공격력, 속도, 스킬 쿨타임 등 전투 및 이동에 필요한 핵심 스탯 관리  
✅ 아이템, 상태이상, 재화, 치명타 등 다양한 속성 통합 구조  

**주요 기능(Player.cs)**  
Start() - 컴포넌트 초기화 및 상태 설정  
Update() - 입력 및 상태 제어 루프  
Move(), Aim(), Jump(), Dodge() - TPS 조작 로직  
HandleWeaponSwitch() - 무기 전환 (근접 ↔ 원거리)  

✅ TPS 시점 기준 이동, 회피, 점프, 조준, 무기 전환  
✅ 근/원거리 무기 방식에 따라 입력 처리 및 애니메이션 연동  

**주요 기능(KeyBindingManager.cs)**  
Start() - 기본 키 설정 및 UI 초기화  
StartRebinding() - UI 클릭 시 키 변경 대기  
WaitForKeyInput() - 입력 수신 및 중복 체크  
SaveKey(), LoadKey() - PlayerPrefs 연동  

✅ 사용자 지정 키 매핑 지원, 실시간 변경 및 저장 가능  
✅ 기능별 키 설정 구조화 + UI 연동  

---

### 🗡️ 전투 시스템

**주요 기능(MeleeAttackModule.cs)**  
HandleCombo() - 3타 콤보 및 연계 공격 처리  
TriggerCombo() - 콤보별 애니메이션 처리  
CancelMeleeAttack(), ResetMeleeCombo() - 공격 상태 초기화  

✅ 3타 콤보 공격 구조  
✅ 보조공격/스킬 연계 가능  
✅ 애니메이션 트리거와 타격 판정 분리  

**주요 기능(RangedAttackModule.cs)**  
HandleRangedAttack() - 발사체 기반 일반 공격  
HandleSkill() - 스킬 발사체 전환 및 스탯 적용  
ShootProjectile() - Raycast 기반 조준 및 발사  

✅ 발사체 기반 원거리 공격 및 스킬 모드 전환  
✅ 스탯 기반 발사력, 쿨타임, 독속성 연계  

**주요 기능(PlayerWeaponTrigger.cs)**  
EnableHit(), DisableHit() - 애니메이션 이벤트 기반 타격 제어  
OnTriggerEnter() - 충돌 시 적 체력 감소  

✅ 근접 무기와 적 충돌 감지  
✅ 애니메이션 타이밍에 맞춘 타격 처리  

---

### 🧠 적 시스템

**주요 기능(enemymove.cs)**  
Update() - 거리 체크 및 추적/공격 상태 관리  
ChasePlayer() - NavMesh 기반 이동  
PerformAttack() - 공격 애니메이션 + 데미지 처리  
HandleDeath() - 사망 애니메이션, 드랍, 제거  

✅ NavMesh를 활용한 자동 추적 및 공격  
✅ 사망 후 드랍 및 제거까지 연동  

**주요 기능(EnemyStats.cs)**  
Start() - 초기 체력 설정  
상태 필드 - 체력, 공격력, 상태이상 누적 및 지속 시간  

✅ 적의 체력/공격력/속도와 상태이상 누적 수치 관리  
✅ 상태이상 지속시간 및 Tick 주기 별도 설정 가능  

**주요 기능(Element.cs)**  
CheckAndApplyStatusEffects() - 누적 수치 100 도달 시 상태 적용  
HandleStatusEffects() - 상태이상별 Tick 데미지 처리  
ApplyXXXStatus(), ApplyXXXDamage() - 효과별 처리  

✅ 화상, 감전, 중독, 출혈, 빙결 등 상태이상 시스템  
✅ 이펙트 프리팹과 데미지 로직 통합  

**주요 기능(Enemy.cs)**  
DropItem() - 확률 기반 아이템 드랍  
DropItemOfType() - 드랍 아이템 구성  

✅ 확률 기반 아이템 드랍 구조  
✅ 캐릭터 스탯 기반 드랍률 보정 지원  

**주요 기능(KillMonster.cs)**  
InitializeMonsterDictionary() - 스테이지 별 몬스터 초기화  
IncreaseMonsterKillCount() - 처치 수 기록  

✅ 스테이지/종류별 몬스터 처치 수 기록  

---

### 💎 아이템 시스템

**주요 기능(GameItem.cs)**  
ApplyEffect() - 아이템 ID에 따라 스탯 변화 적용  
ApplyItemXXEffect() - 스탯 변경 로직 정의  

✅ 최대 200개까지 확장 가능한 스탯 기반 효과 처리 구조  
✅ 쿨타임 감소, 체력 증가, 속도 증가 등 효과 다양  

**주요 기능(CommonItem.cs)**  
Awake() - 초기화 및 기본 아이템 등록  
ScriptableObject로 등록된 아이템 생성  

✅ 기본 아이템 리스트 관리  
✅ 공통 아이템 정보를 ScriptableObject로 분리  

---

### 🧭 UI 시스템

**주요 기능(HealthBarController.cs, UpdateHealthText.cs)**  
Update() - 체력 비율 및 수치 표시 업데이트  
초록 바 위치, 길이 조절  

✅ 체력 비율 기반 UI + 수치 텍스트 표시  

**주요 기능(UpdateMoney.cs, UpdateSpirit.cs)**  
UpdateMoneyText(), UpdateSpiritText() - 골드/영혼 실시간 출력  

✅ 골드 및 영혼 수치 실시간 표시  

**주요 기능(Timer.cs)**  
Update() - 시간 측정 및 UI 반영  
StartTimer(), StopTimer(), ResetTimer() - 시간 제어  

✅ 게임 플레이 시간 표시 및 리셋/정지 기능 포함  

---

## ✨ 핵심 기술 요약

TPS 시점의 캐릭터 컨트롤, 3타 콤보 시스템, 원거리 발사체 + 스킬, 상태이상 시스템 등을 포함한 로그라이크 게임 설계  
확률 드랍, 스탯 기반 아이템 효과, 상태이상 이펙트, 키 설정 커스터마이징 등 다양한 기능 구현  
모든 시스템을 스크립트별로 분리하여 유지보수성과 확장성을 확보하고, 실제 상업 게임 구조에 맞게 설계됨


---

<br><br>

<h3 align="center">🧑‍💻 사용 언어</h3>
<p align="center"> 
    <a href="https://www.w3schools.com/cs/" target="_blank" rel="noreferrer"> 
        <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/csharp/csharp-original.svg" alt="csharp" width="40" height="40"/> 
    </a> 
</p>
