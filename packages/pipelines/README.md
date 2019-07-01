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
* [`heroku pipelines:open [FILE]`](#heroku-pipelinesopen-file)
* [`heroku pipelines:setup [NAME] [REPO]`](#heroku-pipelinessetup-name-repo)

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

## `heroku pipelines:open [FILE]`

describe the command here

```
USAGE
  $ heroku pipelines:open [FILE]

OPTIONS
  -f, --force
  -h, --help       show CLI help
  -n, --name=name  name to print
```

_See code: [src/commands/pipelines/open.ts](https://github.com/chadian/pipelines/blob/v0.0.0/src/commands/pipelines/open.ts)_

## `heroku pipelines:setup [NAME] [REPO]`

bootstrap a new pipeline with common settings and create a production and staging app (requires a fully formed app.json in the repo)

```
USAGE
  $ heroku pipelines:setup [NAME] [REPO]

ARGUMENTS
  NAME  name of pipeline
  REPO  a GitHub repository to connect the pipeline to

OPTIONS
  -t, --team=team  the team which will own the apps (can also use --org)
  -y, --yes        accept all default settings without prompting

EXAMPLE
  $ heroku pipelines:setup example githuborg/reponame -o example-org
  ? Automatically deploy the master branch to staging? Yes
  ? Wait for CI to pass before deploying the master branch to staging? Yes
  ? Enable review apps? Yes
  ? Automatically create review apps for every PR? Yes
  ? Automatically destroy idle review apps after 5 days? Yes
  ? Enable automatic Heroku CI test runs? Yes
  Creating pipeline... done
  Linking to repo... done
  Creating production and staging apps (⬢ example and ⬢ example-staging)
  Configuring pipeline... done
  View your new pipeline by running `heroku pipelines:open e5a55ffa-de3f-11e6-a245-3c15c2e6bc1e`
```

_See code: [src/commands/pipelines/setup.ts](https://github.com/chadian/pipelines/blob/v0.0.0/src/commands/pipelines/setup.ts)_
<!-- commandsstop -->
