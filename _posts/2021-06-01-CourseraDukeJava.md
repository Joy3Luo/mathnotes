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

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/chapelTurnRed.png)

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
![](https://joy3luo.github.io/mathnotes/pics/courseraduke/chapelTurnNoRed.png)


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
![](https://joy3luo.github.io/mathnotes/pics/courseraduke/eastereggsToLessRed.png)

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

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/astrachanAddBlackLine.png)
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
![](https://joy3luo.github.io/mathnotes/pics/courseraduke/chapelAddLineBottomGreenSquare.png)

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

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/chapelAddYellowRectangle.png)

The call result2 = topRightCorner(125, 20, picture2, 255, 0, 0)

where picture2 is the simpleImage on the left below, followed by print(result2) results in a red rectangle of width 125 and height 20 in the top right corner.

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/lionAddRedRect.png)

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

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/redChanges.png)

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

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/changeRedWithBlueGreen.png)

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

#### Changing Pages Interactively

Two \<div> ID’s

```html
<div id="d1" >
  Hello
</div>
<div id="d2" >
  Goodbye
</div>
<p>
<input type="button" value="color change" onclick = "changecolor()" >
</p>
```

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

<div id="d1" >
  Hello
</div>
<div id="d2" >
  Goodbye
</div>
<p>
<input type="button" value="color change" onclick = "changecolor()" >
</p>

Changing HTML Text

```html
function changetext() {
  var dd1 = document.getElementById("d1");
  var dd2 = document.getElementById("d2");

  dd1.innerHTML = "Bonjour";
  dd2.innerHTML = "Sayonara";
}
```

### Programming Exercise: TODO list

Creating an Interactive TODO list

In this programming exercise you will use codepen to write an interactive TODO list that you will be able to add items to, check the items off and remove the items. On the left below shows a TODO list with three items added to it, and on the right below shows the same TODO list in which the task walk dog has been checked off, swim laps has been removed from the list and write paper has been added to the list.

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/todoList1and2.png)

#### Getting Started

You can go to this codepen site and make a copy of it by using the Fork button in the bottom right corner of your browser window.

https://codepen.io/shrodger/pen/yLeGvVO

Or copy the parts from below into a new pen on CodePen to get started. Put the HTML part in the HTML part of CodePen, put the CSS part in the CSS part of CodePen, and put the JavaScript part in the JavaScript part of CodePen. After putting in the starter code below, the webpage should look like this:

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/todoListStartingWith.png)

#### Here is the HTML starter:

```html
<h1 id="myHeader">TO DO List</h1>

<!-- STEPs 1 and 2 below here  -->

 <hr>

<ul id="tasks">

  <li>

    <input type="button" class="done" onclick="markDone(this.parentNode)" value="&#x2713;" />

    <input type="button" class="remove" onclick="remove(this.parentNode)" value="&#x2715;" />

    make todo list

  </li>

 </ul>

<hr>

<!-- STEPs 8 and 9 below here  -->

<!-- STEP 13 below here  -->
```
#### Here is the CSS starter:

```css
/* remove indentation of list items */

ul {
   padding-left: 0;
}

/* remove traditional bullet from front of list items */

/* Step 3 below here */

li {
   list-style-type: none;
   background-color: #eee;
   border: 1px solid #c3c3c3;
   padding: 10px 0px 10px 5px;
}


/* Step 5 below here */

.done {

}

/* mark task as finished */
/* Step 6 below here */

li.finished {

}

input[type="text"] {
   font-size: 18px;
   width: 94%;
   padding: 10px;
}

input[type="button"] {
   font-size: 1.2em;
   margin: -6px 4px 0px 0px;
}

#addButton {
   padding: 10px;
}

/* Step 10 below here */

.aboutcolor {

}

/* Step 12 below here */

#divabout {

}
```

#### Here is the JavaScript Starter:

```javascript
function addTask () {
    var input = document.getElementById("input");
    // get current text from input field
    var newTask = input.value;
    // only add new item to list if some text was entered
    if (newTask != "") {
        // create new HTML list item
        var item = document.createElement("li");
        // add HTML for buttons and new task text
        // Note, need to use '' because of "" in HTML
        item.innerHTML = '<input type="button" class="done" onclick="markDone(this.parentNode)"  value="&#x2713;" /> ' + '<input type="button" class="remove" onclick="remove(this.parentNode)" value="&#x2715;" /> ' + newTask;

        // add new item as part of existing list
        document.getElementById("tasks").appendChild(item);

        /* Step 4 below here */
    }
}

// change styling used for given item
function markDone (item) {
    item.className = 'finished';
}

/* Step 7 below here */
function remove (item) {
    // remove item completely from document
    item.remove();
}

/* Step 11 below here */
function doAbout() {

}

/* Step 14 below here */
function clearAbout() {

}
```

