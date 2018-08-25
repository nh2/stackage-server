stackage-server
===============

[![Build Status](https://travis-ci.org/fpco/stackage-server.svg?branch=master)](https://travis-ci.org/fpco/stackage-server)

Server for stable, curated Haskell package sets

This repo is part of the [Stackage project](https://github.com/fpco/stackage),
and the live server can be viewed at https://www.stackage.org.

postgresql://[user[:password]@][netloc][:port][/dbname][?param1=value1&...]

postgresql://postgres:password@localhost:5432/stackage

## Building locally

Build locally by passing the `dev` flag to it:

``` shellsession
$ stack build . --flag stackage-server:dev
```

Now, initially you need to run the cron job and create and populate the database:

``` shellsession
$ export PGSTRING=postgresql://postgres:password@localhost:5432/stackage
$ stack exec stackage-server-cron
```

Note that you need to modify the PGSTRING according to your actual database configuration. Also, you need to create an empty database before running the cron job.

After this, try running in the stackage server:

``` shellsession
$ export PGSTRING=postgresql://postgres:password@localhost:5432/stackage
$ stack exec stackage-server
```


