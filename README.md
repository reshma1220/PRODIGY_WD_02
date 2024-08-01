index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stopwatch</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <div class="wrapper">
            <p>
                <span class="seconds">00</span>:
                <span class="tens">00</span>
            </p> <br>
            <button class="btn-start">Start</button>
            <button class="btn-stop">Stop</button>
            <button class="btn-reset">Reset</button>
        </div>
    </div>
    <script src="script.js"></script>

</body>
</html>

script.js

let seconds = 0;
let tens = 0;
let getSeconds = document.querySelector('.seconds');
let getTens = document.querySelector('.tens');
let btnStart = document.querySelector('.btn-start');
let btnStop = document.querySelector('.btn-stop');
let btnReset = document.querySelector('.btn-reset');
let interval;

btnStart.addEventListener('click', () => {
   inverval=setInterval(startTimer, 10)
})
btnStop.addEventListener('click', () => {
   clearInterval(inverval);
})
btnReset.addEventListener('click', () => {
   clearInterval(inverval);
   tens ='00';
   seconds ='00';
   getSeconds.innerHTML = seconds;
   getTens.innerHTML = tens;
})

function startTimer(){
   tens++;
   if (tens<= 9){
      getTens.innerHTML = '0' + tens;
   }
   if (tens> 9){
      getTens.innerHTML = tens;
   }
   if (tens> 99) {
      seconds++;
      getSeconds.innerHTML ='0'+ seconds;
      tens=0;
      getTens.innerHTML ='0' + 0;
   }
   if (seconds > 9){
      getSeconds.innerHTML = seconds;
      
   }}

   style.css
   @import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@400;600&display=swap');
*{
    margin: 0;
    padding: 0;
    font-family: 'Source Sans Pro', sans-serif;
}
.container{
    background-color: #222242;
    height: 100vh;
    width: 100%;
    text-align: center;
    position: absolute;
}
.wrapper{
    position: relative;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
}
.wrapper p{
    position: relative;
    display: inline-block;
    color: #ffffff;
    z-index: 9999;
    font-size: 48px;
    margin-bottom: 120px;
}
.wrapper p::before{
    content: '';
    position: absolute;
    width: 200px;
    height: 200px;
    background-color: #151538;
    z-index: -1;
    border-radius: 50%;
	left: -31%;
    top: -118%;
    animation-name: shine;
    animation-duration: 3s;
    animation-iteration-count: infinite;
   
}
@keyframes shine{
    0%,100%{
        box-shadow: 0px 0px 32px -12px rgba(246, 180, 0, .5);
    }
    50%{
        box-shadow: 0px 0px 32px 3px rgba(246, 180, 0, .5);
    }
}
button{
    background-color: #222242;
    padding: 10px 38px;
    border: 1px solid #A9A9A9;
    border-radius: 28px;
    color: #fff;
    transition: all .2s ease;
    outline: 0;
}
button:not(:last-child){
    margin-right: 20px;
}
button:hover,
button:focus
{
    border-color: #F6B400;
    color: #F6B400;
    box-shadow: 0px 4px 27px -12px #F6B400;
}

   