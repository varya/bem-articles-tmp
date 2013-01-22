# Start developing BEM with project-stub

This article says how to develop [online shop
web-page](http://toivonen.github.com/online-shop-dummy/desktop.bundles/index/index.html)
using BEM principles in CSS, JavaScript and BEMHTML templates. We will use `bem
tools` and its subcommand `bem server` when developing.

<img
src="http://img-fotki.yandex.ru/get/6505/14441195.26/0_6f0b2_557ef428_L.jpg"
width="500" height="351" title="Online shop web page" alt="Online shop web page"
border="0"/>

## Tools
To start you will need [bem tools](https://github.com/bem/bem-tools), a command line
toolkit to operate on BEM entities and building your project. Follow the
installing steps in its repository.

## Running your project repository
The easiest way to run a project is to copy similar project repository with
suitable structure. We would like to use full stack of BEM technologies, so this
is the [project-stub](https://github.com/bem/project-stub) repository that
suits.

    $ git clone git://github.com/bem/project-stub.git my-pretty-project
    $ cd my-pretty-project/
    $ rm -rf .git
    $ git init

Then, you need to build the project running `make` command:

    $ make

That takes some time because the first launch also installs all the required npm
packadges.<br/>
When finished, you will see the following message:

   info: Server is listening on port 8080. Point your browser to http://localhost:8080/

This means that there is `bem server` running. It will automatically rebuild your
project if you change something.

## Changing pages
By now you have one page in your project, which is
[index.html](http://localhost:8080/desktop.bundles/index/index.html). Do not
hesitate to open it under your browser.<br/>
When opening the page at the first time, you have to wait some time because `bem
server` is loading all the libraries expected for building the page.

The project structure dictates to store blocks under `desktop.blocks` folder and
pages under `desktop.bundles`.<br/>
Frankly speaking, `desktop.bundles` keeps sets of blocks. These sets can be of
the most popular blocks among several pages, which is usually called as
`common`. Or a set can unite all the blocks from all the pages, being called
`all`. Finally, the easiest case, there could be a set of blocks for each page.
Here we will be using the last easiest way.

Chaning `desktop.bundles/index/index.bemjson.js` file you can modify the page.

### Definig a block in BEMJSON
Fist, let's place `head` block into the page.

    { block: 'head' }

From now on you can find code snapshort on Gist: https://gist.github.com/4175550

Refresh the page to see proper `<div>`.

    <!DOCTYPE html>
    <html class="i-ua_js_yes i-ua_css_standard">
        <head>...</head>
        <body class="b-page b-page__body">
            <div class="head"></div>
        </body>
    </html>

Next, we will fill the head with a search form, logo and an approptiate layout.

Put `layout` block with its 2 element `left` and `right` inside `head`.

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

This will a requisite markup for you to use when writing CSS rules. Or, speaking
in BEM language, you need to implement `layout` block in CSS.

### Creating a new block
You need to use `bem create` command to get a new block file for a technology
you are going to work with.

    $ bem create -l desktop.blocks/ -T css -b layout

Running this command will create `desktop.blocks/layout/layout.css`, and inside
there will be a CSS selector that matches the `layout` block. What you are to do
is to fill in the selector with your CSS properties.<br/>
Or just copy and paste from Gist: https://gist.github.com/4175598
