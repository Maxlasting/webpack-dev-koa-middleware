# webpack-dev-koa-middleware

> The dev middleware for webpack 4.x

How to use ?

```
const koaDevMiddleware = require('webpack-dev-koa-middleware')

const config = {} // your's webpack config

const compiler = webpack(config)

const devMiddleware = koaDevMiddleware(compiler, {
  publicPath: clientConfig.output.publicPath,
  logLevel: 'silent'
})

compiler.plugin('done', (stats) => {
  // stats and errors code ...
  
  // for example: vue ssr ready manifest to memoryfs
  clientManifest = JSON.parse(readFile(
    // Here, you can use the fileSystem
    devMiddleware.fileSystem,
    'vue-ssr-client-manifest.json'
  ))
  
  update()
})

app.use(devMiddleware.middleware)
```