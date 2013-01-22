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
