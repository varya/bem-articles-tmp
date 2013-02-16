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
##ModifierNow to the last notion, a `modifier`.

<table border="0">
    <tr>
        <td>
            <img src="http://img-fotki.yandex.ru/get/6439/14441195.26/0_711dc_2f5ffa46_M.jpg" width="300" height="259" title="" alt="" border="0"/>
        </td>
        <td>
            <img src="http://img-fotki.yandex.ru/get/5627/14441195.27/0_71207_4cfc639a_M.jpg" width="300" height="259" title="" alt="" border="0"/>
        </td>
        <td>
            <img src="http://img-fotki.yandex.ru/get/5632/14441195.27/0_71206_5fb7bc50_M.jpg" width="300" height="259" title="" alt="" border="0"/>
        </td>
    </tr>
</table>

Again, the same block sometimes can look slightly different. Here it is not because of optional elements but because of its own design distinctions.

Of course, it is always possible to implement all these tabbed panes as diverse blocks. But that would be copy paste which we we can't abide.

The way out is to equip a block with an additional CSS class to provide changes. Such an addition is called a modifier.

    <div class="tabbed-pane tabbed-pane_theme_blue">        <ul>            <li class="tabbed-pane__tab">Tab 1</li>            <li class="tabbed-pane__tab">Tab 2</li>        </ul>        <div class="tabbed-pane__pane">            ...        </div>    </div>

Remember, we were wise enough to use classes. So, we can add to a block DOM node as many modifiers as we need.

    <div class="tabbed-pane                tabbed-pane_theme_blue                tabbed-pane_direction_bottom">        ...    </div>    <input class="button                  button_theme_black                  button_size_l" ... />

We can use different modifiers to change different properties. For example, the `theme` modifier can change block's background color and the `size` modifier fixes all the dimensions of the block.

**block-name_mod-name_mod-val**

A modifier is a key-value combination, it consists of modifier name, modifier value and is prefixed with block name.

    tabbed-pane_theme_blue    tabbed-pane_theme_white    tabbed-pane_size_s    tabbed-pane_size_l    button_size_s    button_size_l

Indeed, modifiers are optional. We never link to the page all the block modifiers since blocks are never used in all their modifications within one page.<br/>So, similar to optional elements, we detach their CSS code into their own files.

    blocks/        tabbed-pane.css        tabbed-pane__tab.css        tabbed-pane__pane.css        tabbed-pane_theme_blue.css        tabbed-pane_theme_black.css        tabbed-pane_direction_bottom.css

When building a page CSS file of blocks, you can take only those modifiers which it needs.

### Modifying elements
Elements can be modified in the same way.

<img src="http://img-fotki.yandex.ru/get/4120/14441195.27/0_71214_cff3fb1_M.jpg" width="300" height="259" title="" alt="" border="0"/>The famous examples of modified elements are active tabs and menu items. They look a bit different from their friends.

To deliver design changes to an active tab, you need to add a modifier to an element. Similar to what we was doing for blocks.

    <div class="tabbed-pane">        <span class="                   tabbed-pane__tab                   tabbed-pane__tab_state_current">...</span>    </div>

### Block Modifier DOES Affect Element
Now I'm going to show you where cascade is posible.

<img src="http://img-fotki.yandex.ru/get/5627/14441195.27/0_71207_4cfc639a_M.jpg" width="300" height="259" title="" alt="" border="0"/>

