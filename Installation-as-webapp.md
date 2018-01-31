This pages describes installing Trilium as a web application as opposed to installing desktop (electron) build.

Trilium as web application is typically used as a [[sync|Synchronization]] server, but can be also used as online version of Trilium.

## Requirements

Trilium is a [node.js](http://nodejs.org/) application. Supported version is 8.2.1 and up, but it might work with earlier versions, it's just not tested. It will definitely not run on node version lower than 7.6 though (first version with async/await enabled).

You can check your node version with this command (node.js needs to be installed):
~~~~
node --version
~~~~

If your linux distribution has only outdated version of node.js, you can take a look at the [[installation instructions|https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions]] on node.js website which covers most popular distributions.

### Image requirements

To compile libraries required for image support you need to have "autoconf" installed. In ubuntu you can do this with

~~~~
sudo apt install autoconf
~~~~

To work with PNG files you'll also need libpng16-16 library.

~~~~
sudo apt install libpng16-16
~~~~

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
nohup node src/www &
~~~~

Application by default starts up on port 8080, so you can open your browser and navigate to http://localhost:8080 to access Trilium (replace "localhost" with your hostname).
