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

##Level 3
>The goal for this level is to inject a script to prompt an alert in the app. There is no user input this level so we 
>must manipulate the URL in order to inject the JavaScript
