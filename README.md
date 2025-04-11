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

#### ▶ 캐릭터 이동 & 조작
- `NewPlayer.cs`에서 카메라 회전에 따라 이동 방향이 바뀌는 TPS 스타일 캐릭터 제어 구현  
- 카메라 기준 움직임, 걷기/달리기/점프, Raycast로 벽 충돌 처리  
- Animator 파라미터 연동으로 자연스러운 애니메이션 구성  

✅ “카메라와 캐릭터 이동 벡터를 분리하여 시점 기반의 자유 이동 구현함”  
✅ “Input 처리, 물리 이동, 애니메이션 상태 제어를 기능별로 분리하여 유지보수성 강화”

---

#### ▶ 컬러 체인지 퍼즐 시스템
- `ColorChanger.cs`에서 주기적으로 색상이 변하는 오브젝트 구현  
→ `InvokeRepeating()` 사용, 순차적 색 변경 → `GetCurrentColor()`로 외부 호출 가능  

✅ “색상 상태를 외부에서 읽을 수 있는 getter 제공으로 구조화된 의존성 설계”

---

#### ▶ ColorCounter – 퍼즐 해석 & 스테이지 클리어 조건
- 특정 색상 오브젝트와 상호작용 시, 현재 색상과 태그가 일치하면 카운트 증가  
- UI 텍스트 실시간 갱신  
- 카운트가 맞으면 자동 클리어, 초과 시 자동 리셋 → 실패 조건 관리

✅ “색상 태그/값 비교 기반의 퍼즐 논리 구현, UI 연동까지 통합 구성”

---

#### ▶ 엔딩 폭발 이펙트 & 시각 효과
- `ExplosionEffect.cs`에서 `OnCollisionEnter()` 기반 폭발 처리  
→ `AddExplosionForce()`로 주변 오브젝트 물리 반응  
→ 폭발 이펙트 프리팹 로딩 + 회전값 + 스케일 배수 적용  
→ `OnDrawGizmos()`로 폭발 범위 시각 디버깅 가능

✅ “단순 연출이 아닌 실제 물리 반응과 연동된 연출 시스템 구성”  
✅ “가시성 확보를 위한 개발용 Gizmo 처리도 병행”

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

<h3 align="center">🧰 사용 도구</h3>
<p align="center"> 
    <a href="https://unity.com/" target="_blank" rel="noreferrer"> 
        <img src="https://www.vectorlogo.zone/logos/unity3d/unity3d-icon.svg" alt="unity" width="40" height="40"/> 
    </a> 
</p>

<p align="left"> 
    <img src="https://komarev.com/ghpvc/?username=dreamerschoiminjun&label=Profile%20views&color=0e75b6&style=flat" alt="dreamerschoiminjun" /> 
</p>
