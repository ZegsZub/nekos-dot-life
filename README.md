[![npm](https://img.shields.io/npm/v/nekos.life.svg)](https://www.npmjs.com/package/nekos.life)
[![npm](https://img.shields.io/npm/dt/nekos.life.svg?maxAge=3600)](https://www.npmjs.com/package/nekos.life)

 
[![NPM](https://nodei.co/npm/nekos.life.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/nekos.life/)


# Nekos.life

## Installation
```
npm i -s nekos.life
```
This wrapper has no external dependencies ;).  
The wrapper functions all return promises, so you can use traditional promises or await/async.

| Function | Description |
| -------- | ----------- |
| `getSFWTickle` | Gets a URL of a tickle image/gif |
| `getSFWSlap` | Gets a URL of a slap image/gif |
| `getSFWPoke` | Gets a URL of a poke image/gif |
| `getSFWPat`  | Get a URL of a pat image/gif |
| `getSFWNeko` | Get a URL of a neko image/gif |
| `getSFWMeow` | Get a URL of a cat image/gif |
| `getSFWLizard` | Get a URL of a lizard image/gif |
| `getSFWKiss` | Get a URL of a kiss image/gif |
| `getSFWHug`  | Get a URL of a hug image/gif |
| `getSFWFoxGirl` | Get a URL of a fox girl image/gif |
| `getSFWFeed` | Get a URL of a feeding image/gif |
| `getSFWCuddle` | Get a URL of a cuddle image/gif |
| `getSFWWhy` | Get `text` of a question |
| `getSFWCatText`| Get `text` of a cat emoji |
| `getSFWOwOify` | Get OwOified `text` of a string |
| `getSFWChat` | Sends the text and replies with a `text` as a response |
| `getSFW8Ball` | Sends the text and replies with a `text` as a response to the magic 8Ball and an image as well.|
| `getSFWFact` | Gets the text and replies with a `text` that is a random fact |
| `getNSFWRandomHentaiGif` | Get a URL of hentai gif |
| `getNSFWPussy` | Get a NSFW URL of a pussy image/gif |
| `getNSFWNekoGif`| Get a NSFW URL of a neko gif |
| `getNSFWNeko` | Get a NSFW URL of a neko image |
| `getNSFWLesbian` | Get a NSFW URL of a lesbian image/gif |
| `getNSFWKuni` | Get a NSFW URL of a kuni image/gif |
| `getNSFWCumsluts` | Get a NSFW URL of a cumslut image/gif |
| `getNSFWClassic` | Gets a NSFW URL of the classic endpoint image/gif |
| `getNSFWBoobs` | Gets a NSFW URL of boobs image/gif |
| `getNSFWBj` | Gets a NSFW URL of bj image/gif |
| `getNSFWAnal` | Gets a NSFW URL of anal image/gif |

All of the endpoints but the ones marked with `text`, except Chat/8Ball/Fact in the description will return JSON: `{ url: <theURL>}`.

getSFWCatText will return JSON: `{cat: <catemoji>}`  
getSFWWhy will return JSON `{why: <whytext>}`  
getSFWOwOify will return JSON `{owo: <owoified string>}` 

getSFWFact will return JSON `{response: <fact string>}` 
getSF8Ball will return JSON `{response: <8Ball response string>, url: <URL to a matching 8Ball image>}` 
getSFWChat will return JSON `{response: <reply string>}`, this one is special and will have an example :)  

As of now, `getSFWOwOify` is the only function that takes in querystring parameters. It requires an object containing the parameter, and the key should be the value. In this case, the key is `text` and the value is whatever you want OwOified.  There is an example in this README.
`{text: 'Some text you want weebified.}` 

## Examples

Await/Async example
```js
const client = require('nekos.life');
const neko = new client();

async function test() {
  console.log(await neko.getSFWHug());
}

test();
```
returns: 
```js
{ url: 'https://cdn.nekos.life/hug/hug10050.gif' }
```

Promise example
```js
const client = require('nekos.life');
const neko = new client();

neko.getSFWCatText().then((catText) => console.log(catText));
```
returns
```js
{ cat: '((≡^⚲͜^≡))' }
```

`getSFWOwOify` example
```js
async function work() {
  let owo = await neko.getSFWOwOify({text: 'This lib is really awesome!'});
  console.log(owo);
}

work();
```
returns
```js
{ owo: 'This wib is weawwy awesome >w< ' }
```

`getSFWChat` example  
```js
async function work() {
  let owo = await neko.getSFWChat({text: "What's up?"});
  console.log(owo);
}

work();
```
returns
```js
{ response: 'Not much.' }
```
Try adding `owo: "true"` after the text prop ;). It would look like this `{text: "What's up?", owo: "true"}`  
`getSFW8Ball` is prety much the exact same thing, except you can't use `owo` with it!
