# Deploy app to Heroku

## 設定 MongoDB Production 環境

###  查詢 MongoDB Connection URI

```
$ heroku config --app my-angular-fs | grep MONGOLAB_URI
MONGOLAB_URI: mongodb://heroku_app34561376:pf3dtvmcbabjj4bvk51spsb46l@dbh74.mongolab.com:27747/heroku_app34561376
```

### 填入設定檔

修訂如下檔案：
server/config/environment/production.js

```
module.exports = {
  // Server IP
  ip:       ...,

  // Server port
  port:     ...,

  // MongoDB connection options
  mongo: {
    uri:    process.env.MONGOLAB_URI ||
            process.env.MONGOHQ_URL ||
            process.env.OPENSHIFT_MONGODB_DB_URL+process.env.OPENSHIFT_APP_NAME ||
            'mongodb://heroku_app34561376:pf3dtvmcbabjj4bvk51spsb46l@dbh74.mongolab.com:27747/heroku_app34561376'
  }
};
```

## 設定 heroku 佈署所需的資料

在 Grunt 檔案，於 buildcontrol：heroku 設定佈署所需的資料。

```
module.exports = function (grunt) {
  ...
  var pkg = require('./package.json');
  ...

  grunt.initConfig({

    buildcontrol: {
      options: {
        dir: 'dist',
        commit: true,
        push: true,
        message: 'Built %sourceName% from commit %sourceCommit% on branch %sourceBranch%'
      },

      heroku: {
        options: {
          remote: 'https://git.heroku.com/my-angular-fs.git',
          branch: 'master',
          tag: pkg.version
        }
      }
    }


  )};

}
```

### 加入 Procfile 檔案

建立 Procfile 檔案，並加入如下內容，指示 Heroku 將此 App 當 web 應用系統處理。

```
web: node server/app.js
```

## 佈署到 Heroku

### 簽入修訂

```
$ git add .
```

```
$ git commit -am "Ready for deploy to Heroku
[master c9cab57] Ready for deploy to Heroku
 1 file changed, 2 insertions(+), 2 deletions(-)
```

```
$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)
nothing to commit, working directory clean
```

### 執行 Build 作業

執行 Build 作業，產生佈署到 Heroku  所需的檔案，並放入「根路徑」下的 dist 資料夾。

```
$ grunt build
```

### 執行 Deploy （佈署）作業

將 dist 資料夾中的檔案，佈署到 Heroku 平台。

