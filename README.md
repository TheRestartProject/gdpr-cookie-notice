GDPR Cookie Notice
=============

This is a javascript solution to show a GDPR compliant cookie notice on your website.

##### How it works?

Include the scripts.js and style.css files on your site from the dist folder as such:

```
<script type="text/javascript" src="/gdpr-cookie-notice/dist/script.js"></script>
<link rel="stylesheet" type="text/css" href="/gdpr-cookie-notice/dist/style.css" />
```

Initialise the script with the following config file (place at bottom of file before closing body tag):

```
gdprCookieNotice({
  locale: 'en', //This is the default value
  timeout: 500, //Time until the cookie bar appears
  expiration: 30, //This is the default value, in days
  domain: '.yoursite.com', //If you run the same cookie notice on all subdomains, define the main domain starting with a .
  implicit: false, //Accept cookies on page scroll automatically
  statement: 'https://google.com', //Link to your cookie statement page
  performace: ['JSESSIONID'], //Cookies in the performance category.
  analytics: ['ga'], //Cookies in the analytics category.
  marketing: ['SSID'] //Cookies in the marketing category.
});
```

User will see a banner at the bottom of the screen, describing why the site runs cookies. Clicking on Cookie settings will let the user select which type of cookies they might allow on the site(if something is not allowed, all cookies defined in the config file will be deleted automatically on page load). The bar will be visible always if they don't allow all types of cookies to load, just to annoy them a little.

You can use listen to the gdprCookiesEnabled event to load scripts on your site only when the cookies are enabled by the user:

```
  document.addEventListener('gdprCookiesEnabled', function (e) {
    if(e.detail.marketing) { //checks if marketing cookies are enabled
      //code here when marketing cookies are enabled
    }else{
      //code here when marketing cookies are disabled
    }
  });
```

##### Changes made

1. Model change to explicit. That is when you first load it will not assume consent. Only essential cookies are enabled by default.
2. There is a settings button so you can change your mind at any time.
