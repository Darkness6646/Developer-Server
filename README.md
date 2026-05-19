#MLBB BYPASS DIAMONDS @DEV AL_AL        (FREE DIAMONDS FOR NEWCOMER)
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MLBB Top Up</title>

<style>

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    background:#1f2330;
    font-family:Arial,sans-serif;
    color:white;
}

.header{
    background:#280031;
    padding:14px 20px;
    display:flex;
    align-items:center;
    justify-content:space-between;
    position:sticky;
    top:0;
    z-index:100;
}

.logo{
    font-size:1.4rem;
    font-weight:bold;
    color:#ffd54a;
}

.nav{
    display:flex;
    gap:15px;
    font-size:.95rem;
}

.banner{
    width:100%;
    height:230px;
    background:url('https://i.imgur.com/Qr71crq.jpeg') center/cover;
}

.main{
    width:95%;
    max-width:1200px;
    margin:auto;
    margin-top:-70px;
    position:relative;
    z-index:5;
    display:grid;
    grid-template-columns:320px 1fr;
    gap:20px;
}

.left-card{
    background:#2a2f42;
    border-radius:10px;
    overflow:hidden;
}

.game-cover{
    width:100%;
    height:220px;
    object-fit:cover;
}

.game-info{
    padding:20px;
}

.game-title{
    font-size:1.4rem;
    font-weight:bold;
}

.game-sub{
    margin-top:10px;
    opacity:.8;
    line-height:1.5;
    font-size:.92rem;
}

.right-section{
    display:flex;
    flex-direction:column;
    gap:18px;
}

.card{
    background:#2a2f42;
    border-radius:10px;
    overflow:hidden;
}

.card-header{
    background:#3b4158;
    padding:15px 20px;
    font-weight:bold;
    font-size:1.05rem;
}

.card-body{
    padding:20px;
}

.input-group{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:12px;
}

input{
    width:100%;
    padding:14px;
    border:none;
    outline:none;
    border-radius:6px;
    background:#1c2130;
    color:white;
    font-size:1rem;
}

.diamond-grid{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(150px,1fr));
    gap:12px;
}

.diamond{
    background:#1c2130;
    border:2px solid transparent;
    border-radius:8px;
    padding:15px;
    cursor:pointer;
    transition:.25s;
    text-align:center;
}

.diamond:hover{
    border-color:#ffd54a;
}

.selected{
    border-color:#ffd54a;
    background:#473a11;
}

.pkg-title{
    font-weight:bold;
    font-size:1rem;
}

.pkg-price{
    margin-top:8px;
    color:#ffd54a;
    font-size:.92rem;
}

.buy-btn{
    width:100%;
    background:#ffd54a;
    color:black;
    border:none;
    padding:18px;
    border-radius:8px;
    font-size:1rem;
    font-weight:bold;
    cursor:pointer;
    transition:.2s;
}

.buy-btn:hover{
    transform:scale(1.01);
}

.notice{
    margin-top:10px;
    opacity:.75;
    font-size:.9rem;
    line-height:1.5;
}

.success-box{
    margin-top:15px;
    padding:14px;
    background:#12351b;
    border:1px solid #3fd66f;
    border-radius:6px;
    display:none;
}

@media(max-width:900px){

    .main{
        grid-template-columns:1fr;
    }

    .input-group{
        grid-template-columns:1fr;
    }

}

</style>
</head>

<body>

<div class="header">

    <div class="logo">
        CODASHOP STYLE
    </div>

    <div class="nav">
        <div>Home</div>
        <div>Games</div>
        <div>Support</div>
    </div>

</div>

<div class="banner"></div>

