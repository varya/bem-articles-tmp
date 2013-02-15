# What you can borrow from Yandex frontend dev

This article is a text version of a [presentation](https://vimeo.com/53219242)
given at [Riga WebConf 2012](http://webconf.lv/).

The article sumes up [Yandex](http://www.yandex.com/) over 7-year experience in finding solutions for efficient frontend development.<br/>
Yandex, as a search engine and the larges Internet company in Russia, enjoys the maijor share of the local market and provides over a hundred of associated services with the help of 2500 developers and 150 frontend engineers among them.

<img src="http://img-fotki.yandex.ru/get/5645/14441195.26/0_711d5_b2ab18c0_orig"/>

Yandex developers jointly produce solutions for the problems we run into. At the same time, we are truly nerds connected to the world outside Yandex via conferences, hackatons and meetups. So, the solutions produced by Yandex developers perfectly work outside and can be easily shared.<br/>
Here is an piece of such sharing.

## Web Interface

<img src="http://img-fotki.yandex.ru/get/6429/14441195.26/0_711d6_9a3f328a_XL.jpg" width="800" height="558" title="" alt="" border="0"/>

You can see a draft for an online shop. As you can see it's nothing special. Just an ordinary web site providing all the generally accepted possibilities, such as navigation through the site pages, searching books, some advertising parts and so on.

As web developers, you know that behind the page there are our dear HTML and CSS.

	<!DOCTYPE html>    <html>        <head>...</head>        <body>            ...        </body>

    body {        font: 0.8em Arial, sans-serif;        margin: 0;        color: black;    }    .sidebar ul li {Also, besides the page is really combination of HTML and CSS, it's also a set of interface pieces.
<img src="http://img-fotki.yandex.ru/get/6427/14441195.26/0_711d7_e0975803_XL.jpg" width="800" height="600" title="" alt="" border="0"/>
Each piece is to do something. It provides to a user a functional or design point.
Each has its purpose, similar to pieces of furniture...
<img src="http://img-fotki.yandex.ru/get/4134/14441195.26/0_711d8_3fe2c0c7_XL.jpg" width="800" height="600" title="" alt="" border="0"/>
A chair is to sit on, a cupboard it to keep the kitchen things. A bed is to lay on. A coffee machine helps to survive through deadlines.<br/>You can use furniture to fill our rooms.
Also, we can use interface components to fill pages.Pages are built with this pieces like houses are build with blocks. So, let's call them just that — `blocks`.