let bodypix;
let video;
let segmentation;
let img;
let timer;
let myFont;

var startB; 
var startRGB;
var timerValue = 5;

let tracker = false;

let lastCheck;


const options = {
    outputStride: 8, // 8, 16, or 32, default is 16
    segmentationThreshold: 0.3, // 0 - 1, defaults to 0.5 
}

function preload(){
    bodypix = ml5.bodyPix(options)
    // myFont = loadFont('assets/Canela-Regular.otf');
}

function setup() {
    c = createCanvas(640, 480);

    // load up your video
    video = createCapture(VIDEO);
    video.size(width, height);
    tint(255, 200);

    video.hide(); // Hide the video element, and just show the canvas
    createSimplePalette();

    bodypix.segmentWithParts(video, gotResults, options)
  
      
  startB = createButton("S N A P !");
  startB.position(width - 350 , height + 30);
  startB.style("background-color","#FFFFFF");
  startB.size(100,50);
  startB.mousePressed(timerCountdown);
  
  // startRGB = createButton("R G B");
  // startRBB.position(width - 155 , height + 50);
  // startRGB.mousePressed(createRGBPalette);
}


function gotResults(err, result) {
    if (err) {
        console.log(err)
        return
    }
    segmentation = result;
      bodypix.segmentWithParts(video, gotResults, options)

    }

function draw() {    
  background(255, 0, 0);
  image(video, 0, 0, width, height)
  textSize(20);
  // textFont(myFont);
  text("SILLHOUTTE STAMP", width - 400, 30);


 
  if (segmentation) {
    tint(255, 127)
  image(segmentation.partMask, 0, 0, width, height)
  }
  
    if (timerValue < 10) {
    textSize(40);
    text("0:0" + timerValue, width - 350, height / 2);
  } else {
    textSize(40);
    text("0:" + timerValue, width - 350, height / 2);


  }
  
//   if (millis() > lastCheck + 5000) {
//     takeasnap();
//     lastCheck = millis();
//   }
  
  
  
  if (millis() > lastCheck + 5000) {
      if (tracker == true) {
    takeasnap();
  }  
    // print(tracker);
    lastCheck = millis();

  }


}

function createSimplePalette() {
    options.palette = bodypix.config.palette;
    Object.keys(options.palette).forEach(part => {
        const r = floor(random(215));
        const g = floor(random(10));
        const b = floor(random(215));
        options.palette[part].color = [r, g, b]
    });
}
 
  
  function takeasnap() {   
    saveCanvas(c, 'SillhoutteStamp', 'jpg');
  // print("Download");
    tracker = false;      
}

  
  function timerCountdown() {
  setInterval(function() {
    if (timerValue > 0) {
      timerValue--;
    } 
    
  },1000); 
    
    lastCheck = millis();
    tracker = true;
}
