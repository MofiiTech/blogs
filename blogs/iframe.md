# Using Twitter Widgets in a Chinese Blog

> I've been working on a personal blog using flask. Since front-end designs are not so handy to me, I chose [embeded tweets](https://developer.twitter.com/en/docs/twitter-for-websites/overview) to display timeline on my blog. However, because of the GFW, Twitter is not available in Mainland China, as well as Twitter embeded timeline. The twitter widgets (powered by iframe) would not display when accesing my webiste from China. Since I am hosting my website on a VPS, I tried a few ways to make this beautiful timeline accessible in China.

## Nginx Reverse Proxy

This is the first thing in my mind because many people have created mirror websites of Google in China as a substitute of Baidu. The websites are stable and respond fast. I think I may use Nginx to create a mirror webiste of my personal.

Here are some reference blogs regarding this problem:

1. Configure Apache2 Server to listen to a port other than 80. (e.g. 81)

2. Configure Nginx Server to listen to port 80. And further configure Nginx to point to the original Apache2 Server.

Here I found a problem of this design. When the static files including the HTML, CSS and JS are "downloaded" from a server, the iframe tag is not actually rendered. So when finally download the HTML file to the browser, the Twitter widget is still in the form of a Twitter link, which makes the whold plan fail.
