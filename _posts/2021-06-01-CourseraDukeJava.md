---
layout: post
title: Programming - Programming Foundations with JavaScript
date: 2021-06-01 12:18 +0800
tags: [Programming]
---

<!-- Global site tag (gtag.js) - Google Analytics -->
  <script async src="https://www.googletagmanager.com/gtag/js?id=G-TG0XJZG53F"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());

    gtag('config', 'G-TG0XJZG53F');
  </script>

### Variables
declare a new Variable,
> var x = 3;

more variables
> var y = 4;
var z = x + 2 * y;

update variables
> x = z - 1;
y = y * 2;

more complex
> var fgImage = new SimpleImage("drewRobert.png");
var bgImage = new SimpleImage("dinos.png");

calling methods:Syntax
> var fgImage = new SimpleImage("drewRobert.png");
var w = fgImage.getWidth();
var h = fgImage.getHeight();

Some Methods Have Parameters
> var pixel = fgImage.getPixel(0,0);

### Functions
> function square(x) {
 var ans = x * x;
 return ans;
}
\
var y = square(4);

#### Exercise 1
Make a Phrase From Three Words
Write a function named phrase3words that puts three words together into a phrase that is of type string with blanks between the words. The function phrase3words has three parameters named value1, value2 andvalue3. This function concatenates the words together into one string that has value1 first, followed by a blank, followed by value2, followed by a blank, followed by value3.


> function phrase3words(value1, value2, value3) {
    var answer = value1 + " " + value2 + " " + value3;    return answer;
}
\
var result1 = phrase3words("smile","at","everyone");
print(result1);
var result2 = phrase3words("everyone","wave", "back");
print(result2);
var result3 = phrase3words("coding","is", "fun");
print(result3);

OUTPUT:

smile at everyone
everyone wave back
coding is fun

#### Exercise 2 - Format a name
Write a function namedreformatName that puts a name together in a specific format.  The function reformatName has two parameters named first and last, representing the first and last names. This function puts the names together into one string that has the last name first, followed by a comma and blank, and then followed by the first name.

For example, the call reformatName("Susan", "Rodger") returns the string "Rodger, Susan", and the call reformatName("Robert", "Duvall") returns the string "Duvall, Robert".

>function reformatName(first, last) {
    var answer = last + "," + first;
    return answer;
}
\
var result = reformatName("Susan", "Rodger");
print(result);
result = reformatName("Robert", "Duvall");
print(result);

OUTPUT:

Rodger, Susan
Duvall, Robert

#### Exercise 3 - Number of pixels in an image
Write a function named numberPixels that calculates the total number of pixels in an image. The function numberPixels has one parameter named namefile, which is a string that is the name of an image file. This function calculates and returns the total number of pixels in the specified image filename.

For example, the call numberPixels("chapel.png") returns 71148, and the call numberPixels("dinos.png") returns 2073600. Both of these are images on the dukelearntoprogram.com website. For each image on that website it also displays the size of that image. That website shows that chapel.png has 231 pixels in width and 308 pixels in height, and 231\*308 is 71148 total pixels. That website also shows that dinos.png has 1920 pixels in with and 1080 pixels in height, and 1920*1080 is 2073600 total pixels.

>function numberPixels(namefile) {
    var someImg = new SimpleImage(namefile);
    var height = someImg.getHeight();
    var width = someImg.getWidth();
    var answer = height*width;
    return answer
}
\
var result = numberPixels("chapel.png");
print(result);
result = numberPixels("dinos.png");
print(result);

OUTPUT:

71148
2073600


#### Exercise 4 - Perimeter of an image
Write a function named perimeter that calculates the number of pixels in the perimeter of an image. The perimeter is the number of pixels on the edge of the image, from all four sides. The function perimeter has one parameter named imageName, which is a string that is the name of an image file. This function calculates and returns the perimeter in the specified image filename.

For example, the image "rodger.png" has 315 pixels in width and 424 pixels in height. That means it has 315 pixels on the bottom, 315 on the top, 424 on the right side and 424 on the left side. The perimeter of this image is 315 + 315 + 424 + 424 =  1478. The call perimeter("rodger.png") returns 1478.

>function perimeter(imageName) {
    var someImg = new SimpleImage(imageName);
    var height = someImg.getHeight();
    var width = someImg.getWidth();
    var answer = height*2 + width*2;
    return answer
}
\
print(perimeter("rodger.png"));

OUTPUT:

1478

#### Exercise 5 - Print the RGB values of a pixel
Write a function named printPixel that prints the red, blue and green values of a pixel, in that order, one on each line, and identifies each one.  The function printPixel has three parameters,  namefile, which is a string that is the name of an image file, and xpos and ypos that are numbers representing the x and y coordinates of the pixel location. Consider using the SimpleImage methods getRed, getGreen, and getBlue. Since this function is printing values, it does not need a return statement.

Note that in the image drewgreen.png, Drew is standing in the middle and the background is bright green. So the first pixel printed at x and y location (10,10) is near the edge and is bright green. For its red, green and blue values, it has all green (255), no blue (0)  and only a tiny bit of red (1). The second pixel printed is in the middle of the image and is some part of Drew.