```
$ grunt buildcontrol:heroku
Running "buildcontrol:heroku" (buildcontrol) task

Creating remote.

No changes to your branch. Skipping commit.

Tagging the local repository with 0.0.0

Pushing master to https://git.heroku.com/my-angular-fs.git
remote: Compressing source files... done.
remote: Building source:
remote:
remote: -----> Node.js app detected
remote:
remote: -----> Reading application state
remote:        package.json...
remote:        build directory...
remote:        cache directory...
remote:        environment variables...
remote:
remote:        Node engine:         >=0.10.0
remote:        Npm engine:          unspecified
remote:        Start mechanism:     npm start
remote:        node_modules source: package.json
remote:        node_modules cached: false
remote:
remote:        NPM_CONFIG_PRODUCTION=true
remote:        NODE_MODULES_CACHE=true
remote:
remote: -----> Installing binaries
remote:        Resolving node version >=0.10.0 via semver.io...
remote:        Downloading and installing node 0.12.0...
remote:        Using default npm version: 2.5.1
remote:
remote: -----> Building dependencies
remote:        No cache available
remote:        Installing node modules
remote:
remote:        > kerberos@0.0.9 install /tmp/build_b2e25e89a0b16894fb28b67ddb41ddcb/node_modules/connect-mongo/node_modules/mongodb/node_modules/kerberos
remote:        > (node-gyp rebuild 2> builderror.log) || (exit 0)
remote:
remote: ongodb/node_modules/kerberos/build'
remote:          CXX(target) Release/obj.target/kerberos/lib/kerberos.o
remote:          CXX(target) Release/obj.target/kerberos/lib/worker.o
remote:          CC(target) Release/obj.target/kerberos/lib/kerberosgss.o
remote:          CC(target) Release/obj.target/kerberos/lib/base64.o
remote:          CXX(target) Release/obj.target/kerberos/lib/kerberos_context.o
remote:          SOLINK_MODULE(target) Release/obj.target/kerberos.node
remote:          SOLINK_MODULE(target) Release/obj.target/kerberos.node: Finished
remote:          COPY Release/kerberos.node
remote:        make: Leaving directory `/tmp/build_b2e25e89a0b16894fb28b67ddb41ddcb/node_modules/connect-mongo/node_modules/mongodb/node_modules/kerberos/build'
remote:
remote:        > ws@0.4.31 install /tmp/build_b2e25e89a0b16894fb28b67ddb41ddcb/node_modules/socket.io-client/node_modules/engine.io-client/node_modules/ws
remote:        > (node-gyp rebuild 2> builderror.log) || (exit 0)
remote:
remote:        make: Entering directory `/tmp/build_b2e25e89a0b16894fb28b67ddb41ddcb/node_modules/socket.io-client/node_modules/engine.io-client/node_modules/ws/build'
remote:          CXX(target) Release/obj.target/bufferutil/src/bufferutil.o
remote:        make: Leaving directory `/tmp/build_b2e25e89a0b16894fb28b67ddb41ddcb/node_modules/socket.io-client/node_modules/engine.io-client/node_modules/ws/build'
remote:
remote:        > ws@0.5.0 install /tmp/build_b2e25e89a0b16894fb28b67ddb41ddcb/node_modules/socket.io/node_modules/engine.io/node_modules/ws
remote:        > (node-gyp rebuild 2> builderror.log) || (exit 0)
remote:
remote:        make: Entering directory `/tmp/build_b2e25e89a0b16894fb28b67ddb41ddcb/node_modules/socket.io/node_modules/engine.io/node_modules/ws/build'
remote:          CXX(target) Release/obj.target/bufferutil/src/bufferutil.o
remote:          SOLINK_MODULE(target) Release/obj.target/bufferutil.node
remote:          SOLINK_MODULE(target) Release/obj.target/bufferutil.node: Finished
remote:          COPY Release/bufferutil.node
remote:          CXX(target) Release/obj.target/validation/src/validation.o
remote:          SOLINK_MODULE(target) Release/obj.target/validation.node
remote:          SOLINK_MODULE(target) Release/obj.target/validation.node: Finished
remote:          COPY Release/validation.node
remote:        make: Leaving directory `/tmp/build_b2e25e89a0b16894fb28b67ddb41ddcb/node_modules/socket.io/node_modules/engine.io/node_modules/ws/build'
remote:
remote:        > kerberos@0.0.9 install /tmp/build_b2e25e89a0b16894fb28b67ddb41ddcb/node_modules/mongoose/node_modules/mongodb/node_modules/kerberos
remote:        > (node-gyp rebuild 2> builderror.log) || (exit 0)
remote:
remote:        make: Entering directory `/tmp/build_b2e25e89a0b16894fb28b67ddb41ddcb/node_modules/mongoose/node_modules/mongodb/node_modules/kerberos/build'
remote:          CXX(target) Release/obj.target/kerberos/lib/kerberos.o
remote:          CXX(target) Release/obj.target/kerberos/lib/worker.o
remote:          CC(target) Release/obj.target/kerberos/lib/kerberosgss.o
remote:          CC(target) Release/obj.target/kerberos/lib/base64.o
remote:          CXX(target) Release/obj.target/kerberos/lib/kerberos_context.o
remote:          SOLINK_MODULE(target) Release/obj.target/kerberos.node
remote:          SOLINK_MODULE(target) Release/obj.target/kerberos.node: Finished
remote:          COPY Release/kerberos.node
remote:        make: Leaving directory `/tmp/build_b2e25e89a0b16894fb28b67ddb41ddcb/node_modules/mongoose/node_modules/mongodb/node_modules/kerberos/build'
remote:
remote:        > bson@0.2.19 install /tmp/build_b2e25e89a0b16894fb28b67ddb41ddcb/node_modules/connect-mongo/node_modules/mongodb/node_modules/bson
remote:        > (node-gyp rebuild 2> builderror.log) || (exit 0)
remote:
remote:        make: Entering directory `/tmp/build_b2e25e89a0b16894fb28b67ddb41ddcb/node_modules/connect-mongo/node_modules/mongodb/node_modules/bson/build'
remote:          CXX(target) Release/obj.target/bson/ext/bson.o
remote:          SOLINK_MODULE(target) Release/obj.target/bson.node
remote:          SOLINK_MODULE(target) Release/obj.target/bson.node: Finished
remote:          COPY Release/bson.node
remote:        make: Leaving directory `/tmp/build_b2e25e89a0b16894fb28b67ddb41ddcb/node_modules/connect-mongo/node_modules/mongodb/node_modules/bson/build'
remote:
remote:        > bson@0.2.19 install /tmp/build_b2e25e89a0b16894fb28b67ddb41ddcb/node_modules/mongoose/node_modules/mongodb/node_modules/bson
remote:        > (node-gyp rebuild 2> builderror.log) || (exit 0)
remote:
remote:        make: Entering directory `/tmp/build_b2e25e89a0b16894fb28b67ddb41ddcb/node_modules/mongoose/node_modules/mongodb/node_modules/bson/build'
remote:          CXX(target) Release/obj.target/bson/ext/bson.o
remote:          SOLINK_MODULE(target) Release/obj.target/bson.node
remote:          SOLINK_MODULE(target) Release/obj.target/bson.node: Finished
remote:          COPY Release/bson.node
remote:        make: Leaving directory `/tmp/build_b2e25e89a0b16894fb28b67ddb41ddcb/node_modules/mongoose/node_modules/mongodb/node_modules/bson/build'
remote: remote:
remote:        express-jwt@0.1.4 node_modules/express-jwt
remote:
remote:        composable-middleware@0.3.0 node_modules/composable-middleware
remote:
remote:        method-override@1.0.2 node_modules/method-override
remote:        └── methods@1.0.0
remote:
remote:        serve-favicon@2.0.1 node_modules/serve-favicon
remote:        └── fresh@0.2.2
remote:
remote:        morgan@1.0.1 node_modules/morgan
remote:        └── bytes@0.3.0
remote:
remote:        cookie-parser@1.0.1 node_modules/cookie-parser
remote:        ├── cookie-signature@1.0.3
remote:        └── cookie@0.1.0
remote:
remote:        express-session@1.0.4 node_modules/express-session
remote:        ├── uid2@0.0.3
remote:        ├── utils-merge@1.0.0
remote:        ├── cookie@0.1.2
remote:        ├── cookie-signature@1.0.3
remote:        ├── debug@0.8.1
remote:        └── buffer-crc32@0.2.1
remote:
remote:        passport@0.2.1 node_modules/passport
remote:        ├── pause@0.0.1
remote:        └── passport-strategy@1.0.0
remote:
remote:        passport-local@0.1.6 node_modules/passport-local
remote:        ├── pkginfo@0.2.3
remote:        └── passport@0.1.18 (pause@0.0.1)
remote:
remote:        ejs@0.8.8 node_modules/ejs
remote:
remote:        compression@1.0.11 node_modules/compression
remote:        ├── vary@1.0.0
remote:        ├── on-headers@1.0.0
remote:        ├── bytes@1.0.0
remote:        ├── compressible@1.1.1
remote:        ├── debug@1.0.4 (ms@0.6.2)
remote:        └── accepts@1.0.7 (negotiator@0.4.7, mime-types@1.0.2)
remote:
remote:        jsonwebtoken@0.3.0 node_modules/jsonwebtoken
remote:        └── jws@0.2.6 (jwa@0.0.1, base64url@0.0.6)
remote:
remote:        socketio-jwt@2.3.5 node_modules/socketio-jwt
remote:        ├── xtend@2.1.2 (object-keys@0.4.0)
remote:        └── jsonwebtoken@1.1.2 (jws@0.2.6)
remote:
remote:        passport-google-oauth@0.1.5 node_modules/passport-google-oauth
remote:        ├── pkginfo@0.2.3
remote:        └── passport-oauth@0.1.15 (passport@0.1.18, oauth@0.9.12)
remote:
remote:        passport-twitter@1.0.3 node_modules/passport-twitter
remote:        ├── xtraverse@0.1.0 (xmldom@0.1.19)
remote:        └── passport-oauth1@1.0.1 (utils-merge@1.0.0, passport-strategy@1.0.0, oauth@0.9.12)
remote:
remote:        passport-facebook@2.0.0 node_modules/passport-facebook
remote:        └── passport-oauth2@1.1.2 (uid2@0.0.3, passport-strategy@1.0.0, oauth@0.9.12)
remote:
remote:        express@4.0.0 node_modules/express
remote:        ├── methods@0.1.0
remote:        ├── parseurl@1.0.1
remote:        ├── utils-merge@1.0.0
remote:        ├── merge-descriptors@0.0.2
remote:        ├── debug@0.8.1
remote:        ├── cookie-signature@1.0.3
remote:        ├── escape-html@1.0.1
remote:        ├── fresh@0.2.2
remote:        ├── qs@0.6.6
remote:        ├── range-parser@1.0.0
remote:        ├── buffer-crc32@0.2.1
remote:        ├── cookie@0.1.0
remote:        ├── path-to-regexp@0.1.2
remote:        ├── type-is@1.0.0 (mime@1.2.11)
remote:        ├── send@0.2.0 (mime@1.2.11)
remote:        ├── accepts@1.0.0 (mime@1.2.11, negotiator@0.3.0)
remote:        └── serve-static@1.0.1 (send@0.1.4)
remote:
remote:        body-parser@1.5.2 node_modules/body-parser
remote:        ├── bytes@1.0.0
remote:        ├── qs@0.6.6
remote:        ├── media-typer@0.2.0
remote:        ├── raw-body@1.3.0
remote:        ├── depd@0.4.4
remote:        ├── type-is@1.3.2 (mime-types@1.0.2)
remote:        └── iconv-lite@0.4.4
remote:
remote:        lodash@2.4.1 node_modules/lodash
remote:
remote:        socket.io-client@1.3.5 node_modules/socket.io-client
remote:        ├── to-array@0.1.3
remote:        ├── indexof@0.0.1
remote:        ├── component-bind@1.0.0
remote:        ├── debug@0.7.4
remote:        ├── backo2@1.0.2
remote:        ├── object-component@0.0.3
remote:        ├── component-emitter@1.1.2
remote:        ├── has-binary@0.1.6 (isarray@0.0.1)
remote:        ├── parseuri@0.0.2 (better-assert@1.0.2)
remote:        ├── socket.io-parser@2.2.4 (isarray@0.0.1, benchmark@1.0.0, json3@3.2.6)
remote:        └── engine.io-client@1.5.1 (component-inherit@0.0.3, debug@1.0.4, xmlhttprequest@1.5.0, parseqs@0.0.2, parsejson@0.0.1, parseuri@0.0.4, engine.io-parser@1.2.1, has-cors@1.0.3, ws@0.4.31)
remote:
remote:        socket.io@1.3.5 node_modules/socket.io
remote:        ├── debug@2.1.0 (ms@0.6.2)
remote:        ├── has-binary-data@0.1.3 (isarray@0.0.1)
remote:        ├── socket.io-adapter@0.3.1 (object-keys@1.0.1, debug@1.0.2, socket.io-parser@2.2.2)
remote:        ├── socket.io-parser@2.2.4 (isarray@0.0.1, debug@0.7.4, component-emitter@1.1.2, benchmark@1.0.0, json3@3.2.6)
remote:        └── engine.io@1.5.1 (base64id@0.1.0, debug@1.0.3, engine.io-parser@1.2.1, ws@0.5.0)
remote:
remote:        connect-mongo@0.4.2 node_modules/connect-mongo
remote:        └── mongodb@1.4.33 (readable-stream@1.0.33, kerberos@0.0.9, bson@0.2.19)
remote:
remote:        mongoose@3.8.24 node_modules/mongoose
remote:        ├── regexp-clone@0.0.1
remote:        ├── sliced@0.0.5
remote:        ├── muri@0.3.1
remote:        ├── hooks@0.2.1
remote:        ├── mpath@0.1.1
remote:        ├── mpromise@0.4.3
remote:        ├── ms@0.1.0
remote:        ├── mquery@0.8.0 (debug@0.7.4)
remote:        └── mongodb@1.4.31 (readable-stream@1.0.33, kerberos@0.0.9, bson@0.2.19)
remote:
remote: -----> Checking startup method
remote:        No Procfile; Adding 'web: npm start' to new Procfile
remote:
remote: -----> Finalizing build
remote:        Creating runtime environment
remote:        Exporting binary paths
remote:        Cleaning npm artifacts
remote:        Cleaning previous cache
remote:        Caching results for future builds
remote:
remote: -----> Build succeeded!
remote:
remote:        angular-fullstack@0.0.0 /tmp/build_b2e25e89a0b16894fb28b67ddb41ddcb
remote:        ├── body-parser@1.5.2
remote:        ├── composable-middleware@0.3.0
remote:        ├── compression@1.0.11
remote:        ├── connect-mongo@0.4.2
remote:        ├── cookie-parser@1.0.1
remote:        ├── ejs@0.8.8
remote:        ├── errorhandler@1.0.2
remote:        ├── express@4.0.0
remote:        ├── express-jwt@0.1.4
remote:        ├── express-session@1.0.4
remote:        ├── jsonwebtoken@0.3.0
remote:        ├── lodash@2.4.1
remote:        ├── method-override@1.0.2
remote:        ├── mongoose@3.8.24
remote:        ├── morgan@1.0.1
remote:        ├── passport@0.2.1
remote:        ├── passport-facebook@2.0.0
remote:        ├── passport-google-oauth@0.1.5
remote:        ├── passport-local@0.1.6
remote:        ├── passport-twitter@1.0.3
remote:        ├── serve-favicon@2.0.1
remote:        ├── socket.io@1.3.5
remote:        ├── socket.io-client@1.3.5
remote:        └── socketio-jwt@2.3.5
remote:
remote:        WARNING: Avoid semver ranges starting with '>' in engines.node
remote:        https://devcenter.heroku.com/articles/nodejs-support#specifying-a-node-js-version
remote:
remote: -----> Discovering process types
remote:        Procfile declares types -> web
remote:
remote: -----> Compressing... done, 17.4MB
remote: -----> Launching... done, v5
remote:        https://my-angular-fs.herokuapp.com/ deployed to Heroku
remote:
remote: Verifying deploy... done.
To https://git.heroku.com/my-angular-fs.git
 * [new branch]      master -> master
remote: Pushed to non-master branch, skipping build.
To https://git.heroku.com/my-angular-fs.git
 * [new tag]         0.0.0 -> 0.0.0

Done, without errors.


Execution Time (2015-03-04 04:47:05 UTC)
buildcontrol:heroku  1m 1.2s  ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 100%
Total 1m 1.3s


```