Complete the Steps:

1. In the HTML part under  STEPs 1 and 2 below here  add an \<input> tag with attribute type=”button”. Include attributes id=”addButton” and value=”Add”. This input will be an Add button clicked by a mouse so you will also need to include an attribute onclick=”addTask()”, where addTask() is a function we have already started for you. Note that all these attributes must be inside the input tag, such as:

        <input  type=”button” …    >

You will see the add button appear. You can click it but nothing should happen yet.

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/todoListWithAddButton.png)

2. In the HTML part, right after the add button, add an input field so the user can type in text describing the next task. To do this add another \<input > tag, this time with type=”text”, id=”input”, and placeholder=”enter task …”. Your web page should now look like this

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/todoListWithAddEnterTask.png)

Try it out! Enter in a task and click the Add button. I entered  the phrase, sign up for yoga, and you can see below that task was added!

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/todoListWithAddedTask.png)

3. In the CSS part, let’s make the text in the list items larger. Find the definition for li, look for the comment: /* step 3 below here */. Then add another attribute to li, for font-size of 20px. Then you should see the todo items in larger font.

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/todoListWithLargerFont.png)

4. You may have noticed that after adding an item, it stays in the input field. Let’s fix that.

In the JavaScript part, you will add to the end of the function addTask(). Don’t modify the first part of this function!

At the end of the function addTask(), look for the comment  /* Step  4 below here */ and add the following two items

    a. To make the todo item typed in the input box disappear, set input.value to an empty string.
    b. Change input.placeholder to set it to a new string such as “enter next task …”

 After fixing these two and adding the task “sign up for yoga” the web page should look like:

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/todoListWithEnterNextTask.png)

5. The check mark is to check off a task, and the X is to delete a task. Let’s change the colors for the check box to be green and the X box to be red.

    a. In the CSS, look for /* Step 5 below here */ and you will see the done class started for you. The class  done is the class for the button with the check mark. Add to this class to set the background-color to green.

    b. The removeclass is the class for the button with the X mark. Right below the done class, add a class named remove and set its background-color to red.

Now the menu should look like this.

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/todoListWithAddedColorGreenRed.png)

Right now clicking the check mark doesn’t do anything but clicking the X box should delete an item.

6. When you click on the check mark, the todo item should look like it is checked off. You will add formatting to make it look checked off with a line through it and changing some color. In the CSS part under /* Step 6 below here */ add the following to the li.finished definition

    a. Set color to white
    b. Set background-color to gray
    c. Set text-decoration to line-through

Here is a picture of the list where play with cat has been checked off.

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/todoListWithAddedStrike-through.png)

7. When you click on the red X, the todo item is deleted. Let’s change that so an item has to be checked off before it can be removed from the list.

Here are the functions called in processing items. When you click on the red X the remove function is called.  When you click on the check mark the markDone() function is called. Both functions are in the javaScript part of CodePen. They look like this:

```javascript
function markDone (item) {
    item.className = 'finished';
}

function remove (item) {
    // remove item completely from document
    item.remove();
}
```

You should modify the remove function so that it only removes an item if it has been checked off.

Hint:  How do you know the item can be deleted? The item.className would have been set to ‘finished’. You need to check for that.

Try it out. Try deleting an item without checking it off. Then check it off and try deleting it.

8. In the HTML add an empty div with id=”divabout” below where it says STEPs 8 and 9 below here. This div will be used to show information about the author of this website interactively in a few more steps.

9. Right below the div you just added, add a button that says About and have onclick call a function named doAbout(). Your view may look something like this but could be slightly different on different browsers. If you click on it nothing should happen yet.

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/todoListWithAboutButton.png)

10. In the CSS pane, under  /* Step 10 below here */, complete the class named aboutcolor to set the background-color to yellow. You won’t see anything happen yet after you do this.

11. In the JavaScript pane, under /* Step 11 below here */, complete the doAbout() function. This function should change the text in the div you created with id “divabout”. The text should say that you are the author. You might put something like this: “Author is Susan Rodger” but put your name. In addition the background color of the div should change to yellow. Be sure to use the class from step 10 to do that.

After completing this function, you should be able to click on the About button and see your name and the phrase highlighted in yellow like this (it will be a bit messed up!):

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/todoListWithAuthorMessedup.png)

