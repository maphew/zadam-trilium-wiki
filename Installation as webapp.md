This pages describes installing Trilium as a web application as opposed to installing desktop (electron) build.

Trilium as web application is typically used as a [[sync|Synchronization]] server, but can be also used as online version of Trilium.

## Requirements

Trilium is a [node.js](http://nodejs.org/) application. Supported version is 8.2.1 and up, but it might work with earlier versions, it's just not tested. It will definitely not run on node version lower than 7.6 though (first version with async/await enabled).

## Installation 

### Download
You can either download source code zip/tar from [[latest release|https://github.com/zadam/trilium/releases/latest]] or clone git repository from stable branch with ```git clone -b stable https://github.com/zadam/trilium.git```

## Installation
~~~
cd trilium

# download all node dependencies
npm install
~~~~

## Run

~~~~
cd trilium

# using nohup to make sure trilium keeps running after user logs out
nohup node bin/www &
~~~~

