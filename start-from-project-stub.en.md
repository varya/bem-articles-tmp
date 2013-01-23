# Start developing BEM with project-stub

This article shows you how to develop an [online shop
web page](http://toivonen.github.com/online-shop-dummy/desktop.bundles/index/index.html)
using BEM principles in CSS, JavaScript and BEMHTML templates. While developing, we will use `bem
tools` and its subcommand `bem server`.

<img
src="http://img-fotki.yandex.ru/get/6505/14441195.26/0_6f0b2_557ef428_L.jpg"
width="500" height="351" title="Online shop web page" alt="Online shop web page"
border="0"/>

## Tools
You need a command-line toolkit [bem tools](https://github.com/bem/bem-tools) to begin with the project.
Follow the installation steps in the corresponding repository.

## Start with a project repository
The easiest way to start is to copy a similar project repository with suitable structure.
We intend to use the full power of BEM technologies, so this [project-stub](https://github.com/bem/project-stub)
will suit you just fine.

    $ git clone git://github.com/bem/project-stub.git my-pretty-project
    $ cd my-pretty-project/
    $ rm -rf .git
    $ git init

Build the project by running a `make` command:

    $ make

This might take some time on the first launch as all the required npm
packadges are installed.<br/>
Upon completion, you'll see the following message:

   info: Server is listening on port 8080. Point your browser to http://localhost:8080/

This means `bem server` is up and running; from this point on, your project is automatically rebuilt
each time you change something.

## Changing pages
You have just one page in your project to begin with:
[index.html](http://localhost:8080/desktop.bundles/index/index.html). Try and open it in your browser.<br/>
When opening the page for the first time, be prepared to wait a few seconds while `bem
server` is loading all the libraries used for building the page.

BEM project structure presumes that blocks are stored under the `desktop.blocks` folder and
pages under `desktop.bundles` folder.<br/>
In fact, `desktop.bundles` may contain bundles consisting of blocks most commonly used on most
of the pages, i.e. `common` block bundle, or all the blocks
from all the pages, i.e. `all` block bundle. Finally, the simplest case:
you can have a set of blocks for each page; it's how we will proceed.

You can modify the page by changing the `desktop.bundles/index/index.bemjson.js` file.

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

On the next step, we add a search form, a logo, and describe layout inside the header.

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
Or, saying the same in BEM terms, you have to implement `layout` block in CSS.

## Creating a new block
You need to use `bem create` to get a new block file for the technology
you are going to work with.

    $ bem create -l desktop.blocks/ -T css -b layout

Running this command will create `desktop.blocks/layout/layout.css`, and inside
you will find a CSS selector that matches the `layout` block. It's now your part
to fill up the selector with CSS properties.<br/>
You can just copy and paste from Gist: https://gist.github.com/4175598

## Using block library
You do not need to implement web search form and logo blocks yourself; they are provided by [bem-bl block
library](https://gist.github.com/4175598). So, you can just declare them when
defining your page. This means pasting BEMJSON block definition into the 
`desktop.bundles/index/index.bemjson.js` page file.

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
`b-logo` block provides just a piece of markup. It is developer's responsibility to create
the needed CSS for the block because every new site design usually needs unique styles.

We will keep CSS rules for `b-logo` in its CSS file, which we need to create on
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
