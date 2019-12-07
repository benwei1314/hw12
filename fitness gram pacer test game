# //ball collision https://www.youtube.com/watch?v=JV5XBmaQdIA
//array https://www.youtube.com/watch?v=i2C1hrJMwz0
//array2 https://www.youtube.com/watch?v=VIQoUghHSxU

//Edit game!!!
var wallDs = 2;
var wallSs = 2;
var willlosescore = 40;
var willwinscore = 200;
var playerspeeed = 6;
{
  var screenx = 500;
  var screeny = 1000;
  var started = false;
  var scorelose = 0;
  var scorewin = 0;
}

var player = {
  x: screenx/2,
  y: screeny/2,
  size: 30,
  speed: 4,
}

var pt = {
  x: 0,
  y: 0,
  w: screeny,
  h: screenx/8,
}
var pb = {
  x: 0,
  y: screeny-screenx/8,
  w: screeny,
  h: screenx/8,
}

var walls = [];
var walls2 = [];


function preload() {
scores = loadSound("scores.mp3");  
//bump = loadSound("bump.mp3");
win = loadSound("win.wav");  
price = loadSound("price.mp3");
fitness = loadSound("fitness.mp3"); 
oof = loadSound("oof.mp3");  

}


function setup() {
  noLoop();
  fitness.play();
  
  createCanvas(screenx, screeny);
  for (var i = 0; i < 50; i++) {
    walls[i] = new Walls();
  }
  for (var j = 0; j < 50; j++) {
    walls2[j] = new Walls2();
  }

}

function draw() {
   if(started){
  }
  keyPressed();
  background(0);
  fill(0, 255, 0);
  rect(player.x, player.y, player.size, player.size); //player
   fill(255, 255, 255,);
  rect(pt.x, pt.y, pt.w, pt.h);
  fill(255, 250, 255,);
  rect(pb.x, pb.y, pb.w, pb.h);
  {
  if (player.x + player.size >= pt.x && player.x <= pt.x + pt.w && player.y + player.size >= pt.y && player.y <= pt.y + pt.h) {
 textSize(50);
      text('score', 120, height / 2);
    scorewin = scorewin+1;
      if (scores.isPlaying()) {
    scores.stop();
  } else {
    scores.play();
    
  }
}
  }
  if (player.x + player.size >= pb.x && player.x <= pb.x + pb.w && player.y + player.size >= pb.y && player.y <= pb.y + pb.h) {
 textSize(50);
      text('score', 120, height / 2);
    scorewin = scorewin+1;
     if (scores.isPlaying()) {
    scores.stop();
  } else {
    scores.play();
  }
}
  textSize(50)
  text(scorelose, 300, height / 2);     
  if(scorelose > willlosescore){         //set lose score
    noLoop();
    price.play();
    price.setVolume(0.1);
  }
  textSize(50)
  text(scorewin, 30, height / 2);
  if(scorewin > willwinscore){    //set win score
    noLoop();
    win.play();
}
 
  for (var i = 0; i < 10; i++) {
    walls[i].show();
    walls[i].update();
  }

  for (var j = 0; j < 10; j++) {
    walls2[j].show();
    walls2[j].update();
  }
}

function keyPressed() {
     if(keyCode=== 32 && keyIsPressed) {
    started = true;
      loop();
    }
  
  if (keyCode === UP_ARROW && keyIsPressed) {
    player.y -= playerspeeed;
  }
  if (keyCode === DOWN_ARROW && keyIsPressed) {
    player.y = player.y + playerspeeed;
  }
  if (keyCode === LEFT_ARROW && keyIsPressed) {
    player.x = player.x - playerspeeed;
  }
  if (keyCode === RIGHT_ARROW && keyIsPressed) {
    player.x = player.x + playerspeeed;
  } 
  {
    if (player.x < 0) { //boundary movement ship
      player.x = 0;
    }
    if (player.x > width - 0) {
      player.x = width - 10;
    }
     if (player.y < 0) { //boundary movement ship
      player.y = 0;
     }
    if (player.y > height - 0) {
      player.y = height - player.size;
    }
  }
}

function Walls() { //UP
  this.x = random(0, width);
  this.y = random(height, -height);
  this.w = random(50, 100);
  this.h = random(100, 200);
  this.speed = 1;

  this.show = function() {
    noStroke();
    fill(0, 200, 100);
    rect(this.x, this.y, this.w, this.h);

    if (player.x + player.size >= this.x && player.x <= this.x + this.w && player.y + player.size >= this.y && player.y <= this.y + this.h) {
 textSize(50);
      text('ouch', 380, height / 2);
     scorelose = scorelose+1;
      player.speed = this.speed * -1
      if (oof.isPlaying()) {
         oof.setVolume(5);
    oof.stop();
  } else {
    oof.play();
    
  }
      
    } else {
      player.speed = 5;
 
      }     
    this.update = function() {
      this.speed = wallSs; // wall SPEED!
      this.x = this.x - this.speed;
   }
      if (this.x < -width) {
        this.x = random(screenx, width);
      }

    }
  }

function Walls2() { //DOWN
  this.x = random(0, width);
  this.y = random(height, -height);
  this.w = random(50, 100);
  this.h = random(100, 200);
  this.speed = 1;

  this.show = function() {
    noStroke();
    fill(179, 209, 10);
    rect(this.x, this.y, this.w, this.h);

    if (player.x + player.size >= this.x && player.x <= this.x + this.w && player.y + player.size >= this.y && player.y <= this.y + this.h) {
 textSize(50);
      text('ouch', 380, height / 2);
     scorelose = scorelose+1;
        if (oof.isPlaying()) {
         oof.setVolume(5);
    oof.stop();
  } else {
    oof.play();
      
  }
    } else {
      player.speed = 5;
    }

    this.update = function() {
      this.speed = wallDs; //SPEED
      this.y = this.y + this.speed;

      if (this.y > height) {
        this.y = random(0, -height);
      }else{
      }

    }
  }
}