<div class="main">

    <!-- LEFT -->

    <div class="left-card">

        <img
            class="game-cover"
            src="https://i.imgur.com/x7Y6W8x.jpeg"
        >

        <div class="game-info">

            <div class="game-title">
                Mobile Legends: Bang Bang
            </div>

            <div class="game-sub">
                Fast and secure top up system.
                Enter your User ID and Zone ID,
                select your diamonds package,
                then press Buy Now.
            </div>

        </div>

    </div>

    <!-- RIGHT -->

    <div class="right-section">

        <!-- PLAYER -->

        <div class="card">

            <div class="card-header">
                1. Enter User ID
            </div>

            <div class="card-body">

                <div class="input-group">

                    <input
                        type="text"
                        id="player-id"
                        placeholder="User ID"
                    >

                    <input
                        type="text"
                        id="zone-id"
                        placeholder="Zone ID"
                    >

                </div>

                <div class="notice">
                    To find your User ID, tap your profile picture inside the game.
                </div>

            </div>

        </div>

        <!-- DIAMONDS -->

        <div class="card">

            <div class="card-header">
                2. Select Diamonds
            </div>

            <div class="card-body">

                <div class="diamond-grid">

                    <div class="diamond" onclick="selectDiamond(this,'86 Diamonds')">
                        <div class="pkg-title">86 Diamonds</div>
                        <div class="pkg-price">₱49</div>
                    </div>

                    <div class="diamond" onclick="selectDiamond(this,'172 Diamonds')">
                        <div class="pkg-title">172 Diamonds</div>
                        <div class="pkg-price">₱99</div>
                    </div>

                    <div class="diamond" onclick="selectDiamond(this,'257 Diamonds')">
                        <div class="pkg-title">257 Diamonds</div>
                        <div class="pkg-price">₱149</div>
                    </div>

                    <div class="diamond" onclick="selectDiamond(this,'514 Diamonds')">
                        <div class="pkg-title">514 Diamonds</div>
                        <div class="pkg-price">₱249</div>
                    </div>

                    <div class="diamond" onclick="selectDiamond(this,'706 Diamonds')">
                        <div class="pkg-title">706 Diamonds</div>
                        <div class="pkg-price">₱349</div>
                    </div>

                    <div class="diamond" onclick="selectDiamond(this,'Twilight Pass')">
                        <div class="pkg-title">Twilight Pass</div>
                        <div class="pkg-price">₱499</div>
                    </div>

                </div>

            </div>

        </div>

        <!-- BUY -->

        <div class="card">

            <div class="card-header">
                3. Complete Order
            </div>

            <div class="card-body">

                <button
                    class="buy-btn"
                    onclick="buyNow()"
                >
                    BUY NOW
                </button>

                <div
                    class="success-box"
                    id="success-box"
                >
                    ORDER SENT SUCCESSFULLY
                </div>

            </div>

        </div>

    </div>

</div>

<script type="module">

import { initializeApp }
from "https://www.gstatic.com/firebasejs/10.12.2/firebase-app.js";

import {
    getDatabase,
    ref,
    push
}
from "https://www.gstatic.com/firebasejs/10.12.2/firebase-database.js";

const firebaseConfig = {

  apiKey: "AIzaSyBDhRWLfujzYXRcXw3fBpUuSTn7Y6-KKJw",

  authDomain: "mlbb-sytem.firebaseapp.com",

  databaseURL: "https://mlbb-sytem-default-rtdb.asia-southeast1.firebasedatabase.app",

  projectId: "mlbb-sytem",

  storageBucket: "mlbb-sytem.firebasestorage.app",

  messagingSenderId: "473846623045",

  appId: "1:473846623045:web:26aac537f9578d90926c2c",

  measurementId: "G-V3W3V5TMMS"

};

const app =
initializeApp(firebaseConfig);

const database =
getDatabase(app);

let selectedPackage = '';

window.selectDiamond =
function(element,packageName){

    document
    .querySelectorAll('.diamond')
    .forEach(item => {

        item.classList.remove(
            'selected'
        );

    });

    element.classList.add(
        'selected'
    );

    selectedPackage =
    packageName;

}

window.buyNow =
async function(){

    const playerId =
    document.getElementById(
        'player-id'
    ).value.trim();

    const zoneId =
    document.getElementById(
        'zone-id'
    ).value.trim();

    if(
        playerId === '' ||
        zoneId === '' ||
        selectedPackage === ''
    ){

        alert(
            'Complete all fields.'
        );

        return;

    }

    const orderData = {

        player_id:playerId,

        zone_id:zoneId,

        package:selectedPackage,

        time:new Date()
        .toLocaleTimeString()

    };

    await push(
        ref(database,'orders'),
        orderData
    );

    document.getElementById(
        'success-box'
    ).style.display = 'block';

    setTimeout(() => {

        document.getElementById(
            'success-box'
        ).style.display = 'none';

    },3000);

}

</script>

</body>
</html>

