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
Each has its purpose, similar to pieces of furniture…<br/>
A chair is to sit on, a cupboard it to keep the kitchen things. A bed is to lay on. A coffee machine helps to survive through deadlines.<br/>You can use furniture to fill our rooms.
Also, we can use interface components to fill pages.Pages are built with this pieces like houses are build with blocks. So, let's call them just that — `blocks`.
## Block
A block is an independent interface piece that preserves a design point and some functionality. Anything that can be taken as a solid piece and can be put into a page is an interface block.
<table border="0">
  <tr>
      <td colspan="2" align="center">
          <img src="http://img-fotki.yandex.ru/get/5645/14441195.26/0_711d9_9d9c6157_XL.jpg" width="800" height="52" title="" alt="" border="0"/>
      </td>
  </tr>
  <tr>
      <td rowspan="2">
          <img src="http://img-fotki.yandex.ru/get/6439/14441195.26/0_711dc_2f5ffa46_M.jpg" width="300" height="259" title="" alt="" border="0"/>
      </td>
      <td align="center">
          <img src="http://img-fotki.yandex.ru/get/4122/14441195.26/0_711da_e8f6dee7_M.jpg" width="300" height="271" title="" alt="" border="0"/>
      </td>
  </tr>
  <tr>
      <td>
          <img src="http://img-fotki.yandex.ru/get/5634/14441195.26/0_711db_81f5c441_L.jpg" width="500" height="47" title="" alt="" border="0"/>
      </td>
  </tr></table>
To operate the blocks, it's good to name them. Here there are a `Menu`, a `Calendar` control, a `Footer`, a `Tabbed pane`, a `Dropdown` and a `Search` blocks.
Futhermore, some blocks are large. They usually preserve other blocks. But they still are solid independent pieces.
<table border="0">
    <tr>
    	<td colspan="2">
    	    <img src="http://img-fotki.yandex.ru/get/4120/14441195.26/0_711dd_3d4b199_XL.jpg" width="800" height="77" title="" alt="" border="0"/>
    	</td>
    </tr>
    <tr>
        <td>
            <img src="http://img-fotki.yandex.ru/get/5647/14441195.26/0_711de_ac603720_M.jpg" width="300" height="81" title="" alt="" border="0"/>
        </td>
        <td>
            <img src="http://img-fotki.yandex.ru/get/6440/14441195.26/0_711df_12538ac_M.jpg" width="300" height="72" title="" alt="" border="0"/>
        </td>
    </tr>
    <tr>
        <td colspan="2" align="center">
            <img src="http://img-fotki.yandex.ru/get/5634/14441195.26/0_711db_81f5c441_L.jpg" width="500" height="47" title="" alt="" border="0"/>
        </td>
    </tr>
    <tr>
        <td colspan="2" align="center">
            <img src="http://img-fotki.yandex.ru/get/4128/14441195.26/0_711e0_8beaa73d_M.jpg" width="300" height="33" title="" alt="" border="0"/>
        </td>
    </tr></table>
Here you can see the `Head` block that contains some others.
### Block HTML representation
*Indeed, behind the scenes there are our dear HTML and CSS.*
<img src="http://img-fotki.yandex.ru/get/5626/14441195.26/0_711e1_e0ab223a_XL.jpg" width="645" height="46" title="" alt="" border="0"/>
Each block is represented by a piece of HTML markup. To style the block we write CSS rules, as usual.<br/>`Menu` block is an `ul` tag and its content.
    <ul class="menu">        <li><a href="/new">New titiles</a></li>        <li><a href="/soon">Coming soon</a></li>        <li><a href="/best">Bestsellers</a></li>        ...

<img src="http://img-fotki.yandex.ru/get/5634/14441195.26/0_711db_81f5c441_L.jpg" width="500" height="47" title="" alt="" border="0"/>

The same works for the `Search` block, that is represented by `div` tag with some content.

    <div class="search">        <input type="text" name="search" value="..."/>        <input type="button" name="sbmt" value="Search"/>    </div>
The last example, `Tabbed Pane` block, which is also a combination of HTML and CSS.

<img src="http://img-fotki.yandex.ru/get/6439/14441195.26/0_711dc_2f5ffa46_M.jpg" width="300" style="float: left" height="259" title="" alt="" border="0"/>

    <div class="tabbed-pane">        <ul>            <li>Bestsellers</li><li>...</li>        </ul>        <div>           The Casual Vacancy, J.K. Rowling        </div>     </div>
 <div style="clear:both"></div>