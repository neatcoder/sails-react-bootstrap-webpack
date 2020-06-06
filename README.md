# sails-react-bootstrap-webpack

This is an opinionated base [Sails v1](https://sailsjs.com) application, using Webpack to handle Bootstrap (SASS) and React.

## Main Features

+ [Automatic (incoming) request logging, via Sails models / hooks.](#request-logging)
+ [Setup for Webpack auto-reload dev server.](#local-dev)
+ Setup so Sails will serve Webpack-built bundles as separate apps (so, a marketing site, and an admin site can live side-by-side).
+ Includes [react-bootstrap](https://www.npmjs.com/package/react-bootstrap) to make using Bootstrap styles / features with React easier.

### Request Logging
Automatic incoming request logging, is a 2 part process. First, the [`request-logger` hook](api/hooks/request-logger.js) gathers info from the quest, and creates a new [`RequestLog` record](api/models/RequestLog.js), making sure to mask anything that may be sensitive, such as passwords. Then, a custom response gathers information from the response, again, scrubbing sensitive data (using the [customToJSON](https://sailsjs.com/documentation/concepts/models-and-orm/model-settings?identity=#customtojson) feature of Sails models) to prevent leaking of password hashes, or anything else that should never be publicly accessible. The [`keepModelsSafe` helper](api/helpers/keep-models-safe.js) and the custom responses (such as [ok](api/responses/ok.js) or [serverError](api/responses/serverError.js)) are responsible for the final leg of request logs.

### Using Webpack
#### Local Dev
The script `npm run open:client` will start the auto-reloading Webpack development server, and open a browser window.

#### Remote Builds
The script `npm run build` will make Webpack build all the proper assets into the `.tmp` folder. Sails will serve assets from this folder.

If you want to build assets, but retain spaces / tabs for debugging, you can use `npm run build:dev`.

### Links

+ [Sails Framework Documentation](https://sailsjs.com/get-started)
+ [Sails Deployment Tips](https://sailsjs.com/documentation/concepts/deployment)
+ [Sails Community Support Options](https://sailsjs.com/support)
+ [Sails Professional / Enterprise Options](https://sailsjs.com/enterprise)


### Version info

This app was originally generated on Fri Mar 20 2020 17:39:04 GMT-0500 (Central Daylight Time) using Sails v1.2.3.

<!-- Internally, Sails used [`sails-generate@1.16.13`](https://github.com/balderdashy/sails-generate/tree/v1.16.13/lib/core-generators/new). -->



<!--
Note:  Generators are usually run using the globally-installed `sails` CLI (command-line interface).  This CLI version is _environment-specific_ rather than app-specific, thus over time, as a project's dependencies are upgraded or the project is worked on by different developers on different computers using different versions of Node.js, the Sails dependency in its package.json file may differ from the globally-installed Sails CLI release it was originally generated with.  (Be sure to always check out the relevant [upgrading guides](https://sailsjs.com/upgrading) before upgrading the version of Sails used by your app.  If you're stuck, [get help here](https://sailsjs.com/support).)
-->

