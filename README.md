<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>LIVE ORDER RECEIVER</title>

<style>

body{
    margin:0;
    background:black;
    color:#00ff00;
    font-family:'Courier New',monospace;
}

.header{
    background:#001100;
    padding:20px;
    text-align:center;
    font-size:1.5rem;
    font-weight:bold;
    border-bottom:2px solid #00ff00;
}

.container{
    width:95%;
    max-width:900px;
    margin:auto;
    padding:20px;
}

.order{
    border:1px solid #00ff00;
    background:#001a00;
    padding:15px;
    margin-bottom:15px;
    border-radius:5px;
    box-shadow:0 0 10px rgba(0,255,0,.3);
}

.no-orders{
    text-align:center;
    opacity:.7;
    margin-top:50px;
    font-size:1.2rem;
}

</style>
</head>

<body>

<div class="header">
    LIVE ORDER RECEIVER
</div>

<div class="container">

    <div id="orders">

        <div class="no-orders">
            WAITING FOR ORDERS...
        </div>

    </div>

</div>

<script type="module">

import { initializeApp }
from "https://www.gstatic.com/firebasejs/10.12.2/firebase-app.js";

import {
    getDatabase,
    ref,
    onValue
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

const ordersContainer =
document.getElementById(
    'orders'
);

onValue(
    ref(database,'orders'),
    (snapshot) => {

        ordersContainer.innerHTML = '';

        const data =
        snapshot.val();

        if(!data){

            ordersContainer.innerHTML = `

            <div class="no-orders">
                NO ORDERS RECEIVED
            </div>

            `;

            return;

        }

        Object.values(data)
        .reverse()
        .forEach(order => {

            const div =
            document.createElement(
                'div'
            );

            div.className =
            'order';

            div.innerHTML = `

            <strong>PLAYER ID:</strong>

            <br>

            ${order.player_id}

            <br><br>

            <strong>ZONE ID:</strong>

            <br>

            ${order.zone_id}

            <br><br>

            <strong>PACKAGE:</strong>

            <br>

            ${order.package}

            <br><br>

            <strong>TIME:</strong>

            <br>

            ${order.time}

            `;

            ordersContainer.appendChild(div);

        });

    }
);

</script>

</body>
</html>
