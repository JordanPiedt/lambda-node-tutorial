# lambda-node-tutorial

## Serverless Local

### Install
Inside your project's `serverless.yml` file add following entry to the plugins section: `serverless-offline`. If there is no plugin section you will need to add it to the file.

It should look something like this:

```YAML
plugins:
  - serverless-offline
```

### Usage and command line options

In your project root run:

`serverless offline start` or `sls offline start`.

to list all the options for the plugin run:

`sls offline --help`

All CLI options are optional:

```
--prefix                -p  Adds a prefix to every path, to send your requests to http://localhost:3000/[prefix]/[your_path] instead. E.g. -p dev
--location              -l  The root location of the handlers' files. Defaults to the current directory
--host                  -o  Host name to listen on. Default: localhost
--port                  -P  Port to listen on. Default: 3000
--stage                 -s  The stage used to populate your templates. Default: the first stage found in your project.
--region                -r  The region used to populate your templates. Default: the first region for the first stage found.
--noTimeout             -t  Disables the timeout feature.
--noEnvironment             Turns off loading of your environment variables from serverless.yml. Allows the usage of tools such as PM2 or docker-compose.
--resourceRoutes            Turns on loading of your HTTP proxy settings from serverless.yml.
--dontPrintOutput           Turns off logging of your lambda outputs in the terminal.
--httpsProtocol         -H  To enable HTTPS, specify directory (relative to your cwd, typically your project dir) for both cert.pem and key.pem files.
--skipCacheInvalidation -c  Tells the plugin to skip require cache invalidation. A script reloading tool like Nodemon might then be needed.
--corsAllowOrigin           Used as default Access-Control-Allow-Origin header value for responses. Delimit multiple values with commas. Default: '*'
--corsAllowHeaders          Used as default Access-Control-Allow-Headers header value for responses. Delimit multiple values with commas. Default: 'accept,content-type,x-api-key'
--corsExposedHeaders        Used as additional Access-Control-Exposed-Headers header value for responses. Delimit multiple values with commas. Default: 'WWW-Authenticate,Server-Authorization'
--corsDisallowCredentials   When provided, the default Access-Control-Allow-Credentials header value will be passed as 'false'. Default: true
--exec "<script>"           When provided, a shell script is executed when the server starts up, and the server will shut down after handling this command.
--noAuth                    Turns off all authorizers
--preserveTrailingSlash     Used to keep trailing slashes on the request path
```

Any of the CLI options can be added to your `serverless.yml`. For example:

```
custom:
  serverless-offline:
    httpsProtocol: "dev-certs"
    port: 4000
```

Options passed on the command line override YAML options.

## Deploy Commands

1. **Deploy a Service:**

  Use this when you have made changes to your Functions, Events or Resources in `serverless.yml` or you simply want to deploy all changes within your Service at the same time.
  ```bash
  serverless deploy -v
  ```

2. **Deploy the Function:**

  Use this to quickly upload and overwrite your AWS Lambda code on AWS, allowing you to develop faster.
  ```bash
  serverless deploy function -f hello
  ```

3. **Invoke the Function:**

  Invokes an AWS Lambda Function on AWS and returns logs.
  ```bash
  serverless invoke -f hello -l
  ```

4. **Fetch the Function Logs:**

  Open up a separate tab in your console and stream all logs for a specific Function using this command.
  ```bash
  serverless logs -f hello -t
  ```

5. **Remove the Service:**

  Removes all Functions, Events and Resources from your AWS account.
  ```bash
  serverless remove
  ```