I ran some tests and came to the following conclusions.

I implemented four approaches (https://font-benchmark.netlify.app/):

1. Links in the document head. This is the current approach and the one recommended by Google Fonts.
2. Links in the head, with the main font’s `@font-face` definition inlined, as FP recommends.
3. All `@font-face` definitions inlined.
4. Links in the head, with the main font preloaded.

Fonts had little impact on overall performance in my tests. I was able to achieve nearly perfect performance scores (99–100%) with each demo. Differences were mostly due to server response time.

Approach 4 is the only one in which fonts load at the same time as the CSS. In the other three approaches, the font file loads after the CSS (Bootstrap and/or the `@font-face` definitions). See the attached request-timing charts.

We currently use v1 of the Google Fonts API. V2 produces smaller CSS files for variable fonts, but we still benefit from using variable fonts with v1. (v1: https://fonts.googleapis.com/css?family=Inter:100,100i,200,200i,300,300i,400,400i,500,500i,600,600i,700,700i,800,800i,900,900i&display=swap&subset=latin,latin-ext,vietnamese; v2: https://fonts.googleapis.com/css2?family=Inter:ital,opsz,wght@0,14..32,100..900;1,14..32,100..900&display=swap)

Sources about preload:
+ https://x.com/ShopifyEng/status/844245243948163072
+ https://medium.com/reloading/preload-prefetch-and-priorities-in-chrome-776165961bbf
+ https://web.dev/articles/codelab-preload-web-fonts
