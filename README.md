Third party cookie check for browsers
=====================================

A simple, static, passive (CDN-compatible) way of checking if third party cookies are enabled in a browser.
Consists of two scripts - one that will set a cookie, and another that will post a message depending on if the
cookie is present or not. 

Deploy the two scripts somewhere on a different domain from the main application, then load them similar to the 
example below:


````
<body>
  <script>
    var receiveMessage = function (evt) {
      if (evt.data === 'MM:3PCunsupported') {
        console.log('third party cookies are not supported');
      } else if (evt.data === 'MM:3PCsupported') {
        console.log('third party cookies are supported');
      }
    };
    window.addEventListener("message", receiveMessage, false);
  </script>

  <iframe src="LOCATION_OF_THE_SCRIPTS/start.html" style="display:none" />
</body>
````

It's also a good idea to set up a timeout that will automatically label third party cookies as unsupported if no recognised event comes back
after a while, just in case network fails. 

## Live example

Thanks to github pages, the scripts are hosted already at https://mindmup.github.io/3rdpartycookiecheck/start.html -- so you can use that as a live
version. For production, it's better to deploy somewhere under your control. 

To see the client code in action, run this JSFiddle: https://jsfiddle.net/tugawg8y/
