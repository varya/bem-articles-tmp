# Start developing BEM with project-stub

This article shows you how to develop an [online shop
web page](http://toivonen.github.com/online-shop-dummy/desktop.bundles/index/index.html)
using BEM principles in CSS, JavaScript and BEMHTML templates. While developing,
we will use `bem tools` and its subcommand `bem server`.

<img
src="http://img-fotki.yandex.ru/get/6505/14441195.26/0_6f0b2_557ef428_L.jpg"
width="500" height="351" title="Online shop web page" alt="Online shop web page"
border="0"/>

## Tools
You need a command-line toolkit [bem tools](https://github.com/bem/bem-tools) to
begin with the project.
Follow the installation steps in the corresponding repository.

## Start with a project repository
The easiest way to start is to copy a similar project repository with suitable
structure.<br/>
We intend to use the full power of BEM technologies, so this
[project-stub](https://github.com/bem/project-stub) will suit you just fine.

    $ git clone git://github.com/bem/project-stub.git my-pretty-project
    $ cd my-pretty-project/
    $ rm -rf .git
    $ git init

Build the project by running a `make` command:

    $ make

The first launch may take some time as required npm packadges are being
installed in background.

For development you can run

    $ make server

Upon completion, you'll see the following message:

   info: Server is listening on port 8080. Point your browser to http://localhost:8080/

This means `bem server` is up and running; from this point on, your project is
automatically rebuilt each time you change something.

## Changing pages
You have just one page in your project to begin with:
[index.html](http://localhost:8080/desktop.bundles/index/index.html). Try and
open it in your browser.<br/>
When opening the page for the first time, be prepared to wait a few seconds
while `bem server` is loading all the libraries used for building the page.

This project's structure presumes that blocks are stored under the
`desktop.blocks` folder and pages under `desktop.bundles` folder.<br/>
In fact, `desktop.bundles` may contain bundles consisting of blocks most
commonly used on most of the pages, i.e. `common` block bundle, or all the blocks
from all the pages, i.e. `all` block bundle. Finally, the simplest case:
you can have a set of blocks for each page; it's how we will proceed.

You can modify the page by changing the `desktop.bundles/index/index.bemjson.js`
file.

### Defining a block in BEMJSON
First, let's add `head` block to the page.

    { block: 'head' }

From this point on, find code snapshots on Gist: https://gist.github.com/4175550

Refresh the page to see the corresponding `<div>`.

    <!DOCTYPE html>
    <html class="i-ua_js_yes i-ua_css_standard">
        <head>...</head>
        <body class="b-page b-page__body">
            <div class="head"></div>
        </body>
    </html>

On the next step, we add a search form, a logo, and describe layout inside the
header.

Put a `layout` block along with its 2 elements (`left` and `right`) inside `head`.

    content: [
        {
            block: 'head',
            content: {
                block: 'layout',
                content: [
                    {
                        elem: 'left',
                        content: 'left here'
                    },
                    {
                        elem: 'right',
                        content: 'right here'
                    }
                ]
            }
        }
    ]

https://gist.github.com/4175573

    <!DOCTYPE html>
    <html class="i-ua_js_yes i-ua_css_standard">
        <head>...</head>
        <body class="b-page b-page__body">
            <div class="head">
                <div class="layout">
                    <div class="layout__left">left here</div>
                    <div class="layout__right">right here</div>
                </div>
            </div>
        </body>
    </html>

This markup requires CSS rules to be described.
Or, to say the same in the terms of BEM, you have to implement `layout` block in CSS.

## Creating a new block
You need to use `bem create` to get a new block file for the technology
you are going to work with.

    $ bem create -l desktop.blocks/ -T css -b layout

This command will create `desktop.blocks/layout/layout.css` with
a CSS selector that matches the `layout` block. It's now your part
to fill up the selector with CSS properties.<br/>
You can copy and paste implementation from Gist: https://gist.github.com/4175598

## Using block library
You don't need to implement web search form and logo blocks yourself; they are
provided by [bem-bl block library](https://gist.github.com/4175598). So, you can
just declare them when defining your page. This means pasting BEMJSON block
definition into the `desktop.bundles/index/index.bemjson.js` page file.

We will use
[b-searh](http://bem.github.com/bem-bl/sets/common-desktop/b-search/b-search.en.html)
and
[b-logo](http://bem.github.com/bem-bl/sets/common-desktop/b-logo/b-logo.en.html)
blocks.<br/>
https://gist.github.com/4175640

For the logo, you can use our [cute BEM
image](http://toivonen.github.com/online-shop-dummy/desktop.blocks/b-logo/b-logo.png)
or any other pic.

<img
src="http://img-fotki.yandex.ru/get/4119/14441195.26/0_6f0b9_2d1d77a3_XL.jpg"
width="800" height="187" title="Using the block library"
alt="Using the block library" border="0"/>

### Redefining library blocks
#### Redefining in CSS
`b-logo` block provides just a piece of markup. It is the developer's responsibility
to create the needed CSS for the block because every new site design usually
needs unique styles.

We will keep CSS rules for `b-logo` in its CSS file, has to be created on
the project block level:

    $ bem create -l desktop.blocks/ -T css -b b-logo

Then, save some time and copy CSS from here: https://gist.github.com/4175675

The same can be done for `b-search` block:

    $ bem create -l desktop.blocks/ -T css -b b-search

https://gist.github.com/4195433

<img
src="http://img-fotki.yandex.ru/get/5708/14441195.26/0_6f0ba_bb628e4c_XL.jpg"
width="800" height="141" title="Styled header" alt="Styled header"
border="0"/>

#### Redefining BEMHTML
You need an additional container DOM node to center the page. So, we
define template implementation for `b-page` block by creating the same block on
the project level. We are going to use `BEMHTML` as a templating language.

    $ bem create -l desktop.blocks/ -b b-page -T bemhtml

Write code wrapping page content with an additional container node into the
obtained `desktop.blocks/b-page/b-page.bemhtml` file.

    block b-page, content: {
        elem: 'body-i',
        content: this.ctx.content
    }

https://gist.github.com/4175742

    <!DOCTYPE html>
    <html class="i-ua_js_yes i-ua_css_standard">
        <head>...</head>
        <body class="b-page b-page__body">
            <div class="b-page__body-i">
                <div class="head">
                    <div class="layout">...</div>
                </div>
            </div>
        </body>
    </html>

Then, create `b-page` block in CSS technology to style the resulting markup.

    $ bem create -l desktop.blocks/ -T css -b b-page

Do not hesitate to copy prepared CSS code for the newborn
`desktop.blocks/b-page/b-page.css` file form here: https://gist.github.com/4175763

Define `border` property for `head` block, so that you can see where it is.

    $ bem create -l desktop.blocks/ -T css -b head

Again, you can borrow the content for `desktop.blocks/head/head.css` file from
here: https://gist.github.com/4175776.

<img src="http://img-fotki.yandex.ru/get/6505/14441195.26/0_6f0bc_d000a7a2_L.jpg"
width="500" height="129" title="Borderd header" alt="Bordered header" border="0"/>

## BEMHTML templates
You can use BEMHTML templates not only for declaring output HTML tags but also
for gerenating additional markup respondent of view.

Just to play with it, let's place  a list of goods into the page. It is a
separate `goods` block declared in BEMJSON page description and containing all
the neccessary data.

    {
        block: 'goods',
        goods: [
            {
                title: 'Apple iPhone 4S 32Gb',
                image: 'http://mdata.yandex.net/i?path=b1004232748_img_id8368283111385023010.jpg',
                price: '259',
                url: '/'
            },
            {
                title: 'Samsung Galaxy Ace S5830',
                image: 'http://mdata.yandex.net/i?path=b0206005907_img_id5777488190397681906.jpg',
                price: '73',
                url: '/'
            },
            ...
    }

https://gist.github.com/4176078

This block has to be implemented with BEMHTML technology in order to be turned
into an appropriate piece of HTML. Also, it needs to be styled with CSS. So, you
can create this block with all the default technologies by just removing `-T`
flag.

    $ bem create -l desktop.blocks -b goods

Then, write BEMHTML code turning input data JSON into block elements and place it
into `desktop.blocks/goods/goods.bemhtml` template file. Also, define what are
the DOM nodes of the block and its elements by using `tag` mode.

    block goods {

        tag: 'ul'

        ...

        elem item, tag: 'li'

        elem title, tag: 'h3'

    }

https://gist.github.com/4176118

    <!DOCTYPE html>
    <html class="i-ua_js_yes i-ua_css_standard">
        <head>...</head>
        <body class="b-page b-page__body">
            <div class="b-page__body-i">
                <div class="head">...</div>
                <ul class="goods">
                    <li class="goods__item">
                        <h3 class="goods__title">Apple iPhone 4S 32Gb</h3>
                        <img class="goods__image" src="http://mdata.yandex.net/i?path=b1004232748_img_id8368283111385023010.jpg"/>
                        <span class="goods__price">259</span>
                    </li>
                    <li class="goods__item">...</li>
                    <li class="goods__item">...</li>
                </ul>
            </div>
        </body>
    </html>

Template can produce not only block elements but nested blocks as well. In this
case, you can wrap price digitals with `b-link` block from `bem-bl` library.

    {
        elem: 'price',
        content: {
            block: 'b-link',
            url: item.url,
            content: item.price
        }
    }

https://gist.github.com/4176996

And one more trick. If you would like to avoid cascade when styling the block,
mark this link as an element of `goods` block.

    {
        block: 'b-link',
        mix: [{ block: 'goods', elem: 'link' }],
        url: item.url,
        content: item.price
    }

https://gist.github.com/4177113

    ...
    <ul class="goods">
        <li class="goods__item">
            <h3 class="goods__title">Apple iPhone 4S 32Gb</h3>
            <img class="goods__image" src="http://mdata.yandex.net/i?path=b1004232748_img_id8368283111385023010.jpg"/>
            <span class="goods__price">
                <a class="b-link goods__link" href="/">259</a>
            </span>
        </li>
        <li class="goods__item">...</li>
        <li class="goods__item">...</li>
    </ul>

Then, mark elements corresponsing to new goods with a modifier and with a bit of
skill on your part you can add some layout nodes.<br/>
https://gist.github.com/4177157

Use this code snapshot for block CSS: https://gist.github.com/4177163<br/>
Notice, you don't need to create CSS file for the block here because it has
already been produced when creating the block with all its default techs.

<img src="http://img-fotki.yandex.ru/get/6508/14441195.26/0_6f0c7_e5284b82_L.jpg"
width="500" height="368" title="List of goods" alt="List of goods" border="0"/>

You also need some CSS for our dear friend, the IE browser, since it is not in the
list of default block technologies.

    $ bem create block -l desktop.blocks/ -T ie.css goods

Again, the content for the resulting `desktop.blocks/goods/goods.ie.css` file is
already waiting for your on Gist: https://gist.github.com/4177174

## Block dependencies
Besides declaring blocks in input JSON data you need to ensure linking
corresponding templates, CSS and JavaScript to the page. You can do this by
using special `deps.js` block technology for -- as you can guess -- defining
block dependencies.

    $ bem create -l desktop.blocks/ -T deps.js -b goods

You can use moderate dependency coded `shouldDeps` and declare that you
need `b-link` block.

    ({
        shouldDeps: [
            { block: 'b-link' }
        ]
    })

https://gist.github.com/4177031

## Using libraries
It will be nice if every position in the list is represented as a rectangle with
a shadow. We can borrow a block from [a friend's of mine block
library](https://github.com/john-johnson/j).<br/>
It provides just one block named `box` doing all we need.

You should declare library repository URL in `./bem/make.js` file to get its
code into your project.

    getLibraries: function() {

        return {
            'bem-bl': {
                type: 'git',
                url: 'git://github.com/bem/bem-bl.git',
                treeish: '0.3'
            },
            'bemhtml' : {
                type: 'git',
                url: 'git://github.com/bem/bemhtml.git'
            },
            'john-lib' : {
                type: 'git',
                url: 'git://github.com/john-johnson/j.git'
            }
        };

    }

https://gist.github.com/4177229

Then, make your pages to take blocks from the block level provided by the library
You can do this by tuning bundle configuration in `desktop.bundles/.bem/level.js`.

    exports.getConfig = function() {

        return BEM.util.extend(this.__base() || {}, {
            bundleBuildLevels: this.resolvePaths([
                '../../bem-bl/blocks-common',
                '../../bem-bl/blocks-desktop',
                '../../bemhtml/common.blocks',
                '../../john-lib/blocks/',
                '../../desktop.blocks'
            ])
        });

    };

https://gist.github.com/4177250

Unfortunately, you need to restart `bem server` after chaning configuration.
Cancel the current process and run `make server` again.<br/>
BEM tools` guys promise taking away this need to restart in the future versions.

## Mix for blocks and elements
Having linked the library you can use `box` block. It could be just a wrapper,
but for saving some markup you can `mix` blocks.

One of the possible ways to mix blocks is to declare this mix in BEMJSON input
data.<br/>
Here you can mix `head` and `box` blocks by chaning the page.

    {
        block: 'head',
        mix: [ { block: 'box' } ],
        content: ...
    }

https://gist.github.com/4177292

    <!DOCTYPE html>
    <html class="i-ua_js_yes i-ua_css_standard">
        <head>...</head>
        <body class="b-page b-page__body">
            <div class="b-page__body-i">
                <div class="head box">
                    <div class="layout">...</div>
                </div>
                <ul class="goods">...</ul>
            </div>
        </body>
    </html>

Don't forget to declare that `head` block requires `box`.

    $ bem create -l desktop.blocks/ -T deps.js -b head

    ({
        shouldDeps: [
            { block: 'box' }
        ]
    })

https://gist.github.com/4235143

<img src="http://img-fotki.yandex.ru/get/5803/14441195.26/0_6f0c4_4e3f9249_XL.jpg" width="800"
height="238" title="Head + Box = ❤" alt="Head + Box = ❤" border="0"/>

You also can mix an element and a block.<br/>
Let's write that every `item` element of `goods` block is at the same time `box`
block.

    content.push({
        elem: 'item',
        mods: mods,
        mix: [{ block: 'box' }],
        content: ...

https://gist.github.com/4177350

    <!DOCTYPE html>
    <html class="i-ua_js_yes i-ua_css_standard">
        <head>...</head>
        <body class="b-page b-page__body">
            <div class="b-page__body-i">
                <div class="head box">
                    <div class="layout">...</div>
                </div>
                <ul class="goods">
                    <li class="goods__item box">...</li>
                    <li class="goods__item box">...</li>
                    <li class="goods__item box">...</li>
                    <li class="goods__item goods__item_new_yes box">...</li>
                    <li class="goods__item box">...</li>
                    <li class="goods__sizer">...</li>
                    ...
                </ul>
            </div>
        </body>
    </html>


<img src="http://img-fotki.yandex.ru/get/6511/14441195.26/0_6f0c5_bcef9ce9_L.jpg"
width="500" height="286" title="Inboxed items" alt="Inboxed items" border="0"/>

## Declarative JavaScript
###JavaScript for a block
`box` block borrowed from my friend's library can be rolled up. This is its
dynamic functionality coded in JavaScript.

If you'd like to use this in `head`, change the block BEMJSON declaration, and
set that mixed `box` block has JavaScript implementation.

    mix: [{ block: 'box', js: true }]

https://gist.github.com/4202622

It is required to have `swither` element in the block.

    content: [
        {
            block: 'layout',
            ...
        },
        {
            block: 'box',
            elem: 'switcher'
        }
    ]

https://gist.github.com/4202651

With that you have a block with clickable arrow-shaped element which rolls the
block up.

<img src="http://img-fotki.yandex.ru/get/4603/14441195.26/0_6f0c8_b65eea6_L.jpg"
width="318" height="264" title="Arrow" alt="Arrow" border="0"/>

### Redefining JavaScript
What if you are not sartisfied with the dynamic functionality provided with `box`
block? Maybe you would like it to roll up and left. Otherwise, you cannot change
code of the library you borrowed if it's not yours.<br/>
But thanks to using [i-bem
block-framework](https://github.com/bem/bem-bl/tree/master/blocks-common/i-bem)
you can change (redefine or extend) block JavaScript on your own level.

    bem create -l desktop.blocks -T js -b box

Remove everything but `setMod` section from the resulting `desktop.blocks/box/box.js`
file.

    onSetMod : {

    }

https://gist.github.com/4195865

In this case the block is to react on setting and removing `closed` modifier.

    onSetMod : {

        'closed': {
            'yes': function() {
                // some functionality here
            },
            '': function() {
                // some functionality here
            }
        }

    }

https://gist.github.com/4195879

## Creating pages
In BEM world a page is also a block on a special level. So, you can use
`bem create` for pages as well.

    $ bem create -l desktop.bundles -b contact

As you can see, there is no `-T` flag here. That's because `desktop.bundles`
block level is tuned to know `BEMJSON` technology as a default for a block.<br/>
That results into `desktop.bundles/contact/contact.bemjson.js` file filled with
dummy page content.

You can load a new page in browser
http://localhost:8080/desktop.bundles/contact/contact.html <br/>
When required at the first time `bem server` builds it.

## Production deployment
When developing, every time you require a page in a browser `bem server`
rebuilds what has to be rebuilt after your changes.

For production deployment all the pages have to be built, no matter if someting
was not changed. You can use `bem make` for such a building.<br/>
Recommended to run local project version:

    $ ./node_modules/bem/bin/bem make

-------------

<sup>credits</sup>
Many thanks to [tyv](https://github.com/tyv) and
[gela-d](https://github.com/gela-d) for this cute HTML/CSS markup.<br/>
My gratitude to [ingdir](https://github.com/ingdir) for his tuneful english.
