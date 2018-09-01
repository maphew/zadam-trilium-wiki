This pages describes manually installing Trilium on your server.

## Requirements

Trilium is a [node.js](http://nodejs.org/) application. Supported (tested) version of node.js is latest 8.X.X. Unfortunately node.js 10 currently doesn't work because of problems with scrypt dependency.

You can check your node version with this command (node.js needs to be installed):
~~~~
node --version
~~~~

If your linux distribution has only outdated version of node.js, you can take a look at the [[installation instructions|https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions]] on node.js website which covers most popular distributions.

### Image requirements
If you want to use Trilium server installation only as a [[sync server|Synchronization]], you can skip this section.

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

## TLS

Don't forget to [[configure TLS|TLS configuration]], which is required for secure usage!