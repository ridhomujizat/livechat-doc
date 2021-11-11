# livechat-doc

### Embed in your mobile app

1. get livechat url mobile
2. embed with webview or iframe full width and height in your app
3. add token in param postLogin, example:
    ```
    https://YOUR LIVE CHAT URL/?postLogin=1WZ/0p/Qmet+lVS53oeBYlilBYIiDxSOF4FONX3cSD3uwRY3rhqw2edXUEqY1hbQEN1Q3YKuDOPt7uddiFVJ+jMk69tfv+o8fwIuK7Lg2OMo1svY38DyMvn92LOmCcJ1ApM/Z0/r/DMpaMKZpcE3Uw==
    ```
    
 ### Embed in your web app
 
 1.  get your bundle build file `YOURTENANT.js` 
 2.  add script in index.html (your web production)
```html
    <body>
      ....
      <script type="text/javascript">
        var PRIMARY_COLOR = "#e6193b"; // <-- color for Header and Sticky Button
        var BUBLLE_CHAT_COLOR = "#96e3dc"; // <-- color for bubble chat
        app = document.createElement("div"); // <-- create element for render react
        var postLoginToken =
          "/pOJtrPLh/3d2Zwy4y+esDtgdIk5O6QovelQPCH4toJEDFD+YjFcF1yHyAoGLzth+bI8dMj4uRdePS1+AUxdAU0Htep/Gff0wH98GcErU0E="; // <-- token form postlogin
        app.setAttribute("id", "INFwgChat");
        document.body.appendChild(app);
      </script>
      <script defer="defer" src="YOURTENANT.js"></script>    // <-- add bundle js
     ...
    </body>
```

### generet token
1. running in node js
```js
const crypto = require("crypto");

//example data to encrypt
const example = {
  member_id: "90890230123"
  username: "user name",
  email: "test@email.com",
  mobilePhone: "0812000000"
};

const key = // <---- key for encrypt
const iv = // <---- iv for encrypt

const encrypt_om = (val) => {
  let cipher = crypto.createCipheriv("aes-256-cbc", key, iv);
  let encrypted = cipher.update(JSON.stringify(example), "utf8", "base64");
  encrypted += cipher.final("base64");
  return encrypted.toString();
};

const encrypt = encrypt_om(example); // <---- token for postLoginToken

console.log("encripted", encrypt);
// ---------------
// encripted /pOJtrPLh/3d2Zwy4y+esDtgdIk5O6QovelQPCH4toJEDFD+YjFcF1yHyAoGLzth+bI8dMj4uRdePS1+AUxdAU0Htep/Gff0wH98GcErU0E=
// ---------------
```
