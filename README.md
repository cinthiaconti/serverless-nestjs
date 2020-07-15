# serverless-nestjs

## How to use

### Cloud provider credential

Create the file .aws/credentials in your user root directory with the following content:

```
[default]
aws_access_key_id = YOUR_ACCESS_KEY
aws_secret_access_key = YOUR_SECRET_ACCESS_KEY
```

### Prepare

```
$ npm install @nestjs/cli serverless -g
$ git clone git@github.com:cinthiaconti/serverless-nestjs.git 【projectName】
$ cd 【projectName】
$ npm install
$ npm start
```

### Development

#### use NestCLI

```
$ npm start
```

```
$ npm start
> serverless-nestjs@0.0.0 start /Users/sakakibara/dev/serverless-nestjs
> nest start

[Nest] 41075   - 2020-07-15, 6:19:24 p.m.   [NestFactory] Starting Nest application...
[Nest] 41075   - 2020-07-15, 6:19:24 p.m.   [InstanceLoader] AppModule dependencies initialized +24ms
[Nest] 41075   - 2020-07-15, 6:19:24 p.m.   [RoutesResolver] AppController {/}: +9ms
[Nest] 41075   - 2020-07-15, 6:19:24 p.m.   [RouterExplorer] Mapped {/, GET} route +3ms
[Nest] 41075   - 2020-07-15, 6:19:24 p.m.   [NestApplication] Nest application successfully started +2m
```

Then browse http://localhost:3000

#### use serverless-offline

**after also doing an: `npm run build`**

```bash
$ sls offline
```

```
$ sls offline
Serverless: Starting Offline: dev/us-east-1.

Serverless: Routes for index:
Serverless: ANY /
Serverless: ANY /{proxy*}

Serverless: Offline listening on http://localhost:3000
```

Then browse http://localhost:3000

## How to Deploy

```bash
$ npm run prebuild && sls deploy
```

## Options

### Hot start

See : https://serverless.com/blog/keep-your-lambdas-warm/

These behavior can be fixed with the plugin serverless-plugin-warmup

1 Install the plugin

```
$ npm install serverless-plugin-warmup --save-dev
```

2 Enable the plugin

```
plugins:
  - '@hewmen/serverless-plugin-typescript'
  - serverless-plugin-optimize
  - serverless-offline
  - serverless-plugin-warmup

custom:
  # Enable warmup on all functions (only for production and staging)
  warmup:
      - production
      - staging
```

Resources:
https://blog.theodo.com/2019/06/deploy-a-nestjs-app-in-5-minutes-with-serverless-framework/
