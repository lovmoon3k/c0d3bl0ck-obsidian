//Setting variables.. Int, string, bool, array and object for this chuck of code
var state = 0; //0,1,2,3 will be used to cycle through stages of the puzzle
var curious = 23;
var ranNum = round(random(29,100));
var tempX,tempY;
/*
text to print for each state. Index starts at 0 & ends at 3. to call use stateMes[state]
in a text(); command
*/
var stateMes = ["Begin","If you get this one\nit will be shocking","Congrats, that's it","You failed, that's not surprising!\nRESTART"];
//color value for background stored in RGB
var stateBG = [color(111, 242, 229),color(194, 74, 194),color(0, 255, 4),color(242, 17, 32)];
var taskTwo = {
    pos: {
        x: 0,         //called on like this: .. taskTwo.pos.x
        y: 0
    },
    size: {
        w: 30,        // and taskTwo.size.w
        h: 40
    },
    avatar: getImage("avatars/marcimus-orange")  // taskTwo.avatar
};
//a function... runs when name(); is called. Can be ex funcName(10,2,"Suh");
var head = function() {
    background(stateBG[state]);
    fill(0, 0, 0);
    textSize(650/(stateMes[state].length+10));
    text(stateMes[state],100,50);
    if (state === 0){ text(ranNum,300,50); }
};
var readQlicks = function(task){
    //check for clicks from mouse, conditionally add or subtract
    if (mouseIsPressed && mouseButton === LEFT){
        if (task === 0){ ranNum -= 1; }
        else if (task === 1){ taskTwo.size.w += 1; }
    }else if (mouseIsPressed && mouseButton === RIGHT){
        if (task === 0){ ranNum += 1; }
        else if (task === 1){ taskTwo.size.h += 1; }
    }
};
//checks
var winOrLoose = function(task){
    //check for win or loss
    if (task === 0){
        if (ranNum === curious){ state = 1; }
    }else if (task === 1) {
        if ((taskTwo.size.h <= 300 && taskTwo.size.h >= 290)&&(taskTwo.size.w <= 145 && taskTwo.size.w >= 135)){
            state = 2;
        }else if ((taskTwo.size.h > 300 && taskTwo.size.w < 135)||(taskTwo.size.w > 145 && taskTwo.size.h < 290)||(taskTwo.size.w > 145 && taskTwo.size.h > 300)){
            state = 3;
        }
    }
};
//draw function is the main loop
var draw= function() {
    head();
    readQlicks(state);
    if (state === 1){
        tempX = taskTwo.size.w;
        tempY = taskTwo.size.h;
    image(taskTwo.avatar,mouseX-(tempX/2),mouseY-(tempY/2),tempX,tempY);
    //text(tempX+" : "+tempY,100,300);
    }
    winOrLoose(state);
};