You can see a modified block here. It has a blue theme. Of course, when having a blue theme the block should guarantee that its elements will work correctly. In this situation we allow the block affect its elements.

    .tabbed-pane_theme_blue    .tabbed-pane__tab    {       background-color: #9CF;    }

Here cascade is possible because the tabs' appearance DOES depend on block's modifier.

*************And just to wrap up, to make your blocks independent, please:
 * a block has its "name"   - no "id" but "classname" selectors * avoid cascade * no "tag" selectors
##Block File StructureAll the previously shown examples used flat variant when CSS files for blocks, elements and modifiers are placed into one folder `blocks`.
    blocks/        tabbed-pane.css        tabbed-pane__tab.css        tabbed-pane__pane.css        tabbed-pane_theme_blue.css        tabbed-pane_theme_black.css        tabbed-pane_size_l.css        tabbed-pane_size_s.css        menu.css        menu__item.css        menu_size_l.css        menu_size_s.css            logo.css            search.css        search__checkbox.css        search__autocomplete.css
That works for not very large projects and not very complicated blocks.
If you expect many blocks with elements and modifiers, it's good to contain all the files related to a block in a block folder.
    blocks/        tabbed-pane/            tabbed-pane.css            tabbed-pane__tab.css            tabbed-pane__pane.css            tabbed-pane_theme_blue.css            tabbed-pane_theme_black.css            tabbed-pane_size_l.css            tabbed-pane_size_s.css        logo/            logo.css           menu/            menu.css            menu__item.css            menu_size_l.css            menu_size_s.css            search/            search.css            search__checkbox.css            search__autocomplete.css
Less mess, and also it's much easier to copy block files from project to project.
We, at Yandex, use the most detailed structure with internal folders for elements and modifiers.
    blocks/        tabbed-pane/            __tab/                _state/                    tabbed-pane__tab_state_current.css                tabbed-pane__tab.css            __pane/                tabbed-pane__pane.css            _theme/                tabbed-pane_theme_blue.css                tabbed-pane_theme_black.css            tabbed-pane.css
It is not obligatory, but just works for our case.
Now, before proceeding to the next section, let us sum up.
First, any interface is a set of blocks, which can be combined in different ways, can be placed one into another, can change their parent block. And nothing bad should happen since the blocks are independent.<br/>Also, all the nested tags in a block are elements.</br>And finally, both blocks and elements can be modified.
## BEM
<img src="http://bem.info/bundles-desktop/index/blocks/logo/_type/logo_type_main.png"/>
Now, that the three terms are introduced, I am happy to present you BEM methodology.You've just learnt its parts related to independent CSS blocks.Furthermore, BEM brings some other interesting solutions.
First, BEM is a methodology. It's a way of thinking when developing. It provides us with data domain applicable for all the technologies.<br/>Besides, BEM is a toolkit automating your work.<br/>Finally, BEM is a range of reusable code libraries, making you to develop faster and better.Now let's have a look at all these opportunities in a little more detail.
### CSS for IEFirst, I'd like to show how we deal with our bosom friend, IE browser.
It is possible to link to a page an additional CSS file, especially for IE. Using conditional comments you make other browsers to ignore this file. So that there we can write fixes for IE only.
    <html>        <head>            <!--[if gt IE 7]><!-->             <link rel="stylesheet" href="index.css">             <!--<![endif]-->            <!--[if lt IE 8]>             <link rel=stylesheet href="index.ie.css">             <![endif]-->        </head>        ...
Inside the `ie.css` file you import the general CSS file for the page.
    @import url(index.css);     @import url(blocks/menu/menu.ie.css);     @import url(blocks/button/button.ie.css);     @import url(blocks/footer/footer.ie.css);
Then we can redefine CSS that doesn't work correctly for every piece of interface. It's logical to do it separately for each block.
Blocks that need special IE hacks are equipped with additional `ie.css` files. If all the block files are under the block folder, we can just place one more file in it.
    blocks/        tabbed-pane/            tabbed-pane.css            tabbed-pane.ie.css            ...        menu/            menu.css            menu.ie.css
The same works for elements and modifiers.
    blocks/        tabbed-pane/            tabbed-pane.css            tabbed-pane.ie.css            tabbed-pane__item.css            tabbed-pane__item.ie.css            tabbed-pane_theme_blue.css            tabbed-pane_theme_blue.ie.css with
So, a block folder encapsulates all the CSS needed. Using the project block stack we can assemble CSS files for pages, both the general one and for IE.
## JavaScriptHTML/CSS dummy is not a functional web application yet. But implementing some JavaScript logic we can paint it with colours.
We should code that the `Tabbed Pane` block reacts on leftclick.
<img src="http://img-fotki.yandex.ru/get/4120/14441195.27/0_71214_cff3fb1_M.jpg" width="300" height="259" title="" alt="" border="0"/>
The `Dropdown` block functionality is that it is hidden when a page is just loaded. But if a user makes clicks with the left mouse button on its switcher, the block shows.
`Dropdown` also can be smart enough to calculate its direction according to its place on a page. In the picture the second `Dropdown` block opens up since it's too close to the bottom.

<div style="width: 800px; height: 500px; border: #000 1px solid; position: relative;">
<img src="http://img-fotki.yandex.ru/get/4116/14441195.27/0_71220_33b9df76_M.jpg" width="300" height="271" title="" alt="" border="0" style="position: absolute; top: 20px; left: 20px"/>
<img src="http://img-fotki.yandex.ru/get/5641/14441195.27/0_71225_daf55cf9_M.jpg" width="300" height="271" title="" alt="" border="0" style="position: absolute; bottom: 20px; right: 20px"/>
</div>

This needs JavaScript logic which we have to provide for a page. Pages are usually supplied with JavaScript logic linking a `.js` file to it.

### Sets of Block in JavaScript
Again, for small projects all the magic can fit comfortably into a single one js file.
    <!DOCTYPE html>    <html>        <head>             <link rel=stylesheet href="index.css">            <script type="text/javascript" src="all.js"/>        </head>        ...
But usually we have different functionality for different pages. So that similar to CSS we a have separate JS file for every page.
    <!DOCTYPE html>    <html>        <head>             <link rel=stylesheet href="index.css">            <script type="text/javascript" src="index.js"/>        </head>        ...
Again, block set of a page can be changed and we need to ensure that we link corresponding JavaScript.
Similar to CSS for blocks, we can detach a separate js file for every block and store it under the block folder.
    blocks/         menu/            menu.css            menu.js         dropdown/            dropdown.css            dropdown.js         tabbed-pane/            tabbed-pane.css            tabbed-pane.js 
Inside the `menu.js` file there is a piece of logic related to the `Menu`. The same for the `Tabbed Pane`.
Using these pieces of logic we can build JavaScript file for a page similar to what we've done with CSS before.
    borschik:include:blocks/menu/menu.js    borschik:include:blocks/tabbed-pane/tabbed-pane.js    ...
Each line in the file refers to a particular block.
##CSS and JavaScript flattening with Borschik
Don't be confused with an unfamiliar "include" instruction. Of course, we do not supply a browser with such a strange file but flatten each include.
    /* Menu block begins */    (function($){        $('.menu__item').on('click', function(e) {            $(this).toggleClass('menu__item_state_current');        });    })(jQuery)Here you can see here that including line for the menu turned into the content of the file.
You can do such inlining magic automatically with the tool called [Borschik](https://github.com/veged/borschik).
Besides flattening JavaScript, it does the same with CSS files of imports.
You can work with imports when developing, but for production it's better to decrease the amount of CSS files. Each CSS import causes an HTTP request making a browser to load many files.
    @import url(blocks/header.css);     @import url(blocks/menu.css);    ...
Using borschik to prepare a project for production deployment, you can turn all the imports into relevant CSS content.
    .header {        ...    }    .menu {        ...    }
This is very important that borschik works correctly with relative paths in CSS. So, it's not just stupid inlining.
**blocks/menu/menu.css**
    .menu {        background: url(menu__bg.png);    }
**pages/index.css**
    @import url(blocks/menu/menu.css);
**pages/_index.css**
    .menu {        background: url(../blocks/menu/menu__bg.png);    }
## Building Page Files