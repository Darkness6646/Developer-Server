
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>System Override</title>

<style>

body, html{
    margin:0;
    padding:0;
    width:100%;
    height:100%;
    background:#000;
    overflow:hidden;
    font-family:Courier New, monospace;
    color:#00ff00;
    display:flex;
    justify-content:center;
    align-items:center;
}

canvas{
    position:absolute;
    top:0;
    left:0;
    width:100%;
    height:100%;
    z-index:1;
}

.ui-container{
    position:relative;
    z-index:3;
    text-align:center;
}

#init-btn,
#granted-btn,
#login-btn{
    background:transparent;
    color:#00ff00;
    border:2px solid #00ff00;
    padding:15px 40px;
    font-size:1rem;
    font-family:inherit;
    cursor:pointer;
    border-radius:5px;
    transition:.3s;
}

#init-btn:hover,
#granted-btn:hover,
#login-btn:hover{
    background:#00ff00;
    color:#000;
    box-shadow:0 0 20px #00ff00;
}

#countdown{
    font-size:7rem;
    display:none;
    margin-bottom:20px;
    animation:pulse 1s infinite;
}

#frame-container{
    position:relative;
    z-index:2;
    display:none;
    opacity:0;
    transition:1s;
    padding:40px;
    background:#000;
    border:2px solid #00ff00;
    box-shadow:0 0 30px rgba(0,255,0,.5);
    width:80%;
    max-width:900px;
}

#developer-login{
    margin-bottom:20px;
}

#dev-user,
#dev-pass{
    padding:10px;
    margin:5px;
    background:#000;
    color:#00ff00;
    border:1px solid #00ff00;
    width:220px;
}

#live-output{
    display:none;
    margin-top:20px;
    border:1px solid #00ff00;
    padding:10px;
    max-height:250px;
    overflow:auto;
    text-align:left;
}

#access-panel{
    display:none;
    margin-top:20px;
}

.fake-app{
    border:1px solid #00ff00;
    padding:10px;
    margin:10px 0;
    cursor:pointer;
}

.fake-app:hover{
    background:#00ff00;
    color:#000;
}

@keyframes pulse{
    0%{transform:scale(1);}
    50%{transform:scale(1.05);}
    100%{transform:scale(1);}
}

</style>
</head>

<body>

<canvas id="matrix"></canvas>

<div id="frame-container">

    <div id="developer-login">

        <input
            id="dev-user"
            type="text"
            placeholder="Developer Username"
        >

        <input
            id="dev-pass"
            type="password"
            placeholder="Developer Password"
        >

        <button id="login-btn">
            LOGIN
        </button>

    </div>

    <div id="live-output"></div>

    <button id="granted-btn">
        CORE CONTROL NODE
    </button>

    <div id="access-panel">

        <h2>SIMULATED SYSTEM ACCESS</h2>

        <div
            class="fake-app"
            onclick="openDemo('Messaging Console')"
        >
            Messaging Console
        </div>

        <div
            class="fake-app"
            onclick="openDemo('Archive Database')"
        >
            Archive Database
        </div>

        <div
            class="fake-app"
            onclick="openDemo('Security Logs')"
        >
            Security Logs
        </div>

    </div>

</div>

<div class="ui-container" id="ui-box">

    <button id="init-btn">
        INITIALIZE SYSTEM BYPASS
    </button>

    <div id="countdown">5</div>

</div>

<script src="https://www.gstatic.com/firebasejs/10.12.2/firebase-app-compat.js"></script>

<script src="https://www.gstatic.com/firebasejs/10.12.2/firebase-database-compat.js"></script>

<script>
const canvas = document.getElementById('matrix');
const ctx = canvas.getContext('2d');

const btn = document.getElementById('init-btn');
const countdownEl = document.getElementById('countdown');

const uiBox = document.getElementById('ui-box');

const frameContainer =
document.getElementById('frame-container');

const grantedBtn =
document.getElementById('granted-btn');

const accessPanel =
document.getElementById('access-panel');

const loginBtn =
document.getElementById('login-btn');

const liveOutput =
document.getElementById('live-output');

function resizeCanvas(){

    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

}

resizeCanvas();

window.addEventListener(
    'resize',
    resizeCanvas
);

