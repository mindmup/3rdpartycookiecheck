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
        console.log('thid party cookies are not supported');
      } else if (evt.data === 'MM:3PCsupported') {
        console.log('thid party cookies are supported');
      }
    };
    window.addEventListener("message", receiveMessage, false);
  </script>

  <iframe src="LOCATION_OF_THE_SCRIPTS/start.html" />
</body>
````

It's also a good idea to set up a timeout that will automatically label third party cookies as unsupported if no recognised event comes back
after a while, just in case network fails. 
