# XSS Game Lab 3

## Level 1 

>The goal here is tp inject a script into the search box of the provided frame that prompts an alert onto the webpage. 
>The script used here is: 
> - `<script>alert("Hello")</script>`
>
> Which creates the following alert...
>
>// Insert image file
>
>The reason this works is because the webpage script is not configured to properly sanitize the user input; which then causes the input to be read as script, and executed it.


## Level 2

>The goal here is to again inject an alert into the window. This time the `<script>` tag does not work, 
>but if we create a post using the `<h1>` html tag you
>notice that we can post a message that displays with the Heading 1 format. This tells us that the posted message 
>can still pass the html even though the `<script>` tag does not work. Upon inspection of the code you can see 
>that html is also being passed thought the welcome message as well. Following the hints provided you find that you can 
>use the `img` tag to run through a URL that does not work and creates an error which allows you to insert an `alert()`
>
> - `<img src="" onerror=alert("Hello")>`
>
>Which creates the following alert...
>
>// Insert image file

## Level 3
>The goal for this level is to inject a script to prompt an alert in the app. There is no user text input
>this level so we must manipulate the URL in order to inject the JavaScript alert. As noted in the Hint
>section, we need to check out the code section where the script handles user input. We can see that the
>`window.onload object` gets a URL fragment and used the `choosetab function` to append the fragment to
>the image tag, and load the new tag into the page; as shown below.
> ```bash
> window.onload = function() {
> chooseTab(unescape(self.location.hash.substr(1)) || "1");
> }
> ```

> ```bash
> function chooseTab(num) {
> // Dynamically load the appropriate image.
> var html = "Image " + parseInt(num) + "<br>";
> html += "<img src='/static/level3/cloud" + num + ".jpg' />";
> $('#tabContent').html(html);
> ```

>In order to manipulate the URL we need to do something similar to the previous level where we use the img tag's
>`src` attribute to trigger an `onerror`attribute which will prompt our JavaScript alert. We execute the
>manipulation by closing off the `src` attribute with a single quote and finish off the code by adding a `;//` to
>close the `img` tag and comment out the rest. Click on a different image tab and then append the following code to
>the end of the URL where you see a `#2` for example. 

> ```bash
>  ' onerror='alert("Hello");//
> ```

> The URL should read as such
> ```bash
> https://xss-game.appspot.com/level3/frame#2 ' onerror='alert("Hello");//
> ```

## Level 4



