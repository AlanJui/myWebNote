# NodeJS and NPM

## 安裝

## Upgate NodeJS

1) Clear NPM's cache:

    $   sudo npm cache clean -f

2) Install n : Simple flavour of node binary management

    sudo npm install -g n

3) Install latest stable NodeJS version

    $   sudo n stable

or

    $   sudo n 0.12

## Update NPM

    $   sudo npm install -g npm@latest

## NPM Install

    $   npm install

npm install will install both "dependencies" and "devDependencies"

    $   npm install --production

npm install --production will only install "dependencies"

    $   npm install --dev

npm install --dev will only install "devDependencies"
