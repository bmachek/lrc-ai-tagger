# lrc-ai-tagger

A Lightroom Classic to fill keywords, image title and caption by using Google Gemini (gemini-1.5-flash/pro) or ChatGPT (gpt-4o)

## Privacy / Disclaimer
### Your photos will be sent to Google or OpenAI for analysis! Do not use the plugin, if you don't agree with this.

## Usage
* Install plugin using Lightroom addon module manager.
* Obtain an API key for the model you want to use:
  * [Obtain Google Gemini API key](https://ai.google.dev/gemini-api/docs/api-key)
  * ~~[Obtain ChatGPT API key](https://platform.openai.com/api-keys)~~
* Configure language, phrases and API key in Lightroom module manager.
* Choose the model you want to use on the Lightroom module manager.
* Go to Library in Lightroom
* Select some photos
* Go to menu -> Library -> Addon Modules -> Analyze photo(s) with Generative AI
* If enabled review before save for title and/or caption and the field is already filled with data, a review dialog will show up.
* Wait it to fill your keywords, caption or title as selected.

## Which model should I use:
* **gemini-1.5-pro**: If you want the best results, and are willing to pay for big amounts of photos.
* **gemini-1.5-flash**: If you want very good results for free.
* ~~**ChatGPT**: IMHO it doesn't make sense to use this model for now, as the results turn out to be very generic.~~

## Google rate limits
The free version of gemini-flash-1.5 is limited to 1500 prompts per day. 
There's also a soft limit on how many requests per minute are allowed, which can of course be circumvented by waiting for a few seconds, when a request is denied.
The plugin waits for 5 seconds after each denied prompt, if the error 'RESOURCE_EXHAUSTED' persists for 10 of these wait loops, it assumes that the daily limit has been hit, and stops the process with an error message. 
### You can of course always setup billing at Google to get rid of these limits!

## Notes
* Google AI has safety features, so some content is blocked. Especially:
  * Nudity
  * Dangerous scenes
  * Hatecrime
  * ...
 If a photo gets denied by a safety blocked, it will be skipped without further notice (for now).
* All generated keywords are hierarchically beneath the top keyword "Google AI". Beneath that, there is no more hierarchy.
  But you can easily remove all keywords generated by the plugin, by deleting the top Google AI keyword.
  Additionally you can create smart collections with filters for Google AI to keep track of photos that have or haven't been analyzed yet.
* Feel free to open issues or discussions. Any feedback is welcome.

## Support my work
[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/donate/?hosted_button_id=2LL4K9LN5CFA6)

## Credits
* @gesteves for [his plugin](https://github.com/gesteves/lightroom-alt-text-plugin), which gave me the idea for this one, and on which the source code is based on.
* @kikito for [inspect.lua](http://github.com/kikito/inspect.lua)
* Jeffrey Friedl for [JSON.lua](http://regex.info/blog/lua/json)
