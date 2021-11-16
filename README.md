# Missing stack traces in Nestjs 8.1.4 + nestjs-pino@2.3.0

I created two NestJS projects Nestjs 7.6 + `nestjs-pino@1.4.0` and Nestjs 8.1.4 + `nestjs-pino@2.3.0` and modified `app.controller.ts` to throw an error.

## Nestjs 7.6 + nestjs-pino@1.4.0
```
$ nest start
$ curl localhost:3007
```

Error log contains stack trace:
```
{"level":50,"time":1637054527569,"pid":88250,"hostname":"raidok","req":{"id":1,"method":"GET","url":"/","query":{},"params":{"0":""},"headers":{"host":"localhost:3007","user-agent":"curl/7.68.0","accept":"*/*"},"remoteAddress":"::ffff:127.0.0.1","remotePort":35738},"context":"ExceptionsHandler","trace":"Error: I want to log this error\n    at AppController.getHello (/tmp/tmp.xWHmFKglWp/nestjs-pino-issue/nest7/dist/app.controller.js:20:15)\n    at /tmp/tmp.xWHmFKglWp/nestjs-pino-issue/nest7/node_modules/@nestjs/core/router/router-execution-context.js:38:29\n    at InterceptorsConsumer.intercept (/tmp/tmp.xWHmFKglWp/nestjs-pino-issue/nest7/node_modules/@nestjs/core/interceptors/interceptors-consumer.js:11:20)\n    at /tmp/tmp.xWHmFKglWp/nestjs-pino-issue/nest7/node_modules/@nestjs/core/router/router-execution-context.js:46:60\n    at /tmp/tmp.xWHmFKglWp/nestjs-pino-issue/nest7/node_modules/@nestjs/core/router/router-proxy.js:9:23\n    at Layer.handle [as handle_request] (/tmp/tmp.xWHmFKglWp/nestjs-pino-issue/nest7/node_modules/express/lib/router/layer.js:95:5)\n    at next (/tmp/tmp.xWHmFKglWp/nestjs-pino-issue/nest7/node_modules/express/lib/router/route.js:137:13)\n    at Route.dispatch (/tmp/tmp.xWHmFKglWp/nestjs-pino-issue/nest7/node_modules/express/lib/router/route.js:112:3)\n    at Layer.handle [as handle_request] (/tmp/tmp.xWHmFKglWp/nestjs-pino-issue/nest7/node_modules/express/lib/router/layer.js:95:5)\n    at /tmp/tmp.xWHmFKglWp/nestjs-pino-issue/nest7/node_modules/express/lib/router/index.js:281:22","msg":"I want to log this error"}
```


## Nestjs 8.1.4 + nestjs-pino@2.3.0
```
$ nest start
$ curl localhost:3008
```

Error log does not contain stack trace:
```
{"level":50,"time":1637054552021,"pid":88405,"hostname":"raidok","req":{"id":1,"method":"GET","url":"/","query":{},"params":{"0":""},"headers":{"host":"localhost:3008","user-agent":"curl/7.68.0","accept":"*/*"},"remoteAddress":"::ffff:127.0.0.1","remotePort":49020},"context":"ExceptionsHandler","msg":"I want to log this error"}
```
