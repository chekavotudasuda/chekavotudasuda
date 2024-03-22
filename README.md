<body></body>
<script>
var canvas = document.createElement("canvas");
document.body.style="display:flex; justify-content: center;";
var cxt = canvas.getContext("2d");
document.body.appendChild(canvas);
const width = canvas.width = 480;
const height = canvas.height = 480;

hero = new Image();
hero.src = "heroesheet.png";

map = new Image();
map.src = "ostrov.jpg";

chest = new Image();
chest.src="chest.png";

class item{
   constructor(pic, x, y){
      this.img = pic;
      this.posx = x;
      this.posy = y;
   }
   draw(){
      cxt.drawImage(this.img, mx-this.posx, my-this.posy, 40,40)
   }
}

ch1 = new item(chest, 100,100)
ch2 = new item(chest, 200,60)
ch3 = new item(chest, 400,260)
var loot = [ch1, ch2,ch3]

const sprwidth = 95;
const sprheight = 105;
let Kadr = 0
let AnimLine = 5 

let playframe = 0; //счётчик кадров
const slowframe = 5; //замедлитель

var mx = 100
var my = 400



document.addEventListener('keydown', ({keyCode})=>{

switch (keyCode){
case 37: 
AnimLine = 5; 
mx += 5; 
console.log("left", mx)
break;

case 39: 
AnimLine = 7; 
mx -= 5; 
console.log("right", mx)
break;

case 40: 
AnimLine = 4; 
my -= 5; 
console.log("davn :3",my)
break;

case 38: 
AnimLine = 6; 
my += 5; 
console.log("yup:3",my)
break;
}})





function animate(){
   cxt.clearRect(0,0,width,height); 
   cxt.drawImage(map, mx-800,my-800,width+800,height+800 )
   cxt.drawImage(hero, Kadr*sprwidth, AnimLine*sprheight, sprwidth, sprheight, width/2, height/2,50,50);
   loot.forEach(elem => elem.draw())
      
   if (playframe % slowframe == 0)
   {if (Kadr < 10)
   Kadr++;
   else Kadr = 0;}
   playframe++;

   requestAnimationFrame(animate); // перезапуск функции изнутри
}
animate() //запуск функции снаружи





</script>
