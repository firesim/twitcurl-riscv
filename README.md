## Posting to twitter from a RISC-V system

This is 100% demo-engineering. Original codebase is:

https://github.com/swatkat/twitcurl

How to run on a RISC-V system with internet access

1. assumes you have RISC-V toolchain available as installed by firesim
2. assumes you're using firesim-software 
3. sysroot is currently hardcoded (see Makefile)
4. Create an app on twitter developer's site
5. Paste consumer keys in the twitterClient.cpp file.
6. Install twurl on a host machine to handle OAuth, take the keys it puts in ~/.twurlrc and copy them into files named twitterClient_token_key.txt and twitterClient_token_secret.txt.
7. Run make in libtwitcurl. The lib/client distinction is meaningless in this fork, it just produces one binary called twitterClient.
8. Configure buildroot with libopenssl and libcurl
9. Copy twitterClient, twitterClient_token_key.txt, and twitterClient_token_secret.txt into firesim/sw/firesim-software/buildroot-overlay/
10. Build images in firesim-software
11. Boot a FireSim simulation, connect to the outside network as described in docs
12. On the simulated system, set the date correctly by running date on a host machine, then giving this output to date -s in the simulation
13. In the simulation, cd / and run ./twitterClient


## Original project's readme below:

### Introduction: ###
**twitcurl** is a pure C++ library for twitter APIs. twitcurl uses cURL for handling HTTP requests and responses. twitcurl has been tested on Microsoft Windows, Ubuntu and Debian. In fact, it works just fine on any operating system that supports cURL.
  * v1.1 Twitter REST APIs
  * JSON
  * SSL

### OAuth ###
**twitcurl** supports OAuth authorization methods. Check **twitterClient** example code in **trunk** section to know about twitcurl OAuth flow. Also, check wiki page for more info: http://code.google.com/p/twitcurl/wiki/TwitcurlOAuthFlow


### APIs ###
Currently twitcurl has wrappers for following twitter REST APIs:<br>
<b>Timeline methods:</b><br>
statuses/public_timeline<br>
statuses/friends_timeline<br>
statuses/user_timeline<br>
statuses/mentions<br>

<b>Status methods:</b><br>
statuses/show<br>
statuses/update<br>
statuses/destroy<br>

<b>User methods:</b><br>
users/show<br>
statuses/friends<br>
statuses/followers<br>

<b>Direct Message methods:</b><br>
direct_messages<br>
direct_messages/sent<br>
direct_messages/new<br>
direct_messages/destroy<br>

<b>Friendship methods:</b><br>
friendships/create<br>
friendships/destroy<br>
friendships/show<br>

<b>Social Graph methods:</b><br>
friends/ids<br>
followers/ids<br>

<b>Account methods:</b><br>
account/rate_limit_status<br>

<b>Favorite methods:</b><br>
favorites<br>
favorites/create<br>
favorites/destroy<br>

<b>Block methods:</b><br>
blocks/create<br>
blocks/destroy<br>
blocks/list<br>
blocks/ids<br>

<b>Saved Search methods:</b><br>
saved_searches<br>
saved_searches/show<br>
saved_searches/create<br>
saved_searches/destroy<br>

<b>Trends methods:</b><br>
trends<br>
trends/current<br>
trends/daily<br>
trends/weekly<br>
trends/available<br>

<h3>Source:</h3>
<ul><li>twitcurl source is available in the repository in "Source" tab.<br>
</li><li>Includes Microsoft Visual C++ 6.0 and 2008 workspace for building on Windows; and Makefile for building on UNIX/Linux distroes.<br>
</li><li>Use SVN or tools like TortoiseSVN (<a href='http://tortoisesvn.net/'>http://tortoisesvn.net/</a>) to check-out and download files.</li></ul>


<h3>Help needed?</h3>
See wiki section for more info on building and using twitcurl library.<br>
<a href='http://code.google.com/p/twitcurl/wiki/WikiHowToUseTwitcurlLibrary'>http://code.google.com/p/twitcurl/wiki/WikiHowToUseTwitcurlLibrary</a>


<h3>Note:</h3>
<ul><li>twitcurl returns JSON responses from twitter.com as it is. You need to have a JSON parser to parse the responses.<br>
</li><li>twitcurl uses HMAC_SHA1  from <a href='http://www.codeproject.com/KB/recipes/HMACSHA1class.aspx'>http://www.codeproject.com/KB/recipes/HMACSHA1class.aspx</a>
</li><li>twitcurl uses base64 from <a href='http://www.adp-gmbh.ch/cpp/common/base64.html'>http://www.adp-gmbh.ch/cpp/common/base64.html</a>
</li><li>Check out <a href='http://www.json.org/'>http://www.json.org/</a> for C/C++ parsers.</li></ul>


<h3>Example:</h3>
An example twitter client program using twitcurl as a static library is available in the "Downloads" section.<br>
The Makefile in twitterClient is supposed to run under sudo, and the file is tested under Ubuntu 12.04.<br>
<br>
<br>
<h3>Info:</h3>
<ul><li>More info on cURL can be found here: <a href='http://curl.haxx.se/'>http://curl.haxx.se/</a>
</li><li>More info on twitter REST APIs can be found here: <a href='http://apiwiki.twitter.com/w/page/22554679/Twitter-API-Documentation'>http://apiwiki.twitter.com/w/page/22554679/Twitter-API-Documentation</a>
</li><li>More info on twitter OAuth authorization can be found here:<br>
<ul><li><a href='http://dev.twitter.com/auth'>http://dev.twitter.com/auth</a>
</li><li><a href='http://www.jaanuskase.com/en/2010/01/understanding_the_guts_of_twit.html'>http://www.jaanuskase.com/en/2010/01/understanding_the_guts_of_twit.html</a>
</li><li><a href='http://codebrook.wordpress.com/2010/07/08/twitter-oauth-in-cpp-for-win32/'>http://codebrook.wordpress.com/2010/07/08/twitter-oauth-in-cpp-for-win32/</a>
</li></ul></li><li>Building cURL static library with SSL on Windows: <a href='http://swatrant.blogspot.in/2013/06/how-to-build-curl-static-library-with.html'>http://swatrant.blogspot.in/2013/06/how-to-build-curl-static-library-with.html</a>
