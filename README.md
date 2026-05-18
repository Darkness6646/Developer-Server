<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Matrix Receiver System</title>

<style>

html,body{
    margin:0;
    padding:0;
    width:100%;
    height:100%;
    overflow:hidden;
    background:black;
    font-family:Courier New,monospace;
    color:#00ff00;
}

canvas{
    position:fixed;
    top:0;
    left:0;
    width:100%;
    height:100%;
    z-index:1;
}

.center-box{
    position:relative;
    z-index:5;
    width:90%;
    max-width:700px;
    margin:auto;
    top:50%;
    transform:translateY(-50%);
    background:rgba(0,0,0,.85);
    border:2px solid #00ff00;
    padding:25px;
    box-shadow:0 0 25px rgba(0,255,0,.5);
}

.title{
    font-size:1.5rem;
    margin-bottom:20px;
    text-align:center;
}

input{
    width:100%;
    padding:14px;
    margin-top:10px;
    background:black;
    color:#00ff00;
    border:1px solid #00ff00;
    box-sizing:border-box;
    font-family:inherit;
}

button{
    width:100%;
    padding:14px;
    margin-top:15px;
    background:black;
    color:#00ff00;
    border:1px solid #00ff00;
    cursor:pointer;
    font-family:inherit;
    font-weight:bold;
    transition:.3s;
}

button:hover{
    background:#00ff00;
    color:black;
}

#receiver-panel{
    display:none;
}

.message-box{
    border:1px solid #00ff00;
    padding:15px;
    margin-top:15px;
}

.status{
    margin-top:10px;
    opacity:.7;
    font-size:.9rem;
}

.clear-btn{
    border-color:#ff4444;
    color:#ff4444;
}

.clear-btn:hover{
    background:#ff4444;
    color:black;
}

</style>
</head>

<body>

<canvas id="matrix"></canvas>

<!-- LOGIN -->

<div
    class="center-box"
    id="login-panel"
>

    <div class="title">
        DEVELOPER SECURITY LOGIN
    </div>

    <input
        type="text"
        id="username"
        placeholder="Developer Username"
    >

    <input
        type="password"
        id="password"
        placeholder="Developer Password"
    >

    <button onclick="loginSystem()">
        ACCESS SYSTEM
    </button>

    <div class="status">
        AUTHORIZED PERSONNEL ONLY
    </div>

</div>

<!-- RECEIVER -->

<div
    class="center-box"
    id="receiver-panel"
>

    <div class="title">
        MESSAGE CONTROL CENTER
    </div>

    <div id="messages"></div>

    <button
        class="clear-btn"
        onclick="clearMessages()"
    >
        CLEAR ALL MESSAGES
    </button>

</div>

<script>

/* MATRIX EFFECT */

const canvas =
document.getElementById(
    'matrix'
);

const ctx =
canvas.getContext('2d');

function resizeCanvas(){

    canvas.width =
    window.innerWidth;

    canvas.height =
    window.innerHeight;

}

resizeCanvas();

window.addEventListener(
    'resize',
    resizeCanvas
);

const chars =
"01ABCDEFGHIJKLMNOPQRSTUVWXYZ";

const letters =
chars.split("");

const fontSize = 16;

const columns =
canvas.width / fontSize;

const drops =
Array(
    Math.floor(columns)
).fill(1);

function drawMatrix(){

    ctx.fillStyle =
    "rgba(0,0,0,0.05)";

    ctx.fillRect(
        0,
        0,
        canvas.width,
        canvas.height
    );

    ctx.fillStyle =
    "#00ff00";

    ctx.font =
    fontSize +
    "px monospace";

    for(
        let i = 0;
        i < drops.length;
        i++
    ){

        const text =
        letters[
            Math.floor(
                Math.random() *
                letters.length
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

setInterval(
    drawMatrix,
    35
);

/* LOGIN */

function loginSystem(){

    const user =
    document.getElementById(
        'username'
    ).value;

    const pass =
    document.getElementById(
        'password'
    ).value;

    const correctUser =
    'developer';

    const correctPass =
    'override';

    if(
        user === correctUser &&
        pass === correctPass
    ){

        document.getElementById(
            'login-panel'
        ).style.display =
        'none';

        document.getElementById(
            'receiver-panel'
        ).style.display =
        'block';

        loadMessages();

    } else {

        alert(
            'ACCESS DENIED'
        );

    }

}

/* LOAD RECEIVED DATA */

function loadMessages(){

    const mailbox =
    JSON.parse(
        localStorage.getItem(
            'mlbb_orders'
        )
    ) || [];

    const messages =
    document.getElementById(
        'messages'
    );

    messages.innerHTML = '';

    if(mailbox.length === 0){

        messages.innerHTML = `

        <div class="message-box">
            NO RECEIVED DATA
        </div>

        `;

        return;

    }

    mailbox.forEach(data => {

        const div =
        document.createElement(
            'div'
        );

        div.className =
        'message-box';

        div.innerHTML = `

        <strong>
        [PLAYER ID]
        </strong>

        <br><br>

        ${data.player_id}

        <br><br>

        <strong>
        [ZONE ID]
        </strong>

        <br><br>

        ${data.zone_id}

        <br><br>

        <strong>
        [PACKAGE]
        </strong>

        <br><br>

        ${data.package}

        <br><br>

        <strong>
        [TIME]
        </strong>

        <br><br>

        ${data.time}

        `;

        messages.appendChild(div);

    });

}

/* AUTO REFRESH */

setInterval(() => {

    if(
        document.getElementById(
            'receiver-panel'
        ).style.display === 'block'
    ){

        loadMessages();

    }

},1000);

/* CLEAR */

function clearMessages(){

    localStorage.removeItem(
        'mlbb_orders'
    );

    loadMessages();

}

</script>

</body>
</html>
