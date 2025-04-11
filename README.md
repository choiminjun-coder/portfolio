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

### 🔹 퍼즐 게임 (팀 프로젝트, 외부 개발자 2인 협업)  
[🔗 GitHub Repository](https://github.com/dreamerschoiminjun/puzzle-game)  
⏱ 진행 기간: 2024.03.01 ~ 2024.10.31  

---

### 🔷 🎮 프로젝트 개요
- **장르**: 퍼즐 + 액션  
- **참여 인원**: 외부 개발자 2인 팀  
- **역할**: 캐릭터 제어 시스템, 퍼즐 색상 로직, UI 연동, 컬러 카운터 시스템, 엔딩 연출 담당  
- **주요 구현 요소**: FSM 기반 이동, 컬러 기반 스테이지 클리어 구조, 폭발 연출

---

### 🔧 주요 시스템 및 코드 설계

#### ▶ 캐릭터 이동 & 조작 (`NewPlayer.cs`)
- `Aim()` – 마우스 회전값을 기반으로 카메라 각도와 캐릭터 방향 제어  
- `Move()` – 입력 방향에 따라 이동 벡터 계산 및 속도 적용  
- `Jump()` – 점프 입력 처리, 착지 여부는 `OnCollisionEnter()`에서 복구  
- Animator 파라미터 (`isWalking`, `isRunning`)를 이동 상태에 따라 제어

✅ 카메라와 캐릭터 이동 벡터를 분리하여 시점 기반의 자유 이동 구현  
✅ Input 처리, 물리 이동, 애니메이션 상태 제어를 기능별로 분리하여 유지보수성 강화

---

#### ▶ 컬러 체인지 퍼즐 시스템 (`ColorChanger.cs`)
- `InvokeRepeating()` – 일정 시간 간격으로 색상 순환 (`ChangeColor()` 호출)  
- `ChangeColor()` – 색상 배열을 순회하며 MeshRenderer의 `material.color` 변경  
- `GetCurrentColor()` – 현재 색상을 외부에서 참조할 수 있도록 반환

✅ 색상 상태를 외부에서 읽을 수 있는 getter 제공으로 구조화된 의존성 설계  
✅ 색상 순환을 자동화하여 퍼즐과 연동되는 상태 기반 로직 구현 가능

---

#### ▶ 퍼즐 해석 & 스테이지 클리어 조건 (`ColorCounter.cs`)
- `OnTriggerEnter()` – 플레이어가 특정 색상 오브젝트에 접근 시 UI 활성화 및 현재 태그 저장  
- `Update()` – 입력 키(E, R)에 따라 `IncrementColorCount()` 및 `ResetCounts()` 호출  
- `IncrementColorCount()` – 태그와 현재 색상이 일치하면 해당 색상 카운트 증가  
- `ResetCounts()` – 조건 초과 또는 R키 입력 시 모든 색상 카운트 초기화  
- `GetCountDisplayText()` – 현재 색상 카운트를 문자열로 반환해 UI에 표시  
- `CheckStageClearCondition()` – 색상별 카운트가 조건과 일치할 경우 스테이지 클리어 처리

✅ 색상 태그/값 비교 기반의 퍼즐 논리 구현, UI와 연동되어 직관적 피드백 제공  
✅ 클리어 조건 및 예외(초과) 상황을 함수로 분리하여 관리 용이성 확보

---

#### ▶ 엔딩 폭발 이펙트 및 시각 효과 (`ExplosionEffect.cs`)
- `OnCollisionEnter()` – 특정 태그("letter")와 충돌 시 `Explode()` 호출  
- `Explode()`  
  - `Instantiate()` – 지정된 위치에 폭발 이펙트 생성  
  - `transform.localScale *=` – 스케일 배수 적용  
  - `Physics.OverlapSphere()` – 주변 Rigidbody 탐색  
  - `AddExplosionForce()` – 감지된 Rigidbody에 물리 폭발력 적용  
- `OnDrawGizmos()` – 개발 중 폭발 범위를 시각적으로 디버깅 가능

✅ 단순 연출이 아닌 실제 물리 반응과 연동된 연출 시스템 구성  
✅ 가시성 확보를 위한 개발용 Gizmo 처리도 병행하여 디버깅 편의성 향상

---

### ✨ 핵심 역량 요약
- Unity 구조 설계 경험: 기능별로 클래스를 분리하고 목적에 맞게 구성  
- 실전 API 활용 능력: `InvokeRepeating()`, `Animator`, `OverlapSphere()` 등 다양한 기능을 상황에 맞게 적용  
- 협업과 유지보수를 고려한 개발 습관: getter/조건분기/UI 연결 모두 명확하게 설계

---

### 🔹 FPS 미니게임 (개인 프로젝트)  
[🔗 GitHub Repository](https://github.com/dreamerschoiminjun/fps-minigame)  
⏱ 진행 기간: 2024.09.01 ~ 2024.09.30  

**주요 구현 요소:**  
- UFO 등장 및 추적 로직  
- 적의 공격 패턴과 AI 설계  
- 점수 및 체력 관리 시스템  
- 아이템 드랍 로직 + 난이도 조정 구조 설계  
- 전체 흐름 관리 시스템

---

### 🔹 TPS 로그라이크 장르 게임 (디자이너 1인 협업)  
⏱ 진행 기간: 2022.09.20 ~ 2025.03.01  

**주요 개발 중 요소:**  
- TPS 전투 컨트롤러 (카메라 연동, 조작 커스터마이징)  
- 무기/스킬 슬롯 시스템  
- 웨이브 기반 적 생성 구조  
- UI, 저장 시스템, 게임 루프 설계  
※ 본 프로젝트는 실제 출시와 사업화를 목적으로 진행되었습니다.

---

<div align="center"> 
    <h2 style="border-bottom: 1px solid #21262d; color: #c9d1d9;"> 🏅 게임 대회 참가 </h2> 
    <div style="font-weight: 700; font-size: 15px; text-align: center; color: #c9d1d9;">
        <!-- 차후 업데이트 예정 -->
    </div>
</div>

<br><br>

<div align="center"> 
    <h2 style="border-bottom: 1px solid #21262d; color: #c9d1d9;"> 📊 GitHub Stats </h2> 
    <img src="https://github-readme-stats.vercel.app/api?username=dreamerschoiminjun&show_icons=true&theme=radical" alt="dreamerschoiminjun's GitHub Stats" />  
</div>

<br><br>

<h3 align="center">🧑‍💻 사용 언어</h3>
<p align="center"> 
    <a href="https://www.w3schools.com/cs/" target="_blank" rel="noreferrer"> 
        <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/csharp/csharp-original.svg" alt="csharp" width="40" height="40"/> 
    </a> 
</p>

<h3 align="center">🧰 사용 도구</h3