const chars =
"010101_SYSTEM_ACCESS_GRANTED";

const charArray = chars.split("");

const fontSize = 16;

let columns = canvas.width / fontSize;

let drops =
Array(Math.floor(columns)).fill(1);

function drawMatrix(){

    ctx.fillStyle =
    'rgba(0,0,0,0.05)';

    ctx.fillRect(
        0,
        0,
        canvas.width,
        canvas.height
    );

    ctx.fillStyle = '#00ff00';

    ctx.font =
    fontSize + 'px monospace';

    for(let i = 0; i < drops.length; i++){

        const text =
        charArray[
            Math.floor(
                Math.random() *
                charArray.length
            )
        ];

        ctx.fillText(
            text,
            i * fontSize,
            drops[i] * fontSize
        );

        if(
            drops[i] * fontSize >
            canvas.height &&
            Math.random() > 0.975
        ){
            drops[i] = 0;
        }

        drops[i]++;

    }

}

btn.addEventListener('click', () => {

    btn.style.display = 'none';

    setInterval(drawMatrix, 33);

    countdownEl.style.display = 'block';

    let timeLeft = 5;

    const timer = setInterval(() => {

        timeLeft--;

        if(timeLeft > 0){

            countdownEl.textContent =
            timeLeft;

        } else {

            clearInterval(timer);

            countdownEl.textContent =
            'ACCESSING...';

            revealTargetFrame();

        }

    },1000);

});

function revealTargetFrame(){

    uiBox.style.display = 'none';

    frameContainer.style.display =
    'block';

    setTimeout(() => {

        frameContainer.style.opacity =
        '1';

    },50);

}

const DEV_USERNAME = 'developer';
const DEV_PASSWORD = 'quantum123';

const firebaseConfig = {

    apiKey:'YOUR_API_KEY',

    authDomain:
    'YOUR_PROJECT.firebaseapp.com',

    databaseURL:
    'https://YOUR_PROJECT.firebaseio.com',

    projectId:'YOUR_PROJECT',

    storageBucket:
    'YOUR_PROJECT.appspot.com',

    messagingSenderId:
    'YOUR_SENDER_ID',

    appId:'YOUR_APP_ID'

};

firebase.initializeApp(firebaseConfig);

const database = firebase.database();

grantedBtn.addEventListener('click', () => {

    // Restricted unless login succeeds
    if(
        liveOutput.style.display !==
        'block'
    ){

        alert(
            'ACCESS RESTRICTED\n\n' +
            'Developer authentication required.'
        );

        return;
    }

    accessPanel.style.display = 'block';

    const visitTime = new Date();

    const visitor =
    prompt('Enter your name:')
    || 'Unknown Visitor';

    database.ref('liveVisitors').push({

        visitor:visitor,

        date:
        visitTime.toLocaleDateString(),

        time:
        visitTime.toLocaleTimeString(),

        device:navigator.userAgent

    });

});

loginBtn.addEventListener('click', () => {

    liveOutput.style.display = 'none';

    const username =
    document.getElementById(
        'dev-user'
    ).value;

    const password =
    document.getElementById(
        'dev-pass'
    ).value;

    if(
        username.trim() ===
        DEV_USERNAME &&

        password.trim() ===
        DEV_PASSWORD
    ){

        liveOutput.style.display =
        'block';

        database
        .ref('liveVisitors')
        .on('child_added',
        (snapshot) => {

            const data =
            snapshot.val();

            const log =
            document.createElement(
                'div'
            );

            log.innerHTML = `

            <strong>Visitor:</strong>
            ${data.visitor}<br>

            <strong>Date:</strong>
            ${data.date}<br>

            <strong>Time:</strong>
            ${data.time}<br>

            <strong>Device:</strong>
            ${data.device}

            <hr>

            `;

            liveOutput.prepend(log);

        });

        alert(
        'Developer access granted.'
        );

    } else {

        liveOutput.style.display =
        'none';

        alert(
        'ACCESS DENIED\n\n' +

        'Please check if the ' +

        'username and password ' +

        'are typed correctly.'
        );

    }

});

function openDemo(name){

    alert(
        name +
        ' opened successfully.'
    );

}

</script>
</body>
</html>
