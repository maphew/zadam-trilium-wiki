By server installation we mean installing Trilium as a web application as opposed to installing desktop (electron) build.

## Requirements

Trilium is a [node.js](http://nodejs.org/) application. Supported version is 8.2.1 and up, but it might work with earlier versions, it's just not tested. It will definitely not run on node version lower than 7.6 though (first version with async/await enabled).

## Install from git
~~~
git clone https://github.com/zadam/trilium.git
cd trilium

# stable branch should contain latest stable release
git checkout stable

# download all node dependencies
npm install
~~~~

## Run

~~~~
cd trilium

# using nohup to make sure trilium keeps running after user logs out
nohup node bin/www &
~~~~

