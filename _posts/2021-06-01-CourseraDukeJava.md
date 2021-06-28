---
layout: post
title: Programming - Programming Foundations with JavaScript
date: 2021-06-01 12:18 +0800
tags: [Programming]
toc:  true
---

<!-- Global site tag (gtag.js) - Google Analytics -->
  <script async src="https://www.googletagmanager.com/gtag/js?id=G-TG0XJZG53F"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());

    gtag('config', 'G-TG0XJZG53F');
  </script>

### JavaScript
#### Variables
declare a new Variable,
```javascript
var x = 3;
```
more variables
```javascript
var y = 4;
var z = x + 2 * y;
```
update variables
```javascript
x = z - 1;
y = y * 2;
```
more complex
```javascript
var fgImage = new SimpleImage("drewRobert.png");
var bgImage = new SimpleImage("dinos.png");
```
calling methods:Syntax
```javascript
var fgImage = new SimpleImage("drewRobert.png");
var w = fgImage.getWidth();
var h = fgImage.getHeight();
```
Some Methods Have Parameters
```javascript
var pixel = fgImage.getPixel(0,0);
```

#### Functions
```javascript
function square(x) {
 var ans = x * x;
 return ans;
}

var y = square(4);
```
### Exercises
#### Exercise 1 - Make a Phrase From Three Words
Write a function named phrase3words that puts three words together into a phrase that is of type string with blanks between the words. The function phrase3words has three parameters named value1, value2 andvalue3. This function concatenates the words together into one string that has value1 first, followed by a blank, followed by value2, followed by a blank, followed by value3.

```javascript
function phrase3words(value1, value2, value3) {
    var answer = value1 + " " + value2 + " " + value3;    return answer;
}

var result1 = phrase3words("smile","at","everyone");
print(result1);
var result2 = phrase3words("everyone","wave", "back");
print(result2);
var result3 = phrase3words("coding","is", "fun");
print(result3);
```

OUTPUT:

smile at everyone

everyone wave back

coding is fun

#### Exercise 2 - Format a name
Write a function namedreformatName that puts a name together in a specific format.  The function reformatName has two parameters named first and last, representing the first and last names. This function puts the names together into one string that has the last name first, followed by a comma and blank, and then followed by the first name.

For example, the call reformatName("Susan", "Rodger") returns the string "Rodger, Susan", and the call reformatName("Robert", "Duvall") returns the string "Duvall, Robert".

```javascript
function reformatName(first, last) {
    var answer = last + "," + first;
    return answer;
}

var result = reformatName("Susan", "Rodger");
print(result);
result = reformatName("Robert", "Duvall");
print(result);
```

OUTPUT:

Rodger, Susan

Duvall, Robert

#### Exercise 3 - Number of pixels in an image
Write a function named numberPixels that calculates the total number of pixels in an image. The function numberPixels has one parameter named namefile, which is a string that is the name of an image file. This function calculates and returns the total number of pixels in the specified image filename.

For example, the call numberPixels("chapel.png") returns 71148, and the call numberPixels("dinos.png") returns 2073600. Both of these are images on the dukelearntoprogram.com website. For each image on that website it also displays the size of that image. That website shows that chapel.png has 231 pixels in width and 308 pixels in height, and 231\*308 is 71148 total pixels. That website also shows that dinos.png has 1920 pixels in with and 1080 pixels in height, and 1920*1080 is 2073600 total pixels.

```javascript
function numberPixels(namefile) {
    var someImg = new SimpleImage(namefile);
    var height = someImg.getHeight();
    var width = someImg.getWidth();
    var answer = height*width;
    return answer
}

var result = numberPixels("chapel.png");
print(result);
result = numberPixels("dinos.png");
print(result);
```

OUTPUT:

71148

2073600

#### Exercise 4 - Perimeter of an image
Write a function named perimeter that calculates the number of pixels in the perimeter of an image. The perimeter is the number of pixels on the edge of the image, from all four sides. The function perimeter has one parameter named imageName, which is a string that is the name of an image file. This function calculates and returns the perimeter in the specified image filename.

For example, the image "rodger.png" has 315 pixels in width and 424 pixels in height. That means it has 315 pixels on the bottom, 315 on the top, 424 on the right side and 424 on the left side. The perimeter of this image is 315 + 315 + 424 + 424 =  1478. The call perimeter("rodger.png") returns 1478.

```javascript
function perimeter(imageName) {
    var someImg = new SimpleImage(imageName);
    var height = someImg.getHeight();
    var width = someImg.getWidth();
    var answer = height*2 + width*2;
    return answer
}

print(perimeter("rodger.png"));
```

OUTPUT:

1478

