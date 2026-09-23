<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>전생연분 前生緣分</title>

<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@300;500&display=swap" rel="stylesheet">

<style>
body {
    margin: 0;
    background: #0b1117;
    color: #d7e2f0;
    font-family: 'IBM Plex Mono', monospace;
    transition: 0.8s;
}

.screen {
    display: none;
    height: 100vh;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

.active {
    display: flex;
}

.box {
    background: #111a23;
    border: 1px solid #1e2b38;
    padding: 40px;
    width: 340px;
}

input {
    width: 100%;
    padding: 10px;
    margin-top: 15px;
    background: #0f151c;
    border: 1px solid #243443;
    color: #d7e2f0;
}

button {
    margin-top: 20px;
    width: 100%;
    padding: 10px;
    background: #2f567c;
    border: none;
    color: white;
    cursor: pointer;
}

button:hover {
    background: #3f6f9f;
}

.panel {
    border: 1px solid #1e2b38;
    background: #111a23;
    padding: 20px;
    margin: 15px;
    width: 600px;
}

.hidden {
    display: none;
}

.system-alert {
    position: fixed;
    top: 0;
    width: 100%;
    text-align: center;
    background: #8a1f1f;
    padding: 8px;
    font-size: 14px;
    display: none;
}

/* 침투 이후 반전 효과 */
.infected {
    background: #e6eef7;
    color: #111;
}

.infected .panel {
    background: #ffffff;
    border-color: #999;
}

.infected button {
    background: #111;
}

.glitch-text {
    animation: glitch 0.2s infinite;
}

@keyframes glitch {
    0% { transform: translate(0); }
    25% { transform: translate(-1px, 1px); }
    50% { transform: translate(1px, -1px); }
    75% { transform: translate(-1px, 0); }
    100% { transform: translate(0); }
}
</style>
</head>

<body>

<div class="system-alert" id="alertBox">
    로딩중...
</div>

<!-- 로그인 화면 -->
<div id="loginScreen" class="screen active">
    <div class="box">
        <h3>색귀(色鬼)</h3>
        <input type="password" id="loginPass" placeholder=">
        <button onclick="login()">접속</button>
        <p id="loginError" style="color:#c25a5a;"></p>
    </div>
</div>

<!-- 대시보드 -->
<div id="dashboardScreen" class="screen">
    <div class="panel">
        <h4 id="roleTitle">경고</h4>
        <p id="logText">섹스에 미친 색귀(色鬼)가 당신에게 접근합니다!</p>
    </div>

    <div class="panel">
        <h4>정보</h4>
        <input type="password" id="filePass" placeholder="보기">
        <button onclick="unlockFile()">열람</button>
        <div id="secretFile" class="hidden">
            <p>이름: 이세린</p>
            <p>나이: ??? (약 1000년 전에 죽은 귀신)</p>
            <p>성별: 여성</p>
            <p>성격: ENFP ･ 바보같음 ･ 섹스에 미쳐있음</p>
            <p>좋아하는 것: 딸기 생크림 케이크 ･ 섹스 ･ {{user}}</p>
        </div>
    </div>
</div>

<script>

const LOGIN_CODE = "0427";
const FILE_CODE = "labcore";

function login(){
    const input = document.getElementById("loginPass").value;
    if(input === LOGIN_CODE){
        document.getElementById("loginScreen").classList.remove("active");
        document.getElementById("dashboardScreen").classList.add("active");
        startInfiltration();
    } else {
        document.getElementById("loginError").innerText = "접근 거부됨";
    }
}

function unlockFile(){
    const input = document.getElementById("filePass").value;
    if(input === FILE_CODE){
        document.getElementById("secretFile").classList.remove("hidden");
    }
}

function startInfiltration(){
    setTimeout(() => {

        document.getElementById("alertBox").style.display = "block";

        setTimeout(() => {
            document.body.classList.add("infected");
            document.getElementById("roleTitle").innerText = "감시 대상";
            document.getElementById("roleTitle").classList.add("glitch-text");
            document.getElementById("logText").innerText =
                "통제 권한이 재지정되었습니다. 현재 관찰 대상은 당신입니다.";
        }, 3000);

    }, 20000);
}

</script>

</body>
</html>
