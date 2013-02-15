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
## Independent CSS blocks
But in order to build pages with blocks, we developers should be sure that these interface pieces can be put into any place on a page. This can be possible only if blocks are `independent`.

Block independency means the following.<blockquote>A block must not be affected by its ancestors, and it its turn must not affect the descendants.<br/>Regardless of where this block was placed.</blockquote>
When filling a page with block, we developers, should not care where exactly each block is placed. We just define a set of blocks with the appropriate order. And that's enough for getting a complete functional page.
    <html>        <head>..</head>        <body>            <div class="head">                <div class="logo">...</div>                <ul class="menu">...</ul>                <div class="search">...</div>            </div>            <div class="layout">...</div>
                    <div class="foot">...</div>        </body>    </html>
But, of course, this maybe possible only due to some architectural requirements to each block. Let us now see what these requirements are.
Let's have a look at what situations can cause block affection and how to prevent them beforehand.### RepeatingThe first is repeating blocks.

The same block can appear on the page. For example, one more menu block can be placed into the foot block.<img src="http://img-fotki.yandex.ru/get/4135/14441195.26/0_711e2_5b1a2232_XL.jpg" width="800" height="600" title="" alt="" border="0"/>
Since now the `Menu` block is not a unique within a page. Because of that we cannot use `id` selectors to match the CSS rules to it, this would be invalid.
So,
<blockquote>To apply CSS to a block, we should use classname selectors.</blockquote>

**wrong**    <ul id="menu">        ...
        
    #menu {        ...