#### Exercise 5 - Print the RGB values of a pixel
Write a function named printPixel that prints the red, blue and green values of a pixel, in that order, one on each line, and identifies each one.  The function printPixel has three parameters,  namefile, which is a string that is the name of an image file, and xpos and ypos that are numbers representing the x and y coordinates of the pixel location. Consider using the SimpleImage methods getRed, getGreen, and getBlue. Since this function is printing values, it does not need a return statement.

Note that in the image drewgreen.png, Drew is standing in the middle and the background is bright green. So the first pixel printed at x and y location (10,10) is near the edge and is bright green. For its red, green and blue values, it has all green (255), no blue (0)  and only a tiny bit of red (1). The second pixel printed is in the middle of the image and is some part of Drew.

```javascript
function printPixel(nameImage, xpos, ypos) {
    var someImg = new SimpleImage(nameImage);
    var red = " red is " + someImg.getRed(xpos,ypos);
    var green = " green is " + someImg.getGreen(xpos,ypos);
    var blue = " blue is " + someImg.getBlue(xpos,ypos);
    print(red);
    print(green);
    print(blue);
}

printPixel("drewgreen.png",10, 10);
printPixel("drewgreen.png",250, 500);
```

OUTPUT:

red is 1

green is 255

blue is 0

red is 102

green is 90

blue is 80

#### Exercise 6 - Sum of the RGB values for a Pixel
Write a function named sumPixel that calculates and returns the sum of the red, blue and green values of a pixel.  The function sumPixel has three parameters,  namefile, which is a string that is the name of an image file, and xpos and ypos that are numbers representing the x and y coordinates of the pixel location. Since this function is returning a value, it should NOT have a print statement in the function, and it should have a return statement.

Consider the image drewgreen.png.  The pixel at location (250,500) has red component 102, green component 90 and blue component 80. The call  sumPixel("drewgreen.png", 250, 500) should return 102+90+80 = 272. The pixel at location (10,10) has red component 1, green component 255 and blue component 0. The call  sumPixel("drewgreen.png", 10, 10) should return 1 + 255 + 0 = 256.

```javascript
function sumPixel(nameOfImage, xpos, ypos) {
    var someImg = new SimpleImage(nameOfImage);
    var answer = someImg.getRed(xpos,ypos) + someImg.getGreen(xpos,ypos) + someImg.getBlue(xpos,ypos);
    return answer;
}

var answer = sumPixel("drewgreen.png", 250, 500);
print(answer);
answer = sumPixel("drewgreen.png",10, 10);
print(answer);
```

OUTPUT:

272

256


#### For Loops
```javascript
for ( var pixel of img.values() ) {
 var newG = 255 - pixel.getGreen();
 pixel.setGreen(newG);
}
```

#### Conditional Execution
```javascript
if (x < y) {
 z = 2;
}
else {
 a = y + 1;
 y = x - 3;
}
```

```javascript
var img = new SimpleImage("small.png");
for (var pixel of img.values()) {
 if (pixel.getX() >= img.getWidth()/2){
 pixel.setRed(pixel.getRed()/2);
 }
 else {
 pixel.setBlue(pixel.getRed());
 }
}
```

### Exercises
#### Exercise 1 - Turn the chapel red.
Write code that starts with the image “chapel.png” shown below on the left and turns the red part of every pixel to the highest red value possible, resulting in the image shown on the right.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/FIjLP7q0Rj-Iyz-6tPY_9Q_1065ebf372874c9b9aa909d67b2a550e_chapelTurnRed.png?expiry=1623196800000&hmac=PhJsz1iiOzob773mT81-Vb6KcLi8TlGt94ir5mJPMRE)

```javascript
var image = new SimpleImage("chapel.png");
for (var pixel of image.values())
{
    pixel.setRed(255);
}
print(image);
```

#### Exercise 2 - Remove all the red
Write code that starts with the image “chapel.png” shown below on the left and removes all the red, resulting in the image shown on the right. You will notice that in the resulting image you will mostly see blue and green colors.
![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/WVAWujiLQ2CQFro4iyNgEw_3ae809d7f77f435fa2631b0306020d1a_chapelTurnNoRed.png?expiry=1623196800000&hmac=23c8_e9mQCFzzbtKxpc1mPq7yKLcjyW-yN5Kp-Ai0BA)

```javascript
var image = new SimpleImage("chapel.png");
for (var pixel of image.values())
{
    pixel.setRed(0);
}
print(image);
```

#### Exercise 3 - Turn the eggs less red
Write code that starts with the image “eastereggs.jpg” shown below on the left and reduces all the red pixel values that are greater than 70 to 70, resulting in the image shown on the right. You will notice that in the resulting image you will see some reddish colors but no bright reds.
![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/Js7ajhvQQoiO2o4b0PKI-w_00473ba9f0664c67b2b1638e6cb90ce9_eastereggsToLessRed.png?expiry=1623196800000&hmac=kALR4H0O_bqaPf9mXXJaUb_oJOu5XEiwpOBu-92yMu4)
```javascript
var image = new SimpleImage("eastereggs.jpg");
for (var pixel of image.values()){
    if(pixel.getRed() > 70){
        pixel.setRed(70);
    }
}
print(image);
```

