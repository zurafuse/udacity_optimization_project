# Udacity Website Performance Optimization Project

I have optimized Cameron's portfolio and increase it's functionality speed. My instructions were to optimize the critical rendering path and make this page render as quickly as possible by applying the techniques I learned in the Critical Rendering Path course.

## How to Get Started

Clone my [Optimization Project repository](https://github.com/zurafuse/udacity_optimization_project) or download the zip file. Run index.html in the parent directly to start the app.


## Resources

[Udacity Website Optimization Project](https://github.com/udacity/frontend-nanodegree-mobile-portfolio) 

[Bootstrap Framework](http://getbootstrap.com/getting-started/)

[PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)

## Hosted Version of Project

[Click here to view the hosted version of Tim Horton's project.](http://zurafuse.com/vault/Udacity/OptimizationProject/)

## How to Run the Project

* Run index.html in the parent directory to start the app or visit the live hosted version at [www.zurafuse.com/vault/Udacity/OptimizationProject](http://zurafuse.com/vault/Udacity/OptimizationProject/)
* Copy and paste the url of the hosted version into the [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/) web page URL box and ensure a score of 90 or higher is achieved for both mobile and desktop versions.
* Go to [www.zurafuse.com/vault/Udacity/OptimizationProject/views/pizza.html](http://zurafuse.com/vault/Udacity/OptimizationProject/views/pizza.html) and open dev tools. In the timeline, record the action of scrolling down. Verify that the frames per second are 60 or better.
* In the timeline dev tool, make another recording. This time record the action of using the slider to change the pizza size. Verify that changing the pizza size takes less than 5 ms.

## Optimizations Performed

### images

* I created a different, smaller "pizzeria.jpg" file to use on index.html.
* I used compressed images provided by PageSpeed Insights.

### index.html

* I added the asynch tag to the google script, since google analytics does not need to block the page.
* I moved style.css and print.css to the body of the html instead of loading it as an external file. This prevented the page from being blocked.
* I referenced the googleapis style sheet with an onload attribute so it would not block the page anymore.

### pizza.html

* I moved the css files to the html body instead of referencing them as an external file.

### main.js

* I gave the mover class the will-change property.
* In the for loop that generates the ".mover" sliding pizzas, I changed the number from 200 to 60.
* In the updatePositions function, I moved the body.scrollTop calculation outside of the for loop.
* In main.js, I removed the code's functionality to check for the pizza size of each randomPizzaContainer in the for loop and simply replaced it with code that checks for 3 sizes. I moved the scope of the sizes outside of the for loop, since all pizzas on the screen will be the same size anyway. I don't even need to know what the previous width was. I do not need an offset.
* I removed the determineDx function because I felt like it was not needed.
* In the changePizzaSizes function, I moved the randomPizzaContainer DOM call to a variable outside the for loop and referenced that variable.
* In line 463, I moved the pizzasDiv variable outside the for loop. No need to define it multiple times.