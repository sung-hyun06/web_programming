# web_programming
## 나만의 작은 놀이터
https://github.com/sung-hyun06/ex250310_first.wiki.git
***

## 프로젝트 폴더 구조
***
game_site/
│
├─ index.html        ← 메인 페이지
├─ style.css         ← 디자인 (색상, 배치 등)
├─ main.js
└─ games/
    ├─ slot.html     ← 슬롯머신 게임
    ├─ clicker.html  ← 클릭 게임
    └─ maze.html     ← 미로 게임
***

## index.html(메인 페이지)
***
```html
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8" />
<title>Mini Game Party</title>
<link rel="stylesheet" href="style.css" />
</head>
<body>
<h1>🎮 Mini Game Party</h1>


<!-- 1. 플레이어 수 선택 -->
<section>
<h2>플레이어 수 선택</h2>
<button onclick="setPlayers(1)">1인 플레이어</button>
<button onclick="setPlayers(2)">2~4인 플레이어</button>
<p id="playerInfo">선택 안됨</p>
</section>


<!-- 2. 게임 선택 -->
<section>
<h2>게임 선택</h2>
<div class="games">
<div class="game" onclick="enterGame('slot.html',1)">🎰 슬롯</div>
<div class="game" onclick="enterGame('clicker.html',1)">🖱 클릭</div>
<div class="game" onclick="enterGame('maze.html',2)">🧩 미로</div>
</div>
</section>


<!-- 기록 -->
<section>
<h2>오늘의 기록</h2>
<ul id="log"></ul>
</section>


<script src="main.js"></script>
</body>
</html>
```
***

## style.css
***
```css
body {
font-family: Arial, sans-serif;
background: #111;
color: #fff;
text-align: center;
}


button {
padding: 10px 20px;
margin: 5px;
cursor: pointer;
}


.games {
display: flex;
justify-content: center;
gap: 20px;
}


.game {
background: #222;
padding: 20px;
border-radius: 10px;
cursor: pointer;
}


.game.locked {
opacity: 0.3;
cursor: not-allowed;
}
```
***

## main.js
***
```js
let players = 0;


function setPlayers(num) {
players = num;
document.getElementById('playerInfo').innerText = `선택 인원: ${num}명`;
updateGames();
}


function updateGames() {
document.querySelectorAll('.game').forEach(game => {
game.classList.remove('locked');
});


if (players === 1) {
document.querySelectorAll('.game')[2].classList.add('locked'); // 미로 잠금
}
}


function enterGame(game, minPlayers) {
if (players < minPlayers) {
alert('플레이어 수가 부족합니다');
return;
}


logPlay(game);
location.href = `games/${game}`;
}


function logPlay(game) {
const log = document.getElementById('log');
const li = document.createElement('li');
li.innerText = `${game} 플레이 (${new Date().toLocaleTimeString()})`;
log.appendChild(li);
}
```
***

## games/slot.html
***
```html
<!DOCTYPE html>
<html lang="ko">
<body>
<h1>클릭 게임</h1>
<button onclick="count++">CLICK</button>
<p id="c">0</p>
<script>
let count=0;
setInterval(()=>document.getElementById('c').innerText=count,100);
</script>
</body>
</html>
```
***

## games/clocker.html
***
```html
<!DOCTYPE html>
<html lang="ko">
<body>
<h1>클릭 게임</h1>
<button onclick="count++">CLICK</button>
<p id="c">0</p>
<script>
let count=0;
setInterval(()=>document.getElementById('c').innerText=count,100);
</script>
</body>
</html>
```
***

## games/maze.html
***
```html
<!DOCTYPE html>
<html lang="ko">
<body>
<h1>미로 게임 (2인 이상)</h1>
<p>협동해서 탈출하세요!</p>
</body>
</html>
```
***

## 만들게 된 이유
***
그냥 혼자 넷플이나 유튜브를 보다가 단순하게 광고에서 나오는 작은 미니게임들이 있는데 이 게임들 특징이 항상 광고가 존재                   
→ 광고제거를 구매하기에는 가격도 천차만별이고 그정도로 오랫동안 할만 게임들이 아님              
→ 그 게임들을 그냥 만들어서 친구들이랑 같이 광고 없이 계속 즐기면 좋지 않을까 생각         
→ 이번 기회 그냥 내가 만들자
→ 내가 잠깐잠깐 즐겨하는 미니게임들 모아놓으면 편하지 않을까
***

## 웹사이트 구조
1. 플레이어 수 선택
- "1인 플레이어" / "2인~4인" 중에서 선택
2. 입장 후 게임 선택
- 다양하게 준비한 게임 선택
- 플레이 인원에 따라서 가능한 게임 수 제한
3. 룰 가이드
- 각 게임마다 간단하게 룰 설명
- 텍스트 + 이미지로 제공
4. 승리 포인트 시스템
- 승리할 때 마다 포인트 기록
5. 활동 기록
- 오늘 플레이한 게임 기록
- 사용시간 기록
- 주로 많이 플레이 되는 게임 기록
***

## 와이드 프레임
<img width="891" height="1260" alt="image" src="https://github.com/user-attachments/assets/1dc46954-6d07-40a1-9ddd-b4cc9a84ddd8" />

***

## 사용되는 기술
- 프론트앤드 : html, css, js 같은 웹 프레임워크 사용
- 웹 링크 인식 : 각 아이콘을 선택하면 게임들이 나오게 인식
- 인원수 파일 > 몇명이 플레이 할지 선택 > 해당 인원에 맞게 작동
- 게임 이모지 파일 > 플레이 하고 싶은 게임 아이콘 선택 > 해당 게임 플레이
- 인원수의 맞는 게임 제한 > 자동으로 사용이 불가능한 게임은 잠금 표시와 함께 선택해도 작동 X
***

## 앞으로 추가/개선
* 게임 다양성
* 룰 설명 가이드 이미지/애니메이션 보강(이미지는 세부적 표현, 애니메이션으로 플레이 모습 재생)
* PC/모바일 UI 개선
* 아직 완성하지 못한 코드 바디 완성하기
***