12. In the CSS pane under /* Step 12 below here */, complete the class name divabout to format the div to specify its width, to make its font-size larger, and to include a margin. I used a width of 300px, font-size of 20px and margin of 10px. Then the TODO list should look better, like this:

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/todoListWithAuthorFixed.png)

13. In the HTML pane, add a clear button to clear the about information, under  STEP 13 below here. This input tag should have the onclick call the function clearAbout() that you will write in the next step. After adding the button your screen may look like this:

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/todoListWithClearButton.png)

14. In the JavaScript pane, under /* Step 14 below here */, complete the clearAbout() function. This function should remove everything that was added to the div when About was clicked on. You will need to reset the text to an empty string. If there is no string to display, you won’t see any yellow, so you don’t need to do anything to the color. Then clicking on About will show information about the author and clicking on Clear will remove the information.

Now you should have an awesome interactive TODO list!

#### An Extra Challenge and More on How the Lists Work

#### First, how the lists work in this exercise

You already know how lists work in HTML. You use \<ol> or \<ul> tags and for individual items in the list you use the \<li> and \</li>. In the code we gave you we already started an unordered list with two buttons, one a check mark ( value="&#x2713;" ) and one an X mark ( value="&#x2713;" ) and that said make todo list. That HTML code is here:

```html
<ul id="tasks">
   <li>
       <input type="button" class="done" onclick="markDone(this.parentNode)" value="&#x2713;" />
       <input type="button" class="remove" onclick="remove(this.parentNode)" value="&#x2715;" />
   make todo list
   </li>
</ul>
```

In the JavaScript function addTask(), it has to recreate this \<li> item that has two buttons and a phrase. That is done by making a huge string in single quotes (since we use some double quotes in that string). Here is that function (without your additions):

```javascript
function addTask () {
    var input = document.getElementById("input");
    // get current text from input field
    var newTask = input.value;
    // only add new item to list if some text was entered
    if (newTask != "") {
        // create new HTML list item
        var item = document.createElement("li");
        // add HTML for buttons and new task text
        // Note, need to use '' because of "" in HTML
        item.innerHTML = '<input type="button" class="done" onclick="markDone(this.parentNode)"  value="&#x2713;" /> ' + '<input type="button" class="remove" onclick="remove(this.parentNode)" value="&#x2715;" /> ' + newTask;
        // add new item as part of existing list
        document.getElementById("tasks").appendChild(item);  

        // your code not shown for Step 4
      }
}
```

Here is what this procedure is doing.

In the first line it sets the variable input to the canvas. Then in the second line it assigns to the variable newTask the task the user has typed in, if they typed something in (there is nothing to add otherwise). Then the variable  item is set to a  new li item. In the next several lines, item.innerHTML is set to a huge string of the list item which includes the two buttons and the phrase of the task. There is the first button surrounded by single quotes, followed by a + since we are adding (or concatenating ) strings, followed by the second button surrounded by single quotes and a + and then newTask, the string the user entered. The next line uses the appendChild method with item to make this new list item appear. We will be learning more about lists and arrays, and appending items to lists later.

#### The Challenge - Add an Important button

Add an important button to each list item so you can mark which items should have priority. Here is an example. There are three tasks and one of them, write paper, has been highlighted as important by clicking the ! button.

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/todoListImportantButtonBlueClickedFinished.png)

Complete the Steps:

1. In the HTML add an important button right after the X button by doing the following
    a. Create an <input … /> tag with what type?
    b. Set the  class to ”important” and the  value to ”!”
    c. Set onclick to call a new function named important. (see how the other functions are called).

You should see:

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/todoListWithImportantButton.png)

2. In the CSS, create an important class with background-color lightblue. The result should look like:

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/odoListImportantButtonBlue.png)

3. In the JavaScript, write a new function named important that has one parameter nameditem. You can start with:

```javascript
// highlight item from document
function important (item) {

}
```

You should set item.className to ‘important’. Now when you click on the important icon, the whole line will be highlighted in blue!

![](https://joy3luo.github.io/mathnotes/pics/courseraduke/todoListImportantButtonBlueClicked.png)

4. Try adding a second item. It does not have the important button! That is because you modified the list item in the HTML but not the list items that are added. To do that, in the JavaScript pane,  you will need to expand the huge string in the addTask function. Do the following:

    a. Copy your \<input  …  />  important button from the HTML pane.
    b. In the JavaScript pane, in the addTask function add it at the end of that huge string, between the + and newTask;c.In the JavaScript pane, in the addTask function add it at the end of that huge string, between the + and newTask;
    d. You will need to add a + between the \<input … /> button and newTask;

Now when you add new items they should have the important button!


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
