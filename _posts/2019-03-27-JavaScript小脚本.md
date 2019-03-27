## 2019-03-27-JavaScript小脚本.md
#### 贪吃蛇
```javascript
<html>
<head>
<script type="text/javascript">
var map = null;
//面板
function Map(){
     this.width = 800;
this.height = 400;
this.color = 'lightblue';


this.showmap = function(){
var ban = document.createElement('div');
ban.style.width = this.width+'px';
ban.style.height = this.height+'px';
ban.style.position ='absolute';
ban.style.left =0;
ban.style.top = 0;
ban.style.backgroundColor = this.color;
document.body.appendChild(ban);
}
}


//食物
function Food(){
   this.width = 20;   
   this.color = "red";
   this.shiwu = null;
   this.showfood = function(){
  if(this.shiwu == null){
         this.shiwu = document.createElement('div');
         this.shiwu.style.width = this.width+'px';
this.shiwu.style.height = this.width+'px';
this.shiwu.style.position ='absolute';
  }
this.shiwux = Math.floor(Math.random()*40);
    this.shiwuy = Math.floor(Math.random()*20);
this.shiwu.style.left = this.shiwux*this.width+"px";
         this.shiwu.style.top  = this.shiwuy*this.width+"px";
this.shiwu.style.backgroundColor = this.color;
document.body.appendChild(this.shiwu);
   }
}
//绘制小蛇
function Snake(){
this.direct = "right";
   this.range = 20;
   this.color = "green";
   this.duans = [[0,1,this.color,null],[1,1,this.color,null],[2,1,this.color,null],[3,1,'red',null]];
   //显示小蛇
    this.showsnake = function(){ 
for(var i in this.duans){
if(this.duans[i][3]==undefined){
       this.duans[i][3] = document.createElement('div');
       this.duans[i][3].style.width = this.range+'px';
  this.duans[i][3].style.height = this.range+'px';
  this.duans[i][3].style.backgroundColor = this.duans[i][2];  
}
this.duans[i][3].style.position = 'absolute';
      this.duans[i][3].style.left =this.range*this.duans[i][0]+'px';
  this.duans[i][3].style.top = this.range*this.duans[i][1]+'px';
  document.body.appendChild(this.duans[i][3]);
  }
}
//移动小蛇
this.movesnake = function(){
     for(i=0;i<this.duans.length-1;i++){
this.duans[i][0] = this.duans[i+1][0];
this.duans[i][1] = this.duans[i+1][1];
}
if(this.direct=='right')
      this.duans[this.duans.length-1][0] +=1;
if(this.direct=='left')
      this.duans[this.duans.length-1][0] -=1;
if(this.direct=='up')
      this.duans[this.duans.length-1][1] -=1;
if(this.direct=='down')
      this.duans[this.duans.length-1][1] +=1;
     
//判断蛇是否吃到食物
if( this.duans[this.duans.length-1][0]==food.shiwux&&
this.duans[this.duans.length-1][1]==food.shiwuy){
var newduan = [this.duans[0][0], this.duans[0][1],this.color,null];
this.duans.unshift(newduan);
        food.showfood();
}
     //判断是否出界 0,0 40,0 0,20 40,20
      if( this.duans[this.duans.length-1][0]<0
||this.duans[this.duans.length-1][0]>39||
this.duans[this.duans.length-1][1]<0||
this.duans[this.duans.length-1][1]>19){
                alert('game over');
clearInterval(mytime);
return false;
}
//判断是否吃到自己
for(var i=0;i<this.duans.length-1;i++){
            if( this.duans[i][0] == this.duans[this.duans.length-1][0]&&
this.duans[i][1] == this.duans[this.duans.length-1][1]){
            alert('game over by yourself');
clearInterval(mytime);
return false;
}
}
this.showsnake();
}
   
}
window.onload = function(){
        map = new Map();
map.showmap();


food = new Food();
food.showfood();


snake = new Snake();
snake.showsnake();


mytime = setInterval("snake.movesnake()",200);


    document.body.onkeydown = function(evt){
        if(evt.keyCode == 38){
            snake.direct = "up";
        }
        if(evt.keyCode == 40){
            snake.direct = "down";
        }
        if(evt.keyCode == 37){
            snake.direct = "left";
        }
        if(evt.keyCode == 39){
            snake.direct = "right";
        }
}


}
</script>
</head>
<body>
</body>
</html>

```