#### Exercise 4 - Add Thick Black Line to Bottom of Owen
Write code that starts with the image “astrachan.jpg” shown below on the left and replaces the bottom ten rows with black pixels, resulting in the image shown on the right. Note that the color black has a red value of 0, a green value of 0 and a blue value of 0. Also note that the pixel in the top left corner has x-value 0 and y-value 0.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/6GHq97J_TIqh6veyfzyK3Q_bf6ffb938906460eac33aa23443c8664_astrachanAddBlackLine.png?expiry=1623196800000&hmac=xOLKcfvvsBnMATqT1ML3Z7YeZUxnpVdo_ezNdR2KSU4)
```javascript
var image = new SimpleImage("astrachan.jpg");
for (var pixel of image.values()){
    if(pixel.getY() >= image.getHeight()-10){
        pixel.setRed(0);
        pixel.setGreen(0);
        pixel.setBlue(0)
    }
}
print(image);
```

#### Exercise 5 - Green square in top left corner
Write code that starts with the image “chapel.png” shown below on the left, and replaces the top left corner with an all green square of size 50 by 50, resulting in the image on the right below.
![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/IwB2vkS3SWuAdr5Et5lrgA_6118176763b44fa2bb992e036666e79d_chapelAddLineBottomGreenSquare.png?expiry=1623196800000&hmac=OB5VPdEsVHOvjWeA8KUeSQP19LdOgaP6W0NmCzCa-Zc)

```javascript
var image = new SimpleImage("chapel.png");
for (var pixel of image.values()){
    if(pixel.getY() <= 51 && pixel.getX() <= 51){
        pixel.setRed(0);
        pixel.setGreen(255);
        pixel.setBlue(0)
    }
}
print(image);
```

#### Exercise 6 - Rectangle of any color in top right corner
Write a function named topRightCorner that puts a rectangle of a specified color and size in the top right corner of the image. The function topRightCorner has six parameters named cornerWidth, cornerHeight, someImage, red, green, and blue. This function replaces the top right corner of the image someImage with a rectangle of height cornerHeight and width cornerWidth, and color that has red, green and blue numeric values.

For example, the call result = topRightCorner(30, 60, picture, 255, 255, 0)

where picture is the simpleImage on the left below, followed by print(result) results in a yellow rectangle (all red and all green makes yellow) of width 30 and height 60  in the top right corner.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/9mOuzDSKQ4Gjrsw0ioOBeA_baa7c3bcb2094b9c8b0cff987510b32d_chapelAddYellowRectangle.png?expiry=1623196800000&hmac=yzFTyGI5K285AL8saw_Gokj_lua3zxC_f4NTxSSoZg8)

The call result2 = topRightCorner(125, 20, picture2, 255, 0, 0)

where picture2 is the simpleImage on the left below, followed by print(result2) results in a red rectangle of width 125 and height 20 in the top right corner.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/mrb2FEPsRfW29hRD7MX1sg_66b90ea7c66545c8990bd55342dbb140_lionAddRedRect.png?expiry=1623196800000&hmac=qMsiASX6gR3ivmBLlVrS3PrA7EMbz5XzsIHIjAHnO7E)

```javascript
function topRightCorner(cornerWidth, cornerHeight, someImage, red, green, blue) {
    var image = new SimpleImage(someImage);
    for (var pixel of image.values()){
        if(pixel.getY() <= cornerHeight && pixel.getX() >= image.getWidth()-cornerWidth){
        pixel.setRed(red);
        pixel.setGreen(green);
        pixel.setBlue(blue)
        }
    }
    return image;
}

var picture = new SimpleImage("chapel.png");
var result = topRightCorner(30, 60, picture, 255, 255, 0);
print(result);
var picture2 = new SimpleImage("smalllion.jpg");
var result2 = topRightCorner(125, 20, picture2, 255, 0, 0);
print(result2);
```

#### Exercise 7 - Changes in Red
Write the function named changeRed that draws a rectangle of width 256 showing all the changes of the color red, from left to right repeatedly, while blue and green are both set to 0. With height set to 200, the resulting image is shown here.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/Ef4YDUEdS6--GA1BHXuv1w_d55027e0996241b8ab33d21d5ac860f4_redChanges.png?expiry=1623196800000&hmac=2UL8WjHPPIU6VFDMQKrc624HrwXN8Cb7L0HgMm-OscY)

