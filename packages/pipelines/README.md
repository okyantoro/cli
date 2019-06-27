pipelines
=========



[![oclif](https://img.shields.io/badge/cli-oclif-brightgreen.svg)](https://oclif.io)
[![Version](https://img.shields.io/npm/v/pipelines.svg)](https://npmjs.org/package/pipelines)
[![Downloads/week](https://img.shields.io/npm/dw/pipelines.svg)](https://npmjs.org/package/pipelines)
[![License](https://img.shields.io/npm/l/pipelines.svg)](https://github.com/chadian/pipelines/blob/master/package.json)

<!-- toc -->
* [Usage](#usage)
* [Commands](#commands)
<!-- tocstop -->
# Usage
<!-- usage -->
```sh-session
$ npm install -g @heroku-cli/plugin-pipelines
$ heroku COMMAND
running command...
$ heroku (-v|--version|version)
@heroku-cli/plugin-pipelines/0.0.0 darwin-x64 node-v8.11.2
$ heroku --help [COMMAND]
USAGE
  $ heroku COMMAND
...
```
<!-- usagestop -->
# Commands
<!-- commands -->
* [`heroku pipelines`](#heroku-pipelines)
* [`heroku pipelines:add PIPELINE`](#heroku-pipelinesadd-pipeline)
* [`heroku pipelines:create [NAME]`](#heroku-pipelinescreate-name)
* [`heroku pipelines:setup [FILE]`](#heroku-pipelinessetup-file)

## `heroku pipelines`

list pipelines you have access to

```
USAGE
  $ heroku pipelines

OPTIONS
  --json  output in json format

EXAMPLE
  $ heroku pipelines
  === My Pipelines
  example
  sushi
```

_See code: [src/commands/pipelines/index.ts](https://github.com/chadian/pipelines/blob/v0.0.0/src/commands/pipelines/index.ts)_

## `heroku pipelines:add PIPELINE`

add this app to a pipeline

```
USAGE
  $ heroku pipelines:add PIPELINE

ARGUMENTS
  PIPELINE  name of pipeline

OPTIONS
  -a, --app=app        (required) app to run command against
  -r, --remote=remote  git remote of app to use
  -s, --stage=stage    stage of first app in pipeline

DESCRIPTION
  The app and pipeline names must be specified.
  The stage of the app will be guessed based on its name if not specified.

EXAMPLE
  $ heroku pipelines:add example -a example-admin -s production
  Adding example-admin to example pipeline as production... done
```

_See code: [src/commands/pipelines/add.ts](https://github.com/chadian/pipelines/blob/v0.0.0/src/commands/pipelines/add.ts)_

## `heroku pipelines:create [NAME]`

'create a new pipeline

```
USAGE
  $ heroku pipelines:create [NAME]

ARGUMENTS
  NAME  name of pipeline, defaults to basename of app

OPTIONS
  -a, --app=app        (required) app to run command against
  -r, --remote=remote  git remote of app to use
  -s, --stage=stage    stage of first app in pipeline
  -t, --team=team      the team which will own the apps (can also use --org)

DESCRIPTION
  An existing app must be specified as the first app in the pipeline.
     The pipeline name will be inferred from the app name if not specified.
     The stage of the app will be guessed based on its name if not specified.
     The pipeline owner will be the user creating the pipeline if not specified with -t for teams or -o for orgs.

EXAMPLE
  $ heroku pipelines:create -a example-staging
  ? Pipeline name: example
  ? Stage of example-staging: staging
  Creating example pipeline... done
  Adding example-staging to example pipeline as staging... done
```

_See code: [src/commands/pipelines/create.ts](https://github.com/chadian/pipelines/blob/v0.0.0/src/commands/pipelines/create.ts)_

## `heroku pipelines:setup [FILE]`

describe the command here

```
USAGE
  $ heroku pipelines:setup [FILE]

OPTIONS
  -f, --force
  -h, --help       show CLI help
  -n, --name=name  name to print
```

_See code: [src/commands/pipelines/setup.ts](https://github.com/chadian/pipelines/blob/v0.0.0/src/commands/pipelines/setup.ts)_
<!-- commandsstop -->
