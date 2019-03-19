# problems

## 问题1： 执行npm install -g webpack 时，总是报错，然后为/usr/local/下面的所有文件赋予了读写权限，结果还是不行，一直报错，如下：
```
node-pre-gyp WARN Using needle for node-pre-gyp https download
node-pre-gyp WARN Pre-built binaries not installable for fsevents@1.2.7 and node@8.12.0 (node-v57 ABI, unknown) (falling back to source compilewith node-gyp)
node-pre-gyp WARN Hit error EACCES: permission denied, mkdir '/usr/local/lib/node_modules/webpack/node_modules/fsevents/lib'
gyp ERR! configure error
gyp ERR! stack Error: EACCES: permission denied, mkdir '/usr/local/lib/node_modules/webpack/node_modules/fsevents/build'
gyp ERR! System Darwin 18.0.0
gyp ERR! command "/usr/local/bin/node" "/usr/local/lib/node_modules/npm/node_modules/node-gyp/bin/node-gyp.js" "configure" "--fallback-to-build" "--module=/usr/local/lib/node_modules/webpack/node_modules/fsevents/lib/binding/Release/node-v57-darwin-x64/fse.node" "--module_name=fse" "--module_path=/usr/local/lib/node_modules/webpack/node_modules/fsevents/lib/binding/Release/node-v57-darwin-x64" "--napi_version=3" "--node_abi_napi=napi"
gyp ERR! cwd /usr/local/lib/node_modules/webpack/node_modules/fsevents
gyp ERR! node -v v8.12.0
gyp ERR! node-gyp -v v3.8.0
gyp ERR! not ok
node-pre-gyp ERR! build error
node-pre-gyp ERR! stack Error: Failed to execute '/usr/local/bin/node /usr/local/lib/node_modules/npm/node_modules/node-gyp/bin/node-gyp.js configure --fallback-to-build --module=/usr/local/lib/node_modules/webpack/node_modules/fsevents/lib/binding/Release/node-v57-darwin-x64/fse.node --module_name=fse --module_path=/usr/local/lib/node_modules/webpack/node_modules/fsevents/lib/binding/Release/node-v57-darwin-x64 --napi_version=3 --node_abi_napi=napi' (1)
node-pre-gyp ERR! stack     at ChildProcess.<anonymous> (/usr/local/lib/node_modules/webpack/node_modules/fsevents/node_modules/node-pre-gyp/lib/util/compile.js:83:29)
node-pre-gyp ERR! stack     at emitTwo (events.js:126:13)
node-pre-gyp ERR! stack     at ChildProcess.emit (events.js:214:7)
node-pre-gyp ERR! stack     at maybeClose (internal/child_process.js:915:16)
node-pre-gyp ERR! stack     at Process.ChildProcess._handle.onexit (internal/child_process.js:209:5)
node-pre-gyp ERR! System Darwin 18.0.0
node-pre-gyp ERR! command "/usr/local/bin/node" "/usr/local/lib/node_modules/webpack/node_modules/fsevents/node_modules/node-pre-gyp/bin/node-pre-gyp" "install" "--fallback-to-build"
node-pre-gyp ERR! cwd /usr/local/lib/node_modules/webpack/node_modules/fsevents
node-pre-gyp ERR! node -v v8.12.0
node-pre-gyp ERR! node-pre-gyp -v v0.10.3
node-pre-gyp ERR! not ok
Failed to execute '/usr/local/bin/node /usr/local/lib/node_modules/npm/node_modules/node-gyp/bin/node-gyp.js configure --fallback-to-build --module=/usr/local/lib/node_modules/webpack/node_modules/fsevents/lib/binding/Release/node-v57-darwin-x64/fse.node --module_name=fse --module_path=/usr/local/lib/node_modules/webpack/node_modules/fsevents/lib/binding/Release/node-v57-darwin-x64 --napi_version=3 --node_abi_napi=napi' (1)
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.7 (node_modules/webpack/node_modules/fsevents):
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.7 install: `node install`
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: Exit status 1

```

## 解决方式：执行如下命令，则成功了：
```
npm install -g webpack --unsafe-perm=true --allow-root
```

## 重点在--unsafe-perm=true --allow-root