**right**
    <ul class="menu">        ...
        
    .menu {    ...
This rule is correct for any block.<br/>Even if you think *now* that the block is unique within a page, this can be changed in the future. So, the best practice is to avoid id selectors at all and use classes.
### Moving within a Page
The next that can happen with a block is its movement within a page.
<iframe width="560" height="315" src="http://www.youtube.com/embed/suLQEIcc68g" frameborder="0" allowfullscreen></iframe>
As you can see in the video, the `Tabbed Pane` block was moved to he right side of the page and immediately got broken since it has new ancestors, new parent DOM nodes now.<br/>This is that should not happen. We have do guarantee that a block will work correctly in any place on the page.
Actually we can ensure this only if *avoiding cascade in CSS*.
Such a recomendation sounds provocative. But anyway this is reasonable. Now let's see why.
Cascade is a kind of relations between objects. A cascade rule says that one object depends on the other. It is a connection that can give some benefits.<br/>But we should have a control over all those connections. If not, this may break all.
Trying to fix, we usually add even more connections to the system. That seems to work at first. But each addition just increase uncontrolable mess.
The more cascade code we bring into the service, we more risk of future damages.<br/>So, we should use cascade only when it's really necessary.<br/>
I'll show below the situation when cascade is possible. But in general the suggestion is to avoid it.
### Moving within a Site
The next block's adventure is to be moved from page to page.
The already familiar tabbed pane block can be widely adopted. We can use it on many pages. Of course, on a different page it has another parent block. As I've said above, we should guarantee that it works correctly regardless of its environment. This is what we achieve due to avoiding cascade.
<img src="http://img-fotki.yandex.ru/get/6426/14441195.26/0_711e3_3579af38_XL.jpg" width="800" height="600" title="" alt="" border="0"/>
<img src="http://img-fotki.yandex.ru/get/5632/14441195.26/0_711e4_bf58fb79_XL.jpg" width="800" height="600" title="" alt="" border="0"/>
Again, even if a block *now* is a single one within a whole site, that does not mean it should depend on its surroundings.<br/>The recommendation about avoiding cascade works for all the blocks.
#### Pages are Sets of BlocksThe other point is that when we are developing and maintaining, the block set of every page changes.
<img src="http://img-fotki.yandex.ru/get/4122/14441195.26/0_711e5_77eb4431_XL.jpg" width="800" height="491" title="" alt="" border="0"/>We, developers, should think about keeping associated CSS in the actual state. So that if a block was removed from a page, we should remove its CSS code. Also, if a block was added to a page, we should ensure its CSS is linked there.<br/>That is not a problem for sites of 2-3 pages since we can keep all the stuff in a single one CSS file.<br/>
But usually life is not that easy. We have several pages that are different but still have some common design solutions. At least the Head block is included in all the pages.<br/>So, developers usually place the common stuff into the common.css file. Everything else is distributed per pages.
But let us look a bit closer to this practice.
<img src="http://img-fotki.yandex.ru/get/4137/14441195.26/0_711e6_bc435d6a_XL.jpg" width="800" height="600" title="" alt="" border="0"/>You see in the picture, the `Head` block contains the `Search` block. This design solution seems to be invariable within the whole site.
But not. The page providing advanced search form doesn't have this search block in the head.
<img src="http://img-fotki.yandex.ru/get/4115/14441195.26/0_711e7_a1df577a_XL.jpg" width="800" height="600" title="" alt="" border="0"/>So, should we include search block code into `common.css` file? Seems like shouldn't. Well, should we copy-paste it for all the other pages? Again, no.
Moreover, this is just a simple example. In the real life the variety of interface object combinations indeed can be huge. Usually it is very hard to define the common stuff.<br/>On the other hand, copy paste is even worse.
So, there should be a way out.

<img src="http://img-fotki.yandex.ru/get/4122/14441195.26/0_711e5_77eb4431_XL.jpg" width="800" height="491" title="" alt="" border="0"/>What about turning these drawn sets of blocks into code?
We can store CSS code for every block separately, each in a file with a corresponding name.
    blocks/        header.css         menu.css         button.css         tabbed-pane.css         logo.css         footer.css
So that, CSS for the `Menu` block is in the `menu.css` file, CSS for `Tabbed Pane` block is the `tabbed-pane.css` file and so on.
Then, you can pack CSS files for pages with these blocks using an import keyword.
    @import url(blocks/header.css);     @import url(blocks/menu.css);     @import url(blocks/tabbed-pane.css);     @import url(blocks/text.css);     @import url(blocks/logo.css);     @import url(blocks/footer.css);
That enables us to take only what's necessary for a page.
As a result there is a block stack of our project, stored in a special folder. And some pages that use these blocks.
Looks cool, but
<img src="http://img-fotki.yandex.ru/get/6442/14441195.26/0_711e8_ec41e632_XL.jpg" width="570" height="311" title="" alt="" border="0"/>
## Inside a BlockSo, let's have a look what is inside our blocks.
<img src="http://img-fotki.yandex.ru/get/5626/14441195.26/0_711e1_e0ab223a_XL.jpg" width="645" height="46" title="" alt="" border="0"/>
The menu block is going to be the first example.

    <ul class="menu">        <li><a href="/new">New titles</a></li>        <li><a href="/soon">Coming soon</a></li>        <li><a href="/best">Bestsellers</a></li>        ...    </ul> 
It's represented by `ul` tag and has some `li` children for the items. Also, the `ul` tag is marked with a CSS class, so that you can apply the rules to it.<br/>But the question is what to do with the items?
The wide-spreaded solution is to write the CSS selector similar to the following.
    .menu li    {        list-style: none;        display: inline-block;        padding: 0 0.5em;    }
As you can see, cascade is used here. It seems to work right at first because all the reasons I listed agains cascade are not for this situation. `li` tags are always inside their `ul` parent. So, nothing bad should happen.
But even inside such a small interface piece like a menu item there can be a lot of HTML markup in the future.
<img src="http://img-fotki.yandex.ru/get/6426/14441195.26/0_711e9_8881d49a_-1-L.jpg" width="500" height="101" title="" alt="" border="0"/>
Here you can see that a `Dropdown` block with its own list was placed into the menu item and immediately got broken because of this CSS instruction affects it.<br/>We got the long menu sausage instead of a nice dropdown.
<img src="http://img-fotki.yandex.ru/get/4138/14441195.26/0_711ea_f392c569_L.jpg" width="500" height="174" title="" alt="" border="0"/>
As you can see, except of avoiding cascade there appears even more specific rule. You should not use tag selectors.

The additional explanation why it is a bad practice to use tag selectors can be easily found in the Internet.

<blockquote cite="http://mzl.la/UuwZql">The style system matches rules by starting with the key selector, then moving to the left (looking for any ancestors in the rule’s selector).</blockquote>

Further information can be found in [Davis Hyatt's article](http://mzl.la/UuwZql), from Mozilla.

However we still need a solution to style menu items inside the `Menu` block.

##Element
First, let's clarify a definition and call the things inside a block — `elements`.

<img src="http://img-fotki.yandex.ru/get/5641/14441195.27/0_711eb_80c1b241_L.jpg" width="304" height="500" title="" alt="" border="0"/>

This is a clear picture of what elements are.<br/>As you can see, elements are non-independent pieces of interface. They make no sense on their own, but are to be used within their parent block.
For example, the `Search` block has an input element and a button element.<img src="http://img-fotki.yandex.ru/get/5641/14441195.27/0_711ec_b4fa229f_L.jpg" width="500" height="80" title="" alt="" border="0"/>
The `Tabbed Pane` block has 2 tab elements (and can have more if necessary) and the pane element to keep its content.
<img src="http://img-fotki.yandex.ru/get/6426/14441195.27/0_711ed_5b70323b_M.jpg" width="300" height="264" title="" alt="" border="0"/>

Styling elements you should think about them as self-reliant entities.

<img src="http://img-fotki.yandex.ru/get/5626/14441195.26/0_711e1_e0ab223a_XL.jpg" width="645" height="46" title="" alt="" border="0"/>

To apply CSS rules to elements we need to mark them with classes.<br/>In turn, to avoid cascade, it's necessary to prefix these classes with the block name.

    <ul class="menu">        <li class="menu__item"><a href="/">Index</a></li>        <li class="menu__item"><a href="/new">New</a></li>        <li class="menu__item"><a href="/offer">Special offer</a></li>        <li class="menu__item"><a href="/shipping">Shipping</a></li>    </ul>

    .menu__item    {        list-style: none;        display: inline-block;        padding: 0 0.5em;    }

You can see here that CSS class for a menu item consists of block name, which is `menu`, element name, which is `item` and a group of separation symbols.

We, at Yandex, use 2 underscores for separation. But that's optional. You can choose another symbol or a group of symbols.

    .block__element
    .block-element    .block--element

If you don't like 2 underscores, maybe you'll be pleased with 3 ;-)

###Optional elements
So far so good, a block can be different from page to page.

<img src="http://img-fotki.yandex.ru/get/5634/14441195.26/0_711db_81f5c441_L.jpg" width="500" height="47" title="" alt="" border="0"/>

<img src="http://img-fotki.yandex.ru/get/4127/14441195.27/0_711ef_421e1e8c_L.jpg" width="500" height="88" title="" alt="" border="0"/>

<img src="http://img-fotki.yandex.ru/get/5642/14441195.27/0_711ee_5370e90b_L.jpg" width="500" height="177" title="" alt="" border="0"/>

The difference you can see in the slide is that it comprises different sets of elements. So that, elements are optional. This means we should be able to take CSS code for the elements we use.

Similar to blocks, elements can be stored separately.
    blocks/        search.css        search__checkbox.css        search__autocomplete.css        tabbed-pane.css        tabbed-pane__tab.css        tabbed-pane__pane.css        menu.css        menu__item.css        book.css        book__title.css        book__image.css
That enables to take element code only if we want. If not, we just won't write the import instruction linking it to our page.



Just to wrap up, to make your blocks independent, please:
 * a block has its "name"   - no "id" but "classname" selectors * avoid cascade * no "tag" selectors