# Web Page for Paint Application

## AIM:

To design a static website for Paint Application using HTML5 canvas.

## DESIGN STEPS:

### Step 1:

Requirement collection.

### Step 2:

Creating the layout using HTML,CSS and canvas.

### Step 3:

Write javascript to capture move events.

### Step 4:

Perform the drawing operation based on the user input.

### Step 5:

Validate the layout in various browsers.

### Step 6:

Validate the HTML code.

### Step 6:

Publish the website in the given URL.

## PROGRAM :

```

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Paint Application</title>
    <style>
      * {
        box-sizing: border-box;
        font-family: Arial, Helvetica, sans-serif;
      }
      body {
        background-color: rgb(247, 111, 213);
        color: black;
      }
      .container {
        width: 1080px;
        margin-left: auto;
        margin-right: auto;
      }
      .content {
        display: block;
        width: 100%;
        background-color:rgb(236, 199, 228);
        min-height: 800px;
        margin: 100px 50px 0px 0px;
        padding-top: 20px;
      }
      h1 {
        text-align: center;
      }
      .footer {
        display: inline-block;
        width: 100%;
        height: 40px;
        margin: 0px 0px 0px 0px;
        text-align: right;
        padding-top: 10px;
        color: #000000;
        font-style: italic;
        font-size: 30px;
        padding-right: 10px;
        padding-top: 5px;
      }
      canvas {
        margin-left: 40px;
        margin-right: 40px;
      }
      .toolbar {
        text-align: center;
      }
      .paint-canvas {
        
        margin-left: 40px;
        margin-right: 40px;
      }
      .color-picker {
        margin: 1rem 1rem 0 1rem;
      }
    </style>
    <script type="text/javascript">
    var shape;
    function myClickEvent (e) {
      var message;
    //message = "X=" + e.offsetX + ",Y=" e.offsetY  ;
    //alert(message);
    ctx.beginPath();
    if (shape == 0) {
      ctx.arc (e.offsetX, e.offsetY, 30, 0, 2 * Math.PI);
      ctx.strokeStyle = "#0000FF";
      ctx.linewidth = 3;
    } else if (shape == 1) {
      ctx. rect(e.offsetX, e.offsetY, 50, 50);
      ctx.strokeStyle = "#FF0000";
      ctx.linewidth = 3;
    } 
    if (shape == 2){
      ctx.moveTo(260, 40);
      ctx.lineTo(e.offsetX, e.offsetY, 500, 40);
    }else if (shape == 3) {
      ctx. rect(e.offsetX, e.offsetY, 100, 50);
      ctx.strokeStyle = "#FF0000";
      ctx.linewidth = 3;
    }
    if (shape == 4){
      ctx.clearRect(0, 0, e.offsetX, e.offsetY);
    }
    ctx.stroke();
  } 
  function circleclicked() {
    shape = 0;
  }
  function squareclicked () {
    shape = 1;
  }
  function lineclicked () {
    shape = 2;
  }
  function rectangleclicked () {
    shape = 3;
  }
  function clearclicked () {
    shape = 4;
  }
  </script>
  </head>
  <body>
    <div class="container">
      <div class="content">
        <h1>Drawing Application</h1>
        <div class="toolbar">
          <input type="button" id="circle" value="Circle"/>
          <input type="button" id="square" value="Square"/>
          <input type="button" id="line" value="Line"/>
          <input type="button" id="rectangle" value="Rectangle"/>
          <input type="button" id="clear" value="Clear"/>
          <input type="color"  class="js-color-picker  color-picker">
          <input type="range" class="js-line-range" min="1" max="72" value="1">
          <label class="js-range-value">1</label>Px

        </div>
      </br>
        <canvas
        class="js-paint  paint-canvas"
        id="myCanvas"
        width="1000"
        height="600"
        style="border: 1px solid #000000;"
        >
      </canvas>
          <div class="footer">
            Developed by Sudharshna Lakshmi.S
          </div>
      </div>
    </div>

    <script>
       var c = document.getElementById("myCanvas");
       
       var ctx = c.getContext("2d");  
       
       c.addEventListener("click",myClickEvent);
       document
         .getElementById("circle")
         .addEventListener("click", circleclicked);
       document
         .getElementById("square")
         .addEventListener("click", squareclicked);
       document
         .getElementById("line")
         .addEventListener("click", lineclicked); 
       document
         .getElementById("rectangle")
         .addEventListener("click", rectangleclicked); 
       document
         .getElementById("clear")
         .addEventListener("click", clearclicked); 

         const paintCanvas = document.querySelector( '.js-paint' );
         const context = paintCanvas.getContext( '2d' );
         context.lineCap = 'round';
         
         const colorPicker = document.querySelector( '.js-color-picker');
         
         colorPicker.addEventListener( 'change', event => {
         context.strokeStyle = event.target.value; 
        } );
        const lineWidthRange = document.querySelector( '.js-line-range' );
        const lineWidthLabel = document.querySelector( '.js-range-value' );
        
        lineWidthRange.addEventListener( 'input', event => {
        const width = event.target.value;
        lineWidthLabel.innerHTML = width;
        context.lineWidth = width;
      } );
      let x = 0, y = 0;
      let isMouseDown = false;
      const stopDrawing = () => { isMouseDown = false; }
      const startDrawing = event => {
        isMouseDown = true;   
        [x, y] = [event.offsetX, event.offsetY];  
      }
      const drawLine = event => {
        if ( isMouseDown ) {
          const newX = event.offsetX;
          const newY = event.offsetY;
          context.beginPath();
          context.moveTo( x, y );
          context.lineTo( newX, newY );
          context.stroke();
          //[x, y] = [newX, newY];
          x = newX;
          y = newY;
        }
      }
      paintCanvas.addEventListener( 'mousedown', startDrawing );
      paintCanvas.addEventListener( 'mousemove', drawLine );
      paintCanvas.addEventListener( 'mouseup', stopDrawing );
      paintCanvas.addEventListener( 'mouseout', stopDrawing );
      //alert("Hi, Canvas Drawing");
      </script>
       
 </body>
</html>

```

## OUTPUT:

![output](.//output1.png)

![output](.//output2.png)

## Result:

Thus a website is designed and validated for paint application using HTML5 canvas.
