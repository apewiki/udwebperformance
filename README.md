## Website Performance Optimization portfolio project

Your challenge, if you wish to accept it (and we sure hope you will), is to optimize this online portfolio for speed! In particular, optimize the critical rendering path and make this page render as quickly as possible by applying the techniques you've picked up in the [Critical Rendering Path course](https://www.udacity.com/course/ud884).

To get started, check out the repository, inspect the code,

### Getting started

####Part 1: Optimize PageSpeed Insights score for index.html

Some useful tips to help you get started:

1. Check out the repository
1. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

1. Open a browser and visit localhost:8080
1. Download and install [ngrok](https://ngrok.com/) to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ngrok 8080
  ```

1. Copy the public URL ngrok gives you and try running it through PageSpeed Insights! [More on integrating ngrok, Grunt and PageSpeed.](http://www.jamescryer.com/2014/06/12/grunt-pagespeed-and-ngrok-locally-testing/)

Profile, optimize, measure... and then lather, rinse, and repeat. Good luck!

My reflection on task 1:
	- Add async attribute to javascript not used for DOM construction
	- Move inline javascript from head to bottom of html body
	- Set media query to print for print.css
	- Remove link to google fonts, inline latin subset of used fonts to CSS file
	- Inline entire style.css to index.html
	- Removed unused css rules
	- Resize and optimize pizzareia.jpg, create and optimize pizzareia_sm.jpg of smaller dimensions for portfolio page
	- Optimize all images (pizzareia.jpg, pizzareia_sm.jpg, profilepic.jpg) using jpegtran

Results: I was able to achieve pagespeed score 95 on pagespeed insights.


####Part 2: Optimize Frames per Second in pizza.html

To optimize views/pizza.html, you will need to modify views/js/main.js until your frames per second rate is 60 fps or higher. You will find instructive comments in main.js. 

My reflection on task 2:
	- main.js: move unchanged variable scrollTop outside the loop of updatePosition function
	- main.js: uses getElelmentsByClassName or other getElement(s)By... function instead of querySelector(All) to reference DOM elements
	- main.js: moved unchanged variables dx and newwidth outside the loop of changePizzaSizes function
	- Added backface-visibility: hidden in style.css
	- Inlined style.css in pizza.html since css file is small
	- Minified bootstrap-grid.css to bootstrap-grid-min.css using YUICompression
	- Minified main.js to main-min.js using YUICompression
	- Optimized pizza.png using optipng, but there was little reduction of file size
	- reduced number of floating pizzas to 50 from 200

Results:
	- Improved scrolling speed. On mobile, over 90% of the time scrolling at over 60 FPS. On desktop, scrolling much faster than 60 FPS. 
	- Improved pizza resizing. On mobile at 3-4 ms on average, on desktop 1-2 ms
	- Improved score on pagespeed insights for pizza.html page, 87 on mobile, 93 on desktop

Issues:
    - Not sure how to further improve pizza page load time. On mobile, around 100 ms, on desktop around 28 ms
    - I was not clear about the requirements of this project initially. For instance, I didn't realize that resizing pizza was part of the requirement until I first submitted the project. Nevertheless, it is not excuse not to fix the obvious problem there. 
    - For the portfolio page, if I didn't inline style.css, I could only score 87 on mobile. Is there a way to score above 90 without inlining css?
    - For pizza page scrolling, FPS measurements fluctuate on mobile, occasionally certain frames could be below 60 FPS. Backface-visibility trick works well with desktop, not mobile. Anyway to improved further?
    - What else can be done in addition to minifcation and image optimization to improve pizza load speed? Still takes 100 ms to load on mobile. I tried to resize pizza.png for moving pizzas to 85x110, but it did not affect load time significantly, so I decided not to use this approach as i have to load one small pizza image and one regular size image for the static one. 

You might find the FPS Counter/HUD Display useful in Chrome developer tools described here: [Chrome Dev Tools tips-and-tricks](https://developer.chrome.com/devtools/docs/tips-and-tricks).

### Optimization Tips and Tricks
* [Optimizing Performance](https://developers.google.com/web/fundamentals/performance/ "web performance")
* [Analyzing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp.html "analyzing crp")
* [Optimizing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path.html "optimize the crp!")
* [Avoiding Rendering Blocking CSS](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css.html "render blocking css")
* [Optimizing JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript.html "javascript")
* [Measuring with Navigation Timing](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp.html "nav timing api"). We didn't cover the Navigation Timing API in the first two lessons but it's an incredibly useful tool for automated page profiling. I highly recommend reading.
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads.html">The fewer the downloads, the better</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer.html">Reduce the size of text</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization.html">Optimize images</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching.html">HTTP caching</a>

### Customization with Bootstrap
The portfolio was built on Twitter's <a href="http://getbootstrap.com/">Bootstrap</a> framework. All custom styles are in `dist/css/portfolio.css` in the portfolio repo.

* <a href="http://getbootstrap.com/css/">Bootstrap's CSS Classes</a>
* <a href="http://getbootstrap.com/components/">Bootstrap's Components</a>

### Sample Portfolios

Feeling uninspired by the portfolio? Here's a list of cool portfolios I found after a few minutes of Googling.

* <a href="http://www.reddit.com/r/webdev/comments/280qkr/would_anybody_like_to_post_their_portfolio_site/">A great discussion about portfolios on reddit</a>
* <a href="http://ianlunn.co.uk/">http://ianlunn.co.uk/</a>
* <a href="http://www.adhamdannaway.com/portfolio">http://www.adhamdannaway.com/portfolio</a>
* <a href="http://www.timboelaars.nl/">http://www.timboelaars.nl/</a>
* <a href="http://futoryan.prosite.com/">http://futoryan.prosite.com/</a>
* <a href="http://playonpixels.prosite.com/21591/projects">http://playonpixels.prosite.com/21591/projects</a>
* <a href="http://colintrenter.prosite.com/">http://colintrenter.prosite.com/</a>
* <a href="http://calebmorris.prosite.com/">http://calebmorris.prosite.com/</a>
* <a href="http://www.cullywright.com/">http://www.cullywright.com/</a>
* <a href="http://yourjustlucky.com/">http://yourjustlucky.com/</a>
* <a href="http://nicoledominguez.com/portfolio/">http://nicoledominguez.com/portfolio/</a>
* <a href="http://www.roxannecook.com/">http://www.roxannecook.com/</a>
* <a href="http://www.84colors.com/portfolio.html">http://www.84colors.com/portfolio.html</a>
