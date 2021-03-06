# class GoLogin - class for working with <a href="https://gologin.app" target="_blank">gologin.app</a> API

## Getting Started

GoLogin supported Linux platform, under MacOS and Windows in work

### Installation

`npm install https://github.com/gologinapp/gologin.git`

for running example.js install puppeteer-core

`npm install puppeteer-core`

### Selenium

To use GoLogin with Selenium see  `selenium/example.js`

### DEBUG

For debugging use `DEBUG=* node example.js` command

### Methods

#### constructor

- `options` <[Object]> Options for profile
	- `token` <[string]> your API <a href="https://gologin.app/#/personalArea/TokenApi" target="_blank">token</a>
	- `profile_id` <[string]> profile ID
	- `executablePath` <[string]> path to Orbita browser
	- `vncPort` <[integer]> port of VNC server if you using it
  - `tmpdir` <[string]> path to temporary directore for saving profiles

<a  href="https://gologin.app" target="_blank">Where is token? token is here</a>

![Token API in Settings](https://user-images.githubusercontent.com/62306291/78453427-53220100-769a-11ea-9465-0aae3ae602b7.jpg)

```js
const GoLogin = require('./gologin');
const GL = new GoLogin({
    token: 'yU0token',
    profile_id: 'yU0Pr0f1leiD',
    executablePath: '/usr/bin/orbita-browser/chrome',
});
```

#### start()  

- returns: string 

starting browser with profile id, returning WebSocket url for puppeteer

#### stop()  

stoppin browser with profile id

#### create(options)  

- returns: string - profile_id

- `options` <[Object]> Options for profile
  - `name` <[string]> profile name
  - `notes` <[String]> notes for profile
  - `browserType` <[String]> "chrome"
  - `os` <[String]> lin, mac or win
  - `startUrl`: <[String]>
  - `googleServicesEnabled` <[true, false]>
  - `lockEnabled` <[true, false]>
  - `navigator` <[Object]> navigator options
    - `userAgent` <[String]>
    - `resolution` <[String]>
    - `language` <[String]>
    - `platform` <[String]>
    - `doNotTrack` <[true, false]>
    - `hardwareConcurrency` <[Integer]>
  - `storage` <[Object]>
    - `local` <[true, false]>
    - `extensions` <[true, false]>
    - `bookmarks` <[true, false]>
    - `history` <[true, false]>
    - `passwords` <[true, false]>
  - `proxyEnabled` <[true, false]> 
  - `proxy` <[Object]>
    - `mode` <[String]> proxy type "http"
    - `host` <[String]>
    - `port` <[Integer]>
    - `username`: <[String]>
    - `password`: <[String]>
    - `autoProxyRegion`: <[String]>
  - `dns` <[String]>
  - `plugins` <[Object]>
    - `enableVulnerable`  <[true, false]>
    - `enableFlash`  <[true, false]>
  - `timezone` <[Object]>
    - `enabled`   <[true, false]>
    - `fillBasedOnIp`   <[true, false]>
    - `timezone`: <[String]>
  - `geolocation` <[Object]>
    - `mode` <[String]> "prompt"
    - `enabled` <[true, false]>
    - `customize` <[true, false]>
    - `fillBasedOnIp`  <[true, false]>
  - `audioContext`
    - `mode`   <["on", "off"]>
    - `noise` <[Integer]>
  - `canvas`
    - `mode` <["on"], ["off"]>
    - `noise` <[Integer]>
  - `fonts`
    - `families` <[Array]>
    - `enableMasking` <[true, false]>
    - `enableDomRect` <[true, false]>
  - `mediaDevices`
    - `videoInputs` <[Integer]>
    - `audioInputs` <[Integer]>
    - `audioOutputs` <[Integer]>
    - `enableMasking` <[true, false]>
  - `webRTC` <[Object]>
     - `mode` <[String]>
     - `enabled` <[true, false]>
     - `customize` <[true, false]>
     - `fillBasedOnIp` <[true, false]>
     - `publicIp` <[String]>
     - `localIps` <[Array]>
  - `webGL` <[Object]>
     - `mode` <[String]> "noise"
     - `getClientRectsNoise` <[Integer]>
     - `noise` <[Integer]>
  - `webGLMetadata` <[Object]>
    - `mode` <String> mask
    - `vendor`: <[String]>
    - `renderer`: <[String]>
  - `extensions` <[Object]>
    - `enabled` <[true, false]>
    - `preloadCustom` <[true, false]>
    - `names` <[Array]>
  - `profile`: <[String]>,
  - `googleClientId`: <[String]>

create new profile and returns profile_id

#### update(options)  

- `options` <[Object]> Options for profile
  - `id` <[string]> profile id (required)
	- `name` <[string]> profile name
  - `notes` <[String]> notes for profile
  - `browserType` <[String]> "chrome"
  - `os` <[String]> lin, mac or win
  - `startUrl`: <[String]>
  - `googleServicesEnabled` <[true, false]>
  - `lockEnabled` <[true, false]>
  - `navigator` <[Object]> navigator options
    - `userAgent` <[String]>
    - `resolution` <[String]>
    - `language` <[String]>
    - `platform` <[String]>
    - `doNotTrack` <[true, false]>
    - `hardwareConcurrency` <[Integer]>
  - `storage` <[Object]>
    - `local` <[true, false]>
    - `extensions` <[true, false]>
    - `bookmarks` <[true, false]>
    - `history` <[true, false]>
    - `passwords` <[true, false]>
  - `proxyEnabled` <[true, false]> 
  - `proxy` <[Object]>
    - `mode` <[String]> proxy type "http"
    - `host` <[String]>
    - `port` <[Integer]>
    - `username`: <[String]>
    - `password`: <[String]>
    - `autoProxyRegion`: <[String]>
  - `dns` <[String]>
  - `plugins` <[Object]>
    - `enableVulnerable`  <[true, false]>
    - `enableFlash`  <[true, false]>
  - `timezone` <[Object]>
    - `enabled`   <[true, false]>
    - `fillBasedOnIp`   <[true, false]>
    - `timezone`: <[String]>
  - `geolocation` <[Object]>
    - `mode` <[String]> "prompt"
    - `enabled` <[true, false]>
    - `customize` <[true, false]>
    - `fillBasedOnIp`  <[true, false]>
  - `audioContext`
    - `mode`   <["on", "off"]>
    - `noise` <[Integer]>
  - `canvas`
    - `mode` <["on"], ["off"]>
    - `noise` <[Integer]>
  - `fonts`
    - `families` <[Array]>
    - `enableMasking` <[true, false]>
    - `enableDomRect` <[true, false]>
  - `mediaDevices`
    - `videoInputs` <[Integer]>
    - `audioInputs` <[Integer]>
    - `audioOutputs` <[Integer]>
    - `enableMasking` <[true, false]>
  - `webRTC` <[Object]>
     - `mode` <[String]>
     - `enabled` <[true, false]>
     - `customize` <[true, false]>
     - `fillBasedOnIp` <[true, false]>
     - `publicIp` <[String]>
     - `localIps` <[Array]>
  - `webGL` <[Object]>
     - `mode` <[String]> "noise"
     - `getClientRectsNoise` <[Integer]>
     - `noise` <[Integer]>
  - `webGLMetadata` <[Object]>
    - `mode` <String> mask
    - `vendor`: <[String]>
    - `renderer`: <[String]>
  - `extensions` <[Object]>
    - `enabled` <[true, false]>
    - `preloadCustom` <[true, false]>
    - `names` <[Array]>
  - `profile`: <[String]>,
  - `googleClientId`: <[String]>

update profile metadata

#### delete(profile_id)  

delete profile


### example.js 

```js
const puppeteer = require('puppeteer-core');
const GoLogin = require('./gologin');

(async () =>{
    const GL = new GoLogin({
        token: 'yU0token',
        profile_id: 'yU0Pr0f1leiD',
        executablePath: '/usr/bin/orbita-browser/chrome',
    });

    const wsUrl = await GL.start(); 

    const browser = await puppeteer.connect({
        browserWSEndpoint: wsUrl.toString(), 
        ignoreHTTPSErrors: true,
    });

    const page = await browser.newPage();
    await page.goto('https://myip.gologin.app/mini');   
    console.log(await page.content());
    await browser.close();
    await GL.stop();
})();
```


Running example:

`DEBUG=gologin* node example.js`

## For local profiles

#### startLocal()  

- returns: string 

starting browser with profile id, returning WebSocket url for puppeteer. Before downloading profile on s3, it's check if exists profile in temp directory.

#### stopLocal()  

stoppin current browser without removing archived profile 

### example-local-profile.js

```js
const puppeteer = require('puppeteer-core');
const GoLogin = require('../gologin');

(async () =>{
    const GL = new GoLogin({
        token: 'yU0token',
        profile_id: 'yU0Pr0f1leiD',
        executablePath: '/usr/bin/orbita-browser/chrome',
        tmpdir: '/my/tmp/dir',
    });
    const wsUrl = await GL.startLocal(); 
    const browser = await puppeteer.connect({
        browserWSEndpoint: wsUrl.toString(), 
        ignoreHTTPSErrors: true,
    });

    const page = await browser.newPage();
    await page.goto('https://myip.gologin.app/mini');   
    console.log(await page.content());
    await browser.close();
    await GL.stopLocal({posting: false});
})();
```