Here are more details. When one loops over pixels with a for loop, they are processed row by row starting with the top row and in each row they are processed from left to right. This function should start at the first pixel with red set to 0 and increment red by 1 with each new pixel it processes. Since the width is 256, the range of the color red goes from 0 to 255 as the row is processed. After the red reaches 255, it should be reset back to 0 for the next row. With red set to 0 on the right it looks like black. As the red number increases by 1 each time it eventually looks like bright red.

```javascript
function changeRed(width, height) {
    var picture = new SimpleImage(width, height);
    var red = 0;
    for (var pixel of picture.values()){
        pixel.setGreen(0);
        pixel.setRed(red);
        pixel.setBlue(0);
        if(pixel.getX()<255){
            red++;
        }else{
            red=0;
        }
    }
    return picture;
}

var result = changeRed(256,200);
print(result);
```

#### OPTIONAL: ONE CHANGE
Modify the function changeRed so that numbers for blue and green can also be passed in. Then the call with blue set to 100 and green set to 200 results in the picture:

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/K-O1dgpoSvujtXYKaIr7oA_523f956c46334c80a9e086bbe7f658ce_changeRedWithBlueGreen.png?expiry=1623196800000&hmac=7ho4TyQZD7_yQaBkVBu-tYBrFQaGpdk0wbaDx0hlGjU)

```javascript
function changeRed(width, height) {
    var picture = new SimpleImage(width, height);
    var red = 0;
    for (var pixel of picture.values()){
        pixel.setGreen(200);
        pixel.setRed(red);
        pixel.setBlue(100);
        if(pixel.getX()<255){
            red++;
        }else{
            red=0;
        }
    }
    return picture;
}

var result = changeRed(256,200);
print(result);
```

#### Translating to Code
```javascript
//Start with the foreground image you want(fgImage)
var fgImage = new SimpleImage("drewRobert.png");
//... and with the background image you want(bgImage)
var bgImage = new SimpleImage("dinos.png");
//Make a blank image of the same size(output)
var output = new SimpleImage(fgImage.getWidth(), fgImage.getHeight());

//write code for each of these steps:
//For each pixel (currentPixel) in fgImage
for(var pixel of fgImage.values()){
  //Look at currentPixel and if it is green,
  if(pixel.getGreen() > 240){
    //Look at same position in bgImage
    var x = pixel.getX();
    var y = pixel.getY();
    var bgPixel = bgImage.getPixel(x,y);
    //and set output's corresponding pixel to bgImage's pixel
    output.setPixel(x,y,bgPixel);
  }
  //Otherwise: set output's corresponding pixel to currentPixel
  else{
    output.setPixel(pixel.getX(), pixel.getY(), pixel);
  }
  print(output);
}
```

#### Thinking Critically about Your Program

```javascript
var bb = new SimpleImage("duke_blue_devil.png");
for (var pp of bb.values()) {
 if(pp.getRed() < 200 && pp.getGreen() < 150 && pp.getBlue() != 255){
 pp.setRed(0);
 pp.setGreen(255);
 pp.setBlue(100);
 }
}
print(bb);
```

### Event-Driven programming
####Buttons with Divs

 \<input> tag

```html
<input type = "button"
value = "change"
onclick = "alert('clicked button')" >
```
<p>
<input type = "button"
value = "change"
onclick = "alert('clicked button')" >
</p>

Calling a JavaScript Function

```html
<input type = "button"
value = "change"
onclick = " dochange() " >

function dochange() {
  alert('clicked button');
}
```

####Changing Pages Interactively

Two \<div> ID’s

```html
<div id="d1" >
 Hello
</div>
<div id="d2" >
 Goodbye
</div>
<p>
<input type="button" value="color change"
 onclick = "changecolor()" >
</p>
```

<div id="d1" >
 Hello
</div>
<div id="d2" >
 Goodbye
</div>
<p>
<input type="button" value="color change"
 onclick = "changecolor()" >
</p>

Getting HTML Elements

```javascript
function changecolor() {
  var dd1 = document.getElementById("d1");
  var dd2 = document.getElementById("d2");
  dd1.className = "blueback";
  dd2.className = "yellowback";
}
```
Setting the CSS Class

```css
.yelloback {
  background-color: yellow:
}

.blueback {
  background-color: lightblue;
}
```

###

```html

```

###

```html

```
###

```html

```
###

```html

```
###

```html

```
###

```html

```


###

```javascript

```


###

```javascript

```



###

```javascript

```



###

```javascript

```


####

![]()

```javascript

```


####

![]()

```javascript

```

####

![]()

```javascript

```


####

![]()

```javascript

```








####

![]()

```javascript

```









####

![]()

```javascript

```











####

![]()

```javascript

```










####

![]()

```javascript

```
